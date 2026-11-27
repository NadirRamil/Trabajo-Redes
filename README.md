# TPE — Red de Parque Industrial (CDAR)

Trabajo Práctico Especial de **Configuración y Desarrollo de Aplicaciones en Red** (24/05/2023) centrado en el diseño de direccionamiento IP con VLSM, implementación de topología en **CORE**, configuración de rutas estáticas, filtrado de paquetes con **iptables** y pruebas de conectividad con `ping`, `traceroute`, `netcat` y **Wireshark**[cite: 2, 3, 6, 10, 12, 19, 21, 27].

## Integrantes y equipo

* **Grupo:** Grupo 1[cite: 3]
* **Ayudante designado:** Lucas Telesco[cite: 3]
* **Integrantes:**
  * Florencia Prat (`fprat@alumnos.exa.unicen.edu.ar`)[cite: 3]
  * Martina Diaz (`martuudiaz28@gmail.com`)[cite: 3]
  * Nadir Ramil (`nramil@alumnos.exa.unicen.edu.ar`)[cite: 3]

## Esquema de direccionamiento (VLSM)

### Parque Industrial general

| Nombre de Red | Dirección Base | Máscara | Rango Asignable | Broadcast |
| :--- | :--- | :--- | :--- | :--- |
| Datacenter | `10.1.0.0` | `/23` | `10.1.0.1` - `10.1.1.254` | `10.1.1.255` |
| Red Troncal | `10.1.2.0` | `/23` | `10.1.2.1` - `10.1.3.254` | `10.1.3.255` |
| Fábrica A | `10.1.4.0` | `/24` | `10.1.4.1` - `10.1.4.254` | `10.1.4.255` |
| Fábrica B | `10.1.5.0` | `/24` | `10.1.5.1` - `10.1.5.254` | `10.1.5.255` |

### Subredes internas — Fábrica A

| Nombre de Red | Dirección Base | Máscara | Rango Asignable | Broadcast |
| :--- | :--- | :--- | :--- | :--- |
| Red B (R7) | `10.1.4.0` | `/25` | `10.1.4.1` - `10.1.4.126` | `10.1.4.127` |
| Red A (SW3) | `10.1.4.128` | `/26` | `10.1.4.129` - `10.1.4.190` | `10.1.4.191` |
| Red C (SW4) | `10.1.4.192` | `/27` | `10.1.4.193` - `10.1.4.222` | `10.1.4.223` |
| Red D (R6-R7) | `10.1.4.224` | `/30` | `10.1.4.225` - `10.1.4.226` | `10.1.4.227` |

### Subredes internas — Fábrica B

| Nombre de Red | Dirección Base | Máscara | Rango Asignable | Broadcast |
| :--- | :--- | :--- | :--- | :--- |
| Red A (SW5) | `10.1.5.0` | `/25` | `10.1.5.1` - `10.1.5.126` | `10.1.5.127` |
| Red C (SW6) | `10.1.5.128` | `/26` | `10.1.5.129` - `10.1.5.190` | `10.1.5.191` |
| Red B (HUB) | `10.1.5.192` | `/28` | `10.1.5.193` - `10.1.5.206` | `10.1.5.207` |

## Contenido del trabajo

* **Parte 1 — Diseño y validación base:** Cálculo de requerimientos por fábrica, Datacenter y Red Troncal[cite: 4, 5], aplicación de VLSM[cite: 6, 7, 8], armado de la topología en CORE[cite: 10], asignación de IPs en interfaces de routers[cite: 11] y verificación con `ping`, `traceroute` y capturas en Wireshark[cite: 12, 13, 14].
* **Parte 2 — Enrutamiento, firewall y NAT:** Carga de tablas de ruteo estáticas y rutas por defecto[cite: 15, 16, 17, 18, 19, 20], reglas de filtrado (`ACCEPT` / `REJECT`)[cite: 21, 25], enmascaramiento (`MASQUERADE`)[cite: 22, 23, 24], redirección de puertos (`DNAT`) y pruebas de mensajería con `netcat` (`nc`) entre hosts y `Server 1`[cite: 27, 28, 29].

## Archivos del repositorio

* `Grupo 1- Informe CDAR.pdf`: Informe completo del TPE con tablas, capturas de CORE/Wireshark y conclusiones[cite: 2, 3, 30].
