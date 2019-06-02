#1. Podział sieci
---------
a) maska sieci:
  dla 500 urządzeń jest to ``255.255.254.0`` (/23)
  dla 5000 urządzeń jest to ``255.255.224.0`` (/19)
  
b) podział sieci:
  pierwsza sieć ``LAN1``: zaczyna się od IP ``172.22.128.0`` (bazowe)
  druga sieć ``LAN2``: jako, że sieć ``LAN1`` posiada (2^(32-2)-2 = 510 adresów), to następna (dla /19) zacząć się może dopiero od adresu ``172.22.160.0``
  
  Podsumowując adresy sieci:
    ``LAN1``: 172.22.128.0/23
    ``LAN2``: 172.22.160.0/19

#2.Konfiguracja interfejsów PC0
---------
### /etc/network/interfaces
```auto enp0s8
iface enp0s8 inet static
  adress 172.22.128.1
  netmask 255.255.254.0
atuo anp0s9
iface enp0s9 inet static
  adress 172.22.160.1
  netmask 255.255.224.0```
