> # **VMware vSphere**
>
> ## **Operación, Escalamiento y Seguridad**
>
> ### **Versión 8**
>
> #### **Guía de uso de laboratorio**

## **Laboratorio \# 9**

### **Aplicación de una política de almacenamiento**

#### **Actividades por realizar:**

> **1. Agregar datastores para que los use el almacenamiento basado en
> políticas**
>
> **2. Use vSphere Storage vMotion para migrar el almacenamiento de
> máquinas virtuales**
>
> **3. Configurar etiquetas de almacenamiento**
>
> **4. Crear Políticas de almacenamiento para máquinas virtuales**
>
> **5. Asignar políticas de almacenamiento a las máquinas virtuales**

## **Actividad \# 1**

### **Agregar almacenes de datos para que los use el almacenamiento basado en políticas**

Utilizar la liga de acceso proporcionada por su instructor

A manera de ejemplo:
[**https://vlabs.v2s.us/lab**](https://vlabs.v2s.us/lab)

<img src="./media/image1.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Utilizar el usuario y contraseña que le proporcione su instructor

A manera de ejemplo

> Usuario: `student01a`
>
> Contraseña: `Arn0224!`
>
> Click en **Login**
>
> Seleccionar en esta interfaz el primer pod de trabajo **vPodProd001a**
> (1)
>
> <img src="./media/image2.png" style="width:6.5in;height:3.65625in"
> alt="A screenshot of a computer Description automatically generated" />

Al entrar, en la siguiente interfaz proporcionar

> Usuario: `student01`
>
> Contraseña: `VMware1!`

Click en **OK**

<img src="./media/image3.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

> Se obtiene acceso al escritorio remoto
>
> <img src="./media/image4.png" style="width:6.5in;height:2.85276in"
> alt="A screenshot of a computer Description automatically generated" />

Abrir una instancia del browser Firefox con acceso directo al **vSphere
Client login interface**

User: `administrator@vsphere.local`

Password: `VMware1!`

Click en **Login**

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

2\. En el menú principal, seleccione **Inventory** y haga click en el
ícono **Storage**.

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

3\. Cree un almacén de datos denominado **ds-gold**.

1)  En el panel de navegación, haga click con el botón derecho en
    **SA-Datacenter** y seleccione **Storage**, click **New Datastore**.

> <img src="./media/image7.png" style="width:6.5in;height:3.65625in"
> alt="A screenshot of a computer Description automatically generated" />

Aparece el asistente **New datastorage**.

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Type**, deje **VMFS** seleccionado y haga clic en
**NEXT**.

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Name and device Selection**, ingrese **ds-gold** en el
cuadro de texto **Name**.

En el menú desplegable **Select a host**, seleccione ESXi host
**sa-esxi-04.vclass.local**

En la lista de LUNs, seleccione **LUN 7** con la descripción de entrada
FreeNAS ISCSI Disk (naa..) y capacidad **8.00 GB**, y haga clic en
**NEXT**.

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **VMFS version**, deje **VMFS 6** seleccionado y haga clic
en **NEXT**.

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Partition configuration**, mantenga los valores
predeterminados, click en **NEXT**.

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Ready to complete** para terminar, revise la
configuración y haga clic en **FINISH**.

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el panel de Tareas recientes, verifique que la tarea se haya
completado.

Verifique que el almacén de datos **ds-gold** aparezca en el panel de
navegación.

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Crear un datastore llamado **ds-silver**.

En el panel de navegación, haga clic con el botón derecho en
**SA-Datacenter** y seleccione **Storage**, click en **New datastore**.

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Aparece el asistente **New datastore**.

En la página **Type**, deje **VMFS** seleccionado y haga clic en
**NEXT**.

<img src="./media/image16.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a message Description automatically generated" />

En la página **Name and device selection**, ingrese **ds-silver** en el
campo **Name**.

En el menú desplegable **Select a host**, seleccione ESXi host
**sa-esxi-04.vclass.local**.

En la lista de LUNs, seleccione **LUN 8** con la descripción de entrada
FreeNAS ISCSI Disk (naa..) y capacidad **12.00 GB**, y haga clic en
**NEXT**.

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **VMFS version**, deje **VMFS 6** seleccionado y haga clic
en **NEXT**.

<img src="./media/image18.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Partition configuration**, mantenga los valores
predeterminados y haga clic en **NEXT**.

<img src="./media/image19.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Ready to complete**, revise la configuración y haga clic
en **FINISH**.

<img src="./media/image20.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el panel Tareas recientes, verifique que se haya completado la tarea.

Verifique que el almacén de datos **ds-silver** aparezca en el panel de
navegación

<img src="./media/image21.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 2**

### **Use vSphere Storage vMotion para migrar el almacenamiento de máquinas virtuales**

Utilice **vSphere Storage vMotion** para migrar la máquina virtual
**Photon-01** al almacén de datos **ds-gold**.

En el menú principal, seleccione **Inventory** y haga clic en el icono
**Hosts & clusters**

En el panel de navegación, haga clic con el botón derecho en
**Photon-01** y seleccione **Migrate**.

<img src="./media/image22.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aparece el asistente de migración.

En la página **Select a migration type**, haga clic en **Change storage
only** y haga click en **NEXT**.

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select storage**, seleccione el almacén de datos
**ds-gold**, deje todas las demás configuraciones con sus valores
predeterminados y haga clic en **NEXT**.

<img src="./media/image24.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

En la página **Ready to complete**, haga clic en **FINISH**.

<img src="./media/image25.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

En el panel Tareas recientes, supervise la tarea de migración hasta su
finalización.

Verifique que la migración se haya realizado correctamente.

En el panel de navegación, seleccione **Photon-01**.

En el panel derecho, haga clic en la pestaña **Datastores** y verifique
que el almacén de datos **ds-gold** esté en la lista.

\+

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

## **Actividad \# 3**

### **Configurar etiquetas de almacenamiento**

Se asociarán etiquetas a los diferentes tipos de almacenamiento

Del menú principal seleccionar **Tags & Custom Attibutes**

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para configurar una etiqueta y asociarla a un nivel de almacenamiento

Click en **NEW**

<img src="./media/image28.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aparece el asistente, en el campo **Name** introducir **Gold Tier**,
click en **Create New Category**

<img src="./media/image29.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a message Description automatically generated" />

Aparece una caja de diálogo en la que se muestran opciones de
configuración

En el campo **Category** **Name** escribir **Storage Tiers**, en
**Associable Object Types** click en **All objects** para deseleccionar
todos los objetos, seleccionar la opción **Datastore**, click en
**CREATE**

<img src="./media/image30.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la caja de diálogo **Create** **Tag** dar click en **CREATE**

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra etiqueta **Gold Tier** creada

<img src="./media/image32.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ahora generar otra etiqueta de almacenamiento **Silver Tag**

Click en **NEW**

<img src="./media/image33.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el campo **Name** escribir **Silver Tier,** Click en el menú
desplegabe de **Category**, seleccionar **Storage Tiers** y click en
**CREATE**.

<img src="./media/image34.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se lista la nueva etiqueta Silver Tier

<img src="./media/image35.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Asignar la etiqueta **Gold** **Tier** al datastore **ds-gold**

En la vista de almacenamiento, click derecho sobre el datastore
**ds-gold**, y seleccionar **Tags & Custom Attributes**, seleccionar
**Assign Tag**

<img src="./media/image36.png" style="width:6.5in;height:3.65625in" />

Click en el check box **Gold Tier**, click en **ASSIGN**

<img src="./media/image37.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la vista de almacenamiento, click en el datastore **ds-gold**, click
en la pestaña **Summary** y en la sección de tags ver que tiene ya
asignada la etiqueta **Gold Tier.**

<img src="./media/image38.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Asignar la etiqueta **Silver Tier** al datastore **ds-silver** datastore

En la vista de almacenamiento, click derecho sobre el datastore
**ds-silver**, y seleccionar **Tags & Custom Attributes**, seleccionar
**Assign Tag**

<img src="./media/image39.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en el check box **Gold Tier**, click en **ASSIGN**

<img src="./media/image40.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a message box Description automatically generated" />

En la vista de almacenamiento, click en el datastore **ds-silver**,
click en la pestaña **Summary** y en la sección de tags ver que tiene ya
asignada la etiqueta **Silver Tier.**

<img src="./media/image41.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 4**

### **Crear Políticas de almacenamiento para máquinas virtuales**

Creación de Políticas para asignar posteriormente a las VM sin importar
su estado de energía

Click en el **menú principal**, seleccionar **Polices and Profiles**

<img src="./media/image42.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Crear una política **Gold Tier**

Click **VM Storage Polices**, Click en **CREATE**

<img src="./media/image43.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra el asistente

En la página **Name and description** en el campo **Name** escribir
**Gold Tier Policy,** Click en **NEXT**

<img src="./media/image44.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Policy structure**, en la sección **Datastore specific
rules,** seleccionar **Enable tag** **based placement** rules, click en
**NEXT**

<img src="./media/image45.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Tag based placement** seleccionar **Storage Tiers** en el
menú desplegable **Tag Category**, click en **BROWSE TAGS**

<img src="./media/image46.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Gold Tier**, click en **OK**

<img src="./media/image47.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Click en **NEXT**

<img src="./media/image48.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Storage compatibility** verificar que aparece listado el
datastore **ds-gold,** click **NEXT**

<img src="./media/image49.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página de revisión click en **FINISH**

Aplicar los pasos similares para crear la política de almacenamiento
**Silver Tier Policy**

Verificar que en la lista de políticas aparecen ambas.

<img src="./media/image50.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 5**

### **Asignar políticas de almacenamiento a las máquinas virtuales**

La asignación de una política de almacenamiento se realiza sin importar
el estado de energía de una VM y se utiliza para asegurar el desempeño
en términos de su operación en el almacenamiento.

Seleccionar la vista de **Hosts & Clusters**

Dar click derecho en la VM **Photon-01**

Seleccionar **VM Policies**, click en **Edit VM Storage Policies**

<img src="./media/image51.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Desde el menú desplegable **VM storage policy**, seleccionar **Gold Tier
Policy**, click en **OK**

<img src="./media/image52.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Asegurarse que se asignó la política al dar click en la VM **Photon-01**
click en **Summary**, desplazarse a la sección de **Storage Policies** y
ver la asignación.

La VM cumple (**compliant**) con la política porque migramos los
archivos a este datastore

<img src="./media/image53.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aplicar la política **Silver Tier** a la VM **Photon-02**

Seleccionar la vista de **Hosts & Clusters**

Dar click derecho en la VM **Photon-02**

Seleccionar **VM Policies**, click en **Edit VM Storage Policies**

Desde el menú desplegable **VM storage policy**, seleccionar **Silver
Tier Policy**, click en **OK**

<img src="./media/image54.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Asegurarse que se asignó la política al dar click en la VM **Photon-02**
click en **Summary**, desplazarse a la sección de **Storage Policies** y
ver la asignación.

La VM no cumple (**no compliant**) con la política porque migramos los
archivos a este datastore que no está incluido en esta política.

<img src="./media/image55.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para corregir esta condición de no cumplimiento con la política migremos
la VM al datastore correcto.

Seleccionar la VM **Photon-02**, click derecho, seleccionar **Migrate**

<img src="./media/image56.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En página **Select a migration type,** click en **Change storage only**,
click en **NEXT**

<img src="./media/image57.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select Storage Silver** click en **NEXT**

<img src="./media/image58.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

En la página **Ready to Complete**. Click en **FINISH**

<img src="./media/image59.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Esperar a que se lleve a cabo la migración

Con la VM **Photon-02** seleccionada, click en **Summary**, desplazarse
a la sección de **Storage Policies** y ver que la VM cumple
(**compliant**) con la política porque migramos los archivos de la misma
al datastore correspondiente a esta política.

<img src="./media/image60.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
