# arch-linux-install
My Arch linux install guide

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
<aside class="warning">
如果 windows 快速關機沒取消 boot 會 mount 失敗, 就要先 ntfsfix
</aside>
```bash
ntfsfix /dev/sdaX
```



## Install

## Settings

## GUI

## Boot

## Aur

## Applications

## Ibus

## Tools

## Yarn

## Zsh

## Android

