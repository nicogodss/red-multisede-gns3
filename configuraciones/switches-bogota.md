\# VLAN y puertos de acceso — Bogotá



| Switch | VLAN 10 — Desarrollo | VLAN 20 — Gerencia | VLAN 30 — Sistemas | Trunks |

|---|---|---|---|---|

| Pis1-Sur | Fa1/0–Fa1/1 | Fa1/2 | Fa1/3 | Fa1/14, Fa1/15 |

| Pis1-Norte | Fa1/0–Fa1/1 | Fa1/2 | Fa1/3 | Fa1/14, Fa1/15 |

| Pis2-Sur | Fa1/2 | Fa1/3 | Fa1/0–Fa1/1 | Fa1/14, Fa1/15 |

| Pis2-Norte | Fa1/5 | Fa1/0–Fa1/1 | Fa1/2–Fa1/4 | Fa1/13, Fa1/14, Fa1/15 |



Los enlaces troncales usan 802.1Q y transportan las VLAN 10, 20 y 30. El estado de reenvío de cada enlace depende de STP.



La movilidad se comprobó conectando PC2 a Pis2-Norte Fa1/5: mantuvo `192.168.40.11/24` y alcanzó la puerta de enlace `192.168.40.1`.



Comandos de verificación:



```text

show vlan-switch brief

show interfaces trunk

