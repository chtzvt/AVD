# AppArmor Notes

IMPORTANT NOTE: On Ubuntu 20.04 w/ Libvirt 6.0, there appears to be a [bug](https://bugs.launchpad.net/apparmor/+bug/1825745) preventing guests from being configured to use custom OVMF/BIOS firmware images. 
The best way I've determined to get around this is to simply replace the stock OVMF/SeaBIOS ROMs with my own custom builds. 

In theory specifying a custom bios rom should be fully [supported](https://bugzilla.redhat.com/show_bug.cgi?id=811227), but currently any guest configured as such will fail to start with an AppArmor error:

```
May 17 16:24:00 magrathea libvirtd[109139]: internal error: Child process (LIBVIRT_LOG_OUTPUTS=3:stderr /usr/lib/libvirt/virt-aa-helper -c -u libvirt-822af091-0007-4efd-b0a2-f014c8e40faf) unexpected exit status 1: virt-aa-helper: error: /usr/share/seabios/bios-vmdetect.bin#012virt-aa-helper: error: skipped restricted file#012virt-aa-helper: error: invalid VM definition
```

Another IMPORTANT NOTE: Be sure to apply the included AppArmor entitlements to any patched or custom builds of QEMU, otherwise the emulator will likely fail to function. 
