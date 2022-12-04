# UEFI Recommendations

## InsydeH2O (from Rev. 5.0)

| Option | Setting | Why |
:------- | :------ | :--
| Main > Lid Open | Disabled | Easier to check if laptop is really suspended. |
| Intel Virtualization Technogoly | Enabled | Better performance, mandatory for virtualization technology. |
| Advanced > SW Guard Extensions (SGX) | Disabled | We might want to use SGX in the future to mitigate memory attacks. | 
| Advanced > SATA Configuration > SATA Mode Selection | AHCI | As of now AOS only will supports AHCI and NOT Intel RST Premium, but that it is one of our goals in the future to make legacy systems faster.
| Security > Set Administrator Password | *Your Choice* | This is the only way to lock the BIOS boot order which prevents someone else from using your hardware BUT only when setting **Security > Password Check** to always, otherwise UEFI might can get flashed. [[1](http://d-minds.com.ar/documents/blog.php?entry_id=1359466865&title=how-to-remove-a-bios-password-from-an-insyde-h2o-efi-bios)] <br><br> Entering a password every time you start the computer might be very annoying, also forgetting that password might lock you out of your system and you might lose all the data because AOS might use encryption with the TPM.
| Security > Password Check | Always (or Disabled) | This option only appears with an **Administrator Password** set. <br><br> Setting this to **Setup** will NOT ask for a password when starting the PC BUT only when entering UEFI. But this might not be safe: If you can still boot a system it might be possible to completely flash UEFI [[1](http://d-minds.com.ar/documents/blog.php?entry_id=1359466865&title=how-to-remove-a-bios-password-from-an-insyde-h2o-efi-bios)]
| Security > TPM Device | Enabled | We might want use the TPM for hard disk encryption making the disk and the system only available with the hardware it was installed on. <br><br> Even you don't want this, other systems or software might use the TPM.
| Security > I/O Interface Security > Wireless Network Interface | Your Choice | You need internet for system updates. <br><br> If you want to mitigate wifi security risks you might want to disable. <br><br> Most likely you want wireless internet.
| Security > I/O Interface Security > LAN Network Interface | Your Choice | You need internet for system updates. <br><br> Maybe you see security risks if **Unlock**ed.
| Security > I/O Interface Security > SATA Interface Storage | Unlock on installation, Lock after that | Will disable booting from USB, must be enabled for USB installation. <br><br> Might want to UnLock if you often want to boot from USB.