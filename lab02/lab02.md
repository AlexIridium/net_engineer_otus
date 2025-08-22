# Лабораторная работа. Просмотр таблицы MAC-адресов коммутатора

### Топология

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic01.JPG)

### Таблица адресации

| Устройство | Интерфейс | IP-адрес | Маска подсети |
| --- | --- | --- | --- |
| S1 | VLAN 1 | 192.168.1.11 | 255.255.255.0 |
| S2 | VLAN 1 | 192.168.1.12 | 255.255.255.0 |
| PC-A | NIC | 192.168.1.1 | 255.255.255.0 |
| PC-B | NIC | 192.168.1.2 | 255.255.255.0 |


## Цели

   ### Часть 1. Создание и настройка сети

   #### Шаг 1. Схема подключения сети.

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic01.JPG)


   #### Шаг 2. Настройка узлов ПК.

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic06.JPG)


   #### Шаг 3. Инициализация и перезагрузка коммутаторов.

   Коммутатор S1:

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic07_1.JPG)

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic07_2.JPG)

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic07_3.JPG)

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic07_4.JPG)



   Коммутатор S2:

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic08_1.JPG)

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic08_2.JPG)

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic08_3.JPG)

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic08_4.JPG)


   #### Шаг 4. Выполнение базовых настроек каждого коммутатора


   a) Настройка имен устройств с соответствующей топологией через вкладку Config:

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic09.JPG)


   b) Настройка IP-адресов согласно таблицы адресации:

   Коммутатор S1:

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic10.JPG)


   Коммутатор S2:

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic11.JPG)


   c) Назначение пароля *cisco* для консоли и VTY



   d) Назначение пароля *class* для доступа к привилегированному режиму EXEC.

   

   

   ### Часть 2. Изучение таблицы MAC-адресов коммутатора

   #### Шаг 1. MAC-адреса сетевых устройств

         а) На РС-А и РС-В через команду ipconfig /all выведены MAC-адреса компьютеров:
         
   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic02.JPG)

         b) Используя консоль, подключились к коммутаторам S1, S2 и ввели команду show interfaces F0/1:

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic03.JPG)

   #### Шаг 2. Просмотр таблицы MAC-адресов коммутатроа.

       a,b) Таблица MAC-адресов коммутатора S2 :

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic04.JPG)

На рисунке выше указан только один MAC-адрес подключенного коммутатора S1. Данный MAC-адрес подключен к порту Fa0/1 и имеет динамический тип.
       
В случае если ранее мы не записывали MAC-адреса других устройств, то вероятно, можно определить MAC-адрес хоста отсоединяя поочередно кабеля связи от коммутатора S1, но данное решение не будет работать при обеспечении непрерывной работы какого-либо сервиса (запрещено отключать).

   #### Шаг 3. Очистка таблицы MAC-адресов коммутатора S2 и снова отбражение таблицы MAC-адресов.

   a,b) В привилегированном режиме EXEC введены команды по очистке таблицы MAC-адресов, команда проверки MAC-адресов сразу после очистки и через 10 сек после очистки. Скриншот ниже:

   ![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab02/pic05.JPG)

   Сразу после очистки таблицы MAC-адресов в ней отсутствовала какая-либо информация. Прежний MAC-адрес появился спустя некоторое непродолжительное время. Новых MAC-адресов в таблице не появилось.

   #### Шаг 4. С компьютера РС-В отправка эхо-запросов на устройства в сети и просмотр MAC-адресов коммутатора.

         
        
    
   

   




