
# 🧪 Lab: sr01 – Topología en malla parcial con Nokia SR Linux

## 🗓 Fecha: 08/04/2025

## 📘 Descripción general

Este laboratorio implementa una topología tipo **"malla parcial"** usando cinco routers **Nokia SR Linux (ixrd2l)**, conectados mediante enlaces punto a punto. Se utilizó Containerlab para definir y desplegar la infraestructura virtual, junto con archivos de configuración de arranque (`startup-config`) para cada nodo.

La topología tiene como objetivo practicar:

- Conexiones punto a punto entre routers
- Buenas prácticas en naming convention e interfaces

## 🧱 Estructura de la topología

```
         srl1
        /    \
     srl2    srl3
        \    /
         srl4
           |
         srl5
 ```


## 🔗 Enlaces configurados

| Enlace        | Interfaces                     |
|---------------|--------------------------------|
| srl1 ↔ srl2    | srl1:ethernet-1/1 ↔ srl2:ethernet-1/1 |
| srl1 ↔ srl3    | srl1:ethernet-1/2 ↔ srl3:ethernet-1/1 |
| srl2 ↔ srl4    | srl2:ethernet-1/2 ↔ srl4:ethernet-1/1 |
| srl3 ↔ srl4    | srl3:ethernet-1/2 ↔ srl4:ethernet-1/2 |
| srl4 ↔ srl5    | srl4:ethernet-1/3 ↔ srl5:ethernet-1/1 |

## 📍 Asignación de IPs estáticas a las interfaces conectadas en la topología:

**srl1 ↔ srl2 (10.10.0.0/30)**

srl1 - ethernet-1/1 → 10.10.0.1/30

srl2 - ethernet-1/1 → 10.10.0.2/30

**srl2 ↔ srl4 (10.10.0.4/30)**

srl2 - ethernet-1/2 → 10.10.0.5/30

srl4 - ethernet-1/1 → 10.10.0.6/30

**srl4 ↔ srl5 (10.10.0.8/30)**

srl4 - ethernet-1/3 → 10.10.0.9/30

srl5 - ethernet-1/1 → 10.10.0.10/30 

**srl4 ↔ srl3 (10.10.0.12/30)**

srl4 - ethernet-1/2 → 10.10.0.13/30

srl3 - ethernet-1/2 → 10.10.0.14/30

**srl3 ↔ srl1 (10.10.0.16/30)**

srl3 - ethernet-1/1 → 10.10.0.17/30

srl1 - ethernet-1/2 → 10.10.0.18/30

## 📂 Archivos utilizados

- `sr01.clab.yaml` → define la topología y enlaces
- `cfg-clab-sr01/` → contiene las configuraciones iniciales para:
  - `srl1.cfg`
  - `srl2.cfg`
  - `srl3.cfg`
  - `srl4.cfg`
  - `srl5.cfg`

## ⚙️ Funcionalidades implementadas (hasta ahora)

- Configuración básica de interfaces y habilitación de enlaces
- Preparación para asignación de direcciones IP y pruebas de conectividad con ping bidireccional entre las interfaces de cada red.


## 📌 Notas personales

- La mejor manera de estructurar los enlaces es visualmente usando graph después del deployment (en todas sus variantes)
- Es muy útil el `startup-config` para que cada router arranque con su archivo propio.
- Containerlab facilita el despliegue, pero requiere atención al detalle en las interfaces para que no haya conflictos.


## ⭐ Nuevos hitos 
- Ping de r1 a r5: Pensad cómo hacer que funcione un ping desde r1 a r5.
- Configuraciones de routers: Podéis tener varios archivos de configuración, como r1.cfg y r1-routes.cfg, y subirlos al GitHub.
- Protocolos de routing dinámico(MUY OPCIONAL): Si os atrevéis, podéis montar protocolos de routing dinámico en SR Linux,
- Hosts en la topología: Añadid hosts directamente en la topología, como Ubuntu y Alpine, o la distro de Linux que queráis.
- Captura de tráfico: Podéis capturar tráfico, aunque no haya mucho que analizar.
- Simular problemas en interfaces: Si montáis el entorno en un Ubuntu en VMWare, podéis establecer latencia, jitter, packet loss, etc.