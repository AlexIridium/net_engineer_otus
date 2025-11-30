# Лабораторная работа. Настройка и проверка расширенных списков контроля доступа.

### Топология

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_00.JPG)

### Таблица адресации

| Устройство | Интерфейс | IP-адрес | Маска подсети  | Шлюз по умолчанию |
| --- | --- | --- | --- | --- |
| R1 | G0/0/1 | - | - | - |
| R1 | G0/0/1.20 | 10.20.0.1 | 255.255.255.0 | - |
| R1 | G0/0/1.30 | 10.30.0.1 | 255.255.255.0 | - |
| R1 | G0/0/1.40 | 10.40.0.1 | 255.255.255.0 | - |
| R1 | G0/0/1.1000 | - | - | - |
| R1 | Loopback1 | 172.16.1.1 | 255.255.255.0 | - |
| R2 | G0/0/1 | 10.20.0.4 | 255.255.255.0 | - |
| S1 | VLAN 20 | 10.20.0.2 | 255.255.255.0 | 10.20.0.1 |
| S2 | VLAN 20 | 10.20.0.3 | 255.255.255.0 | 10.20.0.1 |
| PC-A | NIC | 10.30.0.10 | 255.255.255.0 | 10.30.0.1 |
| PC-B | NIC | 10.40.0.10 | 255.255.255.0 | 10.40.0.1 |

### Таблица VLAN

| VLAN | Имя | Назначенный интерфейс |
| --- | --- | --- |
| 20 | Management | S2: F0/5 |
| 30 | Operations | S1: F0/6 |
| 40 | Sales | S2: F0/18 |
| 999 | ParkingLot | S1: F0/2-4, F0/7-24, G0/1-2; S2: F0/2-4, F0/6-17, F0/19-24, G0/1-2 |
| 1000 | Собственная | - |


## Задачи

### Часть 1. Создание сети и настройка основных параметров устройства

### Часть 2. Настройка и проверка списков расширенного контроля доступа


## Ход Работы

### Часть 1. Создание сети и настройка основных параметров устройства

#### Шаг 1. Создайте сеть согласно топологии.

Подключите устройства, как показано в топологии, и подсоедините необходимые кабели.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_01.JPG)

#### Шаг 2. Произведите базовую настройку маршрутизаторов.

a.	Назначьте маршрутизатору имя устройства.

b.	Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

c.	Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

d.	Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

e.	Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

f.	Зашифруйте открытые пароли.

g.	Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

h.	Сохраните текущую конфигурацию в файл загрузочной конфигурации.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_02.JPG)


#### Шаг 3. Настройте базовые параметры каждого коммутатора.

a.	Присвойте коммутатору имя устройства.

b.	Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

c.	Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

d.	Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

e.	Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

f.	Зашифруйте открытые пароли.

g.	Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

h.	Сохраните текущую конфигурацию в файл загрузочной конфигурации.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_03.JPG)


### Часть 2. Настройка сетей VLAN на коммутаторах.

#### Шаг 1. Создайте сети VLAN на коммутаторах.

a.	Создайте необходимые VLAN и назовите их на каждом коммутаторе из приведенной выше таблицы. Скрин ниже.

b.	Настройте интерфейс управления и шлюз по умолчанию на каждом коммутаторе, используя информацию об IP-адресе в таблице адресации. Скрин ниже.

c.	Назначьте все неиспользуемые порты коммутатора VLAN Parking Lot, настройте их для статического режима доступа и административно деактивируйте их. Скрин ниже.

Примечание. Команда interface range полезна для выполнения этой задачи с помощью необходимого количества команд. 

Для S1:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_04.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_05.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_06.JPG)



Для S2:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_08.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_09.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_10.JPG)


#### Шаг 2. Назначьте сети VLAN соответствующим интерфейсам коммутатора.

a.	Назначьте используемые порты соответствующей VLAN (указанной в таблице VLAN выше) и настройте их для режима статического доступа.Скрин ниже.

b.	Выполните команду show vlan brief, чтобы убедиться, что сети VLAN назначены правильным интерфейсам. Скрин ниже.

Для S1:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_07.JPG)

Для S2:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_11.JPG)


### Часть 3. ·Настройте транки (магистральные каналы).

#### Шаг 1. Вручную настройте магистральный интерфейс F0/1.

a.	Измените режим порта коммутатора на интерфейсе F0/1, чтобы принудительно создать магистральную связь. Не забудьте сделать это на обоих коммутаторах. Скрин ниже.

b.	В рамках конфигурации транка установите для native vlan значение 1000 на обоих коммутаторах. При настройке двух интерфейсов для разных собственных VLAN сообщения об ошибках могут отображаться временно. Скрин ниже.

c.	В качестве другой части конфигурации транка укажите, что VLAN 20, 30, 40 и 1000 разрешены в транке. Скрин ниже.

d.	Выполните команду show interfaces trunk для проверки портов магистрали, собственной VLAN и разрешенных VLAN через магистраль.

S1:


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_30_s.JPG)



S2:



![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_32_s.JPG)


#### Шаг 2. Вручную настройте магистральный интерфейс F0/5 на коммутаторе S1.

a.	Настройте интерфейс S1 F0/5 с теми же параметрами транка, что и F0/1. Это транк до маршрутизатора. Скрин выше

b.	Сохраните текущую конфигурацию в файл загрузочной конфигурации.

c.	Используйте команду show interfaces trunk для проверки настроек транка. скрин выше.



![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_31_s.JPG)


### Часть 4. Настройте маршрутизацию.

#### Шаг 1. Настройка маршрутизации между сетями VLAN на R1.

a.	Активируйте интерфейс G0/0/1 на маршрутизаторе. Скрин ниже.

b.	Настройте подинтерфейсы для каждой VLAN, как указано в таблице IP-адресации. Все подинтерфейсы используют инкапсуляцию 802.1Q. Убедитесь, что подинтерфейс для собственной VLAN не имеет назначенного IP-адреса. Включите описание для каждого подинтерфейса. Скрин ниже.

c.	Настройте интерфейс Loopback 1 на R1 с адресацией из приведенной выше таблицы. Скрин ниже.

d.	С помощью команды show ip interface brief проверьте конфигурацию подынтерфейса.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_18.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_19.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_20.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_21.JPG)

#### Шаг 2. Настройка интерфейса R2 g0/0/1 с использованием адреса из таблицы и маршрута по умолчанию с адресом следующего перехода 10.20.0.1

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_22.JPG)




### Часть 5. Настройте удаленный доступ

#### Шаг 1. Настройте все сетевые устройства для базовой поддержки SSH.

a.	Создайте локального пользователя с именем пользователя SSHadmin и зашифрованным паролем $cisco123!

b.	Используйте ccna-lab.com в качестве доменного имени.

c.	Генерируйте криптоключи с помощью 1024 битного модуля.

d.	Настройте первые пять линий VTY на каждом устройстве, чтобы поддерживать только SSH-соединения и с локальной аутентификацией.


For S1:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_23.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_24.JPG)


For R1:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_25.JPG)

For S2:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_26.JPG)

For R2:

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_27.JPG)



#### Шаг 2. Включите защищенные веб-службы с проверкой подлинности на R1.

a.	Включите сервер HTTPS на R1.

*R1(config)# ip http secure-server* в моей версии Cisco PT отсутствует возножность запустить данную команду. Скрин ниже.

b.	Настройте R1 для проверки подлинности пользователей, пытающихся подключиться к веб-серверу.

*R1(config)# ip http authentication local* в моей версии Cisco PT отсутствует возножность запустить данную команду. Скрин ниже.


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_28.JPG)


### Часть 6. Проверка подключения

#### Шаг 1. Настройте узлы ПК.

Адреса ПК можно посмотреть в таблице адресации.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_29.JPG)

#### Шаг 2. Выполните следующие тесты. Эхозапрос должен пройти успешно.



| От | Протокол | Назначение |
| --- | --- | --- |
| PC-A | Ping | 10.40.0.10 |
| PC-A | Ping | 10.20.0.1 |
| PC-B | Ping | 10.30.0.10 |
| PC-B | Ping | 10.20.0.1 |
| PC-B | Ping | 172.16.1.1 |
| PC-B | HTTPS | 10.20.0.1 |
| PC-B | HTTPS | 172.16.1.1 |
| PC-B | SSH | 10.20.0.1 |
| PC-B | SSH | 172.16.1.1 |


![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_33.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_34.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_35.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_36.JPG)

Примечание. Так как HTTPS отсутствует, проверка с данным сервисом не произведена.


### Часть 7. Настройка и проверка списков контроля доступа (ACL)

При проверке базового подключения компания требует реализации следующих политик безопасности:

Политика1. Сеть Sales не может использовать SSH в сети Management (но в  другие сети SSH разрешен). Скриншот ниже.

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_37.JPG)

Политика 2. Сеть Sales не имеет доступа к IP-адресам в сети Management с помощью любого веб-протокола (HTTP/HTTPS). Сеть Sales также не имеет доступа к интерфейсам R1 с помощью любого веб-протокола. Разрешён весь другой веб-трафик (обратите внимание — Сеть Sales  может получить доступ к интерфейсу Loopback 1 на R1).

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_48.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_49.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_50.JPG)



Политика3. Сеть Sales не может отправлять эхо-запросы ICMP в сети Operations или Management. Разрешены эхо-запросы ICMP к другим адресатам. 

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_42.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_51.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_52.JPG)



Политика 4: Cеть Operations  не может отправлять ICMP эхозапросы в сеть Sales. Разрешены эхо-запросы ICMP к другим адресатам. 

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_53.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_54.JPG)

#### Шаг 1. Проанализируйте требования к сети и политике безопасности для планирования реализации ACL.

#### Шаг 2. Разработка и применение расширенных списков доступа, которые будут соответствовать требованиям политики безопасности.

#### Шаг 3. Убедитесь, что политики безопасности применяются развернутыми списками доступа.

Выполните следующие тесты. Ожидаемые результаты показаны в таблице, скрины ниже.

| От | Протокол | Назначение | Результат |
| --- | --- | --- | --- |
| PC-A | Ping | 10.40.0.10 | Сбой |
| PC-A | Ping | 10.20.0.1 | Успех |
| PC-B | Ping | 10.30.0.10 | Сбой |
| PC-B | Ping | 10.20.0.1 | Сбой |
| PC-B | Ping | 172.16.1.1 | Успех |
| PC-B | HTTPS | 10.20.0.1 | Сбой |
| PC-B | HTTPS | 172.16.1.1 | Успех |
| PC-B | SSH | 10.20.0.4 | Сбой |
| PC-B | SSH | 172.16.1.1 | Успех |

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_55.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_56.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_57.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_58.JPG)

![](https://github.com/AlexIridium/net_engineer_otus/blob/main/lab11/pic_59.JPG)









