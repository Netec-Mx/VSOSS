# Práctica 9. Aplicación de una política de almacenamiento

## Objetivos de la práctica:

- Agregar datastores para que los use el almacenamiento basado en políticas.
- Usar vSphere Storage vMotion para migrar el almacenamiento de máquinas virtuales.
- Configurar etiquetas de almacenamiento.
- Crear políticas de almacenamiento para máquinas virtuales.
- Asignar políticas de almacenamiento a las máquinas virtuales.

## Duración aproximada:
- 30 minutos.

## Instrucciones

## **Actividad \# 1**

### **Agregar almacenes de datos para que los use el almacenamiento basado en políticas**

Utilizar la liga de acceso proporcionada por su instructor.

A manera de ejemplo:
[**https://vlabs.v2s.us/lab**](https://vlabs.v2s.us/lab)

<img src="./media/image1.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Utilizar el usuario y contraseña que le proporcione su instructor.

A manera de ejemplo:

> Usuario: `student01a`
>
> Contraseña: `Arn0224!`
>
> Dar clic en **Login**.
>
Seleccionar en esta interfaz el primer pod de trabajo **vPodProd001a** (1).
>
> <img src="./media/image2.png" style="width:6.5in;height:3.65625in"
> alt="A screenshot of a computer Description automatically generated" />

Al entrar, en la siguiente interfaz proporcionar:

> Usuario: `student01`
>
> Contraseña: `VMware1!`

Dar clic en **OK**.

<img src="./media/image3.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

> Se obtiene acceso al escritorio remoto.
>
> <img src="./media/image4.png" style="width:6.5in;height:2.85276in"
> alt="A screenshot of a computer Description automatically generated" />

Abrir una instancia del browser Firefox con acceso directo al **vSphere
Client login interface.**

User: `administrator@vsphere.local`

Password: `VMware1!`

Dar click en **Login**.

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el menú principal, seleccionar **Inventory**, dar clic en la vista de
**DataStorages**.

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Crear un almacén de datos denominado **ds-gold**.

En el panel de navegación, dar clic con el botón derecho en
**SA-Datacenter** (2) y seleccionar **Storage** (3), escoger **New Datastore** (4).

> <img src="./media/image7.png" style="width:6.5in;height:3.65625in"
> alt="A screenshot of a computer Description automatically generated" />

Aparece el asistente **New Datastorage**.

<img src="./media/image8.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Type** (1), dejar **VMFS** seleccionado (2) y hacer clic en
**NEXT** (3).

<img src="./media/image9.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Name and device Selection** (1), ingresar **ds-gold** en el
cuadro de texto **Name** (2).

En el menú desplegable **Select a host**, seleccionar ESXi host
**sa-esxi-04.vclass.local** (3).

En la lista de LUNs, seleccionar **LUN 7** con la descripción de entrada
FreeNAS ISCSI Disk (naa..) y capacidad **8.00 GB** (4). **NEXT** (5).

<img src="./media/image10.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **VMFS version** (1), dejar **VMFS 6** seleccionado (2). **NEXT** (3).

<img src="./media/image11.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Partition configuration**, mantener los valores
predeterminados (1). **NEXT** (2).

<img src="./media/image12.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Ready to complete,** para terminar, revisar la
configuración. **FINISH** (1).

<img src="./media/image13.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En el panel de tareas recientes, verificar que la tarea se haya
terminado.

Verificar que el almacén de datos **ds-gold** aparezca en el panel de
navegación (1).

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Crear un datastore llamado **ds-silver**.

En el panel de navegación (1), dar clic con el botón derecho en
**SA-Datacenter** (2) y seleccionar **Storage** (3), escoger **New datastore** (4).

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Aparece el asistente **New datastore**.

En la página **Type** (1), dejar **VMFS** seleccionado (2). **NEXT** (3).

<img src="./media/image16.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a message Description automatically generated" />

En la página **Name and device selection** (1), ingresar **ds-silver** en el
campo **Name** (2).

En el menú desplegable **Select a host**, seleccionar ESXi host
**sa-esxi-04.vclass.local** (3).

En la lista de LUNs, seleccionar **LUN 8** con la descripción de entrada
FreeNAS ISCSI Disk (naa..) y capacidad **12.00 GB** (4). **NEXT** (5).

<img src="./media/image17.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **VMFS version** (1), dejar **VMFS 6** seleccionado (2). **NEXT** (3).

<img src="./media/image18.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Partition configuration** (1), mantener los valores
predeterminados. **NEXT** (2).

<img src="./media/image19.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Ready to complete** (1), revisar la configuración. **FINISH** (2).

<img src="./media/image20.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En el panel de tareas recientes, verificar que se haya terminado la tarea.

Verificar que el almacén de datos **ds-silver** aparezca en el panel de
navegación.

<img src="./media/image21.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 2**

### **Usar vSphere Storage vMotion para migrar el almacenamiento de máquinas virtuales**

Utilizar **vSphere Storage vMotion** para migrar la máquina virtual
**Photon-01** al almacén de datos **ds-gold**.

En el menú principal, seleccionar **Inventory** y hacer clic en el icono
**Hosts & clusters** (1).

En el panel de navegación, hacer clic con el botón derecho en
**Photon-01** (2) y seleccionar **Migrate** (3).

<img src="./media/image22.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aparece el asistente de migración.

En la página **Select a migration type** (1), escoger **Change storage
only** (2). **NEXT** (3).

<img src="./media/image23.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select storage** (1), seleccionar el almacén de datos
**ds-gold** (2) y dejar las demás configuraciones con sus valores
predeterminados, estos elementos de configuración son:

- **Select virtual disk format:** **Same as source**, para conservar la configuración de discos pesados o ligeros.
- También, mantendrá la política de almacenamiento asignada.
- Sin utilizar la migración de discos con **storage DRS**.

**NEXT** (3).

<img src="./media/image24.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer Description automatically generated" />

En la página **Ready to complete** (1). **FINISH** (2).

<img src="./media/image25.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer Description automatically generated" />

En el panel de tareas recientes, supervisar la tarea de migración hasta su
término.

Verificar que la migración se haya realizado correctamente.

En el panel de navegación, seleccionar **Photon-01** (1).

En el panel derecho, dar clic en la pestaña **Datastores** (2) para verificar que
el almacén de datos **ds-gold** esté en la lista (3).

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

## **Actividad \# 3**

### **Configurar etiquetas de almacenamiento**

Se asociarán etiquetas a los diferentes tipos de almacenamiento.

Del menú principal, seleccionar **Tags & Custom Attibutes** (2).

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para configurar una etiqueta y asociarla a un nivel de almacenamiento

Hacer clic en **NEW** (1).

<img src="./media/image28.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aparece el asistente. En el campo **Name** introducir **Gold Tier** (1),
seleccionar **Create New Category** (2).

<img src="./media/image29.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a message Description automatically generated" />

Aparece una caja de diálogo en la que se muestran opciones de
configuración.

En el campo **Category** **Name** escribir **Storage Tiers** (1), en
**Associable Object Types**, seleccionar **All objects** para deseleccionar
todos los objetos (2). Seleccionar la opción **Datastore** (3). **CREATE** (4).

<img src="./media/image30.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la caja de diálogo **Create** **Tag** dar clic en **CREATE** (1).

<img src="./media/image31.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la etiqueta **Gold Tier** creada.

<img src="./media/image32.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Generar otra etiqueta de almacenamiento **Silver Tag**.

Hacer clic en **NEW** (1).

<img src="./media/image33.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el campo **Name** escribir **Silver Tier** (1). Hacer clic en el menú
desplegabe de **Category** y seleccionar **Storage Tiers** (2). **CREATE** (3).

<img src="./media/image34.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Se lista la nueva etiqueta **Silver Tier.**

<img src="./media/image35.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Asignar la etiqueta **Gold Tier** al datastore **ds-gold.**

En la vista de almacenamiento, dar clic derecho sobre el datastore
**ds-gold** (2) y seleccionar **Tags & Custom Attributes** (3), escoger
**Assign Tag** (4).

<img src="./media/image36.png" style="width:6.5in;height:3.65625in" />

Seleccionar **Gold Tier** en el check box (1). **ASSIGN** (2).

<img src="./media/image37.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

En la vista de almacenamiento, seleccionar el datastore **ds-gold** (1). Dirigirse a la pestaña **Summary** (2) y en la sección de tags (3) ver que tiene ya asignada la etiqueta **Gold Tier** (4).

<img src="./media/image38.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Asignar la etiqueta **Silver Tier** al datastore **ds-silver**

En la vista de almacenamiento (1), dar clic derecho sobre el datastore
**ds-silver** (2), escoger **Tags & Custom Attributes** (3) y seleccionar
**Assign Tag** (4).

<img src="./media/image39.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Gold Tier** en el check box (1). **ASSIGN** (2).

<img src="./media/image40.png" style="width:4.48698in;height:3.39823in"
alt="A computer screen with a message box Description automatically generated" />

En la vista de almacenamiento, escoger el datastore **ds-silver** (1).
Dirigirse a la pestaña **Summary** (2) y en la sección de tags (3) ver que tiene ya asignada la etiqueta **Silver Tier** (4).

<img src="./media/image41.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 4**

### **Crear políticas de almacenamiento para máquinas virtuales**

Crear políticas para asignarlas posteriormente a las VMs sin importar su
estado de energía.

Hacer clic en el **menú principal** (1) y seleccionar **Polices and Profiles** (2).

<img src="./media/image42.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Crear una política **Gold Tier**.

Seleccionar **VM Storage Polices** (1) y hacer clic en **CREATE** (2).

<img src="./media/image43.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra el asistente.

En la página **Name and description** (1) escribir en el campo **Name** 
**Gold Tier Policy** (2). **NEXT** (3).

<img src="./media/image44.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Policy structure** (1), en la sección **Datastore specific
rules** (2), seleccionar **Enable tag** **based placement** rules (3).
**NEXT** (4).

<img src="./media/image45.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Tag based placement** (1), en el menú desplegable de **Tag Category**, seleccionar **Storage Tiers** (2). **BROWSE TAGS** (3).

<img src="./media/image46.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Gold Tier** (1). **OK** (2).

<img src="./media/image47.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer Description automatically generated" />

**NEXT** (1).

<img src="./media/image48.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Storage compatibility** (1) verificar que aparece listado el
datastore **ds-gold** (2). **NEXT** (3).

<img src="./media/image49.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página de revisión dar clic en **FINISH**.

Aplicar los pasos similares para crear la política de almacenamiento
**Silver Tier Policy**

Verificar que en la lista de políticas aparecen ambas políticas.

<img src="./media/image50.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 5**

### **Asignar políticas de almacenamiento a las máquinas virtuales**

La asignación de una política de almacenamiento se realiza sin importar
el estado de energía de una VM y se utiliza para asegurar el desempeño
en términos de su operación en el almacenamiento.

Seleccionar la vista de **Hosts & Clusters** (1). Dar clic derecho en la VM **Photon-01** (2) y seleccionar **VM Policies** (3). Elegir **Edit VM Storage Policies.**

<img src="./media/image51.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Desde el menú desplegable **VM storage policy** (1), seleccionar **Gold Tier
Policy** (2). **OK** (3).

<img src="./media/image52.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Asegurarse que se asignó la política al dar click en la VM **Photon-01** (1).
Dirigirse a la pestaña **Summary** (2), desplazarse a la sección de **Storage Policies** (3) y ver la asignación.

La VM cumple (**compliant**) con la política porque migramos los
archivos a este datastore (5).

<img src="./media/image53.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aplicar la política **Silver Tier** a la VM **Photon-02.**

Seleccionar la vista de **Hosts & Clusters.**

Dar click derecho en la VM **Photon-02.**

Seleccionar **VM Policies**, dar clic en **Edit VM Storage Policies.**

Desde el menú desplegable **VM storage policy** (1), seleccionar **Silver
Tier Policy** (2). **OK** (3).

<img src="./media/image54.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Asegurarse que se asignó la política al dar clic en la VM
**Photon-02** (1). Dirigirse a la pestaña de **Summary** (2), desplazarse a la sección de **Storage Policies** (3) y ver la asignación.

La VM no cumple (**no compliant**) con la política (5), porque migramos los
archivos a este datastore que no está incluido en esta política.

<img src="./media/image55.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para corregir esta condición de no cumplimiento con la política migremos
la VM al datastore correcto.

Seleccionar la VM **Photon-02** (2), dar clic derecho, seleccionar **Migrate** (3).

<img src="./media/image56.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select a migration type** (1), dar clic en **Change storage only** (2). **NEXT** (3).

<img src="./media/image57.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select Storage Silver** click en **NEXT**

<img src="./media/image58.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer Description automatically generated" />

En la página **Ready to Complete**. **FINISH**.

<img src="./media/image59.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Esperar a que se lleve a cabo la migración.

Con la VM **Photon-02** seleccionada (2), dirigirse a la pestaña **Summary** (2), desplazarse a la sección de **Storage Policies** (3) y ver que la VM cumple
(**compliant**) con la política porque migramos los archivos de la misma
al datastore correspondiente a esta política (5).

<img src="./media/image60.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
