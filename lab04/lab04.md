# Лабораторная работа. Настройка IPv6-адресов на сетевых устройствах 

### Топология:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic00.JPG)


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic16.JPG)


### Таблица адресации:

| Устройство | Интерфейс | IPv6-адрес | Link local IPv6-адрес | Длина префикса | Шлюз по умолчанию |
| :--- | --- | --- | --- | --- | --- |
| R1 | G0/0/0 | 2001:db8:acad:a::1 | fe80::1 | 64 | - |
| R1 | G0/0/1 | 2001:db8:acad:1::1  | fe80::1 | 64 | - |
| S1 | VLAN 1 | 2001:db8:acad:1::b | fe80::b | 64 | - |
| PC-A | NIC | 2001:db8:acad:1::3 | SLACC | 64 | - |
| PC-B | NIC | 2001:db8:acad:a::3 | SLACC | 64 | - |


## Задачи

### Часть 1. Настройка топологии и конфигурация основных параметров маршрутизатора и коммутатора


#### Шаг 1. Базовые настройка маршрутизатора

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic09.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic10.JPG)



#### Шаг 2. Базовые настройки коммутатора

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic11.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic12.JPG)




### Часть 2. Ручная настройка IPv6-адресов

#### Шаг 1. Установка IPv6-адреса интерфейсу Ethernet на R1.


       a, b, c, d) Назначен глобальный индивидуальный IPv6-адрес, указанный в таблице адресации обоим интерфейсам Ethernet на R1. Обеспечено соответствие локальных адресов канала индивидуальному адресу, вручную введен локальный адреса канала на каждом интерфейсе Ethernet на R1. Проверено, что локальный адрес связи изменен на fe80::1. Скриншоты ниже:  


Установка IPv6 адреса и перезагрузка маршрутизатора:


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic01.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic02.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic03.JPG)


Установка и проверка link-local адреса:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic04.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic05.JPG)


*Какие группы многоадресной рассылки назначены интерфейсу G0/0?*




#### Шаг 2. Активация IPv6-маршрутизацию на R1.

        a)	В командной строке на PC-B введена команда ipconfig, чтобы получить данные IPv6-адреса, назначенного интерфейсу ПК:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic13.JPG)


       Индивидуальный IPv6-адрес сетевой интерфейсной карте (NIC) на PC-B назначен.


       b)	В Части 1 Шаг 1 была активирована IPv6-маршрутизация на R1 с помощью команды IPv6 unicast-routing.

       c)	R1 входит в группу многоадресной рассылки всех маршрутизаторов. 
       
*Вопрос: Почему PC-B получил глобальный префикс маршрутизации и идентификатор подсети, которые вы настроили на R1?*




#### Шаг 3. Назначение IPv6-адреса интерфейсу управления (SVI) на S1.

      a)	Назначение адреса IPv6 для S1, назначение этому интерфейсу локального адреса канала fe80::b  :

  ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic07.JPG)

      
     b)	Проверка правильности назначения IPv6-адресов интерфейсу управления с помощью команды show ipv6 interface vlan1.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic08.JPG)


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic14.JPG)


#### Шаг 4. Назначение компьютерам статических IPv6-адресов.

     a, b)	В свойствах Ethernet для каждого ПК назначен адрес IPv6 согласно исходной таблицы адресов. Оба компьютера имеют правильную информацию адреса IPv6. Каждый компьютер имеет два глобальных адреса IPv6: один статический и один SLACC. Скриншот ниже:
     

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic15.JPG)



### Часть 3. Проверка сквозного соединения

      С PC-A отправлен эхо-запрос на FE80::1. Это локальный адрес канала, назначенный G0/1 на R1:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic17.JPG)

      
      Отправлен эхо-запрос на интерфейс управления S1 адрес IPv6 и link local адрес IPv6  с PC-A:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic18.JPG)


       Введена команда tracert на PC-A, чтобы проверить наличие сквозного подключения к PC-B:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic19.JPG)


       С PC-B отправлен эхо-запрос на PC-A. С PC-B отправлен эхо-запрос на локальный адрес канала G0/0 на R1:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab04/pic20.JPG)


       Успешные эхо-запросы подтверждают правильность подключения, а также подтверждают ,что IPv6-адреса на всех устройствах указаны верно.




#### Вопросы для повторения:
       
1.	Почему обоим интерфейсам Ethernet на R1 можно назначить один и тот же локальный адрес канала — FE80::1?
2.	Какой идентификатор подсети в индивидуальном IPv6-адресе 2001:db8:acad::aaaa:1234/64?


