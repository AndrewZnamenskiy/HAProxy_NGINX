# Домашнее задание к занятию 2 «Кластеризация и балансировка нагрузки»

 ---

### Задание 1

- Запустите два simple python сервера на своей виртуальной машине на разных портах
- Установите и настройте HAProxy, воспользуйтесь материалами к лекции
- Настройте балансировку Round-robin на 4 уровне.
- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy.


### Решение 1

#### Команды запуска  Python Web серверов


	'python3 -m http.server 8888 --bind 0.0.0.0'

	'python3 -m http.server 9999 --bind 0.0.0.0'



  *Скриншоты задания №1*

*На одном сервере запущен HAProxy (порт 8080) и два Python3 Web сервера (порты 8888 и 9999)*

![Commit Task1](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task1p1.png)


*Файл конфигурации Task1: [HAproxy_Task1](task1-cfg/haproxy.cfg.bak1)*

 ---

### Задание 2

- Запустите три simple python сервера на своей виртуальной машине на разных портах
- Настройте балансировку Weighted Round Robin на 7 уровне, чтобы первый сервер имел вес 2, второй - 3, а третий - 4
- HAproxy должен балансировать только тот http-трафик, который адресован домену example.local
- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy c использованием домена example.local и без него.


### Решение 2

#### Команды запуска  Python Web серверов

	
	'python3 -m http.server 8888 --bind 0.0.0.0'

        'python3 -m http.server 9999 --bind 0.0.0.0'


#### Команда имитации запросов на 7-м уровне:

	'curl -H 'Host:example.local' http://127.0.0.1:8080'


  *Скриншоты задания №2*


![Commit Task2](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task2p1.png)


*Файл конфигурации Task2: [HAProxy_Task2](task2-cfg/haproxy.cfg.bak2)*


 ---

### Задание 3*
- Настройте связку HAProxy + Nginx как было показано на лекции.
- Настройте Nginx так, чтобы файлы .jpg выдавались самим Nginx (предварительно разместите несколько тестовых картинок в директории /var/www/), а остальные запросы переадресовывались на HAProxy, который в свою очередь переадресовывал их на два Simple Python server.
- На проверку направьте конфигурационные файлы nginx, HAProxy, скриншоты с запросами jpg картинок и других файлов на Simple Python Server, демонстрирующие корректную настройку.


### Решение 3

#### Команды запуска  Python Web сервера


        'python3 -m http.server 8800 --bind 0.0.0.0'


  *Скриншоты задания №3*

  *Запрос картинок по заданному имени ресурса*

![Commit Task3](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task3p1.png)


![Commit Task3](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task3p2.png)

 *Направление остальных запросов NGINX на HAProxy*

![Commit Task3](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task3p3.png)


*Размещение картинок jpg в целевой папке*

![Commit Task3](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task3p4.png)


*Запрос несуществующего файла*

![Commit Task3](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task3p5.png)


*Файл конфигурации Task3: [HAProxy_Task3](task3-cfg/haproxy.cfg.bak3)*


---

### Задание 4*
- Запустите 4 simple python сервера на разных портах.
- Первые два сервера будут выдавать страницу index.html вашего сайта example1.local (в файле index.html напишите example1.local)
- Вторые два сервера будут выдавать страницу index.html вашего сайта example2.local (в файле index.html напишите example2.local)
- Настройте два бэкенда HAProxy
- Настройте фронтенд HAProxy так, чтобы в зависимости от запрашиваемого сайта example1.local или example2.local запросы перенаправлялись на разные бэкенды HAProxy
- На проверку направьте конфигурационный файл HAProxy, скриншоты, демонстрирующие запросы к разным фронтендам и ответам от разных бэкендов.


### Решение 4

#### Команды запуска  Python Web серверов первой и второй

	__Первая группа - домен example1.local__
	
	'python3 -m http.server 8800 --bind 0.0.0.0'

	'python3 -m http.server 8801 --bind 0.0.0.0'

	__Вторая группа - домен example2.local__

	'python3 -m http.server 9900 --bind 0.0.0.0'

	'python3 -m http.server 9901 --bind 0.0.0.0'



  *Скриншоты задания №4*


![Commit Task4](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task4p1.png)

*Отработка запросов серверами перовой группы*

![Commit Task4](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task4p2.png)

*Отработка запросов серверами второй группы*

![Commit Task4](https://github.com/AndrewZnamenskiy/HAProxy_NGINX/blob/main/img/task4p3.png)


*Файл конфигурации Task4: [HAProxy_Task4](task4-cfg/haproxy.cfg.bak4)*

*Файл конфигурации Task4: [NGINX_Task4](task4-cfg/new-server)*


------
