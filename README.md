*This package is very the much the definition of throwing shit at the wall and seeing what sticks*. Try at your own risk.

The package is based on the original [ricoh-e823-fix](https://github.com/aur-archive/ricoh-e823-fix/), but while the aim of that is to have your SD card reader working after resuming ("recent" kernels do this automatically, which is why the original package hasn't been needed for a long time), the aim of this is to *try* and turn it off. Tested on only one X230 for a day: mine. I wouldn't use this on any other laptop.

Anecdotally speaking, I've seen people observe that in Windows, the Ricoh card reader siphons huge amounts of power until its driver is installed. I have only a hunch, but I suspect it's one of the reasons of my poor battery life with my X230 in Linux.

[`e823fix.wrapper`](https://github.com/qwerty12/ricoh-e823-fix/blob/main/e823fix.wrapper) is a script that attempts the following:

* Disabling PCIe extended tags on the Ricoh SD card reader, 'cause why not

* Disabling PCIe Fatal Error Reporting on the Ricoh SD card reader

* Disables the MMC controller if enabled (the sdhci module does this). ThinkPads don't actually need this, but may as well check for it so as to disable another thing

* Sets the SD base clock frequency to 50 MHz (as per sdhci)

    * And then tries for 1 MHz 🤷‍♂️

* If active, stops the Ricoh from claiming BusMaster status. Also, I think, removes its ability to write to memory

* Disables PME-Enable (gets enabled when resuming from suspend). AFAIK, this relates to the ability to wake your device up from sleep. Not sure.

* Puts the Ricoh device into D3hot which, theoretically, should mostly power it down

* Tries to power off the PCIe root port the Ricoh is connected to (this is very much guesswork...)

The `remove` writes aren't attempted because it stops the script from working on resume.

This package also installs a modprobe.d.conf that prevents `modprobe` from loading the sdhci module. If you have this installed, there's no point to it loading - and it might interfere.

You may as well disable the device in the BIOS too, but note it doesn't (on the surface) appear to do anything. If you have 1vyrain flashed (and if you're not into coreboot, you should!), you can disable the root port but then the BIOS will also disable root port 2, which means your Wi-Fi goes bye bye. You can use 1vyrain to enforce maximum power saving and Gen1 speed on root port 1, however.

`makepkg -si && sudo systemctl enable e823fix`