## 🧭 Catálogo de Aprendizaje Azure — Proyecto Empresarial

### 🔹 1. **Fundamentos de Azure**
- ✅ Crear una cuenta y suscripción
- ✅ Crear grupos de recursos
- 🔲 Comprender regiones y zonas de disponibilidad
- 🔲 Etiquetado de recursos para control de costos

 

### 🔹 2. **Control de Accesos y Gobernanza**
- ✅ Crear roles personalizados
- ✅ Crear usuarios
- ✅ Políticas y directivas (Azure Policy)
- ✅ Agregar bloqueos (Resource Locks)
- 🔲 Azure Blueprints (plantillas de gobernanza)
- 🔲 RBAC vs. ABAC (control basado en roles vs atributos)

 
### 🔹 3. **Seguridad**
- ✅ VPN (Site-to-Site y Point-to-Site)
- ✅ Proxys
- 🔲 Azure Firewall
- 🔲 Azure Bastion (acceso seguro a VMs sin IP pública)
- 🔲 Defender for Cloud (recomendaciones de seguridad)
- 🔲 Key Vault (gestión de secretos y certificados)

 

### 🔹 4. **Redes**
- ✅ Crear VNET
- ✅ Crear NSG (grupo de seguridad de red)
- ✅ Crear DNS
- 🔲 Peering entre VNets
- 🔲 NAT Gateway
- 🔲 Private Link y Endpoints
- 🔲 Azure Route Table (ruteo personalizado)

 

### 🔹 5. **Alta Disponibilidad y Escalabilidad**
- ✅ Balanceadores de carga (Load Balancer)
- 🔲 Azure Application Gateway (con WAF)
- 🔲 Azure Traffic Manager (balanceo geográfico)
- 🔲 Escalado automático (VMSS, App Service Plan)

 

### 🔹 6. **Máquinas Virtuales y Migración**
- 🔲 Crear VMs Linux y Windows
- 🔲 Configurar discos, NICs, NSGs
- 🔲 Migrar servidores on-premise con Azure Migrate
- 🔲 Usar imágenes personalizadas (Managed Images)
- 🔲 Backup y recuperación (Azure Backup)

 

### 🔹 7. **DNS y Nombres Públicos**
- ✅ Crear zona DNS pública
- 🔲 Delegar dominio desde registrador
- 🔲 Crear registros A, CNAME, MX, etc.
- 🔲 Integrar con servicios como App Service o VMs

 

### 🔹 8. **Base de Datos y Almacenamiento**
- 🔲 Azure SQL, PostgreSQL, MySQL
- 🔲 Migración con Data Migration Service
- 🔲 Azure Storage (Blob, File, Queue, Table)
- 🔲 Replicación y redundancia

 

### 🔹 9. **Monitorización y Automatización**
- 🔲 Azure Monitor y Log Analytics
- 🔲 Alertas y métricas
- 🔲 Azure Automation (runbooks)
- 🔲 Cost Management + presupuestos

--- 
## 🏗️ Proyecto Final: Migración Empresarial a Azure

**Escenario:** Una empresa quiere migrar 3 servidores (Linux, Windows, DNS), su red, seguridad y servicios a Azure.

### 🔧 Lo que debes implementar:
1. Red virtual con subredes separadas (web, app, DB)
2. NSGs por subred y por VM
3. VPN Site-to-Site con su red local
4. Migración de servidores con Azure Migrate
5. DNS público para servicios web
6. Balanceador de carga para alta disponibilidad
7. Backup y monitoreo
8. Control de acceso con roles y políticas
9. Seguridad con Bastion, Firewall y Key Vault
