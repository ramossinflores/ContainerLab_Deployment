# Laboratorios de VLAN y LAN - Cisco IOL en Containerlab

Este es el segundo laboratorio de prácticas con Containerlab y dispositivos Cisco IOL:

1. **LAN básica** (Conectividad dentro de la misma LAN)
2. **VLAN** (Segmentación mediante VLANs y trunking)

---

## 🧪 1. LAN básica

### Topología:

- **Dos LANs separadas** (`LAN1` y `LAN2`)
- Cada LAN contiene:
    - 1 switch `cisco_iol` tipo L2
    - 3 routers
- No hay VLANs, solo conectividad simple

### Objetivo:

> Verificar que los hosts conectados al mismo switch pueden comunicarse directamente usando IPs en la misma red.
> 

### Direccionamiento sugerido:

- **LAN1:** `10.0.0.0/29` → `router1: 10.0.0.1/29`, `router2: 10.0.0.2/29`, `router3: 10.0.0.3/29`
- **LAN2:** `router4: 10.0.0.8/29` → `router5: 10.0.0.10/29`

---

## 🧪 2. VLAN (Segmentación de red)

### Topología:

- 3 switches Cisco IOL:
    - `sw1` (arriba)
    - `sw2` (abajo)
    - `sw3` (central, interconexión)
- 4 routers:
    - `rt1`, `rt2`, `rt3`, `rt4`, `rt5`
- VLANs definidas:
    - VLAN10 → `rt1`, `rt2`,
    - VLAN20 → `rt3`, `rt4`,
    - VLAN30 → `rt5`

### Objetivo:

> Garantizar conectividad entre hosts que pertenecen a la misma VLAN, incluso si están en diferentes switches, usando trunking.
> 

### Configuraciones:

- **Interfaces de acceso**: asignadas a las VLANs correspondientes
- **Enlaces troncales**: entre `sw1` ↔ `sw3` ↔ `sw2`, permitiendo `VLAN10`, `VLAN20`, `VLAN30`

---


## 📎 Notas adicionales

- Todos los switches están configurados con `.partial` para conservar la interfaz de administración y el acceso SSH
- Todos los routers simulados como hosts tienen IP configurada y `no shutdown` en su interfaz



