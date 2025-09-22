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


---

## 🧩 ¿Qué es un ASG?

Un **ASG** es un contenedor lógico que agrupa máquinas virtuales (o sus interfaces de red) **por función o rol**, como por ejemplo:

- `asg-web` → VMs que sirven páginas web
- `asg-db` → VMs que alojan bases de datos
- `asg-app` → VMs que ejecutan lógica de negocio

No es un grupo de seguridad como el NSG, sino una **forma de agrupar recursos** para aplicar reglas de NSG de forma más flexible.

---

## 🔐 ¿Cómo se usan los ASGs?

Los ASGs Grupos de seguridad de aplicaciones se usan **dentro de las reglas de NSG** para definir el **origen o destino** del tráfico. En lugar de usar direcciones IP, usas el nombre del ASG.

### Ejemplo:
> Permitir tráfico desde `asg-web` hacia `asg-db` en el puerto 1433 (SQL Server)

Esto evita tener que escribir IPs manualmente y facilita la administración cuando agregas o quitas VMs.

## ⚠️ Consideraciones

- Los ASGs **solo funcionan dentro de la misma VNet**.
- No reemplazan los NSGs, sino que **complementan** su uso.
- No tienen reglas propias; se usan **dentro de NSGs**.

---

## 🧱 ¿Qué es un Conjunto de Disponibilidad?

Un **Availability Set** es una agrupación lógica de máquinas virtuales que Azure usa para distribuirlas entre:

- **Dominios de actualización (Update Domains)** → para evitar que todas las VMs se reinicien al mismo tiempo durante actualizaciones de mantenimiento.
- **Dominios de error (Fault Domains)** → para evitar que todas las VMs que estan en el mismo DataCenter estén en el mismo rack físico o fuente de energía, refrigeracion y red.

> ✅ Esto **no garantiza 100% de disponibilidad**, pero **reduce el riesgo de interrupciones simultáneas**.
 
## 🧩 ¿Cuándo se usa?

- Cuando tienes **2 o más VMs** que ejecutan la misma función (por ejemplo, servidores web).
- Quieres que **si una falla, otra siga funcionando**.
- No estás usando escalado automático ni balanceadores de carga avanzados.
 
 

## 🆚 ¿Availability Set vs. Availability Zone?

| Característica         | Availability Set         | Availability Zone           |
|------------------------|--------------------------|------------------------------|
| Nivel de protección    | Dentro de un datacenter  | Entre datacenters en una región |
| Alta disponibilidad    | ~99.95%                  | ~99.99%                      |
| Costo adicional        | No                       | Sí                           |
| Recomendado para       | VMs redundantes simples  | Aplicaciones críticas        |



## 🧪 Ejemplos reales de uso de Availability Sets

### 🔹 1. **Servidores Web Redundantes**
**Escenario:** Una empresa tiene 3 servidores web que atienden tráfico HTTP.

**Uso del Availability Set:**
- Se colocan las 3 VMs en un Availability Set.
- Se configura un Load Balancer para distribuir el tráfico.
- Si Azure actualiza o reinicia una VM, las otras siguen funcionando.

> ✅ Alta disponibilidad sin necesidad de zonas geográficas.
 


### 🔹 1. **Controladores de Dominio (Active Directory)**
**Escenario:** Infraestructura de AD en Azure.

**Uso del Availability Set:**
- Se crean 2 controladores de dominio (DCs).
- Se colocan en un Availability Set.
- Se asegura que no estén en el mismo rack físico.

> ✅ Evita que el dominio quede inoperante por falla de hardware.




### 🔹 3. **Servidores de Base de Datos No Críticos**
**Escenario:** Bases de datos que no requieren replicación geográfica.

**Uso del Availability Set:**
- Se colocan 2 VMs con PostgreSQL o SQL Server.
- Se usa un Availability Set para evitar reinicios simultáneos.
- Se configuran backups y monitoreo.

> ✅ Aumenta la disponibilidad sin usar zonas ni servicios administrados.

 

## 🧠 ¿Cuándo **NO** usar Availability Sets?

- Cuando necesitas **alta disponibilidad geográfica** → usa **Availability Zones**.
- Cuando usas **servicios administrados** como Azure SQL, App Service, etc.
- Cuando tienes **solo una VM** → no tiene sentido usar Availability Set.


---

## 🌍 ¿Qué es una **Región** en Azure?
 
Una **región** es una ubicación geográfica (país/ciudad) amplia donde Azure tiene **centros de datos**. Ejemplos de regiones:

- `East US` (Virginia, EE.UU.)
- `West Europe` (Países Bajos)
- `Brazil South` (São Paulo)
- `Mexico Central` (Ciudad de México)

Cada región puede tener **uno o varios datacenters**, y es donde se alojan tus recursos.
 

## 🏢 ¿Qué son las **Zonas de Disponibilidad**?

Las **Zonas de Disponibilidad (Availability Zones)** son **ubicaciones físicas separadas pero se encuentran dentro de una misma región **. Cada zona tiene:

- Su propio **datacenter independiente**
- Su propia **energía, red y refrigeración**
- Alta tolerancia a fallos

Por ejemplo, la región `East US` puede tener:
- Zona 1 → Datacenter A
- Zona 2 → Datacenter B
- Zona 3 → Datacenter C

> ✅ Si colocas tus recursos en diferentes zonas, **siguen en la misma región**, pero están **aislados físicamente** para mayor disponibilidad.

 

## 🧠 ¿Entonces están en diferentes ciudades?

**No necesariamente.** Las zonas están en **diferentes edificios o campus dentro de la misma ciudad o área metropolitana**. No están tan lejos como para considerarse otra ciudad, pero sí lo suficiente para que **una falla física no afecte a todas**.

 

## 🧪 Ejemplo práctico

Supongamos que estás en la región `West Europe`:

- Si creas 3 VMs en **zonas diferentes** (`Zona 1`, `Zona 2`, `Zona 3`), y una zona falla, las otras siguen funcionando.
- Si usas un **Load Balancer con zonas**, puedes distribuir tráfico entre ellas.
 

## 🛠️ ¿Cuándo elegir zonas?

- Cuando necesitas **alta disponibilidad crítica** (99.99%)
- Cuando quieres **resistencia a fallos físicos**
- Cuando usas servicios que **soportan zonas**, como:
  - VMs
  - Load Balancer
  - Azure SQL
  - App Gateway
 
  ---

  ### 🧭 **Ruta clara para implementar Control de Accesos en Azure**

Aquí tienes una guía paso a paso para comenzar desde cero:

 

## 🔐 1. **Entender el modelo de identidad en Azure**

Azure usa **Azure Active Directory (Azure AD)** como base para la gestión de identidades y accesos.

- **Usuarios**: Empleados, contratistas, servicios.
- **Grupos**: Para asignar permisos de forma masiva.
- **Roles**: Definen qué acciones pueden realizar los usuarios.
- **Recursos**: Máquinas virtuales, bases de datos, redes, etc.

 

## 🧱 2. **Crear usuarios y grupos**

Puedes hacerlo desde el portal de Azure o con PowerShell/CLI.

- **Portal**: Azure AD → Usuarios → Nuevo usuario.
- **Grupos**: Azure AD → Grupos → Crear grupo (por departamento, rol, proyecto).
 

## 🛡️ 3. **Asignar roles con Azure RBAC (Role-Based Access Control)**

Azure RBAC permite asignar **roles predefinidos o personalizados** a usuarios/grupos sobre recursos específicos.

- Ejemplo: El grupo "DB Admins" tiene el rol "Contributor" sobre la base de datos `prod-db`.
- Roles comunes:
  - **Reader**: Solo lectura.
  - **Contributor**: Lectura y escritura, sin borrar.
  - **Owner**: Control total.
  - **User Access Administrator**: Puede asignar roles.
 
## 📜 4. **Aplicar políticas con Azure Policy**

Azure Policy te permite **definir reglas y restricciones** sobre los recursos.

- Ejemplos:
  - Solo se pueden crear VMs en ciertas regiones.
  - Las VMs deben tener etiquetas específicas.
  - Las bases de datos deben tener cifrado activado.
 

## 🧩 5. **Usar Conditional Access (Acceso Condicional)**

Controla el acceso según condiciones como:

- Ubicación geográfica.
- Dispositivo usado.
- Estado de seguridad del usuario.

Ejemplo: "Solo permitir acceso al portal de Azure desde México y con MFA (autenticación multifactor)".
 

## 🔐 6. **Implementar MFA y seguridad de inicio de sesión**

- Activar **Multi-Factor Authentication** para todos los usuarios.
- Configurar **Identity Protection** para detectar riesgos de inicio de sesión.
 

## 🧰 7. **Auditoría y monitoreo**

- Usa **Azure Monitor**, **Log Analytics** y **Microsoft Defender for Cloud** para:
  - Ver quién accedió a qué.
  - Detectar accesos sospechosos.
  - Generar alertas y reportes.
 

### 📚 Recursos recomendados para aprender y aplicar

1. Documentación oficial de Azure AD
2. Azure RBAC
3. Azure Policy
4. Acceso condicional
5. Microsoft Learn - Ruta de aprendizaje de seguridad en Azure





