# Netgear M4100 Switch Recovery (Locked, Used Enterprise Switch)

**Tags:** #networking #serial-console #bootloader #tftp #homelab

> **Guided lab.** I did every step hands-on, with step-by-step guidance. I understand what each step does and why, but I would want a runbook or a senior engineer on hand before doing this on a production switch.

## Objective

Recover a used Netgear ProSafe M4100-50G-POE+ managed switch that was still locked with the previous owner's credentials, and return it to a clean factory configuration for lab use.

## Environment

- Switch: Netgear ProSafe M4100-50G-POE+ (bought used, locked)
- Workstation: Windows 11 desktop running PuTTY and Tftpd64
- Console: Mini-USB console port (label on the switch: `115200,N,8,1`)
- Link: direct Ethernet from the workstation to copper combo port 49T on an isolated 192.168.0.0/24 subnet
- Firmware: Netgear M4100 image `m4100v10.0.2.35.stk`

## Steps

### 1. Establish a serial console

- Identified the console port as **Mini-USB, not DB9**, from the label on the switch. The label also gave the serial settings: 115200 baud, no parity, 8 data bits, 1 stop bit.
- Device Manager would not install the USB-to-serial driver, so I installed the Silicon Labs CP210x driver from the command line:

```cmd
pnputil /add-driver <path-to-driver>.inf /install
```

- Opened a PuTTY serial session on `COM3` at `115200`.

### 2. Break into the bootloader

Power-cycled the switch and pressed `Ctrl+C` during boot to drop into the **CFE (Common Firmware Environment)** prompt. CFE is the low-level bootloader that runs before the switch operating system, similar to BIOS on a PC.

### 3. Network-boot clean firmware over TFTP

- Ran **Tftpd64** on the workstation at `192.168.0.100`, serving the firmware renamed to `os.bin`.
- Configured the switch's boot interface and booted the image over the network:

```text
ifconfig eth0 -addr=192.168.0.238 -mask=255.255.255.0 -gw=192.168.0.254
boot -stk 192.168.0.100:os.bin
```

The firmware loaded, but the switch still read the old configuration from flash, so the previous credentials were still in place.

### 4. Reset credentials and wipe the configuration

- Rebooted and pressed `2` to open the boot menu, then chose **option 13: Password Recovery Procedure** and set new credentials.
- Wiped the old configuration and reloaded:

```text
erase startup-config
reload
```

- Confirmed a clean login at the `(M4100-50G-POE+) >` prompt with factory default credentials.

## Troubleshooting Along the Way

| Problem | Cause | Fix |
| --- | --- | --- |
| No console output | Wrong serial settings assumed | Read the baud rate off the switch label (115200, not 9600) |
| Boot variables gone | I ran `clearenv` in CFE, which wiped them | Booted manually over TFTP instead of from flash |
| TFTP requests timing out | Tftpd64 had switched to listening on `127.0.0.1` (loopback) | Bound Tftpd64 back to the Ethernet interface at `192.168.0.100` |
| Windows Explorer wouldn't remove the `.txt` extension from a config file | Explorer rename limits | Renamed from an admin command prompt with `ren` |
| Old credentials survived a clean firmware boot | Network boot replaced only the running image; the saved configuration on flash still loaded (`printenv` showed images on `flash2.stk1` / `flash2.stk2`) | Password Recovery menu, then `erase startup-config` |

## Lessons Learned

- **Read the hardware.** The label on the switch had the right console settings; my assumption didn't.
- **Firmware and configuration are separate.** Reflashing the operating system doesn't wipe credentials stored in the config.
- **Know what a command does before you run it in a bootloader.** `clearenv` cost me the boot variables.
- **Check the server side too.** The TFTP timeout was the server listening on the wrong interface, not the switch.

## Outcome

Switch fully recovered and used as the core lab switch. It has since been retired and replaced with a Cisco Catalyst 3560G.
