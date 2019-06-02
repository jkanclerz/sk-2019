# firewall

  * https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-iptables
  * https://linux.die.net/man/8/iptables

## iptables

### tabele / tables (-t)

| tabela    |  przeznaczenie   | 
| ------------- |:-------------| 
|   ``nat``    |   NAT / przekierowania          |
|   ``filter``    |  filtrowanie                 |
|   ``mangle``    |  modyfikacje, (ex. TTL       |

### łańcuchy / chains iptab

![input](input.svg)

![output](output.svg)

![forward](forward.svg)


| łańcuch    |  przeznaczenie   | 
| ------------- |:-------------| 
|   ``INPUT``    |                               |
|   ``OUTPUT``    |                              |
|   ``FORWARD``    |                             |
|   ``PREROUTING``    |                          |
|   ``POSTROUTING``    |                         |

### co zrobić / target (-j)

|     |  przeznaczenie   | 
| ------------- |:-------------| 
|   ``ACCEPT``    |                               |
|   ``DROP``    |                              |
|   ``REJECT``    |                             |
|   ``LOG``    |                             |


### Użycie

```bash
iptables -A -i <interface> -p <protocol (tcp/udp) -s <source> --dport <port> -j <target>

dhclient -v {interfejs} - resetowanie żeby przyznało adresy
iptables -A INPUT -p tcp --dport 80 -j ACCEPT - akceptowanie komunikacji z portem 80(http)
iptables -D -||- -||- - usuwa regułę

ipatables-save > /etc/iptables.up.rules
iptables-restore < /etc/iptables.up.rules
dodać do /etc/network/interfaces
post-up iptables-restore < /etc/iptables.up.rules (savować kolejne reguły trzeba ręcznie)

żeby kolejne interfejsy wstawały przy boocie
auto {interface}
iface {interface} inet dhcp/static
```

### wykorzystanie

* Lista obecnych reguł 
  * format tabeli
  * format listy
* Czyszczenie obecnych reguł aka flush
* Domyślne zachowanie ACCEPT / DROP
* Zezwolenie na połączenie dla konkretnego portu
* NAT
  * Przekierowanie portów ip:port -> ip2:port
  * Przekierowanie portów ip:port1 -> ip2:port2

### Zadanie 


1.
   * Przygotuj konfigurację sieci gdzie ``PC0`` pełni rolę bramy NAT
   * Przygotuj konfigurację sieci gdzie ``PC1`` udostępnia usługi
   
2. * Rozbuduj konfigurację sieci dla ``PC0`` o kolejny interfejs umożliwiający komunikację z hostem ``host-only`` 
  Zabezpiecz ``PC1`` konfigurując firewall z wykorzystanie ``iptables`` tak aby zezwolicz na połącznia przychodzace
 z portem 22 (SSH) włącznie z lokalnej sieci (komputera hosta)
   * Ustaw domyślne polityki dla INPUT, OUTPUT, FORWARD kolejno, DROP, ACCEPT, ACCEPT
   * Zapisz konfigurację firewall, tak aby została odtworzona po konownym uruchomieniu maszyny
   * Zweryfikuj możliwość połączenia wykorzystując program putty (klient SSH)

3. * Skonfiguruj ``NAT`` dla PC0
   * Zweryfikuj poprawność konfiguracji dla ``PC1`` pingując dowolny adres publiczny
   * Zainstaluj serwer http ``apache`` lub ``nginx``
   * dokonaj przekierowania portów tak aby odwiedzając w przeglądarce adres w sieci ``host-only `` dla ``PC0``
     wyświetlona została strona startowa serwera zainstaloanego dla ``PC1`` 

4. * Zainstaluj program ``udp-echo-serwer`` dla ``PC1`` oraz ``udp-echo-client`` dla ``PC0``
   * skonfiguruj firewall dla ``PC1`` tak aby umożliwiał połączenia przychodzące wyłącznie dla następujacych portów
    * 80
    * 65433
   * zapewnij aby konfiguracja została załadowana po każdym uruchomieniu systemu
   * sprawdź konfigurację wykonując testowe polączenie na wskazanych wyżej portach
   * zweryfikuj brak możliwości ustanowienia połączenia na porcie 22 (SSH)
