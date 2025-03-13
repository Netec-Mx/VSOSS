# Vmware vSphere Operación, Escalamiento y Seguridad 

**Plataforma de Laboratorios**

Bienvenido a la **Plataforma de Laboratorios** del curso **Vmware vSphere Operación, Escalamiento y Seguridad**. Aquí podrás explorar diferentes tecnologías a través de prácticas guiadas. ¡Desarrolla tus habilidades y lleva tus conocimientos al siguiente nivel!

---

## 🌟 **Lista de Laboratorios**

Cada uno de estos laboratorios está diseñado para ofrecerte una experiencia práctica. Haz clic en los enlaces para comenzar.

---
 
## Índice:
 - [Práctica 1. Acceso al escritorio y revisión del inventario del vCenter Server.](./Laboratorio1/main.md)
   - **Descripción**: Acceder al vCenter Server, revisar el inventario del datacenter para verificar la infraestructura. Finalmente, comprobar el estado de licenciamiento de los hosts y del vCenter Server para asegurar que todo esté correctamente licenciado.
   - ⏱️ **Duración estimada**: 30 minutos.

 - [Práctica 2. Compartir en forma centralizada los VMware VMtools.](./Laboratorio2/main.md)
   - **Descripción**: Ver el valor por default de la ubicación de las VMtools para poder modificar la variable avanzada de ubicación mediante un comando ESXi.
   - ⏱️ **Duración estimada**: 50 minutos.

 - [Práctica 3. Administración de pools de recursos.](./Laboratorio3/main.md)
   - **Descripción**: Revisar el desempeño de VMs sin condiciones de contención para evaluar los cambios que experimenta su funcionamiento al utilizar condiciones de contención y pools de recursos.
   - ⏱️ **Duración estimada**: 40 minutos.

 - [Práctica 4. Manejo adecuado de las vCLS VMs en operaciones del storage.](./Laboratorio4/main.md)
   - **Descripción**: Explorar el estado de las VMs vCLS en el clúster y gestionar su operación configurando el modo de mantenimiento del almacenamiento en el que residen, utilizando el modo de retiro para su correcta administración. 
   - ⏱️ **Duración estimada**: 20 minutos.

 - [Práctica 5. Creación y configuración de un switch distribuido.](./Laboratorio5/main.md)
   - **Descripción**: Crear y configurar un switch distribuido, integrando hosts al mismo y realizando la migración de las VMs. Finalmente, verificar la correcta configuración del switch distribuido para asegurar su funcionalidad. 
   - ⏱️ **Duración estimada**: 30 minutos.

 - [Práctica 6. Administración de switches distribuidos.](./Laboratorio6/main.md)
   - **Descripción**: Agregar un grupo de puertos a un switch distribuido. Activar y verificar su estado de salud. Corregir cualquier error reportado y, una vez solucionados, anular la verificación de estado de salud. Finalmente, exportar la configuración del switch distribuido para su respaldo o transferencia. 
   - ⏱️ **Duración estimada**: 30 minutos.

 - [Práctica 7. Aplicación de la función Port Mirroring en los switches distribuidos.](./Laboratorio7/main.md)
   - **Descripción**: Establecer las condiciones necesarias para la captura de tráfico y configurar el switch distribuido para ello. Realizar la captura de tráfico y verificar su correcta funcionalidad. Finalmente, restaurar la configuración original del switch distribuido desde un respaldo. 
   - ⏱️ **Duración estimada**: 40 minutos.

 - [Práctica 8. Exploración de la configuración de un datastore vSAN.](./)
   - **Descripción**: Revisar la configuración de un datastore de vSAN y su política de almacenamiento predeterminada. Finalmente, verificar el estado de una VM en el datastore de vSAN. 
   - ⏱️ **Duración estimada**: 30 minutos.

 - [Práctica 9.Aplicación de una política de almacenamiento .](./Laboratorio9/main.md)
   - **Descripción**: Agregar datastores para su uso en almacenamiento basado en políticas, y, posteriormente, utilizar vSphere Storage vMotion para migrar el almacenamiento de las máquinas virtuales. Además, configurar etiquetas de almacenamiento, crear políticas de almacenamiento específicas para las VMs y, finalmente, asignar dichas políticas a las máquinas virtuales correspondientes. 
   - ⏱️ **Duración estimada**: 30 minutos.

 - [Práctica 10. Creación de una política de vSAN.](./Laboratorio10/main.md)
   - **Descripción**: Examinar la política de almacenamiento predeterminada, luego crear una política personalizada sin tolerancia a errores. Posteriormente, asignar esta política a una máquina virtual y asegurarse de que la máquina virtual cumpla con la configuración preestablecida. 
   - ⏱️ **Duración estimada**: 30 minutos.

 - [Práctica 11. Respaldo del vCenter Server.](./Laboratorio11/main.md)
   - **Descripción**: Acceder a la consola de administración del vCenter Server, examinar las opciones disponibles para respaldos programados e inmediatos, y lanzar un proceso de respaldo del vCenter Server. Finalmente, visualizar la opción de restauración de un backup utilizando la aplicación Install. 
   - ⏱️ **Duración estimada**: 30 minutos.

 - [Práctica 12. Manejo de Host Profiles en Vsphere.](./Laboratorio12/main.md)
   - **Descripción**: Configurar un clúster con una imagen única y, luego, con perfiles de configuración. Posteriormente, retornar un host a una configuración específica y revisar el documento de configuración para asegurar que todos los parámetros estén correctamente establecidos. 
   - ⏱️ **Duración estimada**: 60 minutos.

 - [Práctica 13. Trabajo con certificados.](./Laboratorio13/main.md)
   - **Descripción**: Examinar el certificado SSL de una máquina virtual, generar una solicitud de firma de certificado. Finalmente, reemplazar el certificado SSL de la máquina por un certificado de CA pregenerado. 
   - ⏱️ **Duración estimada**: 30 minutos.

 - [Práctica 14. Monitoreo del desempeño de un máquina virtual.](./Laboratorio14/main.md)
   - **Descripción**: Establecer afinidad de CPU y configurar la contención en dos VMs. Luego, explorar las opciones disponibles en las gráficas de desempeño para evaluar el rendimiento de las máquinas virtuales. 
   - ⏱️ **Duración estimada**: 40 minutos.

 - [Práctica 15. Manejo de alarmas.](./Laboratorio15/main.md)
   - **Descripción**: Establecer una alarma para monitorear una condición específica y disparar la alarma cuando se cumpla. Luego, configurar una alarma para monitorear un evento y activar la alarma correspondiente. Finalmente, se deben desactivar ambas alarmas una vez realizadas las verificaciones necesarias. 
   - ⏱️ **Duración estimada**: 40 minutos.

 - [Práctica 16. Configuración del modo Lockdown mode en un host ESXi.](./Laboratorio16/main.md)
   - **Descripción**: Activar el servicio SSH, habilitar y probar el modo Lockdown mode para restringir el acceso a los hosts. Finalmente, deshabilitar el modo Lockdown mode una vez completadas las pruebas. 
   - ⏱️ **Duración estimada**: 20 minutos.

 - [Práctica 17. Configuración de vCenter para trabajar con un KMS externo.](./Laboratorio17/main.md)
   - **Descripción**: Configurar un KMS en vCenter y, posteriormente, establecer la confianza entre el KMS y vCenter, lo que permitirá la gestión segura de claves de cifrado y garantizará la integración adecuada entre ambos sistemas. 
   - ⏱️ **Duración estimada**: 40 minutos.

 - [Práctica 18. Creando una máquina virtual cifrada.](./Laboratorio18/main.md)
   - **Descripción**: Crear una máquina virtual cifrada y, a continuación, confirmar que la máquina virtual está cifrada utilizando un proveedor de llaves estándar, asegurando así la protección de los datos en la VM. 
   - ⏱️ **Duración estimada**: 40 minutos.
