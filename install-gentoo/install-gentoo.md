# Установка gentoo 
## Подготовка системы и разметка диска, скачивание дистрибутива 
```    
    gdisk /dev/sda
    partprobe
    mkswap -f /dev/sda2
    mkfs.ext4 -L tmp /dev/sda3
    mkfs.ext4 -L root /dev/sda4
    mount /dev/sda4 /mnt/gentoo/
    cd /mnt/gentoo/
    mkdir tmp
    mount /dev/sda3 /mnt/gentoo/tmp/
    chmod 1777 tmp
    ls -a
    ls -la
    wget https://mirror.yandex.ru/gentoo-distfiles/releases/amd64/autobuilds/current-stage3-amd64-systemd/stage3-amd64-systemd-20240526T163557Z.tar.xz
    tar -xvpf stage3-amd64-systemd-20240526T163557Z.tar.xz
    rm -rf stage3-amd64-systemd-20240526T163557Z.tar.xz
    ls -la
    cat /etc/resolv.conf
    cp /etc/resolv.conf etc/
    mount -o /dev dev
    mount -o bind /dev dev
    mount -o bind /dev/pts dev/pts
    mount -o bind /dev/shm dev/shm
    mount -t proc proc proc
    mount -t sysfs sysfs sys
    chroot /mnt/gentoo /bin/bash --login
```
   ## Работа в новом окружении 
```    
    export PS1="(chroot) $PS1"
    emerge --sync
    eselect news read
    eselect profile list
    eselect profile set 10
    eselect profile list
    emerge app-editors/vim
    emerge -vp app-editors/vim
    echo "app-editors/vim -X" >> /etc/portage/package.use/package.use
    emerge -vp app-editors/vim
    nano /etc/portage/package.use/package.use
```

   ### редактируем /etc/portage/package.use/package.use 

```
app-editors/vim -X -sound
```

### настраиваем флаги компиляции для всей системы файл /etc/portage/make.conf 

```
# These settings were set by the catalyst build script that automatically
# built this stage.
# Please consult /usr/share/portage/config/make.conf.example for a more
# detailed example.
COMMON_FLAGS="-O2 -pipe"
CFLAGS="${COMMON_FLAGS}"
CXXFLAGS="${COMMON_FLAGS}"
FCFLAGS="${COMMON_FLAGS}"
FFLAGS="${COMMON_FLAGS}"

# NOTE: This stage was built with the bindist Use flag enabled
USE="-ldap -gtk -gnome -bluetooth dbus perl python ssl usb networkmanager json idn vim-syntax alsa pulseaudio curl cups
        lzma lzo lz4 kms usbredir split-usr sqlite"

ACCEPT_LICENSE="*"
ALSA_CARDS="hda-intel"
VIDEO_CARDS="nvidia"
MAKEOPTS="-j4"
INPUT_DEVICES="libinput"

L10N="en ru"
LINGUAS="en ru"

# This sets the language of build output to English.
# Please keep this setting intact when reporting bugs.
LC_MESSAGES=C.utf8
```
    настраиваем /etc/portage/package.use/package.use
```
app-editors/vim -X -sound
```
   ### собираем vim и системные программы
```
   emerge app-editors/vim
   eselect editor list
   eselect editor set 2
   emerge -vp --depclean
   emerge --depclean
   eselect news read
   emerge -evp @system
   emerge -e @system
```
