# bpf

Check if BPF is enabled in your kernal:
```bash
cat /sys/kernel/security/lsm
```

Add `bpf` to the **grub** file:
```bash
sudo vim /etc/default/grub
```
```bash
GRUB_CMDLINE_LINUX="lsm=lockdown,capability,landlock,yama,apparmor,bpf"
```

Update grub:
```bash
sudo update-grub
```

Now reboot system:
```bash
sudo reboot
```
