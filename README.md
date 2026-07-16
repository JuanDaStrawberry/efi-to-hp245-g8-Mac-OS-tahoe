# efi-to-hp245-g8-Mac-OS-tahoe

## EFI

OpenCore EFI files for my laptop, designed for use with macOS Tahoe (though they should work with earlier versions, Ventura and later). Remember to generate a smbios; this EFI file is empty in that section.

## Specifications

CPU: AMD Ryzen 5 5500U (6 cores, 12 threads)
GPU: iGPU, 4 GB VRAM (changed with Smokeless_UMAF)
RAM: 1 x 16 GB DDR4 module at 3200 MHz and 1 x 4 GB DDR4 module at 3200 MHz
Wi-Fi/Bluetooth: Realtek RTL8822CE
SSD: Kingston SNV2S/1000G

## Features:
Wi-Fi and Bluetooth (Wi-Fi will be fixed later with rt88.kext)
Ethernet
All USB ports
Speakers
Audio (patched with mykextinstaller)
Sleep mode
Keyboard
Touchpad
iGPU (not compatible with Electron, Steam, Chrome, Spotify, and other Electron-based apps. They require...) Disable hardware acceleration)
iServices

## Features that don't work:
AirDrop
Hardware DRM/VCN (I use Mozilla for streaming apps)
Keyboard mute LED
Most Continuity features (the only ones that seem to work are Universal Clipboard and Handoff)


macOS Tahoe is quite unstable, although the injection order of some kexts seems incorrect or out of order, it's actually the one I personally found most efficient.

## Installation guide: 
Install macOS with Secure Boot disabled, as it comes with this EFI. PLEASE INSTALL WITHOUT INTERNET CONNECTION. During the initial macOS setup, create a local account; do not log in to your iCloud account. This will display the File Vault tab. DO NOT ACTIVATE FILE VAULT (it's very problematic to activate it).

Once macOS is installed, place the EFI in its corresponding location. You can now connect to the internet and log in with your iCloud account. Log in, and it will ask for the password of your other Apple device to decrypt iCloud. Enter it, let the process fail, and it will say it forgot the password and add it later. Now mount your EFI partition and edit its config.plist file. Enable Secure Boot (in this case, the value is j214k). (MacbookPro16,2) Restart your system, then return to the Apple Account settings tab. Try syncing iCloud again, this time entering the password from your other Apple device. This should succeed. This process will enable iServices.

If File Vault is not active, start your Apple Account without Secure Boot and then sync it with Secure Boot enabled. For some reason, this will make Universal Clipboard and Handoff work.

Fixing Wi-Fi: To fix Wi-Fi, you need to download rt88kext. It's not included in this EFI because if it were, the EN0 value would be used by this kext, causing problems with the initial activation of iServices. Once iServices are activated, you can install this kext.

Fixing Audio: macOS Tahoe removed Apple HDA audio support. You can repair it with MyKext Installer (this requires disabling Secure Boot again; iServices will continue to work, don't worry). Alternatively, you can use VoodooHDAkext if you prefer. Keep Secure Boot enabled. I don't recommend using Voodoo because the audio quality is lower and it sounds strange.

amdpowermanagemetkext: Many EFIS include it, but in this case, it's not included because the system works quite well. Although there's a slight improvement in battery life (very minimal) with the implementation of this kext, I see a significant impact on Wi-Fi performance. You can try it, and if you don't detect any instability, use it.

Remember to make a backup of your EFI before adding any kexts or other things. Be very careful when altering the kext injection order; it's really easy to cause problems.

If you want to dual-boot, create an exFAT partition from macOS and then install Windows normally. Using Boot Camp might not work or could break everything.

I prefer to have eight operating systems installed. I prefer and recommend using Refind. OpenCore can cause conflicts when loading multiple systems. I personally prefer that OpenCore only load macOS.
