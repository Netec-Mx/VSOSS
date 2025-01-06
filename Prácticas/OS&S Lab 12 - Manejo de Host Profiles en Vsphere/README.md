> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> ### Versión 8**
>
> #### Guía de uso de laboratorio

## Laboratorio \# 12

> ### Manejo de Host Profiles en Vsphere
>
> Revisión 1.1 2024

## Laboratorio \# 12

### Manejo de Host Profiles en Vsphere

#### Actividades por realizar:

1.  Revisión de la versión de vSphere en los hosts de un cluster

2.  Actualización y homogenización de la versión de los Host ESXi

3.  Creación de un perfil de configuración homogénea de Host en el
    Cluster

4.  Desviación de la configuración de un Host

5.  Retorno a la configuración preestablecida de un host modificado.

## Actividad \# 1

### Revisión de la versión de vSphere en los hosts de un cluster

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionar el shortcut de **vCenter**

Con el propósito de poder administrar las actualizaciones de los host
ESXi se puede configurar un cluster basado en imágenes.

Observar la versión de la imagen del Host **ESXi_01**, seleccionar el
host para identificar que la versión es **ESXi 8.0.0** (1) y (2)

<img src="./media/image1.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Una buena práctica es que las imágenes de todos los hosts en un cluster
sea la misma, esto se puede realizar desde la creación misma del cluster

Enseguida se muestra el procedimiento de actualización y homogeneización
del cluster con Hosts que tienen máquinas virtuales encendidas, en donde
el cluster tiene habilitado DRS.

En resumen, se seleccionará la nueva versión a la que se actualizarán
los hosts y en cada caso para actualizar el Host, DRS moverá las VMS a
otro Host para que el host en turno se ponga en modo mantenimiento, se
actualice, se reinicie para que enseguida se puedan retornar VMS
conforme sea necesario.

## Tarea \#2

### Actualización y homogenización de la versión de los Host ESXi

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **Configure** (3), en la
sección **Desired State** click en **Configuration** (4).

Se nota que el cluster está configurado basado en configuraciones base
“baselines”

<img src="./media/image2.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En amarillo se nos indican las ventajas de la configuración basada en
perfiles de Hosts

Procedamos a actualizar las versiones de los hosts

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **Updates** (3), en la
sección **Image** (4), click en **Edit** (5).

<img src="./media/image3.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar la imagen del Host en la lista desplegable (1), click en
**ver 8.0 U3c** (3), click en **VALIDATE**, esta nueva versión se
aplicará a todos los hosts del cluster

<img src="./media/image4.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Con espera para la validación se presenta que la imagen es válida (1),
click en **SAVE** (2).

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Observar que los dos hosts no tienen esta versión 8.3 (1), importante
notar que los hosts se tendrán que reiniciar (2)

En el proceso, se tiene que dar click en **RUN PRE-CHECK** (3) en primer
término para tener información de las posibles implicaciones de la
actualización

Después, dar click en **REMEDIATE ALL** (4).

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Al dar click en **RUN PRE-CHECK** (2),

<img src="./media/image7.png"
style="width:6.50069in;height:3.65347in" />

Se muestra que no se encontraron problemas en el cluster si se desea
aplicar la actualización de imagen

<img src="./media/image8.png"
style="width:6.50069in;height:3.65347in" />

Para iniciar la homogenización de imagen, click en **REMEDIATE ALL**
(2).

<img src="./media/image9.png"
style="width:6.50069in;height:3.65347in" />

En la lista de tareas se nota el inicio del proceso (1)

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en el host **Esxi_01** (3), click en
la pestaña **VMs** (4), Observar las VMs que están encendidas en el
**Host ESXi_01** que está próximo en la actualización (5)

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se inicia la migración de la VM **Linux_01** al host **Esxi_02** (3)
esto se realiza con apoyo de **DRS**

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ahora el host **Esxi_02** tiene a las dos VMs **Linux** y una VM
**vCLS** (1)

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El host **ESXi_01** entra en mantenimiento y la VM vCLS se apaga (2)

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El host ESXi_01, se actualiza y se reinicia (1)

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se pierde conexión al host al reinicio (1)

<img src="./media/image16.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El host se reconecta (1), sale de modo de mantenimiento y se enciende la
VM vCLS (2)

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se inicia migración de las VMs (1) y (2) que están en el host
**ESXi_02** para actualizarlo

<img src="./media/image18.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ahora el host **Esxi_01** tiene las VMs (3)

<img src="./media/image19.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El host ESXi_02 entra en modo de mantenimiento (1), la VM **vCLS** se
apagó (2)

<img src="./media/image20.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se aplica la actualización, se reinicia el host, se desconecta (1)

<img src="./media/image21.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se reincorpora el host Esxi_02 (1), se enciende la VM vCLS (2)

<img src="./media/image22.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se balancea el cluster, cada host tiene una VM Linux y una VM vCLS (2)

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para revisar que un host está en cumplimiento con la versión del cluster

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **Updates** (3), Click
en **Image** (4), Click en **CHECK COMPLIANCE** (5)

<img src="./media/image24.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El host **ESXi_01** tiene la **versión 8.0.3** (1) sujeto de
actualización (2)

<img src="./media/image25.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El host **ESXi_02** tiene la **versión 8.0.3** (1) sujeto de
actualización (2)

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## Tarea \#3

### Creación de un perfil de configuración homogénea de Host en el Cluster

Para mantener a través del tiempo la configuración homogénea de los
hosts es preferible usar el recurso de perfiles de Host llamado “Host
Profiles”.

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **Configure** (3), en la
sección de **Desired State** (4) click en **Configuration** (5), click
en **CREATE CONFIGURATION** (6)

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En este paso determinaremos desde donde se toma como referencia la
configuración que deberá estar presente en todos los hosts en el cluster

Seleccionar **IMPORT FROM REFERENCE HOST**

<img src="./media/image28.png" style="width:6.51461in;height:3.56894in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar como referencia el Host **ESXi_01** (1), **IMPORT** (2)

<img src="./media/image29.png"
style="width:6.50069in;height:3.65347in" />

Se muestra que la importación de la configuración fue exitosa

<img src="./media/image30.png"
style="width:6.50069in;height:3.49375in" />

Se muestra cual es la configuración seleccionada (1), Click en **NEXT**
(2)

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se ve que la configuración es válida (5) y que todos los hosts cumplen
con una configuración homogénea (6), click en **NEXT** (7)

<img src="./media/image32.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se verifica que no hay problemas para finalizar el proceso (2), click en
**FINISH and APPLY** (3)

<img src="./media/image33.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se confirma la aplicación al click **CONTINUE** (1)

<img src="./media/image34.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se aplicado finalmente como configuración homogénea la configuración que
se tomó del Host ESXi_01, click en **VIEW CONFIGURATION**

<img src="./media/image35.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la configuración establecida en el cluster.

<img src="./media/image36.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

## Tarea \# 4

### Desviación de la configuración de un Host

Para mostrar la aplicación de la configuración de un cluster

Crear un puerto vkernel en el host **ESXi_02** para desviarlo de la
configuración homogénea e ilustrar como detectarlo y retornarlo a la
configuración original

En la vista de **Hosts & Clusters** (1), click en el **Host ESXi_02**
(2), click en la pestaña **Configure** (3), click en **Virtual
switches** (4), click en el Switch **vSwitch0** (5), Click en **ADD
NETWORKING** (6)

<img src="./media/image37.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Dejar opciones por default (1), click en **NEXT** (2)

<img src="./media/image38.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Selecionar **Select an existing standard switch** (2), seleccionar el
**vSwitch0** (3), **NEXT** (4)

<img src="./media/image39.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Dejar opciones por default (1), click en **NEXT** (2)

<img src="./media/image40.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Dejar opciones por default (1), click en **NEXT** (2)

<img src="./media/image41.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aceptar resumen **FINISH** (1)

<img src="./media/image42.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se agregó un puerto vKernel al host **ESXi_02**.

## Tarea \# 5

### Retorno a la configuración preestablecida de un host modificado.

Evaluar si hay un host que no cumple con la configuración

Click en el cluster **Production cluster** (1), click en **Configure**
(2), click **Configuration** (3), click **Compliance** (4)

<img src="./media/image43.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en **CHECK COMPLIANCE** (2), Se muestra como resultado que el host
**ESXi_2** no cumple con la configuración,

<img src="./media/image44.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para retornar el host **Esxi_02** a la configuración original, click en
**REMEDIATE** (1)

<img src="./media/image45.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestran las posibles implicaciones en un Pre-check, **NEXT** (1)

<img src="./media/image46.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en **REMEDIATE** (1)

<img src="./media/image47.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se anuncia que el retorno a la configuración fue un éxito (2) y los dos
hosts se ven en compliance

<img src="./media/image48.png" style="width:6.5in;height:3.65625in" />

Si retorna a revisar el **vSwitch0** este ya no tendrá el puerto
**vKernel** creado.
