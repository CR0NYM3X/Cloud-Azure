 
#  1. **Suscripción (Subscription):**
### 🧩 ¿Qué es una suscripción en Azure?

Una **suscripción** es como una **carpeta contable y administrativa** que agrupa todos los recursos que creas en Azure (máquinas virtuales, bases de datos, redes, etc.). 

Cada suscripción tiene:
- **Un límite de recursos** (dependiendo del tipo de suscripción).
- **Un método de pago** o contrato asociado.
- **Un conjunto de permisos y políticas** que puedes aplicar.
- **Un identificador único** para facturación y administración.
 
### ✅ ¿Para qué sirve?

1. **Facturación separada**: Puedes tener una suscripción para producción y otra para pruebas, y ver cuánto cuesta cada una por separado.
2. **Control de acceso**: Puedes dar permisos diferentes por suscripción. Por ejemplo, el equipo de desarrollo solo accede a la suscripción de pruebas.
3. **Organización de recursos**: Ayuda a separar entornos, departamentos o clientes.
4. **Aplicación de políticas**: Puedes aplicar reglas de seguridad, límites de uso, etc., por suscripción.

 

### 🔄 ¿Se pueden crear varias suscripciones?

**Sí**, puedes tener varias suscripciones bajo una misma cuenta de Azure (también llamada "tenant"). Esto es muy común en empresas.


---
# 🧩 ¿Qué es un Grupo de recursos en Azure?

Un **Grupo de recursos** es una **unidad lógica** dentro de una **suscripción** que sirve para **organizar y administrar recursos relacionados** (como máquinas virtuales, bases de datos, redes, etc.).

 

### 🧬 Relación entre Suscripción y Grupo de recursos

- Una **suscripción** puede tener **muchos grupos de recursos**.
- Cada **grupo de recursos** pertenece **a una sola suscripción**.
- Dentro de un grupo de recursos puedes tener **todos los recursos que comparten un ciclo de vida**, permisos o propósito.

## 🏢 Caso real: Empresa de tecnología con múltiples entornos

### 🎯 Objetivo:
La empresa quiere separar sus entornos de **producción**, **desarrollo** y **seguridad**, y organizar sus recursos para facilitar la administración, facturación y control de acceso.

 

### 🔹 Estructura en Azure

#### 🔸 Suscripciones:
1. **Suscripción-Producción**
2. **Suscripción-Desarrollo**
3. **Suscripción-Seguridad**

Cada una tiene su propia facturación, límites y políticas.

 

#### 🔸 Grupos de recursos dentro de cada suscripción:

##### 🟢 Suscripción-Producción
| Grupo de recursos | Recursos incluidos | Propósito |
|-------------------|--------------------|-----------|
| `RG-WebAppProd` | VM, App Service, SQL Database | Aplicación web en producción |
| `RG-RedesProd` | VNET, NSG, Firewall | Infraestructura de red |
| `RG-MonitoringProd` | Log Analytics, Azure Monitor | Monitoreo y alertas |

##### 🔵 Suscripción-Desarrollo
| Grupo de recursos | Recursos incluidos | Propósito |
|-------------------|--------------------|-----------|
| `RG-WebAppDev` | VM, App Service, SQL Dev | Entorno de pruebas |
| `RG-RedesDev` | VNET, NSG | Red de desarrollo |
| `RG-TestTools` | Azure DevTest Labs | Herramientas de testing |

##### 🔴 Suscripción-Seguridad
| Grupo de recursos | Recursos incluidos | Propósito |
|-------------------|--------------------|-----------|
| `RG-SIEM` | Sentinel, Log Analytics | Seguridad y auditoría |
| `RG-Backup` | Recovery Vault, Azure Backup | Respaldos |
| `RG-Compliance` | Azure Policy, Defender | Cumplimiento normativo |

 

### 🧠 Beneficios de esta estructura

- **Separación clara de entornos**: Evita que errores en desarrollo afecten producción.
- **Control de acceso granular**: Cada equipo accede solo a lo que necesita.
- **Facturación independiente**: Puedes ver cuánto cuesta cada entorno.
- **Facilidad de automatización**: Puedes aplicar plantillas ARM o Bicep por grupo.
- **Escalabilidad**: Puedes agregar más suscripciones o grupos según crezca la empresa.
 
---

# 🏷️ ¿Qué son las etiquetas en Azure?

Las **etiquetas** son pares clave-valor que puedes asignar a **cualquier recurso**, **grupo de recursos** o incluso a una **suscripción**.  
Sirven para **clasificar, organizar, buscar, automatizar y controlar costos** de tus recursos.

 

### 🔗 Relación con suscripciones y grupos de recursos

- Puedes aplicar etiquetas a:
  - Recursos individuales (VMs, bases de datos, etc.)
  - Grupos de recursos
  - Suscripciones completas

- Las etiquetas **no afectan el funcionamiento** del recurso, pero sí ayudan a:
  - Filtrar en el portal
  - Generar reportes de costos
  - Aplicar políticas
  - Automatizar tareas

 

## 📌 Ejemplo real de uso de etiquetas

### 🎯 Escenario: Empresa con múltiples proyectos y equipos

Supongamos que tienes una **suscripción de producción** con varios grupos de recursos y recursos dentro de ellos.

#### 🔸 Grupo de recursos: `RG-WebAppProd`
Contiene:
- VM: `vm-web-01`
- SQL Database: `sql-web-prod`
- App Service: `webapp-prod`

#### 🔸 Etiquetas aplicadas:

| Recurso | Etiquetas |
|--------|-----------|
| `RG-WebAppProd` | `Proyecto = WebApp`, `Ambiente = Producción`, `Equipo = Desarrollo` |
| `vm-web-01` | `Owner = Juan`, `CostoCentro = 1001` |
| `sql-web-prod` | `Ambiente = Producción`, `Backup = Diario` |
| `webapp-prod` | `Proyecto = WebApp`, `Cliente = Interno` |

 

### 🧠 ¿Para qué sirven estas etiquetas?

1. **Costos**: Puedes generar reportes por `CostoCentro` o `Proyecto`.
2. **Automatización**: Puedes aplicar scripts que actúen solo sobre recursos con `Ambiente = Producción`.
3. **Seguridad**: Puedes aplicar políticas que obliguen a tener la etiqueta `Owner` en cada VM.
4. **Auditoría**: Saber quién es responsable de cada recurso (`Owner = Juan`).
5. **Filtrado en el portal**: Buscar todos los recursos del `Proyecto = WebApp`.

---

# 🧩 ¿Qué es una directiva en Azure?

En el contexto de **Azure Policy**, una **directiva** es una **regla específica** que define **qué está permitido, prohibido, auditado o configurado automáticamente** en tus recursos de Azure.
Se pueden asignar a Managment Groups -> Suscripción -> Grupos de recursos -> recuros . 
Estas tambien se heredan.


## 🧠 Estructura general

1. **Definición de directiva**: Describe la regla (por ejemplo, “todos los recursos deben tener la etiqueta `Owner`”).
2. **Asignación de directiva**: Aplica esa regla a un ámbito (suscripción, grupo de recursos).
3. **Efecto**: Define qué pasa si no se cumple la regla (`Deny`, `Audit`, `DeployIfNotExists`, etc.).

 

## 📌 Ejemplo real

### 🎯 Objetivo:
Evitar que se creen recursos sin la etiqueta `Ambiente`.

#### 🔸 Directiva:
- **Nombre**: `Require tag 'Ambiente'`
- **Descripción**: Requiere que todos los recursos tengan la etiqueta `Ambiente`.
- **Efecto**: `Deny` (bloquea la creación si no se cumple)

#### 🔸 Asignación:
- Se asigna a la **suscripción de producción**.

#### 🔸 Resultado:
Si alguien intenta crear una VM sin la etiqueta `Ambiente`, Azure **rechaza la operación automáticamente**.

 

## 🧰 Tipos de directivas comunes

| Nombre | Efecto | Uso |
|--------|--------|-----|
| `Allowed Locations` | Deny | Solo permite crear recursos en ciertas regiones |
| `Require Tags` | Deny | Obliga a usar etiquetas específicas |
| `Audit VMs without backup` | Audit | Detecta máquinas sin respaldo |
| `Deploy Diagnostic Settings` | DeployIfNotExists | Configura monitoreo automáticamente |
| `Allowed Resource Types` | Deny | Restringe tipos de recursos permitidos |


## 🧩 Diferencias entre Directiva e Iniciativa en Azure Policy

| Concepto | **Directiva** | **Iniciativa** |
|----------|----------------|----------------|
| ¿Qué es? | Una **regla individual** que define una condición específica para los recursos. | Un **conjunto de directivas agrupadas** para cumplir un objetivo más amplio. |
| Propósito | Aplicar una regla puntual (ej. exigir una etiqueta). | Aplicar varias reglas relacionadas (ej. gobernanza de recursos). |
| Ejemplo | “Requiere la etiqueta `Owner` en todos los recursos.” | “Cumplimiento de gobernanza básica” que incluye varias directivas: etiquetas, ubicación, tipos de recursos, etc. |
| Alcance | Se asigna directamente a una suscripción o grupo de recursos. | Se asigna igual, pero aplica **todas las directivas incluidas**. |
| Reutilización | Se usa para reglas específicas. | Se usa para **estándares corporativos o regulatorios**. |

## 🧩 Diferencias entre Definición y Asignación en Azure Policy

| Concepto | **Definición** | **Asignación** |
|----------|----------------|----------------|
| ¿Qué es? | Es la **plantilla o regla** que describe lo que se quiere controlar o auditar. | Es el **acto de aplicar** esa definición a un ámbito específico (suscripción, grupo de recursos, etc.). |
| ¿Contiene lógica? | ✅ Sí, incluye condiciones, parámetros, efectos (`Deny`, `Audit`, etc.). | ❌ No contiene lógica, solo usa la definición existente. |
| ¿Se puede reutilizar? | ✅ Sí, puedes usar la misma definición en múltiples asignaciones. | ✅ Sí, puedes asignar la misma definición en diferentes lugares. |
| ¿Dónde se crea? | En **Azure Policy > Definiciones**. | En **Azure Policy > Asignaciones** o desde la definición misma. |
| ¿Ejemplo? | “Requiere etiqueta `Owner` en todos los recursos.” | “Aplicar la política de etiqueta `Owner` a la suscripción de producción.” |


---

## 🧩 ¿Qué es una Red Virtual (VNet) en Azure?

Una **VNet (Virtual Network)** es como una red física tradicional, pero dentro de Azure. Permite que tus recursos (máquinas virtuales, bases de datos, etc.) se comuniquen entre sí, con internet o con tu red local.

### Componentes clave de una VNet:
1. **Subredes (Subnets):** Dividen la VNet en segmentos más pequeños.
2. **Interfaces de red (NICs):** Cada máquina virtual tiene una o más interfaces que se conectan a una subred.
3. **Direcciones IP:** Cada NIC tiene una IP privada (y opcionalmente una pública).
4. **NSG (Network Security Groups):** Controlan el tráfico que entra y sale de las subredes o NICs.
5. **Peering:** Permite conectar dos VNets para que se comuniquen entre sí.
6. **VPN Gateway / ExpressRoute:** Para conectar tu red local con Azure.


Los **Grupos de Seguridad de Red (NSG - Network Security Groups)** en Azure son como **firewalls básicos** que controlan el tráfico de red hacia y desde los recursos dentro de una red virtual. Son esenciales para proteger tus máquinas virtuales y otros servicios.

---

## 🔐 ¿Qué es un NSG?

Un **NSG** contiene una lista de **reglas de seguridad** que permiten o deniegan el tráfico de red **entrante (inbound)** y **saliente (outbound)** basado en:

- Dirección IP origen/destino
- Puerto origen/destino
- Protocolo (TCP/UDP)
- Prioridad de la regla
 

Puedes asociar un NSG a:

1. **Una subred completa** → afecta a todos los recursos dentro de esa subred.
2. **Una interfaz de red (NIC)** → afecta solo a la VM conectada a esa NIC.

> ⚠️ Si hay NSG en la subred y en la NIC, **ambos aplican** y las reglas se combinan.
 
Las reglas tienen:

- **Prioridad:** número entre 100 y 4096 (menor número = mayor prioridad).
- **Acción:** permitir o denegar.
- **Nombre:** identificador único.
- **Origen/Destino:** IP, rango o etiqueta (como `Internet`, `VirtualNetwork`, etc.).
- **Puerto:** específico o rango.
- **Protocolo:** TCP, UDP o ambos.

 

## 🧪 Ejemplo de reglas comunes

| Prioridad | Nombre         | Origen     | Puerto destino | Acción  | Descripción                  |
|-----------|----------------|------------|----------------|---------|------------------------------|
| 100       | Allow-SSH      | Internet   | 22             | Allow   | Permite acceso SSH a Linux   |
| 200       | Allow-RDP      | Internet   | 3389           | Allow   | Permite acceso RDP a Windows |
| 300       | Deny-All       | Internet   | *              | Deny    | Bloquea todo lo demás        |


