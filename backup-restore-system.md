# Перенос системы на другой ПК
1. [x] Загрузить с livecd
2. [x] Смонтировать диски. cd /mnt
3. [x] архвация tar -cvzf имя_архива.tar.gz bin....etc...var
4. [x] Загрузить с livecd
5. [x] gdisk подготовка диска 1 - grub...
6. [x] 5.5 создать файловые системы на новых разделах, смониторовать в /mnt
7. [x] скопировать архив в /mnt с другого пк
8. [x] распаковать tar -xvpf имя_архива.tar.gz
9. [x] смонтировать
10. [x] mount -o bind /dev dev
11. [x] ....
12. [x] /dev/pts dev/pts
13. [x] /dev/shm dev/shm
14. [x] mount -t proc proc proc
15. [x] mount -t sysfs sysfs sys
16. [x] chroot /mnt /bin/bash --login
17. [x] grub-install --force --no-floppy /dev/sda
18. [x] заменить точки монтирования в /etc/fstab UUID
19. [x] reboot