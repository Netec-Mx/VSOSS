> # **VMware vSphere**
>
> ## **Operación, Escalamiento y Seguridad**
>
> ### **Versión 8**
>
> #### **Guía de uso de laboratorio**

## **Laboratorio \# 10**

> ### **Creación de una política de vSAN**

#### Actividades por realizar:

> 1\. Examinar la política de almacenamiento predeterminada
>
> 2\. Crear una política personalizada sin tolerancia a errores
>
> 3\. Asignar la política personalizada a una máquina virtual
>
> 4\. Hacer que la máquina virtual cumpla con la configuración
> preestablecida

## **Actividad \# 1**

### **Examinar la política de almacenamiento predeterminada**

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

Examinar la política de almacenamiento predeterminada de vSAN.

Se ha preconfigurado un almacén de datos de **vSAN**

En el menú principal, seleccionar **Policies and Profiles**.

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en **VM Storage Policies**

Seleccionar **vSAN Default Storage Policy** en la sección derecha, click
en **EDIT**

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En la página **Name and description**, click en **NEXT**

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **vSAN**, examinar las reglas en las pestañas
**Availability, Storage Rules, Advanced Policy Rules, and Tags.**

Identificar cuantas fallas puede tolerar

<img src="./media/image9.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Click en **CANCEL**.

## **Tarea \# 2**

### **Crear una política personalizada sin tolerancia a errores**

Crear una política de almacenamiento **vSAN** personalizada que no
proporciona tolerancia a errores.

En el panel derecho, click en **CREATE**.

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Name and description**, ingresar
**vSAN-VM-Custom-Policy-FTT0** en el cuadro de texto **Name**, click en
**NEXT**.

<img src="./media/image11.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Policy structure**, en la sección **Datastore specific
rules**, activar la opción de verificación **Enable rules for “vSAN”
storage**, click en **NEXT**.

<img src="./media/image12.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **vSAN,** en la pestaña **Availability**, en la lista
desplegable **Failures to tolerate**, seleccionar **No data
redundancy.** Observar la información del espacio de almacenamiento
consumido debajo del menú desplegable, click en **NEXT**.

<img src="./media/image13.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En la página **Storage compatibility**, click en **NEXT**.

Solo **vsanDatastore** aparece en la lista de Almacenamiento compatible.

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En la página **Review and finish**, click en **FINISH**.

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que la política de almacenamiento
**vSAN-VM-Custom-Policy-FTT0** se haya creado y aparezca en la lista.

Es posible que sea necesario desplazarse por la lista de **VM Storage
Policies**.

<img src="./media/image16.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 3**

### **Asignar la política personalizada a una máquina virtual**

Crear una máquina virtual y aplicar la nueva política de almacenamiento
de **vSAN**.

En el menú principal, seleccionar **Inventory**, click en el ícono
**Hosts & clusters**.

Clonar una máquina virtual desde **Photon-01**.

En el panel de navegación, dar click con el botón derecho en
**Photon-01** y seleccionar **Clone**, click **Clone to Virtual
Machine**.

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

En la página **Select a name and folder**, ingresar **Payload-02** en el
cuadro de texto **Virtual machine name,** seleccionar **Lab VMS** como
ubicación y dar click en **NEXT**.

<img src="./media/image18.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En la página **Select a compute resource**, expander **SA-Datacenter** y
**SA-Compute-02**

Seleccionar **sa-esxi-05.vclass.local** y dar click en **NEXT**.

Es posible que se vea una advertencia de compatibilidad para el host
ESXi. Esta advertencia se puede ignorar de forma segura.

<img src="./media/image19.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select storage**, seleccionar **Datastore Default** en el
menú desplegable **VM Storage Policy**.

Seleccionar **OPSCALE-Datastore** de la lista de datastores, click en
**NEXT**.

<img src="./media/image20.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select clone options**, seleccionar solamente **Power on
virtual machine after creation,** click en **NEXT**.

<img src="./media/image21.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a chat Description automatically generated" />

En la página **Ready to complete**, click en **FINISH**.

<img src="./media/image22.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Observar el panel de tareas recientes para verificar que la tarea Clonar
máquina virtual se complete correctamente.

Verificar que la nueva máquina virtual esté incluida en el panel de
navegación y esté encendida.

Si no ve la máquina virtual incluida y encendida, click en el ícono
**Update**

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Asignar la política de almacenamiento **vSAN-VM-Custom-Policy-FTT0** a
**Payload-02**.

En el panel de navegación, click con el botón derecho en la VM
**Payload-02** y seleccionar **VM Policies**, seleccionar **Edit VM
Storage Policies**

<img src="./media/image24.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **vSAN-VM-Custom-Policy-FTT0** en el menú desplegable **VM
storage policy**, click en **OK**.

<img src="./media/image25.png" style="width:6.19419in;height:3.5298in"
alt="A screen shot of a computer Description automatically generated" />

Supervisar el panel de tareas recientes para verificar que la tarea
**Reconfigure virtual machine** se termine correctamente.

En el panel de navegación, seleccionar **Payload-02**.

En la pestaña **Summary**, revisar el recuadro **Related Objects** y el
recuadro **VM Storage Policies**.

Es posible que sea necesario desplazarse hacia abajo en el panel derecho
para ver estos recuadros. Revisar la configuración

Notar que **VM Storage Policy Compliance** marca como **Not Applicable**

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

## **Actividad \# 4**

### **Hacer que la máquina virtual cumpla con la configuración preestablecida**

Migrar la máquina virtual **Payload-02** desde el datastore **VMFS**
compartido al almacén de datos **vSAN** para hacerla compatible con su
política de almacenamiento.

En el panel de navegación, click con el botón derecho en **Payload-02**
y seleccionar **Migrate**.

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select a migration type**, click en **Change storage
only**, click en **NEXT**.

<img src="./media/image28.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select Storage**, dejar seleccionada la opción **Keep
existing VM storage policies** en el menú desplegable **VM Storage
Policy**.

En la lista de datastores, seleccionar **vsanDatastore**, click en
**NEXT**.

Tener en cuenta que **vsanDatastore** es el único almacén de datos que
aparece como compatible.

<img src="./media/image29.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Ready to complete**, click en **FINISH**.

<img src="./media/image30.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Supervisar el panel de tareas recientes hasta que la tarea se termine
correctamente.

En el panel derecho, con la VM seleccionada, click en **Summary** y
observar el recuadro **VM Storage Policies**, click en **Check
Compliance**.

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Es posible que el cliente vSphere haya actualizado automáticamente el
estado de cumplimiento. Si es así, no es necesario hacer click en
**Check Compliance**.

Apagar la VM
