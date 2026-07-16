# efi-to-hp245-g8-Mac-OS-tahoe

EFI

OpenCore EFI files for my laptop, designed for use with macOS Tahoe (though they should work with earlier versions, Ventura and later). Remember to generate a smbios; this EFI file is empty in that section.

Specifications

CPU: AMD Ryzen 5 5500U (6 cores, 12 threads)
GPU: iGPU, 4 GB VRAM (changed with Smokeless_UMAF)
RAM: 1 x 16 GB DDR4 module at 3200 MHz and 1 x 4 GB DDR4 module at 3200 MHz
Wi-Fi/Bluetooth: Realtek RTL8822CE
SSD: Kingston SNV2S/1000G

Features:
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

Features that don't work:
AirDrop
Hardware DRM/VCN (I use Mozilla for streaming apps)
Keyboard mute LED
Most Continuity features (the only ones that seem to work are Universal Clipboard and Handoff)
