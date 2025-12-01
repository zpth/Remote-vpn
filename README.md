# Cisco Remote Access VPN Implementation (IPsec)

![Cisco](https://img.shields.io/badge/Cisco-Packet%20Tracer-blue?style=for-the-badge&logo=cisco)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

## 📖 Descripción

Este proyecto simula un escenario de **red corporativa segura** donde un empleado remoto necesita acceder a los recursos internos de la empresa a través de internet. 

Se implementa una VPN de Acceso Remoto  utilizando el protocolo **IPsec**. Esto permite que el tráfico viaje encriptado desde la laptop del usuario en su casa hasta el router de borde de la empresa, garantizando confidencialidad, integridad y autenticación.

<table align="center">
<tr>
<td>
https://github.com/user-attachments/assets/7d58194e-1d15-459c-b5ba-c08b1ea36294
<h3 align="center">Tecnologías implementadas</h3>
<ul>
    <li><b>IPsec</b> – Protocolo principal para la seguridad del túnel y encapsulamiento.</li>
    <li><b>NAT Overload (PAT)</b> – Traducción de direcciones para la salida a Internet.</li>
    <li><b>AAA (New Model)</b> – Autenticación local (UserVPN) y autorización de red (GroupVPN).</li>
    <li><b>SHA / HMAC</b> – Algoritmo de hashing para asegurar que los datos no sean alterados.</li>
    <li><b>AES 256</b> – Algoritmo de cifrado simétrico robusto para la confidencialidad</li>
</ul>
</td>
</tr>
</table>

</p>
<p align="center">
<a href="images/TopologiaVPN.png">Topología</a> | <a href="packet-tracer/">Packet Tracer</a> | <a href="config/router-home.md">Conf router home</a> | <a href="config/router-internet.md">Conf router internet</a> | <a href="config/router-empresa.md">Conf router empresa</a> </p>

## 🏗️ Arquitectura de red

La topología consta de tres segmentos principales:

1.  **LAN Home (192.168.100.0/24):** Simula la red doméstica del usuario. Utiliza **NAT Overload** para salir a Internet.
2.  **Internet :** Simula la infraestructura pública. Conecta el sitio remoto con la empresa mediante enlaces seriales.
3.  **LAN Empresa (10.10.129.0/24):** Red interna empresarial. Aquí se encuentra un  servidor de destino y las pcs de la red interna.

## 🚀 Instalación y uso

1.  **Requisitos:** Necesitas tener instalado **Cisco Packet Tracer** (versión 7.3 o superior recomendada).
2.  **Clonar el repositorio:**
    ```bash
    git clone [https://github.com/TU_USUARIO/nombre-repo-vpn.git](https://github.com/TU_USUARIO/nombre-repo-vpn.git)
    ```
3.  **Abrir la simulación:** Carga el archivo `.pkt` ubicado en la carpeta `packet-tracer/`.

### 🧪 Probar la conexión VPN

Para verificar el funcionamiento dentro de Packet Tracer:

1.  Abre la **Laptop** en la red "LAN-HOME".
2.  Ve a **Desktop > VPN**.
3.  Ingresa los siguientes credenciales (basados en la configuración):
    * **Group Name:** `GroupVPN`
    * **Group Key:** `ciscogroupvpn`
    * **Host IP:** `200.200.166.204` (IP Pública de la Empresa)
    * **Username:** `test`
    * **Password:** `cisco`
4.  Haz clic en **Connect**. Deberías ver el mensaje: *"VPN is connected"*.
5.  Desde la consola de la Laptop, intenta hacer ping al servidor de la empresa: `ping 10.10.129.31`.



