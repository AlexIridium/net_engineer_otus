# Лабораторная работа - Конфигурация безопасности коммутатора 

### Топология:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_00.JPG)

### Таблица адресации:

| Устройство | interface/vlan | IP-адрес | Маска подсети |
| --- | --- | --- | --- |
| R1 | G0/0/1 | 192.168.10.1 | 255.255.255.0 |
| R1 | Loopback 0 | 10.10.1.1 | 255.255.255.0 |
| S1 | VLAN 10 | 192.168.10.201 | 255.255.255.0 |
| S2 | VLAN 10 | 192.168.10.202 | 255.255.255.0 |
| PC A | NIC | DHCP | 255.255.255.0 |
| PC B | NIC | DHCP | 255.255.255.0 |


## Цели

### Часть 1. Настройка основного сетевого устройства

•	Создайте сеть.

•	Настройте маршрутизатор R1.

•	Настройка и проверка основных параметров коммутатора


### Часть 2. Настройка сетей VLAN

•	Сконфигруриуйте VLAN 10.

•	Сконфигруриуйте SVI для VLAN 10.

•	Настройте VLAN 333 с именем Native на S1 и S2.

•	Настройте VLAN 999 с именем ParkingLot на S1 и S2.



### Часть 3: Настройки безопасности коммутатора

•	Реализация магистральных соединений 802.1Q.

•	Настройка портов доступа

•	Безопасность неиспользуемых портов коммутатора

•	Документирование и реализация функций безопасности порта.

•	Реализовать безопасность DHCP snooping .

•	Реализация PortFast и BPDU Guard

•	Проверка сквозной связанности.



### Часть 1. Настройка основного сетевого устройства

#### Шаг 1. Создайте сеть.

a.	Создайте сеть согласно топологии.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_01.JPG)


b.	Устройства инициализированы

#### Шаг 2. Настройте маршрутизатор R1.

a.	Загрузите следующий конфигурационный скрипт на R1.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_02.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_03.JPG)

P.S. команда *ip dhcp relay information trusted* не определяется моей версией Cisco PT:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_03.JPG)

В качестве аналога была применена команда *ip dhcp relay information trust-all*

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_05.JPG)


b.	Проверьте текущую конфигурацию на R1, используя следующую команду:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_06.JPG)

c.	IP-адресация и интерфейсы находятся в состоянии up / up.

#### Шаг 3. Настройка и проверка основных параметров коммутатора

Для S1 и S2 выполнены следующие действия:

a.	Настройте имя хоста для коммутаторов S1 и S2. Откройте окно конфигурации

b.	Запретите нежелательный поиск в DNS.

c.	Настройте описания интерфейса для портов, которые используются в S1 и S2.

d.	Установите для шлюза по умолчанию для VLAN управления значение 192.168.10.1 на обоих коммутаторах.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_07.JPG)


### Часть 2. Настройка сетей VLAN на коммутаторах.

#### Шаг 1. Сконфигруриуйте VLAN 10. 

Добавьте VLAN 10 на S1 и S2 и назовите VLAN - Management. *Скриншот ниже.*

#### Шаг 2. Сконфигруриуйте SVI для VLAN 10.

Настройте IP-адрес в соответствии с таблицей адресации для SVI для VLAN 10 на S1 и S2. Включите интерфейсы SVI и предоставьте описание для интерфейса. *Скриншот ниже.*

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_08.JPG)

#### Шаг 3. Настройте VLAN 333 с именем Native на S1 и S2.

*Скриншот ниже.*

#### Шаг 4. Настройте VLAN 999 с именем ParkingLot на S1 и S2.

*Скриншот ниже.*

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_10.JPG)

### Часть 3. Настройки безопасности коммутатора.

#### Шаг 1. Релизация магистральных соединений 802.1Q.

a.	Настройте все магистральные порты Fa0/1 на обоих коммутаторах для использования VLAN 333 в качестве native VLAN.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_11.JPG)

b.	Убедитесь, что режим транкинга успешно настроен на всех коммутаторах.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_12.JPG)

c.	Отключить согласование DTP F0/1 на S1 и S2. 

Необходимо отключить неиспользуемые порты и назначить их в неиспользуемой VLAN. Отключить согласование DTP (автоматические магистральные каналы) на немагистральных портах с помощью команды интерфейсной настройки *switchport mode access*

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_13.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_14.JPG)

d.	Проверьте с помощью команды *show interfaces.*

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_15.JPG)

#### Шаг 2. Настройка портов доступа

a.	На S1 настройте F0/5 и F0/6 в качестве портов доступа и свяжите их с VLAN 10.

b.	На S2 настройте порт доступа Fa0/18 и свяжите его с VLAN 10.


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_16.JPG)

#### Шаг 3. Безопасность неиспользуемых портов коммутатора

a.	На S1 и S2 переместите неиспользуемые порты из VLAN 1 в VLAN 999 (создал ранее VLAN 1000 для неисползуемых портов) и отключите неиспользуемые порты.

b.	Убедитесь, что неиспользуемые порты отключены и связаны с VLAN 999 (создал ранее VLAN 1000 для неисползуемых портов), введя команду  *show interfaces status*


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_17.JPG)

#### Шаг 4. Документирование и реализация функций безопасности порта.

Интерфейсы F0/6 на S1 и F0/18 на S2 настроены как порты доступа. На этом шаге вы также настроите безопасность портов на этих двух портах доступа.

a.	На S1, введите команду *show port-security interface f0/6*  для отображения настроек по умолчанию безопасности порта для интерфейса F0/6. Запишите свои ответы ниже.

Конфигурация безопасности порта по умолчанию:

| Функция | Настройка по умолчанию |
| --- | --- |
| Защита портов | Disabled |
| Максимальное количество записей MAC-адресов | 1 |
| Режим проверки на нарушение безопасности | Shutdown |
| Aging Time | 0 mins | 
| Aging Type | Absolute |
| Secure Static Address Aging | Disabled |
| Sticky MAC Address | 0 |

b.	На S1 включите защиту порта на F0 / 6 со следующими настройками:

o	Максимальное количество записей MAC-адресов: 3

o	Режим безопасности: restrict

o	Aging time: 60 мин.

o	Aging type: неактивный

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_18_1.JPG)


Команда *switchport port-security aging type inactivity* отсутствует в моей верси Cisco PT

d.	Включите безопасность порта для F0 / 18 на S2. Настройте каждый активный порт доступа таким образом, чтобы он автоматически добавлял адреса МАС, изученные на этом порту, в текущую конфигурацию.

e.	Настройте следующие параметры безопасности порта на S2 F / 18:

o	Максимальное количество записей MAC-адресов: 2

o	Тип безопасности: Protect

o	Aging time: 60 мин.

f.	Проверка функции безопасности портов на S2 F0/18:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_19_1.JPG)

#### Шаг 5. Реализовать безопасность DHCP snooping.

a.	На S2 включите DHCP snooping и настройте DHCP snooping во VLAN 10.

b.	Настройте магистральные порты на S2 как доверенные порты.

c.	Ограничьте ненадежный порт Fa0/18 на S2 пятью DHCP-пакетами в секунду.

d.	Проверка DHCP Snooping на S2.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_20.JPG)


e.	В командной строке на PC-B освободите, а затем обновите IP-адрес.

*C:\Users\Student> ipconfig /release*

*C:\Users\Student> ipconfig /renew*

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_21.JPG)

f.	Проверьте привязку отслеживания DHCP с помощью команды *show ip dhcp snooping binding*

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_22.JPG)

#### Шаг 6. Реализация PortFast и BPDU Guard

a.	Настройте PortFast на всех портах доступа, которые используются на обоих коммутаторах.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_23.JPG)

b.	Включите защиту BPDU на портах доступа VLAN 10 S1 и S2, подключенных к PC-A и PC-B.

Скрин ниже.

c.	Убедитесь, что защита BPDU и PortFast включены на соответствующих портах, используя команду *show spanning-tree interface f0/6 detail*

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_24.JPG)

#### Шаг 7. Проверьте наличие сквозного ⁪подключения.

Проверьте PING свзяь между всеми устройствами в таблице IP-адресации. 

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab09/pic_25.JPG)



### Вопросы для повторения

1.	С точки зрения безопасности порта на S2, почему нет значения таймера для оставшегося возраста в минутах, когда было сконфигурировано динамическое обучение - sticky?

*Ответ:

2.	Что касается безопасности порта на S2, если вы загружаете скрипт текущей конфигурации на S2, почему порту 18 на PC-B никогда не получит IP-адрес через DHCP?

*Ответ:

3.	Что касается безопасности порта, в чем разница между типом абсолютного устаревания и типом устаревание по неактивности?

*Ответ:










