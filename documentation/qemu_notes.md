# QEMU Notes

## Creating QEMU antivm build 0.01 (manual patching)

The initial version of the antivm QEMU build was created by manually editing an existing QEMU binary using the `ghex` editor. While inelegant, this approach proved effective in erasing the necessary hardcoded vendor and product strings in order to avoid detection. 
This process was referenced against the QEMU source code in order ot determine static identifiers that should be changed (e.g. USB tablet vendor and product IDs, SCSI IDs etc). 

In the future, a much more sane approach will be necessary, rolling all of the necessary changes into a proper QEMU fork. 

## Differences between the two QEMU builds

The BACKUP version includes my attempts to manually patch out the USB HID identifiers. It appeared to work, but I didn't actually roll that version out. 

## Convert Domain XML to QEMU Cmdline

```
virsh dumpxml DomainNameHere  >vm_def.xml
virsh domxml-to-native qemu-argv vm_def.xml
```

## Specifying IDE drive models

See [link](https://lists.gnu.org/archive/html/qemu-devel/2012-03/msg02132.html)

## Passing cmdline arguments via libvirt

See [link](https://blog.vmsplice.net/2011/04/how-to-pass-qemu-command-line-options.html)

## Override GPU PCI device ID

See [link1](https://old.reddit.com/r/VFIO/comments/gelcqx/how_to_override_gpu_pci_device_id/) [link2](https://old.reddit.com/r/VFIO/comments/d6cmes/possible_to_spoof_pciid_of_device_passed_through/)

## More virtualization hiding techniques

[Fighting error 43 – Nvidia GPU in a virtual machine](https://mathiashueber.com/fighting-error-43-nvidia-gpu-virtual-machine/)
