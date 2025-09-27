# Лабораторная работа. Развертывание коммутируемой сети с резервными каналами

### 	Топология

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic00.JPG)


### 	Таблица адресации

| Устройство | Интерфейс | IP-адрес | Маска подсети |
| --- | --- | --- | --- |
| S1 | VLAN 1 | 192.168.1.1 | 255.255.255.0 |
| S2 | VLAN 1 | 192.168.1.2 | 255.255.255.0 |
| S3 | VLAN 1 | 192.168.1.3 | 255.255.255.0 |

# 	Цели

#### Часть 1. Создание сети и настройка основных параметров устройства


#### Часть 2. Выбор корневого моста


#### Часть 3. Наблюдение за процессом выбора протоколом STP порта, исходя из стоимости портов


#### Часть 4. Наблюдение за процессом выбора протоколом STP порта, исходя из приоритета портов


### Часть 1:	Создание сети и настройка основных параметров устройства

В этой части необходимо настроить топологию сети и основные параметры маршрутизаторов.

#### Шаг 1:	Создайте сеть согласно топологии:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic01.JPG)


#### Шаг 2:	Выполните инициализацию и перезагрузку коммутаторов:


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic02.JPG)


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic03.JPG)


#### Шаг 3:	Настройте базовые параметры каждого коммутатора.

Выполнены следующие операции:

a.	Отключите поиск DNS.

b.	Присвойте имена устройствам в соответствии с топологией.

c.	Назначьте class в качестве зашифрованного пароля доступа к привилегированному режиму.

d.	Назначьте cisco в качестве паролей консоли и VTY и активируйте вход для консоли и VTY каналов.

e.	Настройте logging synchronous для консольного канала.

f.	Настройте баннерное сообщение дня (MOTD) для предупреждения пользователей о запрете несанкционированного доступа.

g.	Задайте IP-адрес, указанный в таблице адресации для VLAN 1 на всех коммутаторах.

h.	Скопируйте текущую конфигурацию в файл загрузочной конфигурации.

Для коммутатора S1 :

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic04.JPG)


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic05.JPG)


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic06.JPG)


Для коммутатора S2 :

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic07.JPG)


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic08.JPG)


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic09.JPG)


Для коммутатора S3 :

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic10.JPG)


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic11.JPG)


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic12.JPG)



#### Шаг 4:	Проверьте связь.

Проверьте способность компьютеров обмениваться эхо-запросами. Скрин ниже.

Успешно ли выполняется эхо-запрос от коммутатора S1 на коммутатор S2?	*успешно*

Успешно ли выполняется эхо-запрос от коммутатора S1 на коммутатор S3?	*успешно*

Успешно ли выполняется эхо-запрос от коммутатора S2 на коммутатор S3?	*успешно*


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab07/pic13.JPG)


