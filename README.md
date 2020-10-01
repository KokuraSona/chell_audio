# chell_audio
Guide to working Linux audio on Chromebook hardware "CAROLINE, CHELL, SENTRY". Tested on Arch Linux 5.8 kernel and Debian Buster.

## Requirements

  - You need the kernel module `snd_soc_skl` available and loaded. This commonly is already built into your kernel; if not you will need to build it from source using the configuration item `CONFIG_SND_SOC_INTEL_SKYLAKE`
  - Clone this repo: `git clone https://github.com/iofq/chell_audio`

## Steps:
  
  Copy the contents of the `firmware` folder into /lib/firmware
  ```bash
  sudo cp -r firmware/ /lib/firmware/
  ```



## Config:
Configuration can be made by editing the `config` file. The defaults are set by the script and any changes will override them.

