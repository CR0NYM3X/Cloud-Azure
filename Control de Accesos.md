## 👤 ¿Qué es una **cuenta Microsoft ID**?

Una **Microsoft ID** (también conocida como **cuenta de Microsoft**) es una cuenta de usuario que puede ser:

- **Personal**: como `usuario@hotmail.com` o `usuario@outlook.com`.
- **Organizacional**: como `empleado@tuempresa.com` gestionada por Azure AD.

### ✅ ¿Para qué sirve?
- Autenticarse en servicios de Microsoft como Azure, Office 365, Teams, etc.
- Asociar roles y permisos en Azure mediante **Azure Active Directory**.
- Aplicar políticas de seguridad, MFA, acceso condicional, etc.

 
## 🧩 Diferencias clave

| Característica | SAS | Microsoft ID |
|----------------|-----|--------------|
| Tipo de acceso | Temporal y limitado | Permanente y gestionado |
| Seguridad | Basado en token | Basado en identidad |
| Uso común | Compartir archivos o blobs | Acceso a portal, recursos, apps |
| Control | Permisos por URL | Roles, grupos, políticas |

 



 
## 🔐 ¿Qué es una **firma de acceso compartido (SAS)**?

Una **SAS (Shared Access Signature)** es una **URL especial** que otorga acceso limitado a recursos de almacenamiento en Azure (como blobs, archivos, colas o tablas) **sin necesidad de compartir la clave de la cuenta**.

### ✅ ¿Para qué sirve?
- Permitir que aplicaciones o usuarios accedan a recursos **por tiempo limitado**.
- Controlar **qué operaciones** se pueden hacer: lectura, escritura, eliminación, etc.
- Evitar dar acceso completo a la cuenta de almacenamiento.

### 📦 Ejemplo de uso:
Supongamos que tienes un archivo en Azure Blob Storage y quieres que un proveedor externo lo descargue sin tener acceso a toda tu cuenta. Generas una SAS con permisos de lectura válidos por 24 horas.

```plaintext
https://miaccount.blob.core.windows.net/micontenedor/miarchivo.txt?sv=2022-11-02&st=2025-09-22T00%3A00%3A00Z&se=2025-09-23T00%3A00%3A00Z&sr=b&sp=r&sig=abc123...
```



### ¿Cuándo usar cada uno?

- Usa **SAS** cuando quieras compartir acceso a un archivo o recurso de almacenamiento **sin crear usuarios**.
- Usa **Microsoft ID** cuando quieras que un empleado o sistema tenga acceso **gestionado y seguro** a recursos de Azure.
