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