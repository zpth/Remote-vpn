
El router doméstico actúa como puerta de enlace. Se configuró **NAT/PAT** para permitir que múltiples dispositivos internos compartan una única dirección IP pública.
* **Routing:** Rutas estáticas por defecto.
* **Traducción:** `ip nat inside source list ACL_NAT interface serial 0/0/0 overload`.

### Comandos básicos y hostname

```bash
en
conf t
hostname Home
```
### Configuración de interfaces

```bash
interface gigabitEthernet 0/0
ip address 192.168.100.1 255.255.255.0
no sh
exit
interface Serial0/0/0
ip address 200.200.165.201 255.255.255.0
no shutdown
exit
```

### Configuración de routing estático

```bash
ip route 0.0.0.0 0.0.0.0 serial 0/0/0
```

### Configuración de ACL y NAT

```bash
ip access-list standard ACL_NAT
permit 192.168.100.0 0.0.0.255
exit
ip nat inside source list ACL_NAT interface serial 0/0/0
int serial 0/0/0
ip nat outside
int g0/0
ip nat inside
```
