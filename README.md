# Laboratorio de red multisede en GNS3

Diseño e implementación de una red académica para conectar las sedes de Bogotá y Medellín. El laboratorio integra segmentación por VLAN, enrutamiento entre sedes y servicios centralizados.

## Topología y direccionamiento

| Sede | Segmento | Red | Puerta de enlace |
|---|---|---|---|
| Bogotá | VLAN 10 — Desarrollo | `192.168.40.0/24` | `192.168.40.1` |
| Bogotá | VLAN 20 — Gerencia | `192.168.41.0/24` | `192.168.41.1` |
| Bogotá | VLAN 30 — Sistemas | `192.168.42.0/24` | `192.168.42.1` |
| Medellín | Subred A | `192.168.43.0/25` | `192.168.43.1` |
| Medellín | Subred B | `192.168.43.128/26` | `192.168.43.129` |

El servidor Alpine está en la VLAN 30 de Bogotá, con dirección `192.168.42.2`. La ubicación física propuesta para alojar la VM es el centro de datos de la empresa en Bogotá.

## Servicios y tecnologías

- **VLAN:** separación de las áreas de la empresa y puertos de acceso para las VLAN 10, 20 y 30 en los switches de Bogotá.
- **Enrutamiento:** OSPF entre los routers de Bogotá y Medellín.
- **DHCP:** un servidor central en Alpine, con un rango para cada una de las cinco subredes y relay DHCP en los routers.
- **DNS:** BIND para el dominio interno `grupo4.test`.
- **FTP:** vsftpd con usuarios autenticados.
- **NAT/PAT:** salida hacia redes externas mediante la conexión NAT de GNS3.

## Pruebas realizadas

- Obtención de direcciones DHCP en las cinco subredes.
- Resolución de `ftp.grupo4.test` desde Medellín.
- Movilidad de PC2 a un puerto de VLAN 10 en Pis2-Norte, conservando `192.168.40.11/24` y conectividad con su puerta de enlace.
- Traducciones NAT observadas para tráfico de Bogotá y Medellín hacia `1.1.1.1:443`.
- Carga y descarga FTP con usuario autenticado desde Alpine; acceso TCP al puerto 21 verificado desde Medellín.

## Archivo del laboratorio

El repositorio incluye la exportación portable del proyecto de GNS3. Para abrirlo se requieren GNS3 y las imágenes de dispositivos correspondientes; estas imágenes no forman parte de la exportación.
