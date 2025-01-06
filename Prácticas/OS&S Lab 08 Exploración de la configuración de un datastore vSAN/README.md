> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> ### Versión 8

> ### Guía de uso de laboratorio

## Laboratorio \# 8

> ### Exploración de la configuración de un datastore vSAN
>
> Revisión 1.1 2024

## Laboratorio \# 8

> ### Exploración de la configuración de un datastore vSAN

#### Actividades por realizar:

1.  Revisar la configuración de un datastore de vSAN

2.  Revisar la política por default de almacenamiento en vSAN

3.  Revisar una VM en el datastore de vSAN

## Actividad \# 1

### Revisar la configuración de un datastore de vSAN

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

1.- **Abrir una instancia de Firefox, seleccionar el shortcut de
_vCenter_**

2.- **Verificar que _VSAN_ está habilitado en el cluster**

En la vista de **Hosts & Clusters** (1), seleccionar el cluster
**Production Cluster** (2), click en la pestaña **Configure** (3), en la
sección de configuración seleccionar **Quickstart,** revisar que
**vSAN** aparece como un servicio activo

3.- **Revisar que Hosts pertenecen al cluster de _vSAN_**

En la vista de **Hosts & Clusters** (1), seleccionar el cluster
**Production Cluster** (2), click en la pestaña **Summary** (3)

Desplazarse entre las secciones y checar que en la sección de **Cluster
Resources** el número de hosts que están relacionados en el cluster de
**vSAN.**

Click en la pestaña de **Host**s para ver el nombre de los host ESXi en
el cluster

4.- **Revisar la configuración de grupos de discos en el cluster de
_vSAN_**

En la vista de **Hosts & Clusters** (1), seleccionar el cluster
**Production Cluster** (2), click en la pestaña **Configure** (3)

En la sección de **vSAN** click **Disk Managment**

En cada host seleccionar **VIEW DISK** y expanda el grupo de discos
**Disk group** para ver sus detalles

5.- **Identificar la configuración del puerto VMkernel que se usa para
accesar la red de _vSAN_**

En la vista de **Hosts & Clusters** (1), seleccionar el cluster
**Production Cluster** (2), click en el host **ESXI_01** (3), click en
la pestaña **Configure**, en la sección de **Networking** seleccionar
**Vmkernel Adapters**

En la lista de puertos VMkernel expandir el **vmk1** para revisar sus
detalles

Click en la pestaña de **Properties** para el puerto **vmk1**

Verificar que aparece el servicio **vSAN** activo para este puerto.

6.- **Ver la capacidad de almacenamiento del cluster de vSAN**

En la vista de **Hosts & Clusters** (1), seleccionar el cluster
**Production Cluster** (2), click en la pestaña **Summary** (3),

Desplazarse entre la secciones para hallar en la sección de **vSAN** que
muestra la capacidad de almacenamiento.

Para ver el uso del espacio de vSAN click **VIEW CAPACITY** en el
recuadro de **vSAN Capacity**, se muestra la pestaña **MONITOR** click
**vSAN**, seleccionar **Capacity**, **Click Capacity Over**view esto
muestra el espacio libre y ocupado en **vSAN**

## Actividad \# 2

### Revisar la política por default de almacenamiento en vSAN

Desde el menú principal seleccionar **Policies and Profiles**

En el panel de navegación verificar que políticas de almacenamiento para
VMs están activas

En el panel derecho desplazarse en la lista de políticas y seleccionar
**vSAN Default Storage Policy**

En la pestaña de reglas ver la especificación para esta política de
almacenamiento

La misma una política de RAID 1 (mirroring)

## Tarea \#3

### Revisar una VM en el datastore de vSAN

Para tener la certeza de que una VM está almacenada en un datastore de
vSAN**

En la vista de **datastore** click en el datastore vsanDatastore, click en
la pestaña de VMs

En la misma aparece la lista de VMs
