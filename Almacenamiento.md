


### 📘 ¿Qué es una cuenta de almacenamiento en Azure?

Una **cuenta de almacenamiento** en Azure es un contenedor lógico que te permite acceder y administrar servicios de almacenamiento, primero crear una cuenta de almacenamiento. Esta cuenta es como una "carpeta principal" donde se guardan todos tus contenedores. Sin ella, no puedes subir ni acceder a archivos.

### 🧠 Tipos de almacenamiento en Azure

Azure ofrece varios servicios de almacenamiento, agrupados principalmente en:

1. **Blob Storage**  
   - Para almacenar objetos no estructurados, Solo lectura y eliminación* como imágenes, vídeos, backups, etc. 
   - **Uso típico**: Archivos históricos, respaldos legales, registros que deben conservarse por años.
   - Tipos: Block Blob, Append Blob, Page Blob.

2. **File Storage**  
   - Sistema de archivos compartido basado en SMB/NFS.
   - Ideal para lift-and-shift de aplicaciones que usan archivos.

3. **Queue Storage**  
   - Para almacenar mensajes en cola entre componentes distribuidos.

4. **Table Storage**  
   - Almacenamiento NoSQL para datos estructurados con acceso rápido.

5. **Disk Storage**  
   - Discos gestionados para máquinas virtuales (HDD, SSD estándar/premium).

Cuando creas una cuenta de almacenamiento, defines:

1. **Tipo de redundancia** (LRS, ZRS, GRS, GZRS, etc.)
2. **Tipo de rendimiento** (Standard o Premium)
   
| Tipo de rendimiento | Tecnología | Características | Escenarios recomendados |
|---------------------|------------|------------------|--------------------------|
| **Estándar**        | HDD (disco duro) | Más económico, buena capacidad, latencia moderada | Archivos generales, backups, datos no críticos |
| **Prémium**         | SSD (estado sólido) | Alta velocidad, baja latencia, mayor costo | Bases de datos, apps críticas, discos de VM |

- **Estándar** usa almacenamiento basado en discos duros (HDD), ideal para cargas de trabajo que no requieren acceso ultra rápido.
- **Prémium** usa discos SSD, lo que permite **latencia muy baja** y **mayor rendimiento**, especialmente útil en escenarios como:
  - Discos administrados para máquinas virtuales (Premium SSD)
  - Bases de datos con alta demanda de IOPS
  - Aplicaciones empresariales sensibles al rendimiento

4. **Tipo de Almacenamiento** (General Purpose v2, BlobStorage, FileStorage, etc.)
5. **Ubicación geográfica**
6. **Acceso público o privado**

--- 




## 💰 **Modelos de costos en Azure Storage**

Azure cobra según **varios factores**, no solo por el espacio ocupado:

### 1. **Por capacidad (GB almacenados)**
- Aplica a todos los tipos: Blob, File, Disk, etc.
- **Ejemplo**: Guardar 100 GB en Blob Hot cuesta más que en Blob Cool o Archive.

### 2. **Por operaciones (consultas, escrituras, eliminaciones)**
- Blob Storage cobra por cada operación: lectura, escritura, listado, etc.
- **Ejemplo**: Leer 10,000 archivos cuesta más que leer 100.

### 3. **Por transferencia de datos**
- Salida de datos (egreso) hacia internet tiene costo.
- **Ejemplo**: Descargar archivos desde Blob Storage a un cliente externo.

### 4. **Por Tipos de redundancia en Azure Storage**
> En Azure, la redundancia de almacenamiento se refiere a cuántas copias de tus datos se guardan y dónde. Esto ayuda a protegerlos contra fallos.
 
Azure ofrece varios tipos de redundancia para proteger tus datos ante fallos locales, regionales o geográficos. Aquí están los principales:

| Tipo de Redundancia | Copias | Ubicación | Nivel de protección |
|---------------------|--------|-----------|----------------------|
| **LRS** (Locally Redundant Storage) | 3 copias | Dentro de un solo datacenter | Protección contra fallos de hardware local |
| **ZRS** (Zone-Redundant Storage) | 3 copias | En 3 zonas de disponibilidad dentro de una región | Protección contra fallos de zona |
| **GRS** (Geo-Redundant Storage) | 6 copias (3 local + 3 en región secundaria) | Región primaria + región secundaria | Protección contra fallos regionales |
| **GZRS** (Geo-Zone-Redundant Storage) | 6 copias (3 en zonas + 3 en región secundaria) | Zonas en región primaria + región secundaria | Protección avanzada contra fallos de zona y región |
| **RA-GRS / RA-GZRS** | Igual que GRS/GZRS pero con acceso de solo lectura a la región secundaria | | Ideal para alta disponibilidad de lectura |
---

## 📊 Comparativa rápida

| Tipo de almacenamiento | Modificable | Costos por consulta | Ideal para |
|------------------------|-------------|----------------------|-------------|
| Blob Hot               | ✅ Sí       | ✅ Sí                | Acceso frecuente |
| Blob Cool              | ✅ Sí       | ✅ Sí (más barato)   | Acceso ocasional |
| Blob Archive           | ❌ No       | ✅ Sí (muy barato)   | Archivos históricos |
| File Storage           | ✅ Sí       | ✅ Sí                | Compartir archivos |
| Table Storage          | ✅ Sí       | ✅ Sí                | Datos NoSQL |
| Queue Storage          | ✅ Sí       | ✅ Sí                | Mensajería |
| Disk Storage           | ✅ Sí       | ❌ No (incluido en VM) | Discos de VM |

 
---

### ✅ Ventajas y ❌ Desventajas

| Tipo | Ventajas | Desventajas |
|------|----------|-------------|
| Blob | Escalable, económico, ideal para datos no estructurados | No apto para acceso tipo archivo |
| File | Compatible con SMB/NFS, fácil integración | Menor rendimiento que Blob |
| Queue | Ideal para sistemas distribuidos | No apto para grandes volúmenes |
| Table | Rápido y barato para NoSQL | Limitado en consultas complejas |
| Disk | Alto rendimiento para VMs | Coste más alto |



### 📊 Tabla comparativa

| Servicio     | Tipo de datos     | Acceso     | Redundancia | Coste | Casos de uso |
|--------------|-------------------|------------|-------------|-------|--------------|
| Blob         | No estructurados  | HTTP/HTTPS | LRS/ZRS/GRS | Bajo  | Backups, multimedia |
| File         | Archivos          | SMB/NFS    | LRS/ZRS     | Medio | Compartir archivos |
| Queue        | Mensajes          | API REST   | LRS         | Bajo  | Microservicios |
| Table        | NoSQL estructurado| API REST   | LRS         | Bajo  | Logs, datos de usuario |
| Disk         | Persistente para VMs | VM directa | LRS/ZRS     | Alto  | Discos de sistema |


---


### 🚀 ¿Para qué sirve AzCopy?

AzCopy se usa principalmente para:

- Subir archivos a **Azure Blob Storage**, **File Storage** o **Table Storage**.
- Descargar archivos desde Azure a tu máquina local o a otro servidor.
- Copiar datos entre cuentas de almacenamiento en Azure.
- Automatizar transferencias de datos en scripts o procesos de migración.

 

### 🧰 Características clave

- **Alta velocidad**: Optimizado para transferencias grandes.
- **Seguridad**: Compatible con SAS tokens, Azure AD, y claves de cuenta.
- **Multiplataforma**: Funciona en Windows, Linux y macOS.
- **Automatizable**: Ideal para tareas programadas o scripts.

 

### 📦 Ejemplo de uso básico

Supongamos que quieres subir un archivo local a un contenedor en Azure Blob Storage:

```bash
azcopy copy "C:\archivos\miarchivo.txt" "https://miaccount.blob.core.windows.net/micontenedor?SAS_TOKEN" --overwrite=true
```

O descargar un archivo desde Azure:

```bash
azcopy copy "https://miaccount.blob.core.windows.net/micontenedor/miarchivo.txt?SAS_TOKEN" "C:\descargas\" --recursive
```

 

### 🔐 ¿Cómo se autentica AzCopy?

Puedes usar:

- **SAS tokens** (como los que mencionaste antes).
- **Azure AD** (si estás autenticado con `az login`).
- **Clave de cuenta** (menos recomendado por seguridad).


