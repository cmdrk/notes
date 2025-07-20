---
title: Debian VM Installation on FreeBSD
---
### Installation

Download the ISO:

```bash
vm iso https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.11.0-amd64-netinst.iso 
```

You will need to create the VM before picking installation media. Here are the
settings I used, just a clone of the default with some tweaks for CPU/Memory:
```
/mnt/vm/.templates # cat debian.conf 
loader="grub"
cpu=4
memory=4096M
network0_type="virtio-net"
network0_switch="public"
disk0_type="ahci-hd"
disk0_name="disk0.img"
grub_run_partition="1"
grub_run_dir="/boot/grub"
```

The defaults are located at `/usr/local/share/examples/vm-bhyve`, but need to be copied into your local config area (for me, `/mnt/vm/.templates`)

Create the VM:
```bash
vm create -s 100G -t debian deb-base
```

Start the installation, and attach to console:
```bash
vm install deb-base debian-12.11.0-amd64-netinst.iso
```

At this point, the VM should be running with the installer going.

Attaching to the console:
```bash
vm console deb-base
```

To exit the console, try `~^D` (tilde, plus CTRL-D). This seems superior to `~.` because the latter will be intercepted by SSH first, and you can kick yourself out of your working session.

### Using BHyve in anger
#### Hard killing a VM
If you have to hard-kill a VM: 
 - You can kill the process in the usual way (e.g., `kill <vm pid>`, perhaps `kill -9`
 - If necesasry, remove the lockfile in the VM's configuration directory (e.g. `/mnt/vm/debian/run.lock` in my case)
 - If necessary, remove the VMM device. In my case, `/etc/vmm/debian`
 (This seems incomplete, as the server didn't want to launch my new debian VM afterwards :) )

