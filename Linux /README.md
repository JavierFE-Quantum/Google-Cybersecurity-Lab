ª Bitacora de Prácticas 
# Reporte de Auditoría: Control de Acceso y Permisos en Linux

Como parte de la formación en ciberseguridad, auditmos permisos operativos en un entorno Linux para asegurar la integridad de archivos sensibles, aplicando el **Principio de Menor Privilegio**.

## 1. Escenario y Objetivo
El objetivo fue actualizar los permisos del directorio `/projects` para restringir accesos no autorizados, asegurando que solo el personal con las credenciales adecuadas pudiera modificar o ejecutar archivos críticos.

## 2. Metodología de Auditoría
Se utilizó la terminal para realizar un análisis de los permisos actuales y aplicar cambios inmediatos mediante comandos de administración.

### Comprobación Inicial
Se ejecutó el comando `ls -la` para listar los permisos de usuario, grupo y otros (u, g, o) en todos los archivos del directorio.

## 3. Acciones de Endurecimiento (Hardening)

### Restricción en archivos de texto
Para el archivo `project_k.txt`, se identificó un riesgo de escritura por usuarios externos. Se aplicó:
* **Comando:** `chmod o-w project_k.txt`
* **Resultado:** Se revocó el permiso de escritura a "otros", protegiendo el contenido de modificaciones externas.

### Gestión de archivos ocultos y sensibles
En el archivo oculto `.project_x.txt`, se detectó una configuración de permisos laxa. Se procedió a:
* **Comando:** `chmod u-w,g-w,g+r .project_x.txt`
* **Resultado:** Se eliminó la capacidad de escritura para el usuario y el grupo, otorgando únicamente permisos de lectura al grupo para mantener la operatividad sin riesgos.

### Seguridad a nivel de Directorio
Para el directorio `drafts`, se aplicó una restricción de navegación:
* **Comando:** `chmod g-x drafts`
* **Resultado:** Se eliminó el permiso de ejecución para el grupo, impidiendo que los miembros del mismo puedan entrar al directorio o listar su contenido.

## 4. Conclusión
La práctica resultó exitosa. Mediante el uso preciso de `chmod`, se logró alinear la estructura de archivos con las políticas de seguridad de la organización, garantizando que cada entidad (Usuario, Grupo, Otros) posea únicamente los permisos estrictamente necesarios para su función.
