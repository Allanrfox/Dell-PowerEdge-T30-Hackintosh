# Dell-PowerEdge-T30-Hackintosh
![Capture d’écran 2021-09-06 à 12 09 49 PM](https://user-images.githubusercontent.com/76212533/132251588-ee22b022-3e5a-4df9-98f5-b292feb06e38.png)

Another one of my Opencore archives

As stated in the X1 Carbon repo this is an effort of mine to actively backup my EFIs, you're free to use them though I can't garantuee all features will work (Even if we have the exact same hardware)

Yes I own a Skylake Dell Server that retails for 999USD (last time i checked), obviously I have no love life, but that doesnt impeed me from having a flexible and an overall great experience on this machine 

# My Specs

| Part        | Model Number
| ---         | ---
| CPU         | Intel(R) Xeon(R) CPU E3-1225 v5 @ 3.30GHz (Quad Core)
| PSU         | Stock Factory Dell PSU
| Motherboard | Dell 07T4MC
| BIOS        | 1.6.0
| Chipset     | Intel C236
| Memory      | Samsung 2133Mhz ECC RAM (2x8GB)
| GPU         | Intel HD P530 iGPU
| Monitor     | Dell D2015H
| Storage     | Samsung SSD 860 EVO 500GB
|             | Toshiba MQ01ABD100 1TB HDD
| Ethernet    | Intel I219LM2 (onboard)
| USB         | Intel 100 Series/C230 Series USB 3.00 xHCI Controller
| Sound       | Realtek ALC899 (Layout ID: 3)
| Keyboard    | Apple USB Keyboard Model A1243
| Mouse       | Dell Mouse of which I don't know the model
| Bootloader  | Opencore 0.7.3

# Tested in
Tested Big Sur 11.0.1 up to 11.6 (update, I have managed to fix the Issue and it just requires to raise DVMT Preallocated memory and DVMT Total Gfx Memory to MAX  using a modified grub shell Huge thanks to cstrouse for documenting this on his repo)

![Capture d’écran 2021-09-27 à 3 48 39 PM](https://user-images.githubusercontent.com/76212533/134996825-70455c19-71ca-4919-9be1-c8b2745bdb4f.png)


I have no WiFI card/BT card so no continuity but as far as testing the following features work 

# What works
Sidecar
iServices (including iMessage, FaceTime does recieve calls but since I don’t have a mic or camera plugged in I really can’t use it)
Sleep
USB
All sensors work under macOS

# What kinda works.
Audio (this machine has 4 audio jacks and well only 2 work, the ones that don’t are the microphone jack, and the mic/ headphone combo jack, though on the bright side HDMI audio now fucntions so have fun plugging in to a TV or a display with an audio jack) 

![Capture d’écran 2021-09-27 à 4 10 23 PM](https://user-images.githubusercontent.com/76212533/134997317-44d08425-6935-4258-96e7-7c83aabda902.png)

**Warning**, This EFI won't work unless you make all of the UEFI modifications.If you're not up for that, you'll need to add ```npci=0x2000``` to your boot args, enable ```KernelPm``` and ```AppleIntelCPUPM``` in your config.plist, DO be warned monterey will mostlikely won't display post XNU.

Below here I leave you with cstrouses' work on disabling CFG Lock and co. on BIOS 1.6.0

1. **Disable CFG Lock**
```setup_var 0xAF 0x0```

2. **Enable Above 4GB MMIO BIOS Assignment**
```setup_var 0x355 0x1```

3. **Set DVMT pre-alloc to 64MB** 
```setup_var 0x350 0x2```

4. **Set DVMT Total Gfx Memory to MAX**
```setup_var 0x351 0x3```

# Ventura Support
Yes I'm back, I've been lazy with updates but here it is, for those who still own one of these.

![CEB122EF-C1DA-4EAE-A5F9-91E2188D23A2](https://user-images.githubusercontent.com/76212533/226148821-eb781cc6-ba78-45d9-a8ec-0a769b4f5fd6.JPG)

Update coming soon, I just need to get my carbon working again, cuz the hard drive that has the efi is currently in use trying to get that machine to boot ventura 


# Credits 

Dortania & Acidanthera for Opencore and the guides to installing macOS using it

Thanks to Cstrouse for documenting his work on disabling CFG Lock and incresing DVMT memory allocations using the modded grub shell 



