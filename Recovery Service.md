## 🛡️ ¿Qué es Azure Recovery Services?

**Azure Recovery Services** es un conjunto de herramientas dentro de Microsoft Azure que permite **proteger, respaldar y recuperar** datos, máquinas virtuales, servidores físicos, bases de datos y más, ante fallos, desastres o pérdidas de información.

---

## 🎯 ¿Para qué sirve?

Principalmente para:

1. **Backup (Respaldo):**
   - Realiza copias de seguridad automáticas y programadas.
   - Protege máquinas virtuales, archivos, carpetas, bases de datos SQL, SAP HANA, etc.

2. **Site Recovery (Recuperación ante desastres):**
   - Replica máquinas virtuales y servidores físicos a otra región o zona.
   - Permite la conmutación por error (failover) automática o manual.
   - Minimiza el tiempo de inactividad en caso de desastre.

---

## 🧰 ¿Qué se puede hacer?

### Con **Azure Backup** puedes:
- Respaldar máquinas virtuales de Azure.
- Respaldar servidores físicos (Windows/Linux) on-premises.
- Respaldar bases de datos SQL Server, SAP HANA, SharePoint, Exchange.
- Restaurar archivos individuales o sistemas completos.

### Con **Azure Site Recovery** puedes:
- Replicar VMs de Azure entre regiones.
- Replicar servidores físicos o VMs de VMware/Hyper-V a Azure.
- Realizar pruebas de recuperación sin afectar la producción.
- Automatizar la recuperación con runbooks y planes de recuperación.

---

## 🌍 ¿Dónde se puede usar?

- En **Azure Portal**: usando el recurso llamado **Recovery Services Vault**.
- En **Azure CLI / PowerShell**: para automatizar tareas.
- En **Azure Backup Server (MABS)**: para entornos híbridos.
- En **System Center DPM**: para empresas con infraestructura local.

---

## 🧩 Tipos de Recovery Services

1. **Recovery Services Vault**:
   - Contenedor lógico para almacenar backups y configuraciones de recuperación.
   - Se configura por región.

2. **Backup**:
   - Respaldo de datos y restauración.

3. **Site Recovery**:
   - Replicación y recuperación ante desastres.

---

## 💰 Costos

Los costos se dividen en:

### 1. **Azure Backup**
- **Costo por instancia protegida** (por mes):
  - Ejemplo: VM de hasta 50 GB ≈ \$5 USD/mes.
- **Costo por almacenamiento**:
  - **Locally Redundant Storage (LRS)**: más barato.
  - **Geo-Redundant Storage (GRS)**: más seguro, más caro.

### 2. **Azure Site Recovery**
- **Costo por instancia replicada**:
  - ≈ \$25 USD/mes por VM.
- **Costo por almacenamiento, transferencia de datos y snapshots**.

> 💡 Puedes usar la calculadora de precios de Azure para estimar costos según tu infraestructura.

---

## 📋 Ejemplo de uso empresarial

Supongamos que tienes 100 VMs críticas en producción:

- Configuras un **Recovery Services Vault** en cada región.
- Activas **Azure Backup** para respaldos diarios.
- Configuras **Site Recovery** para replicar las VMs a otra región.
- Automatizas la recuperación con **Azure Automation**.

---

## ✅ Ventajas

- Alta disponibilidad.
- Cumplimiento normativo (ISO, GDPR, etc.).
- Escalabilidad.
- Integración con otras soluciones de Azure.

## ⚠️ Desventajas

- Costos pueden escalar rápidamente si no se optimiza.
- Requiere planificación para evitar duplicación innecesaria de datos.
- Algunas configuraciones avanzadas requieren experiencia técnica.
