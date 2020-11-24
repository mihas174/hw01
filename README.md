# hw01
Kernel update. Create custom box for Vagrant Clound. Packer.

Подключаю репозиторий:

>sudo yum install -y http://www.elrepo.org/elrepo-release-7.0-3.el7.elrepo.noarch.rpm

Устанавливаю последнее ядро:

>sudo yum --enablerepo elrepo-kernel install kernel-ml -y
Обновляю конфигурацию загрузчика:

>sudo grub2-mkconfig -o /boot/grub2/grub.cfg
Загрузка с новым ядром:

>sudo grub2-set-default 0

Перезагружаю VM.

Далее захожу в файл centos.json:
Убираю строку:

>"iso_checksum_type": "sha256",

И корректирую строки на достоверные значения, так как ссылка на ISO файл недействительна:

>"iso_url": "http://mirror.yandex.ru/centos/7.7.1908/isos/x86_64/CentOS-7-x86_64-Minimal-1908.iso",
>"iso_checksum": "9a2c47d97b9975452f7d582264e9fc16d108ed8252ac6816239a3b58cef5c53d",

Далее запускаем packer

>packer build centos.json

Результатом работы packer'a получился файл c расширением .box
Добавляем его в репозиторий:

>vagrant box add --name centos-7-5 centos-7.7.1908-kernel-5-x86_64-Minimal.box

Создаем директорию и инициализируем среду vagrant в этой папке:

>mkdir test

>cd test

>vagrant init centos-7-5

Проверяем версию ядра в созданной VM

> vagrant up

...

> vagrant ssh

> uname -r

Загружаю полученный файл .box на https://app.vagrantup.com/


