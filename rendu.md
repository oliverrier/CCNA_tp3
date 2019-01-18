# TP 3 - Plusieurs réseaux : routage statique

## I. Utilisation simple d'une VM CentOS

---

### 5. Faire joujou avec quelques commandes

---

#### Ping

- Ping Hôte -> VM

```powershell
PS C:\Users\Irohn> ping 192.168.127.10

Envoi d’une requête 'Ping'  192.168.127.10 avec 32 octets de données :
Réponse de 192.168.127.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.127.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.127.10 : octets=32 temps<1ms TTL=64
```

- Ping VM -> Hôte

```bash
[iroh@localhost ~]$ ping 192.168.127.1
PING 192.168.127.1 (192.168.127.1) 56(84) bytes of data.
64 bytes from 192.168.127.1: icmp_seq=1 ttl=128 time=0.255 ms
64 bytes from 192.168.127.1: icmp_seq=2 ttl=128 time=0.590 ms
64 bytes from 192.168.127.1: icmp_seq=3 ttl=128 time=0.597 ms
64 bytes from 192.168.127.1: icmp_seq=4 ttl=128 time=0.656 ms
64 bytes from 192.168.127.1: icmp_seq=5 ttl=128 time=0.701 ms
64 bytes from 192.168.127.1: icmp_seq=6 ttl=128 time=0.650 ms
64 bytes from 192.168.127.1: icmp_seq=7 ttl=128 time=0.722 ms
64 bytes from 192.168.127.1: icmp_seq=8 ttl=128 time=0.670 ms
64 bytes from 192.168.127.1: icmp_seq=9 ttl=128 time=0.579 ms
64 bytes from 192.168.127.1: icmp_seq=10 ttl=128 time=0.716 ms
^C
--- 192.168.127.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9017ms
rtt min/avg/max/mdev = 0.255/0.613/0.722/0.131 ms

```

---

#### Table de routage

- Table de routage Host

```powershell
PS C:\Users\Irohn> route print -4
===========================================================================
Liste d Interfaces
 17...0a 00 27 00 00 11 ......VirtualBox Host-Only Ethernet Adapter
  4...02 00 4c 4f 4f 50 ......Npcap Loopback Adapter
 64...0a 00 27 00 00 40 ......VirtualBox Host-Only Ethernet Adapter #2
 20...34 f3 9a f9 50 9d ......Microsoft Wi-Fi Direct Virtual Adapter
  7...36 f3 9a f9 50 9c ......Microsoft Wi-Fi Direct Virtual Adapter #2
 15...00 50 56 c0 00 01 ......VMware Virtual Ethernet Adapter for VMnet1
  5...00 50 56 c0 00 08 ......VMware Virtual Ethernet Adapter for VMnet8
 10...34 f3 9a f9 50 9c ......Intel(R) Dual Band Wireless-AC 8260
 21...34 f3 9a f9 50 a0 ......Bluetooth Device (Personal Area Network)
  1...........................Software Loopback Interface 1
===========================================================================

IPv4 Table de routage
===========================================================================
Itinéraires actifs :
Destination réseau    Masque réseau  Adr. passerelle   Adr. interface Métrique
          0.0.0.0          0.0.0.0      10.33.3.253        10.33.2.6     35
        10.33.0.0    255.255.252.0         On-link         10.33.2.6    291
        10.33.2.6  255.255.255.255         On-link         10.33.2.6    291
      10.33.3.255  255.255.255.255         On-link         10.33.2.6    291
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    331
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    331
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    331
      169.254.0.0      255.255.0.0         On-link   169.254.185.209    281
  169.254.185.209  255.255.255.255         On-link   169.254.185.209    281
  169.254.255.255  255.255.255.255         On-link   169.254.185.209    281
     192.168.19.0    255.255.255.0         On-link      192.168.19.1    291
     192.168.19.1  255.255.255.255         On-link      192.168.19.1    291
   192.168.19.255  255.255.255.255         On-link      192.168.19.1    291
     192.168.47.0    255.255.255.0         On-link      192.168.47.1    291
     192.168.47.1  255.255.255.255         On-link      192.168.47.1    291
   192.168.47.255  255.255.255.255         On-link      192.168.47.1    291
     192.168.56.0    255.255.255.0         On-link      192.168.56.1    281
     192.168.56.1  255.255.255.255         On-link      192.168.56.1    281
   192.168.56.255  255.255.255.255         On-link      192.168.56.1    281
    192.168.127.0    255.255.255.0         On-link     192.168.127.1    281
    192.168.127.1  255.255.255.255         On-link     192.168.127.1    281
  192.168.127.255  255.255.255.255         On-link     192.168.127.1    281
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    331
        224.0.0.0        240.0.0.0         On-link      192.168.56.1    281
        224.0.0.0        240.0.0.0         On-link         10.33.2.6    291
        224.0.0.0        240.0.0.0         On-link      192.168.47.1    291
        224.0.0.0        240.0.0.0         On-link   169.254.185.209    281
        224.0.0.0        240.0.0.0         On-link      192.168.19.1    291
        224.0.0.0        240.0.0.0         On-link     192.168.127.1    281
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    331
  255.255.255.255  255.255.255.255         On-link      192.168.56.1    281
  255.255.255.255  255.255.255.255         On-link         10.33.2.6    291
  255.255.255.255  255.255.255.255         On-link      192.168.47.1    291
  255.255.255.255  255.255.255.255         On-link   169.254.185.209    281
  255.255.255.255  255.255.255.255         On-link      192.168.19.1    291
  255.255.255.255  255.255.255.255         On-link     192.168.127.1    281
===========================================================================
Itinéraires persistants :
  Aucun
```

- Table de routage VM

```bash
[iroh@localhost ~]$ ip route
default via 10.0.2.2 dev enp0s3 proto dhcp metric 100
10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.15 metric 100
192.168.127.0/24 dev enp0s8 proto kernel scope link src 192.168.127.10 metric 101
```

- Ligne permettant la discussion

  - Sur l'hôte

  ```powershell
  192.168.127.0    255.255.255.0         On-link     192.168.127.1    281
  ```

  - Sur la VM

  ```bash
  192.168.127.0/24 dev enp0s8 proto kernel scope link src 192.168.127.10 metric 101
  ```

---

#### curl VM

```bash
[iroh@localhost ~]$ curl google.com
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="http://www.google.com/">here</A>.
</BODY></HTML>

```

---

#### dig VM

- ynov.com

  ```bash
  [iroh@localhost ~]$ dig ynov.com
  ;; SERVER: 10.33.10.20#53(10.33.10.20)
  ```

- google.com

  ```bash
  [iroh@localhost ~]$ curl google.com
  ;; SERVER: 10.33.10.20#53(10.33.10.20)
  ```

## II. Notions de ports et SSH

---

### 1.Exploration des ports locaux

- ss -4

  ```bash
  [iroh@localhost ssh]$ ss -4
  Netid State      Recv-Q Send-Q Local Address:Port                 Peer Address:Port
  tcp   ESTAB      0      64     192.168.127.10:ssh                  192.168.127.1:17951
  ```

- ss TCP

```bash
[iroh@localhost ~]$ ss -t
State       Recv-Q Send-Q Local Address:Port                 Peer Address:Port
ESTAB       0      64     192.168.127.10:ssh                  192.168.127.1:17951
```

- ss *listening*

```bash
[iroh@localhost ~]$ ss -l
Netid State      Recv-Q Send-Q Local Address:Port                 Peer Address:Port
tcp   LISTEN     0      128     *:ssh                   *:*
tcp   LISTEN     0      128    :::ssh                  :::*
```

- ss -n

```bash
[iroh@localhost ~]$ ss -n
Netid State      Recv-Q Send-Q Local Address:Port               Peer Address:Port
tcp   ESTAB      0      2432   192.168.127.10:22                 192.168.127.1:17951
```

- ss -p

```bash
[iroh@localhost ~]$ ss -p
Netid State      Recv-Q Send-Q Local Address:Port                 Peer Address:Port
tcp   ESTAB      0      0      192.168.127.10:ssh                  192.168.127.1:17951
```

### 2. SSH

---

![PuTTy](images/PuTTy.png)

### 3. Firewall

- A.SSH

-- Modification du port d'écoute

  J'ai modifié le fichier sshd_config en changeant le port par 2222.

  ```bash
  [iroh@localhost ssh]$ sudo cat sshd_config
  Port 2222
  #AddressFamily any
  #ListenAddress 0.0.0.0
  #ListenAddress ::
  ```

J'ai redémarré mon serveur ssh.

```bash
[iroh@localhost ssh]$ sudo ss -naltp4
State       Recv-Q Send-Q                                 Local Address:Port                                                Peer Address:Port
LISTEN      0      128                                                *:2222                                                           *:*                   users:(("sshd",pid=3807,fd=3))
LISTEN      0      100                                        127.0.0.1:25                                                             *:*                   users:(("master",pid=3379,fd=13))
```

La connexion échoue car on a changer le port d'écoute, il faut donc l'autoriser sur le firewall pour pouvoir réutliser le serveur ssh.

En autorisant la connexion on peut réutiliser notre serveur.

```bash
[iroh@localhost ~]$ sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: ssh dhcpv6-client
  ports: 2222/tcp
  protocols:
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```

---

- B. netcat

-- Terminal serveur

  ```bash
  [iroh@localhost ~]$ nc -l 5454
  zokkod
  skd
  hola
  ```

-- Terminal client

  ```powershell
  PS C:\Netcat\netcat-1.11> .\nc64.exe 192.168.127.10 5454
  zokkod
  skd
  hola
  ```

-- Terminal espion

  ```bash
  [iroh@localhost ~]$ ss -nat
  State       Recv-Q Send-Q Local Address:Port               Peer Address:Port 
  LISTEN      0      128        *:2222                   *:*
  LISTEN      0      100    127.0.0.1:25                     *:*               
  ESTAB       0      0      192.168.127.10:5454               192.168.127.1:1524
  ESTAB       0      0      192.168.127.10:2222               192.168.127.1:1271
  ESTAB       0      64     192.168.127.10:2222               192.168.127.1:1260
  LISTEN      0      128       :::2222                  :::*
  LISTEN      0      100      ::1:25                    :::*
  ```

---

## III. Routage statique

### 1. Préparation des hôtes (vos PCs)

#### Ping à travers le cable ethernet

```bash
PS C:\Users\Notitou> ping 192.168.255.1

Envoi d’une requête 'Ping'  192.168.255.1 avec 32 octets de données :
Réponse de 192.168.255.1 : octets=32 temps=2 ms TTL=128
Réponse de 192.168.255.1 : octets=32 temps=1 ms TTL=128
Réponse de 192.168.255.1 : octets=32 temps=1 ms TTL=128
Réponse de 192.168.255.1 : octets=32 temps=1 ms TTL=128

Statistiques Ping pour 192.168.255.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 1ms, Maximum = 2ms, Moyenne = 1ms
```

Changement d'ip sur les cartes ethernet pour être dans le réseau 192.168.112.0/30

#### Préparation Virtual Box

Rémi et Louis ont changé leurs IP de leur carte Host-Only et de leur VM par celle recquise.

#### Check

Ping PC 1 -> PC 2
```powershell
PS C:\Users\Notitou> ping 192.168.112.2

Envoi d’une requête 'Ping'  192.168.112.2 avec 32 octets de données :
Réponse de 192.168.112.2 : octets=32 temps=2 ms TTL=128
Réponse de 192.168.112.2 : octets=32 temps=2 ms TTL=128
Réponse de 192.168.112.2 : octets=32 temps=2 ms TTL=128
Réponse de 192.168.112.2 : octets=32 temps=2 ms TTL=128

Statistiques Ping pour 192.168.112.2:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 2ms, Maximum = 2ms, Moyenne = 2ms
```

Ping PC 1 -> VM 1

```powershell
PS C:\Users\Notitou> ping 192.168.101.10

Envoi d’une requête 'Ping'  192.168.101.10 avec 32 octets de données :
Réponse de 192.168.101.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.101.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.101.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.101.10 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 192.168.101.10:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```

Ping VM1 -> PC1

```bash
[root@localhost ~]# ping 192.168.101.1
PING 192.168.101.1 (192.168.101.1) 56(84) bytes of data.
64 bytes from 192.168.101.1: icmp_seq=1 ttl=128 time=0.270 ms
64 bytes from 192.168.101.1: icmp_seq=2 ttl=128 time=0.684 ms
64 bytes from 192.168.101.1: icmp_seq=3 ttl=128 time=0.401 ms
64 bytes from 192.168.101.1: icmp_seq=4 ttl=128 time=0.409 ms
64 bytes from 192.168.101.1: icmp_seq=5 ttl=128 time=0.328 ms
64 bytes from 192.168.101.1: icmp_seq=6 ttl=128 time=0.452 ms
^X^C
--- 192.168.101.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5002ms
rtt min/avg/max/mdev = 0.270/0.424/0.684/0.130 ms
```

Ping PC2 -> PC1

```console
PS C:\Users\louis_tbixp39> ping 192.168.112.1

Envoi d’une requête 'Ping'  192.168.112.1 avec 32 octets de données :
Réponse de 192.168.112.1 : octets=32 temps=3 ms TTL=128
Réponse de 192.168.112.1 : octets=32 temps=1 ms TTL=128
Réponse de 192.168.112.1 : octets=32 temps=2 ms TTL=128
Réponse de 192.168.112.1 : octets=32 temps=2 ms TTL=128

Statistiques Ping pour 192.168.112.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 1ms, Maximum = 3ms, Moyenne = 2ms
```

Ping VM1 -> PC1

```bash
[root@localhost ~]# ping 192.168.101.1
PING 192.168.101.1 (192.168.101.1) 56(84) bytes of data.
64 bytes from 192.168.101.1: icmp_seq=1 ttl=128 time=0.270 ms
64 bytes from 192.168.101.1: icmp_seq=2 ttl=128 time=0.684 ms
64 bytes from 192.168.101.1: icmp_seq=3 ttl=128 time=0.401 ms
64 bytes from 192.168.101.1: icmp_seq=4 ttl=128 time=0.409 ms
64 bytes from 192.168.101.1: icmp_seq=5 ttl=128 time=0.328 ms
64 bytes from 192.168.101.1: icmp_seq=6 ttl=128 time=0.452 ms
^X^C
--- 192.168.101.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5002ms
rtt min/avg/max/mdev = 0.270/0.424/0.684/0.130 ms
```
Ping VW2 -> PC2

```console
[louis@localhost ~]$ ping 192.168.112.2                                         PING 192.168.112.2 (192.168.112.2) 56(84) bytes of data.
64 bytes from 192.168.112.2: icmp_seq=1 ttl=127 time=0.483 ms
64 bytes from 192.168.112.2: icmp_seq=2 ttl=127 time=1.05 ms
64 bytes from 192.168.112.2: icmp_seq=3 ttl=127 time=1.23 ms
64 bytes from 192.168.112.2: icmp_seq=4 ttl=127 time=1.16 ms
^C
--- 192.168.112.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 0.483/0.985/1.238/0.299 ms
```
Ping PC2 -> VM2

```bash
PS C:\Users\louis_tbixp39> ping 192.168.102.10

Envoi d’une requête 'Ping'  192.168.102.10 avec 32 octets de données :
Réponse de 192.168.102.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.102.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.102.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.102.10 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 192.168.102.10:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```

### 2. Configuration du routage

- PC 1

```Powershell
PS C:\WINDOWS\system32> route add 192.168.102.1/24 mask 255.255.255.0 192.168.112.2
 OK!
PS C:\WINDOWS\system32> ping 192.168.102.1

Envoi d’une requête 'Ping'  192.168.102.1 avec 32 octets de données :
Réponse de 192.168.102.1 : octets=32 temps=2 ms TTL=127
Réponse de 192.168.102.1 : octets=32 temps=2 ms TTL=127
Réponse de 192.168.102.1 : octets=32 temps=2 ms TTL=127
Réponse de 192.168.102.1 : octets=32 temps=2 ms TTL=127

Statistiques Ping pour 192.168.102.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 2ms, Maximum = 2ms, Moyenne = 2ms
````

- PC 2

```powershell
PS C:\WINDOWS\system32> route add 192.168.101.1/24 mask 255.255.255.0 192.168.112.1
 OK!
PS C:\WINDOWS\system32> ping 192.168.101.1

Envoi d’une requête 'Ping'  192.168.101.1 avec 32 octets de données :
Réponse de 192.168.101.1 : octets=32 temps=3 ms TTL=127
Réponse de 192.168.101.1 : octets=32 temps=2 ms TTL=127
Réponse de 192.168.101.1 : octets=32 temps=1 ms TTL=127
Réponse de 192.168.101.1 : octets=32 temps=2 ms TTL=127

Statistiques Ping pour 192.168.101.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 1ms, Maximum = 3ms, Moyenne = 2ms
```
- VM 1

```bash
[root@localhost ~]$ sudo ip route add 192.168.112.0/30 via 192.168.101.1 dev enp0s8
[root@localhost ~]$ sudo ip route add 192.168.102.0/24 via 192.168.101.1 dev enp0s8
[root@localhost ~]# ping 192.168.112.2
PING 192.168.112.2 (192.168.112.2) 56(84) bytes of data.
64 bytes from 192.168.112.2: icmp_seq=1 ttl=127 time=2.63 ms
64 bytes from 192.168.112.2: icmp_seq=2 ttl=127 time=3.58 ms
64 bytes from 192.168.112.2: icmp_seq=3 ttl=127 time=3.09 ms
64 bytes from 192.168.112.2: icmp_seq=4 ttl=127 time=3.90 ms
64 bytes from 192.168.112.2: icmp_seq=5 ttl=127 time=3.01 ms
^C
--- 192.168.112.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4012ms
rtt min/avg/max/mdev = 2.630/3.245/3.900/0.449 ms
[root@localhost ~]# ping 192.168.102.1
PING 192.168.102.1 (192.168.102.1) 56(84) bytes of data.
64 bytes from 192.168.102.1: icmp_seq=1 ttl=126 time=2.82 ms
64 bytes from 192.168.102.1: icmp_seq=2 ttl=126 time=3.13 ms
64 bytes from 192.168.102.1: icmp_seq=3 ttl=126 time=2.93 ms
64 bytes from 192.168.102.1: icmp_seq=4 ttl=126 time=2.86 ms
^C
--- 192.168.102.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3008ms
rtt min/avg/max/mdev = 2.829/2.939/3.130/0.122 ms
```

- VM 2

```bash
[louis@localhost ~]$ sudo ip route add 192.168.112.0/30 via 192.168.102.1 dev enp0s8
[louis@localhost ~]$ sudo ip route add 192.168.101.0/24 via 192.168.102.1 dev enp0s8
[louis@localhost ~]$ ping 192.168.112.1
PING 192.168.112.1 (192.168.112.1) 56(84) bytes of data.
64 bytes from 192.168.112.1: icmp_seq=1 ttl=127 time=5.16 ms
64 bytes from 192.168.112.1: icmp_seq=2 ttl=127 time=2.38 ms
64 bytes from 192.168.112.1: icmp_seq=3 ttl=127 time=2.83 ms
64 bytes from 192.168.112.1: icmp_seq=4 ttl=127 time=3.24 ms
^C
--- 192.168.112.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3010ms
rtt min/avg/max/mdev = 2.384/3.406/5.163/1.060 ms
[louis@localhost ~]$ ping 192.168.101.1
PING 192.168.101.1 (192.168.101.1) 56(84) bytes of data.
64 bytes from 192.168.101.1: icmp_seq=1 ttl=126 time=2.27 ms
64 bytes from 192.168.101.1: icmp_seq=2 ttl=126 time=2.54 ms
64 bytes from 192.168.101.1: icmp_seq=3 ttl=126 time=2.43 ms
64 bytes from 192.168.101.1: icmp_seq=4 ttl=126 time=2.83 ms
^C
--- 192.168.101.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3007ms
rtt min/avg/max/mdev = 2.278/2.522/2.831/0.201 ms
```
#### Ping VM1 

- Ping VM 1 -> PC 1
```bash
[root@localhost etc]# ping pc1.tp3.b1
PING pc1 (192.168.112.1) 56(84) bytes of data.
64 bytes from pc1 (192.168.112.1): icmp_seq=1 ttl=127 time=0.237 ms
64 bytes from pc1 (192.168.112.1): icmp_seq=2 ttl=127 time=0.477 ms
64 bytes from pc1 (192.168.112.1): icmp_seq=3 ttl=127 time=0.461 ms
64 bytes from pc1 (192.168.112.1): icmp_seq=4 ttl=127 time=0.504 ms
^C
--- pc1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 0.237/0.419/0.504/0.109 ms
```

- Ping VM 1 -> PC 2

```bash
[root@localhost etc]# ping pc2.tp3.b1
PING pc2 (192.168.112.2) 56(84) bytes of data.
64 bytes from pc2 (192.168.112.2): icmp_seq=1 ttl=127 time=2.66 ms
64 bytes from pc2 (192.168.112.2): icmp_seq=2 ttl=127 time=2.78 ms
64 bytes from pc2 (192.168.112.2): icmp_seq=3 ttl=127 time=2.68 ms
64 bytes from pc2 (192.168.112.2): icmp_seq=4 ttl=127 time=2.73 ms
64 bytes from pc2 (192.168.112.2): icmp_seq=5 ttl=127 time=3.27 ms
^C
--- pc2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4013ms
rtt min/avg/max/mdev = 2.669/2.829/3.279/0.238 ms
```

- Ping VM 1 -> VM 2

```bash
[root@localhost etc]# ping vm2.tp3.b1
PING vm2 (192.168.102.10) 56(84) bytes of data.
64 bytes from vm2 (192.168.102.10): icmp_seq=1 ttl=62 time=2.82 ms
^[[A64 bytes from vm2 (192.168.102.10): icmp_seq=2 ttl=62 time=3.09 ms
64 bytes from vm2 (192.168.102.10): icmp_seq=3 ttl=62 time=3.83 ms
64 bytes from vm2 (192.168.102.10): icmp_seq=4 ttl=62 time=3.21 ms
64 bytes from vm2 (192.168.102.10): icmp_seq=5 ttl=62 time=3.54 ms
^C
--- vm2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 2.829/3.302/3.834/0.357 ms

```

- Ping VM 2 -> PC 1

```bash
[louis@localhost /]$ ping pc1.tp3.b1
PING pc1 (192.168.112.1) 56(84) bytes of data.
64 bytes from pc1 (192.168.112.1): icmp_seq=1 ttl=127 time=2.27 ms
64 bytes from pc1 (192.168.112.1): icmp_seq=2 ttl=127 time=2.62 ms
64 bytes from pc1 (192.168.112.1): icmp_seq=3 ttl=127 time=2.43 ms
64 bytes from pc1 (192.168.112.1): icmp_seq=4 ttl=127 time=2.29 ms
^C
--- pc1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 2.271/2.406/2.622/0.151 ms
```

- Ping VM 2 -> PC 2

```bash
[louis@localhost /]$ ping pc2.tp3.b1
PING pc2 (192.168.112.2) 56(84) bytes of data.
64 bytes from pc2 (192.168.112.2): icmp_seq=1 ttl=127 time=0.356 ms
64 bytes from pc2 (192.168.112.2): icmp_seq=2 ttl=127 time=0.662 ms
64 bytes from pc2 (192.168.112.2): icmp_seq=3 ttl=127 time=0.600 ms
64 bytes from pc2 (192.168.112.2): icmp_seq=4 ttl=127 time=0.625 ms
^C
--- pc2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 0.356/0.560/0.662/0.123 ms
```

- Ping VM 2 -> VM 1

```bash
[louis@localhost /]$ ping vm1.tp3.b1
PING vm1 (192.168.101.10) 56(84) bytes of data.
64 bytes from vm1 (192.168.101.10): icmp_seq=1 ttl=62 time=2.50 ms
64 bytes from vm1 (192.168.101.10): icmp_seq=2 ttl=62 time=2.82 ms
64 bytes from vm1 (192.168.101.10): icmp_seq=3 ttl=62 time=2.26 ms
64 bytes from vm1 (192.168.101.10): icmp_seq=4 ttl=62 time=2.53 ms
^C
--- vm1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 2.261/2.530/2.820/0.207 ms
```

#### Netcat VM 1 -> VM 2

```bash
[louis@localhost /]$ nc vm1.tp3.b1 5454
salut
je suis la vm1
et moi la vm2
ahahah
^C
```