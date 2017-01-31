# arch-linux-install
My Arch linux install guide
special thanks [@geniusgordon](https://github.com/geniusgordon) [@afg984](https://github.com/afg984)

## Disk
```bash
fdisk /dev/sda
```
```bash
mkswap /dev/sdaX  # 我都不做 swap 了
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


如果 windows 快速關機沒取消 /mnt/boot 會 mount 失敗, 就要先 ntfsfix
```bash
ntfsfix /dev/sdaX
```
## Install
```bash
wifi-menu # 先連網, arch 的安裝需要下載
```
```bash
pacstrap /mnt base base-devel
```
```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

## Settings
```bash
arch-chroot /mnt # 從隨身碟進入我們剛灌好的 arch 裡面
```
```bash
echo hostname > /etc/hostname # 自己設定 hostname
```
```bash
ln -s /usr/share/zoneinfo/Asia/Taipei /etc/localtime # 如果已經存在 localtime 這個檔案的話就把已經存在的 localtime 改成 localtime.backup
```
```bash
vim /etc/locale.gen # "zh_TW BIG5" "zh_TW.UTF-8 UTF-8" "zh_CN.UTF-8 UTF-8" "en_US.UTF-8 UTF-8" "en_US ISO-8859-1" "chr_US UTF-8"
```
```bash
vim /etc/locale.conf # 創造 conf 並寫入這行 LANG="en_US.UTF-8"
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
pacman -S os-prober
```
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
makepkg # 他會提示兩個缺的東西, 用 pacman 把那兩個裝起來
pacman -U packer-20160325-1-any.pkg.tar.xz # 版本可能會長不一樣
```
裝完記得把安裝資料夾移除

## Fonts
```
packer noto
```
安裝以下幾個
* noto-fonts
* noto-fonts-cjk
* noto-fonts-emoji

要記得去 google-chrome 設定 noto-fonts-cjk 才能顯示中文

## 設定
```bash
pacman -S openssh
```
* install vundle
* 把 .ssh 從 google drive 拉下來
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
* arc-gtk-theme ( 記得去 tweak-tool 裡面打開 )
* networkmanager
* paper-icon-theme-git ( 記得去 tweak-tool 裡面打開 )
* tmux
* wget
* vim

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

