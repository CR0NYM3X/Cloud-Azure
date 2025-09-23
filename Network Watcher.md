 

## 🧩 ¿Para qué sirve Network Watcher?

Network Watcher te ayuda a:

### 🔍 1. **Diagnosticar problemas de conectividad**
- Verifica si una máquina virtual puede conectarse a otra.
- Detecta bloqueos por NSG (Network Security Groups), firewalls o rutas mal configuradas.

### 📈 2. **Monitorear tráfico de red**
- Captura paquetes (como Wireshark) para analizar tráfico entre recursos.
- Útil para detectar tráfico sospechoso o problemas de rendimiento.

### 🧭 3. **Visualizar topología de red**
- Muestra un diagrama interactivo de cómo están conectados tus recursos (VMs, subredes, NSGs, etc.).
- Facilita la comprensión de la arquitectura de red.

### 🛡️ 4. **Auditoría y seguridad**
- Detecta cambios en reglas de seguridad.
- Identifica rutas efectivas que toma el tráfico (IP Flow Verify).

---

## 📌 Casos de uso reales

| Caso | Descripción |
|------|-------------|
| **Problemas de conexión entre VMs** | Usas "Connection Troubleshoot" para saber si una VM puede comunicarse con otra. |
| **Análisis de tráfico lento** | Capturas paquetes para ver si hay congestión o pérdida de paquetes. |
| **Auditoría de seguridad** | Verificas si las reglas de NSG están bloqueando tráfico legítimo. |
| **Visualización de arquitectura** | Generas un mapa de red para documentar tu infraestructura. |

---

## 🏢 ¿Cómo te serviría en tu empresa?

Aunque tengas infraestructura on-premise, si estás usando **Azure para VMs, redes virtuales o VPNs**, Network Watcher te permite:

- **Detectar problemas de conectividad entre tu red local y Azure.**
- **Auditar configuraciones de red en la nube.**
- **Visualizar cómo se conectan tus recursos en Azure.**
- **Capturar tráfico para análisis forense o de rendimiento.**
