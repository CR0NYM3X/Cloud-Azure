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
  - **Locally Redundant Storage (LRS)**: más barato, tres copias de manera local en el mismo centro de datos.
  - **Geo-Redundant Storage (GRS)**: más seguro, más caro, tres copias en total cada uno en tres zonas diferentes.

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



---

### 🛡️ ¿Cómo es posible hacer backups on-premise en Azure?

Azure ofrece varias soluciones para esto:

 
### 🔗 Requisitos generales

- Conectividad a internet desde tus servidores locales.
- Configuración de **Recovery Services Vault** en Azure.
- Instalación de agentes o configuración de Azure Arc.
- Políticas de backup definidas (frecuencia, retención, etc.).
 

### 1. **Azure Backup**
- Puedes instalar el **Azure Backup Agent** en tus servidores físicos (Windows Server, por ejemplo).
- Este agente se conecta a Azure y permite hacer **copias de seguridad de archivos, carpetas, y volúmenes** directamente en la nube.
- También puedes usar **Microsoft Azure Recovery Services (MARS)** para programar backups automáticos.

 

### 2. **Azure Site Recovery**
- Aunque está diseñado para **recuperación ante desastres**, también puede replicar máquinas virtuales y servidores físicos hacia Azure.
- Esto permite tener una copia actualizada de tu infraestructura en caso de falla.
 

### 3. **Azure Arc + Azure Backup**
- Si tienes servidores Linux o Windows en on-premise, puedes **registrarlos en Azure Arc**.
- Una vez registrados, puedes aplicar políticas de backup como si fueran recursos nativos de Azure.

 

### 4. **Azure File Sync**
- Si tienes servidores de archivos locales, puedes sincronizar carpetas con **Azure Files**.
- Esto permite tener una copia en la nube y usarla como respaldo o para recuperación.
