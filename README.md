# hw01
Kernel update. Create custom box for Vagrant Clound. Packer.
Подключаю репозиторий:
>sudo yum install -y http://www.elrepo.org/elrepo-release-7.0-3.el7.elrepo.noarch.rpm

Устанавливаю последнее ядро:
>sudo yum --enablerepo elrepo-kernel install kernel-ml -y

Обновляю конфигурацию загрузчика:
>sudo grub2-mkconfig -o /boot/grub2/grub.cfg
