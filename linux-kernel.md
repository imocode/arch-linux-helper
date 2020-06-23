pacman -S base-devel xmlto kmod inetutils bc libelf git
wget https://www.kernel.org/pub/linux/kernel/v5.x/linux-5.7.5.tar.xz
tar -xvJf linux-5.7.5.tar.xz
cd linux-5.7.5
make mrproper
zcat /proc/config.gz > .config
make
