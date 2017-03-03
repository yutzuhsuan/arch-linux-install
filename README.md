# arch-linux-install
My Arch linux install guide

My device is thinkpad T450 with windows 10 pro and arch linux

special thanks [@geniusgordon](https://github.com/geniusgordon) [@afg984](https://github.com/afg984)

[@geniusgordon's note](http://simp.ly/p/pzgqzL)

2017/01/31

## Disk
```bash
fdisk /dev/sda
```
```bash
mkswap /dev/sdaX  # I don't need swap
```
```bash
mkfs -t ext4 /dev/sdaX
```

## Mount
```bash
mount /dev/sdaX /mnt
```
```bash
mount /dev/sdaX /mnt/boot
```

if your mount fail due to the windows fast startup
```bash
ntfsfix /dev/sdaX
```
## Install
```bash
wifi-menu # connect to wifi, your install needs to download lots of things
```
```bash
pacstrap /mnt base base-devel
```
```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

## Settings
```bash
arch-chroot /mnt # now we are in our new arch linux
```
```bash
echo hostname > /etc/hostname # name your own hostname
```
```bash
ln -s /usr/share/zoneinfo/Asia/Taipei /etc/localtime # if the localtime is already exist mv it to localtime.backup
```
```bash
vim /etc/locale.gen # "zh_TW BIG5" "zh_TW.UTF-8 UTF-8" "zh_CN.UTF-8 UTF-8" "en_US.UTF-8 UTF-8" "en_US ISO-8859-1" "chr_US UTF-8"
```
```bash
vim /etc/locale.conf # create a file and paste LANG="en_US.UTF-8"
```
```bash
locale-gen
```
```bash
passwd
```

## GUI
```bash
pacman -S xf86-video-intel xorg-server gnome
```
```bash
systemctl enable gdm
```

## Boot
```bash
pacman -S os-prober # to find your windows
```
I can't find my windows at the first time, but after reboot os-prober successfully find my windows
```bash
mkinitcpio -p linux
```
```bash
pacman -S grub efibootmgr
```
```bash
grub-install /dev/sdaX --efi-directory=/boot
```
```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

## Aur
```bash
git clone https://aur.archlinux.org/packer.git
makepkg # install two missing dependencies
pacman -U packer-20160325-1-any.pkg.tar.xz # the version might not be the same
```
remember to remove the install directory after successfully install packer

## Fonts
```
packer noto
```
i use traditional chinese
* noto-fonts
* noto-fonts-cjk
* noto-fonts-emoji

remember to set your google-chrome font's to cjk

## Config
```bash
pacman -S openssh
```
* install vundle
* clone my .ssh directory from google-drive
* dotfiles from github ( .vimrc )



## Applications
* google-chrome
* slack-desktop

## Ibus
* ibus
* ibus-chewing

## Tools
* albert
* gnome-tweak-tool
* arc-gtk-theme ( enable it in tweak-tool )
* networkmanager
* paper-icon-theme-git ( enable it in tweak-tool )
* tmux
* wget
* vim
* dash-to-dock ( enable it in tweak-tool )
* xfce4-terminal ( background opacity is soooo great )
* hub

## Yarn
* yarn
* create-react-app
* http-server
* react-native-cli

## Zsh
* zsh
* oh-my-zsh
* plugins=(zsh-autosuggestions)

## Android
* android-sdk
* android-sdk-build-tools
* android-sdk-platform-tools
* genymotion

