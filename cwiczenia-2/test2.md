Ustawianie parametrów sieci
---------------------------

![alt text][network]

[network]: ./network.png "Logo Title Text 2"

1. na 1 z komputerów zainstaluj oprogramowanie ``http-chat`` dostępne pod adresem ``https://github.com/jkanclerz/http-chat``

Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  debian | |
| IP - address  | 10.0.2.15 | |
| MASKA  | /24 | |
|   |  | |
| PC 2  | debian | |
| IP - address  |10.0.2.4 | |
| MASKA  | /24 | |

Weryfikacja połączenia
```
ping
```

Polecenie
```
ping 10.0.2.15
ping 10.0.2.4
```

Efekt
```
64 bytes from 10.0.2.15: icmp_seq=1 ttl = 64 time = 0.187 ms
64 bytes from 10.0.2.4: icmp_seq=1 ttl = 64 time = 0.275 ms
```

Statyczna konfiguracja parametrów połączenia
Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 192.168.10.10 | |
| MASKA  | 255.255.255.0 | |
|   |  | |
| PC 2  |  | |
| IP - address  | 172.16.100.100 | |
| MASKA  | 255.255.0.0 | |

Weryfikacja połączenia

Polecenie
```
```

Efekt
```
```

Nowa statyczna konfiguracja 

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  |  | |
| MASKA  |  | |
|   |  | |
| PC 2  |  | |
| IP - address  |  | |
| MASKA  |  | |

Weryfikacja połączenia

Polecenie
```
```

Efekt
```
```

Warto wiedzieć
--------------

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
| Lokalizacja pliku z konfiguracją sieci| /etc/network/interfaces (dla Ubuntu/Debian) /etc/sysconfig/network (dla Red Hat/Fedora/CentOS) | |
| UP -> Włączenie interfejsu sieciowego| if up | |
| DOWN -> Wyłączenie interfejsu sieciowego| ifdown | |
| Sprawdzenie obecnych parametrów | nmcli | |
| lista wszystkich interfejsów | ip a | |
| Które interfejsy jakie porty słuchają | netstat | |

Komendy:
```
ip a
nmcli
ifup enp0s3
apt-get install git - instalacja gita (na debian)
yum install git - instalacja gita (ns centos)
su <- root
ping
iptables -F
git copy https://github.com/jkanclerz/http-chat <- clone z gita, potem: cd http-chat -> cd server -> python httpchat.py

su - > apt update -> apt install git git clone https://github.com/jkanclerz/http-chat cd /http-chat/server python httpchat.py
```

Pobranie wiadomości:
```
curl -X POST -d '{"text": "Hello World"}' http://{ip_address}:8888
```

Odebranie wiadomości:
```
curl -X POST -d '{"last_message_id":-1}' http://{ip_address}:8888/messages | python -m json.tool
```
