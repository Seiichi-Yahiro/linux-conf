wifi-menu // setup wifi
ping 8.8.8.8 // test connection
timedatectl set-ntp true // get time from internet
loadkeys de // for german keyboard

lsblk // list drives
fdisk // 550M Boot / 12G SWAP / ?? (25G) root / ?? (remaining) home
mkfs.fat -F32 /dev/?? // boot
mkfs.ext4 /dev/?? (every dev that is not SWAP or boot)
mkswap /dev/??
swapon /dev/??
mount /dev/?? /mnt  //mount root
mkdir /mnt/boot
mkdir /mnt/home
mount /dev/?? /mnt/boot
mount /dev/?? /mnt/home
pacstrap /mnt base base-devel vim // install arch with some packages
genfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt

pacman -S networkmanager
systemctl enable NetworkManager

pacman -S grub efibootmgr
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=arch_grub //grub-install --target=i386-pc /dev/?? //disk (not partition) where boot is e.g. /sda1 = boot then /sda
grub-mkconfig -o /boot/grub/grub.cfg

vim /etc/hostname // just put your prefered pc name here
passwd

vim /etc/locale.gen // uncomment your language
locale-gen
vim /etc/locale.conf // insert LANG=de_DE.UTF-8
vim /etc/vconsole.conf // insert KEYMAP=de
ln -sf /usr/share/zoneinfo/Europe/Berlin /etc/localtime

exit
umount -R /mnt


adduser julian -m -g wheel
vim /etc/sudoers

//nmcli dev wifi list // list wifi signals
//nmcli device wifi connect <SSID> password <PW>

pacman -S xorg-server xorg-xinit
pacman -S nvidia
install i3
startx

// put this into ~/.zprofile after you have zsh
if [[ ! $DISPLAY && $XDG_VTNR -eq 1 ]]; then
  exec startx
fi


// set in zshrc
export BROWSER=""
export TERMINAL=""
export EDITOR=""



setxkbmap de
pacman -S nm-connection-editor network-manager-applet
