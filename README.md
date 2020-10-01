# chell_audio
Guide to working Linux audio on Chromebook hardware `CAROLINE, CHELL, SENTRY`. Tested on Arch Linux 5.8 kernel and Debian Buster.

## Requirements

  - You need the kernel module `snd_soc_skl` available and loaded. You can check with `lsmod snd_soc_skl`. This commonly is already built into your kernel; on Ubuntu, try installing `linux-modules-extra`, otherwise you will need to build it from source using the configuration item `CONFIG_SND_SOC_INTEL_SKYLAKE`
  - Some have reported issues with intel_iommu using this firmware, if you don't need it disable it in your bootloader. 
  - Clone this repo: `git clone https://github.com/iofq/chell_audio`
  - Optional but recommended: package `acpid` for auto-detecting headphone plug events. 
    - Installed by default on Ubuntu 12.04+.
    - On Arch, `pacman -S acpid && systemctl enable --now acpid`

## Steps:
  
Copy the contents of the `firmware` directory into /lib/firmware:
```bash
sudo cp -r firmware/ /lib/firmware/
```
Copy the contents of the `ucm2` directory into /usr/share/alsa/ucm2:
```bash
sudo cp -r ucm2/ /usr/share/alsa/ucm2/
```
Copy the contents of the `modprobe.d` directory into /etc/modprobe.d:
```bash
sudo cp modprobe.d/* /etc/modprobe.d/
```
Copy the contents of the `incoming/acpi` directory into /etc/acpi/:
```bash
sudo cp -r * incoming/acpi /etc/acpi/
```
At this point, after a reboot you should have working audio! Volume can be set with `amixer set Master 50% unmute` and headphone<->speaker detection should work.

## Sources:
[This github issue](https://github.com/GalliumOS/galliumos-distro/issues/379#issuecomment-415823541) is the main source of all work done on this issue. If this guide didn't work, start here. Mad props to everyone over at GalliumOS.
Also thank you to [metaquanta](https://github.com/metaquanta) for compiling the necessary files into a repository. 
