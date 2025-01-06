> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> **Versión 8**
>
> **Guía de uso de laboratorio**

## Laboratorio \# 4

### Manejo adecuado de las vCLS VMs en operaciones del storage

> Revisión 1.1 2024

## Laboratorio \# 4

### Manejo adecuado de las vCLS VMs en operaciones del storage

#### Actividades a realizar:

1.  **Explorar en el cluster el estado de las vCLS VMs**

2.  **Manejo de vCLS VMs al establecer el modo de mantenimiento del
    storage en donde residen**

## Actividad \# 1

### Explorar en el cluster el estado de las vCLS VMs

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Recordemos que las vCLS VMs se utilizan para garantizar que ciertas
operaciones del clúster, como DRS y HA, sigan funcionando incluso si
vCenter está temporalmente inaccesible.

Las vCLS VMs son creadas automáticamente por vSphere en cada host del
clúster.

Si en las operaciones del cluster es requerido poner el datastore en el
que se alojan los discos de estas máquinas virtuales en mantenimiento es
necesario proactivamente migrar con storage vMotion las vCLS VMS a otro
datastore compartido para continuar la protección.

Se pueden observar las VMs que se han creado en el cluster y las vCLS
VMs

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **VMs** (3), se ven las
VMs de operación (4) y las vCLS (5)

<img src="./media/image1.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para observar las vCLS VMs también se puede seleccionar la vista de
**VMS & Templates** (1), en la misma se muestran por separado (2)

<img src="./media/image2.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Veamos cómo están ubicadas a nivel de servidor

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en el host **ESXi_01** (3), click en
la pestaña **VMs** (4), aquí se puede observar que en el host
**ESXi_01** está registrada una vCLS VM (5).

<img src="./media/image3.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

De manera semejante y por temas de alta disponibilidad vemos la otra
VCLS en el Host **ESXi_02**

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en el host **ESXi_02** (3), click en
la pestaña **VMs** (4), aquí se puede observar que en el host
**ESXi_02** está registrada otra vCLS VM (5).

<img src="./media/image4.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ahora, observar a manera de ejemplo en que datastore está alojada la
vCLS que está en el host **ESXi_01**.

En la vista de **VMs & Templates** (1), click en la **vCLS VM** (2),
Observar la sección de objetos relacionados (3).

El datastore en el que se encuentra es el **NFS**.

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Las dos vCLS están en el mismo datastore

En la vista de **Datastores** (1), click en el datastore **NFS** (2),
click en la pestaña **Files** (3), Observar que se encuentran los dos
directorios relacionados con las **vCLS VMs**. (4)(5)

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \#2

### Manejo de vCLS VMs al establecer el modo de mantenimiento del storage en donde residen


Veamos cómo se da el proceso ordenado de poner el datastore NFS que
aloja las vCLS VMs,

En la vista de **Datastores** (1), click en el datastore **NFS** (2), en
el menú contextual, click en **Maintenance Mode** (3), seleccionar
**Enter maintenance mode** (4).

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En este caso se detecta que el datastore tiene dos vCLS VMs (1), por lo
tanto, se nos ofrece la opción de hacer un storage vMotion de ambas VMs
antes de poner el datastore en modo mantenimiento.

Activar la opción de migración anticipada (2), **CONTINUE** (3),

<img src="./media/image8.png" style="width:6.44145in;height:4.12182in"
alt="A screenshot of a computer Description automatically generated" />

Se nos solicita confirmar una migración colectiva, aceptar, **Yes** (1)

<img src="./media/image9.png" style="width:5.8687in;height:2.07186in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Change storage only** (2), **NEXT** (3)

<img src="./media/image10.png" style="width:6.12534in;height:3.6443in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar un storage compartido **ICM8-Datastore** (2), **NEXT** (3)

<img src="./media/image11.png" style="width:6.1576in;height:3.71116in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra el resumen, aceptar **FINISH** (1)

<img src="./media/image12.png" style="width:6.28762in;height:3.77816in"
alt="A screenshot of a computer Description automatically generated" />

Se realiza la migración, ya no están los directorios de las vCLS VMs
(2), y el datastore está en modo mantenimiento (1)

<img src="./media/image13.png" style="width:7.04776in;height:3.46998in"
alt="A screenshot of a computer Description automatically generated" />

Al revisar el datastore relacionado, ahora la vCLS VMs están en el nuevo
datastore, manteniendo la protección de HA y DRS

En la vista de **VMs & Templates** (1), click en la **vCLS VM** (2),
observar la sección de objetos relacionados (3).

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Cuando no se hace una migración ordenada vCenter Server trata de hacer
una migración a otro datastore disponible de forma automática, si no se
cuenta con esa condición falla el proceso de poner en modo mantenimiento
el datastore
