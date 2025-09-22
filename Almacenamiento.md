
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


### 💰 Modelos de costos

Azure cobra por:

- **Capacidad**: GB almacenados por mes.
- **Transacciones**: operaciones de lectura/escritura.
- **Transferencia de datos**: especialmente salidas (egress).
- **Redundancia**: más copias = más coste.



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




#### Tipos de redundancia:

| Tipo | Descripción | Costo |
|------|-------------|-------|
| LRS (Locally Redundant) | 3 copias en un datacenter | Bajo |
| ZRS (Zone Redundant) | Copias en zonas de disponibilidad | Medio |
| GRS (Geo Redundant) | Copias en otra región | Alto |
| RA-GRS (Read Access GRS) | Igual que GRS pero con lectura en región secundaria | Alto |

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
