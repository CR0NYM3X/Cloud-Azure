 
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

 

### 🔗 Relación entre Azure Policy y las directivas

- **Azure Policy** es el **servicio** que gestiona el cumplimiento de reglas.
- Una **directiva** es una **unidad individual** dentro de Azure Policy que contiene una regla específica.
- Puedes **asignar** una directiva a una **suscripción**, **grupo de recursos** o **recurso**.
 

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
