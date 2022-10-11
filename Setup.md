# Setup procedue

## Optional steps before begin

## Install Almalinux

### Create bootable disk [Control machine]

1. Download `AlmaLinux-8.6-x86_64-minimal.iso` from [mirrosr](https://mirrors.almalinux.org/isos/x86_64/8.6.html)
2. Create bootable USB
  1. I personally use [Rufus](https://rufus.ie/) because it is easy to use and it can be used on Windows.

### Prepare [Control machine]

1. Open 80/tcp of your control machine
2. `cd hosts` and `sudo python3 -m http.server 80`
3. Open other terminal and run `ip a` and check IP of your Control machine.


### Kickstart [Cluster machine]

```console
vmlinuz initrd.img inst.stage2=hd:LABEL=Almalinux-8-6-x86_64-dvd inst.ks http://10.0.2.15/anaconda-ks.cfg quiet
```

## Setup clusters using ansible [Control machine]

### Setup `ansible/inventry.yaml`

Copy `ansible/inventry.example.yaml` as `ansible/inventry.yaml`.

Edit hosts.

### Run playbook

```console
cd ansible
ansible-playbook site.yaml -i inventory.yaml -K -v
```

You will be asked by prompt like:

```console
The authenticity of host '10.0.2.7 (10.0.2.7)' can't be established. 
ECDSA key fingerprint is SHA256:xxxxxxxxxxxxxxxyyyyyyyyyyyyyyzzzzzzzzzzz.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Enter `yes` and push the enter key.

## Appendix

### Installation of Control Machine

Create Control machine.

Install Almalinux and these packages

- git
- tar
- python3

```console
sudo yum install git tar python3
```

Install ansible

```console
pip install --upgrade pip
python3 -m pip install ansible
```

Verify you installation

```console
ansible-playbook --version
```
