# Домашнее задание к занятию 2. «Применение принципов IaaC в работе с виртуальными машинами» - Паромов Роман

## Задача 1

### Опишите основные преимущества применения на практике IaaC-паттернов.
Какой из принципов IaaC является основополагающим?
*  процесс создания, настройки инфраструктуры аналогичен процессу разработки программного обеспечения. Что и понимается под "Инфраструктура как код"
*  Основные преимущества IaC: скорость, уменьшение затрат, маштабируемость, стандартизация, индепатентность.
## Задача 2

### Чем Ansible выгодно отличается от других систем управление конфигурациями?
Какой, на ваш взгляд, метод работы систем конфигурации более надёжный — push или pull?
* Ansible отличатся тем что не нужно устанавливать клиент на хосты для управления ими.
* На мой взгляд надежнее pull, потому что мы получаем больше информации об объекте.

## Задача 3

### Установите на личный компьютер:

### VirtualBox,
Vagrant,
Terraform,
Ansible.
Приложите вывод команд установленных версий каждой из программ, оформленный в Markdown.
```
MacBook-Air-User:~ MacAir$ vagrant -v
Vagrant 2.3.5
```
```
MacAir@MacBook-Air-User ~ % terraform -v
Terraform v1.4.6
on darwin_amd64
```
```
MacAir@MacBook-Air-User ~ % ansible --version
ansible [core 2.14.5]
  config file = None
  configured module search path = ['/Users/MacAir/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.11/site-packages/ansible
  ansible collection location = /Users/MacAir/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/local/bin/ansible
  python version = 3.11.3 (main, May 17 2023, 16:49:17) [Clang 12.0.0 (clang-1200.0.32.29)] (/usr/local/opt/python@3.11/bin/python3.11)
  jinja version = 3.1.2
  libyaml = True
  ```
## Задача 4

### Воспроизведите практическую часть лекции самостоятельно.

Создайте виртуальную машину.
Зайдите внутрь ВМ, убедитесь, что Docker установлен с помощью команды
docker ps,
Vagrantfile из лекции и код ansible находятся в папке.

Примечание. Если Vagrant выдаёт ошибку:

URL: ["https://vagrantcloud.com/bento/ubuntu-20.04"]     
Error: The requested URL returned error: 404:
выполните следующие действия:

Скачайте с сайта файл-образ "bento/ubuntu-20.04".
Добавьте его в список образов Vagrant: "vagrant box add bento/ubuntu-20.04 <путь к файлу>".

столкнулся с проблемой с vagrant и ansible:
```
ansible-playbook: error: unrecognized arguments: --sudo
...

Vagrant gathered an unknown Ansible version:


and falls back on the compatibility mode '1.8'.
```
решил удалением строчки ```setup.become = true``` из блока
```
      node.vm.provision "ansible" do |setup|
        setup.inventory_path = INVENTORY_PATH
        setup.playbook = "/Users/MacAir/playbook.yml"
        setup.become = true
        setup.extra_vars = { ansible_user: 'vagrant' }
```
после это ругался на ключи
```
TASK [Adding rsa-key in /root/.ssh/authorized_keys] ****************************
An exception occurred during task execution. To see the full traceback, use -vvv. The error was: If you are using a module and expect the file to exist on the remote, see the remote_src option
fatal: [server1.netology]: FAILED! => {"changed": false, "msg": "Could not find or access '~/.ssh/id_rsa.pub' on the Ansible Controller.\nIf you are using a module and expect the file to exist on the remote, see the remote_src option"}
...ignoring
```
но видимо проигнорировал и все установилось
![](https://github.com/Romera14/05-virt-02-iaac/blob/main/Снимок%20экрана%202023-05-21%20в%2015.16.48.png)


