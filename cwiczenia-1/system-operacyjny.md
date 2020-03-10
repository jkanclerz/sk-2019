System operacyjny w środowisku sieciowym
=========================================

Charakterystyka systemu operacyjnego
------------------------------------

| Charakterystyka | wartość           | komentarzu |
| ------------- |:-------------:| -----:|
| nazwa      | linux | debian 9 |
| program (parametry sieci)      | terminal |  |


Konfiguracja połączenia sieciowego
----------------------------------

| Parametr | wartość           | komentarzu |
| ------------- |:-------------:| -----:|
| Adres IP      | 10.0.2.15 | przydzielony przez DHCP |
| Maska podsieci      | /24 |  |
| Brama      | 10.0.2.2 |  |
| DNS 1      | 192.168.1.1 |  |
| DNS 2      |  |  |

Schemat sieci
-------------

![alt schemat](schemat.png)

Komendy:
- ip addr show
- ip route
- nmcli
