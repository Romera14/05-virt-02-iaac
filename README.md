# Домашнее задание к занятию 2. «Применение принципов IaaC в работе с виртуальными машинами» - Паромов Роман

## Задача 1

### Опишите основные преимущества применения на практике IaaC-паттернов.
Какой из принципов IaaC является основополагающим?
## Задача 2

###Чем Ansible выгодно отличается от других систем управление конфигурациями?
Какой, на ваш взгляд, метод работы систем конфигурации более надёжный — push или pull?

## Задача 3

### Установите на личный компьютер:

### VirtualBox,
Vagrant,
Terraform,
Ansible.
Приложите вывод команд установленных версий каждой из программ, оформленный в Markdown.

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
