# Reporte de Auditoría: Control de Acceso y Permisos en Linux

Como parte de la formación en ciberseguridad, se realizó una auditoría operativa en un entorno Linux para asegurar la integridad de archivos sensibles, aplicando el **Principio de Menor Privilegio**.

## 1. Escenario y Objetivo
El objetivo fue actualizar los permisos del directorio `/projects` para restringir accesos no autorizados.

## 2. Metodología de Auditoría

### Comprobación Inicial
Se ejecutó el comando `ls -la` para auditar los permisos vigentes en el directorio.

![Comprobación Inicial de Permisos](Permisos_Linux1.jpg)

## 3. Acciones de Endurecimiento (Hardening)

### Restricción en archivos de texto (project_k.txt)
Se revocó el permiso de escritura a "otros" para evitar modificaciones no autorizadas.
* **Comando:** `chmod o-w project_k.txt`

![Modificación de permisos en project_k.txt](Permisos_Linux2.jpg)

### Gestión de archivos ocultos (.project_x.txt)
Se eliminó la capacidad de escritura para el usuario y el grupo, manteniendo solo lectura para el grupo.
* **Comando:** `chmod u-w,g-w,g+r .project_x.txt`

![Ajuste de permisos en archivo oculto](Permisos_Linux3.jpg)

### Seguridad a nivel de Directorio (drafts)
Se eliminó el permiso de ejecución para el grupo, impidiendo el acceso al contenido sensible.
* **Comando:** `chmod g-x drafts`

![Restricción de ejecución en directorio drafts](Permisos_Linux4.jpg)

## 4. Conclusión
La auditoría y las acciones de endurecimiento resultaron exitosas, alineando la estructura de archivos con las políticas de seguridad mediante el uso preciso de comandos de administración.
