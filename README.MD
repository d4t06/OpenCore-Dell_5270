## Opencore  1.03
## MacOS 10.15 Catalina
This Opencore follow [Dortina guide.](https://dortania.github.io/OpenCore-Install-Guide/ "Dortina guide.")
Also work with **High Sierra 10.13** but i switched to 10.15 to use node v20.
## Super Ultra Ultimate Pro Max Very Important advices
- Back up our **EFI** folder before install
- Don't use youtube tutorials use Dortina docs instead

#### Making use installer
There are to way for you to make the installer
- Use recovery.dmg: For small usb (4GB), but in installing step require internet to download Mac OS (I have ethernet cable, I don't know wifi is working in this step or not)
- Burn MacOs image to usb: For larger usb, use tool likes rufus, etcher..., 8GB is enought for High Sierra, others need above.

#### Working
- **Except Wifi**: Because my wireless card not supported, I use  Realtek usb dongle, driver link [here](https://www.tp-link.com/us/support/download/tl-wn725n/v3.6/ "here") 
- ...

#### Boot Opencore from Ubuntu grub
Add this boot entry to /boot/grub/grub.cfg
Change (hd_,gpt_) with your own

```shell
menuentry 'MacOS' $menuentry_id_option 'macOS-efi' {
	insmod chain
	insmod part_gpt
	insmod fat
	set root=(hd_,gpt_)
	chainloader /EFI/Mac/OC/OpenCore.efi
	set root=(hd_,gpt_)/EFI	/Mac
}

```
