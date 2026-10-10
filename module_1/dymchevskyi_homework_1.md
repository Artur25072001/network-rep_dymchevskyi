<!-- Завдання 1. Дослідження мережі -->

artyr@Arhivar:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
valid_lft forever preferred_lft forever
inet 10.255.255.254/32 brd 10.255.255.254 scope global lo
valid_lft forever preferred_lft forever
inet6 ::1/128 scope host
valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
link/ether 10:ff:e0:01:5e:5c brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
link/ether 0a:00:27:00:00:1a brd ff:ff:ff:ff:ff:ff
4: loopback0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
link/ether 00:15:5d:39:45:ae brd ff:ff:ff:ff:ff:ff
5: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
link/ether ec:75:0c:42:86:e5 brd ff:ff:ff:ff:ff:ff
inet 192.168.2.19/24 brd 192.168.2.255 scope global noprefixroute eth2
valid_lft forever preferred_lft forever
inet6 fe80::e1c0:1921:72c5:1e5/64 scope link nodad noprefixroute
valid_lft forever preferred_lft forever

Інтерфейс : eth2
Тип підключення : Ethernet (дротове локальне підключення)
MAC-адреса ec:75:0c:42:86:e5
IP-адреса 192.168.2.19 — 3-й рівень моделі OSI
Маска мережі/24 (або 255.255.255.0) — 3-й рівень моделі OSI
Gateway 192.168.2.1
Broadcast 192.168.2.255
Кількість хостів 254 доступних IP-адрес для пристроїв у цій підмережі

<!-- Завдання 2. Дослідження маршрутизації  -->

artyr@Arhivar:~$ ip r
default via 192.168.2.1 dev eth2 proto kernel metric 35
192.168.2.0/24 dev eth2 proto kernel scope link metric 291
192.168.2.1 dev eth2 proto kernel scope link metric 35

1. Результат виконання команди
   Дефолтний маршрут :
   default via 192.168.2.1 dev eth2 proto kernel metric 35

Маршрут до локальної підмережі:
192.168.2.0/24 dev eth2 proto kernel scope link metric 291

Маршрут до конкретної IP-адреси шлюзу:
192.168.2.1 dev eth2 proto kernel scope link metric 35

2. Протокол маршрутизації
   Протокол: kernel ( це ядро операційної системи Linux)

<!-- Завдання 3. Знаходження публічної IP-адреси  -->

artyr@Arhivar:~$ curl ifconfig.io
174.91.111.80

<!-- Вони однакові? -->

різні бо
Локальна адреса: 192.168.2.19
Публічна адреса: 174.91.111.80

<!-- Якщо різні, то чому?  -->

тому що локальна адреса вона потрібна тільки для приватної мережі щоб ідентифікувати мій пк, а ось публічна адреса це вже адреса яку виділив мій провайдер на мене і вона унікальна в мережі і мій роутер працює як NAT щоб працювати як шлюз між локальною та публічню адресою
