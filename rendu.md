# TP 3 - Plusieurs réseaux : routage statique

## I. Utilisation simple du'n VM CentOS

### 4. Configuration réseau d'une machine CentOS

Ping Host -> VM

```powershell
PS C:\Users\Irohn> ping 192.168.127.10

Envoi d’une requête 'Ping'  192.168.127.10 avec 32 octets de données :
Réponse de 192.168.127.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.127.10 : octets=32 temps<1ms TTL=64
Réponse de 192.168.127.10 : octets=32 temps<1ms TTL=64*
```

Table de routage Host

```powershell
PS C:\Users\Irohn> route print -4
===========================================================================
Liste d'Interfaces
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

Table de routage VM

```bash
ip route
```

curl VM
```
```