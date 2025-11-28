## Comandos básicos y hostname

```bash
enable
configure terminal
hostname Empresa
```
## Configuración de interfaces

```bash
interface gigabitEthernet 0/0
 ip address 10.10.129.1 255.255.255.0
 no shutdown
 exit

interface serial 0/0/0
 ip address 200.200.166.204 255.255.255.0
 no shutdown
 exit
```
### Rutas por defecto hacia internet

```bash
ip route 0.0.0.0 0.0.0.0 serial 0/0/0
```

### Licencias y pool de direcciones

```bash
license boot module c1900 technology-package securityk9
ip local pool RemoteVPN 10.10.129.100 10.10.129.115
```

### Configuración AAA (Authentication, Authorization, Accounting)

```bash
aaa new-model
aaa authentication login UserVPN local
aaa authorization network GroupVPN local
username test secret cisco
```

### Configuración IPsec

```bash
crypto isakmp policy 100
 encryption aes 256
 hash sha
 authentication pre-share
 group 5
 lifetime 3600
 exit

crypto isakmp client configuration group GroupVPN
 key ciscogroupvpn
 pool RemoteVPN
 exit

crypto ipsec transform-set SetVPN esp-aes esp-sha-hmac
crypto dynamic-map DynamicVPN 100
 set transform-set SetVPN 
 reverse-route
 exit
```

### Creación de crypto map

```bash
crypto map StaticMap client configuration address respond
crypto map StaticMap client authentication list UserVPN
crypto map StaticMap isakmp authorization list GroupVPN

crypto map StaticMap 20 ipsec-isakmp dynamic DynamicVPN

interface serial 0/0/0
 crypto map StaticMap
 exit
```

