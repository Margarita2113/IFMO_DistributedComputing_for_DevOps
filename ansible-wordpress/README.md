**Deploy WordPress with MySQL Ansible Playbook**

Этот Ansible плейбук, deploy_wordpress.yml, предназначен для автоматизации развертывания WordPress с использованием MySQL на сервере под управлением Ubuntu. Плейбук создает среду, в которой WordPress будет взаимодействовать с базой данных MySQL, используя Docker и Docker Compose, и настраивает репликацию между двумя экземплярами MySQL.

**Предварительные требования**

Для запуска данного плейбука потребуется:

- Установить Ansible и необходимые модули.
- На целевом сервере установленаустановить операционная операционную систему Ubuntu.

**Установка для лабораторной 3**

- Клонируйте репозиторий на ваш локальный или удаленный сервер, используя следующую команду:
   git clone [https://github.com/Margarita2113/IFMO_DistributedComputing_for_DevOps/tree/Lab3]
- cd ansible-wordpress
- Заполните файл inventory.ini
  Для подготовки серверов к инсталяции запустите плейбук deploy_prepare.yml.
  *ansible-playbook -i inventory.ini deploy_prepare.yml*
- Для инсталяции wordpress используйте плейбук deploy_wordpress.yml
  *ansible-playbook -i inventory.ini deploy_wordpress_master_slave.yml*
- Для настройки мониторинга используйте плейбук deploy_prometheus.yml
  *ansible-playbook -i inventory.ini deploy_prometheus.yml*-

**Установка для лабораторной 4**
- Клонируйте репозиторий на ваш локальный или удаленный сервер, используя следующую команду:
  git clone [https://github.com/Margarita2113/IFMO_DistributedComputing_for_DevOps/tree/Lab3]
- cd ansible-wordpress
- Заполните файл inventory.ini
  Для подготовки серверов к инсталяции запустите плейбук deploy_prepare.yml.
  *ansible-playbook -i inventory.ini deploy_prepare.yml*
- Развертывание отказоустойчивого кластера Galera cluster
  *ansible-playbook -i inventory.ini deploy_galera_cluster.yml*
- Для инсталяции wordpress используйте плейбук deploy_wordpress_galera.yml
  *ansible-playbook -i inventory.ini deploy_wordpress_galera.yml*-


**Описание задач**

1. Обновление пакетов: Плейбук обновляет кэш пакетов и устанавливает необходимые библиотеки для работы Docker.
2. Установка Docker: Добавление GPG-ключа, установка необходимых компонентов Docker и Docker Compose.
3. Создание директории: Создание директории для WordPress в указанном пути.
4. Настройка файла Docker Compose: Конфигурация файла docker-compose.yml, который описывает сервисы для базы данных и WordPress.
5. Запуск MySQL: Запуск сервисов базы данных и ожидание их готовности.
6. Настройка репликации MySQL: Создание пользователя для репликации и предоставление необходимых привилегий.
7. Запуск WordPress: Запуск сервиса WordPress и ожидание его доступности.

**Дополнительно**

Убедитесь, что порты 8080, 3306 и 3307 не конфликтуют с другими сервисами на вашем сервере.
Для доступа к WordPress откройте браузер и перейдите по адресу http://<IP-адрес_вашего_сервера>:8080.

#sudo docker volume rm $(sudo docker volume ls -q)