# Installation commands

* loadkeys la-latin1
* timedatectl set-ntp true
* fdisk /dev/sda1 
* --aca se crean las particiones que sean necesarias
* mkfs.ext4 /dev/sda1
mount /dev/sda1 /mnt
pacstrap /mnt base linux
getnfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt
ln -sf /usr/share/zoneInfo/Europe/Madrid /etc/localtime
hwclock --systohc
pacman -S vim
vim /etc/locale-gen 
*Uncomment en_US.UTF-8 UTF-8

vim /etc/locale.conf (y agregar LANG=es_US.UTF-8)
vim /etc/vconsole.conf (y agregar KEYMAP=la-latin1)
vim /etc/hosts

127.0.0.1	localhost
::1	localhost
127.0.1.1	myhostname.localdomain myhostname


passwd (and set the password)
pacman -S grub
grub-install --target=i386-pc /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
pacman -S dhcpcd
systemctl enable dhcpcd
exit
umount -R /mnt
reboot
