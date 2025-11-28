### Comandos básicos y hostname

```bash
enable
configure terminal
hostname Internet
```
### Configuración de interfaces

```bash
interface serial 0/0/0
ip address 200.200.165.202 255.255.255.0
no sh
exit
interface serial 0/0/1
ip address 200.200.166.203 255.255.255.0
no sh
```
