Ustawianie parametrów sieci ip
------------------------------

* stan interfejsu
    * interfejs up
    * interfejs down
* adresacja
    * dodaj adres
    * zmień adres
    * usuń adres
* routing
    * dodaj trasę default
    * dodaj trasę przez bramę
    * dodaj trasę przez interfejs
    * usuń trasę
    * zmień trasę
    * pobierz trasę dla adresu
* adresacja fizyczna
    * pokaż adresy interfejsów dostępnych w sieci
    * pokaż adresy dla konkretnego interfejsu
     


ip 
-------------------------
| subcommand    |  polecenie   | opis  |
| ------------- |:-------------| :---------------| 
|   ``addr``    |                                | infirmacje o adresacji i własnościach interfejsów |
|               |   ``ip addr``                  | informacja o wszystkich interfejsach              |
|               |   ``ip addr show dev enp0s3``  | informacja o konkretnym interfejsie               |
|               |``ip addr add {ip} dev {nazwa}``|    dodaj ip                                       |
|               |``ip addr del {ip} dev {nazwa}``|      usuń ip                                      |
|   ``link``    |                                |  |
|               | ``ip link set enp0s3 down``    | wyłącz |
|               | ``ip link set {nazwa} up``     | włącz |
|   ``route``   |  | |
|               | ``ip route show`` | pokazuje tablice routingu |
|               | ``ip route get {ip}`` | którym interfejsem poleci pakiet|
|               | ``ip route add default via {ip}`` | dodanie domyślnego adresu routingu |
|               | ``ip route del {ip}`` | |
|               | ``ip route add {ip} via {ip}`` | |
|               | ``ip rotue add {ip} dev {nazwa}`` | |
|               | ``echo 1 > /proc/sys/net/ipv4/ip_forward`` | włączanie forwardowania ip |
|               | /etc/sysctl.d/99-sysctl.conf | odkomentować ipforwarding
|   ``maddr``   |  | |
|   ``neigh``   |  | |
|   ``help``    |  | |

**********************************
```
statyczny config

nano /etc/network/interfaces

allow-hotplug enp0s3
iface enp0s3 inet static
   address 192.168.100.1
   netmask 255.255.255.0
 
auto enp0s8
iface enp0s8 inet static
   address 192.168.200.1
   netmask 255.255.255.0
   up ip route add 192.168.0.0/24 via 192.168.200.2
   down ip route del 192.168.0.0/24
zresetować
```
**************************************
DNS
/etc/resolv.conf

Zadanie
------------

![zadanie 3](cwiczenia3.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem, 
   * Przetestuj połączenie poleceniem ping
2.
   * Zainstaluj na komputerze ``PC1`` serwer programu ``HTTP CHAT`` dostępnego pod adresem ``https://github.com/jkanclerz/http-chat``
   * Przetestuj komunikację wysyłając wiadomość z komputera ``PC2``, upewnij się czy jest widoczna w konsoli serwera
3.
   * Dodaj do istniejącej sieci komputer ``PC3`` pod kontroloą systemu windows
   * Skonfiguruj ``PC3`` zgodnie z poniższym diagramem
   * Zweryfkuj połączenie kożystając z przeglądarki, odwiedzając graficzny interfejs ``HTTP CHAT`` pod adresem ``http://172.16.100.10:8888``
   * Przygotuj dokumentację pisemno obrazkową z wykonania zadania w formacie ``markdown`` zamieść ją w serwisie ``github.com`` obok obocnego tematu ``cwiczenia-3``
