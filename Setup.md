# Setup procedue

## Install Almalinux

### Create bootable disk [Control machine]

1. Download `AlmaLinux-8.6-x86_64-minimal.iso` from [mirrosr](https://mirrors.almalinux.org/isos/x86_64/8.6.html)
2. Create bootable USB
  1. I personally use [Rufus](https://rufus.ie/) because it is easy to use and it can be used on Windows.

### Boot your cluster machine [Cluster machine]

```console
vmlinuz initrd.img inst.stage2=hd:LABEL=Almalinux-8-6-x86_64-dvd inst.ks http://10.0.2.15/anaconda-ks.cfg quiet
```
