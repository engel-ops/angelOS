# InsydeH2O Setup Utility (from Rev. 5.0)

## Main

### Lid open

>  Option to enable system to automatically
resume after opening the display panel. [[1](https://us.v-cdn.net/6029997/uploads/editor/io/45ntz45p35m5.pdf)]

## Advanced

### Intel Virtualization Technology

> Intel® Virtualization Technology (VT-x) allows one hardware platform to function as multiple “virtual” platforms. It offers improved manageability by limiting downtime and maintaining productivity by isolating computing activities into separate partitions. [[2](https://ark.intel.com/content/www/us/en/ark/products/122589/intel-core-i78550u-processor-8m-cache-up-to-4-00-ghz.html)]

> This allows an operating system to more effectively & efficiently utilize the CPU power in the computer so that it runs faster. This feature is also a requirement for many virtual machine software and is required to be enabled in order for them to run properly or even at all. [[3](https://www.compuhoy.com/should-i-enable-virtualization-technology-in-bios/)] 

### Legacy USB Support

InsydeH20 UEFI does not natively support USB, the `Legacy USB Support` option enables the possibility to make USB devices available during boot e.g. for a flashed installation ISO on an USB flash drive. [[4](https://www.helpster.de/legacy-usb-support-bedeutung_196074)] [[5](https://www.reddit.com/r/virtualreality/comments/g5md47/comment/fo46u80/?utm_source=share&utm_medium=web2x&context=3)]

> Also known as “USB Keyboard” or “USB Mouse support” in the BIOS Setup is a feature that allows one to use the USB mouse and keyboard as if they were their classic PS/2 counterparts. [[6](https://docs.kernel.org/x86/usb-legacy-support.html)]

### SW Guard Extensions (SGX)

> Intel Software Guard Extensions (SGX) is a set of security-related instruction codes that are built into some Intel central processing units (CPUs). They allow user-level and operating system code to define protected private regions of memory, called enclaves. SGX is designed to be useful for implementing secure remote computation, secure web browsing, and digital rights management (DRM). [[7](https://en.wikipedia.org/wiki/Software_Guard_Extensions)]

> A pivot by Intel in 2021 resulted in the deprecation of SGX from the 11th and 12th generation Intel Core Processors, but development continues on Intel Xeon for cloud and enterprise use. [[7](https://en.wikipedia.org/wiki/Software_Guard_Extensions)]

### SATA Configuration

#### SATA Mode Selection

##### AHCI

> The Advanced Host Controller Interface (AHCI) is a technical standard defined by Intel ... . The specification describes a system memory structure for computer hardware vendors to exchange data between host system memory and attached storage devices. [[8](https://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)]

> For modern solid state drives, the interface has been superseded by NVMe. [[8](https://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)]

##### Intel RST Premium

> Intel Rapid Storage Technology (RST) is a driver SATA AHCI and a firmware-based RAID solution built into a wide range of Intel chipsets. Currently also is installed as a driver for Intel Optane temporary storage units. [[9](https://en.wikipedia.org/wiki/Intel_Rapid_Storage_Technology)]

> Do you plan to use RAID? <br>
> Do you plan to use an Optane Memory module to accelerate the performance of a SATA HDD? <br>
> Do you plan to use an Optane SSD? <br>
> If the answer to all three of these questions is No, then you do not need to enable or install RST at all. Once upon a time, the Intel Storage driver in RST would get you slightly better performance than the  Storage driver that was provided with Windows 7. In fact, with Windows 10, the performance of the Storage drivers is on par and there is no advantage to using RST at all (well, unless the answer to one of those questions had been Yes). [[1ß](https://community.intel.com/t5/Rapid-Storage-Technology/New-system-build-AHCI-or-RST-Premium-I-m-confused/m-p/1274544/highlight/true#M9864)]

> The Intel RST is a driver/control program for the Intel Optane memory system, which is an M.2 memory device that acts like a 16gb disk cache, a "Supersized" cache <br>
> The Optane memory + HDD + RST get you better than SATA III HDD performance but not as fast as an SSD <br>
> With the prices of SSDs falling as they are, if you have at least a Gen 8 CPU & motherboard I'd consider using that M.2 slot for a NVMe SSD, FOUR times faster than SATA III [[11](https://www.tenforums.com/drivers-hardware/168770-intel-rst-vs-windows-ahci-drivers.html#post2085687)]

> The RAID devices can be managed in different ways:
>   - Software RAID
>   - Hardware RAID
>   - FakeRAID 
>     - This type of RAID is properly called BIOS or Onboard RAID, but is falsely advertised as hardware RAID. The array is managed by pseudo-RAID controllers where the RAID logic is implemented in an option ROM or in the firmware itself with a EFI SataDriver (in case of UEFI), but are not full hardware RAID controllers with all RAID features implemented. ... Here are some examples of FakeRAID controllers: Intel Rapid Storage ... [[11](https://wiki.archlinux.org/title/RAID#Implementation)]

## Security

### Administrator Password

The admin password *might* be stored as a hash on a Hardware Security Module, it will highly likely will not reset when the system it out of power. [[12](https://chat.stackexchange.com/transcript/message/54855785#54855785)]

This setting only makes sense when setting **Password Check** to **Always** which means the PC will ask for the password even before booting from ANY device. 

If **Password Check** is set to **Setup** the boot order can not get changed, but systems allow booting other devices making it possible to just flash a new UEFI completely: [How To Remove A Bios Password From an Insyde H2O EFI BIOS](http://d-minds.com.ar/documents/blog.php?entry_id=1359466865&title=how-to-remove-a-bios-password-from-an-insyde-h2o-efi-bios) [13]

> In the past, with AMI/Award/Phoenix BIOSes, there have been tools available to decrypt, reset, or otherwise mangle the BIOS settings into removing the password. Unfortunately, none of those tools work on EFI firmwares, which are the next generation of BIOS. [[13](http://d-minds.com.ar/documents/blog.php?entry_id=1359466865&title=how-to-remove-a-bios-password-from-an-insyde-h2o-efi-bios)]

BE AWARE that you might completely lock yourself out of the system by setting an UEFI password with the only option left to replace the motherboard. [[14](https://superuser.com/questions/1564044/reset-insyde-h20-bios-admin-password)]

### TPM Device

> Trusted Platform Module (TPM, also known as ISO/IEC 11889) is an international standard for a secure cryptoprocessor, a dedicated microcontroller designed to secure hardware through integrated cryptographic keys. [[15](https://en.wikipedia.org/wiki/Trusted_Platform_Module)]

> Disc Encryption: If somebody steals your storage disc and runs it on a different machine to steal your data then due to the mismatch of system configuration TPM will automatically encrypt the Disc whose cryptographic key (which can be created with encryption software such as Windows BitLocker) will only be available with the TPM module of the machine from where it is Stolen. Access to the data will be denied if the system configuration mismatches. [[16](https://www.techsectora.com/2021/02/tpm-header-what-is-it-and-why-is-it-used.html?m=1)]

### I/O Interface Security

- Wireless Network Interface
- LAN Network Interface
- SATA Interface Storage
- USB Interface
  - External Ports
  - Bluetooth
  - CMOS Camera
  - Card Reader

AOS should have a portable version that does not require internet, on a normal system you might want to disable the **USB Interface** making it impossible to boot from USB BUT you can't use any USB devices then.

### SATA Interface Storage

This DOES not prevent the system from booting systems installed on HDDs BUT prevents the booting from external sources.

#### USB Interface

##### CMOS Camera

Interface for CMOS (complementary metal oxide semiconductor) image sensor which convert light to digital signals making them readable by the OS displaying these signals as pictures or videos. [[17](https://www.tel.com/museum/exhibition/principle/cmos.html)]

### Security Boot Management

#### Enforce Secure Boot

> When a PC starts, it first finds the OS bootloader. PCs without Secure Boot run whatever bootloader is on the PC's hard drive. There's no way for the PC to tell whether it's a trusted OS or a rootkit.
> 
> When a PC equipped with UEFI starts, the PC first verifies that the firmware is digitally signed, reducing the risk of firmware rootkits. If Secure Boot is enabled, the firmware examines the bootloader's digital signature to verify that it hasn't been modified. If the bootloader is intact, the firmware starts the bootloader only if one of the following conditions is true:
> - The bootloader was signed using a trusted certificate. For PCs certified for Windows, the Microsoft certificate is trusted.
> - The user has manually approved the bootloader's digital signature. This action allows the user to load non-Microsoft operating systems. 
> [[18](https://learn.microsoft.com/en-us/windows/security/information-protection/secure-the-windows-10-boot-process#secure-boot)]

## Boot

### PXE Boot

> Preboot execution environment (PXE), pronounced pixie, is a set of standards that enables a computer to load an operating system (OS) over a network connection. PXE can be used to quickly install an OS and is commonly used for both servers and clients. It may also be called PXE boot, boot from network, network boot or local area network boot.
> 
> Here are the steps in the PXE boot process:
> 1. The client basic input/output system (BIOS) initiates PXE boot. This may be selected by the client operator or may be a fallback option when other boot media fails.
> 2. The client broadcasts a DHCP request and a PXE request.
> 3. The DHCP server responds with the DHCP response so the client can set an IP address, and it replies with the IP address of the TFTP server and the file name of the NBP.
> 4. The client downloads and boots the NBP.