> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> ### Versión 8
>
> #### Guía de uso de laboratorio

## Laboratorio \# 10

> ### Creación de una política de vSAN
>
> Revisión 1.1 2024

## Laboratorio \# 10

> ### Creación de una política de vSAN

#### Actividades por realizar:

> 1\. Examinar la política de almacenamiento predeterminada
>
> 2\. Crear una política personalizada sin tolerancia a errores
>
> 3\. Asignar la política personalizada a una máquina virtual
>
> 4\. Hacer que la máquina virtual cumpla con la configuración
> preestablecida

## Actividad \# 1

### Examinar la política de almacenamiento predeterminada

1.- Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

### Examinar la política de almacenamiento predeterminada de vSAN.

1\. Se ha preconfigurado un almacén de datos de **vSAN**

2\. En el menú principal, seleccione **Policies and Profiles**.

3\. Verifique que esté seleccionada la opción **VM Storage Policies** en
el panel de navegación.

4\. En el panel derecho, seleccione **vSAN Default Storage Policy** y
haga click en **EDIT**.

5\. En la página **Name and description**, haga click en **NEXT**

6\. En la página **vSAN**, examine las reglas en las pestañas
**Availability, Storage Rules, Advanced Policy Rules, and Tags.**

7\. Haga click en **CANCEL**.

## Actividad \# 2

### Crear una política personalizada sin tolerancia a errores

Crea una política de almacenamiento vSAN personalizada que no
proporciona tolerancia a errores.

1\. En el panel derecho, haga click en **CREATE**.

2\. En la página **Name and description**, ingrese
**vSAN-VM-Custom-Policy-FTT0** en el cuadro de texto

**Name** y haga click en **NEXT**.

3\. En la página **Policy structure**, y en Reglas **Datastore specific
rules**, seleccione la casilla de verificación **Enable rules** para
“**vSAN storage**” y haga click en **NEXT**.

4\. En la pestaña **vSAN page Availability**, en **Failures to
tolerate**, seleccione **No data redundancy**

en el menú desplegable. Vea la información del espacio de almacenamiento
consumido debajo del menú desplegable.

5\. Para terminar la página vSAN, haga click en **NEXT**.

6\. En la página **Storage compatibility**, haga click en **NEXT**. Solo
**vsanDatastore** aparece en la lista de Almacenamiento compatible.

7\. En la página Revisar y finalizar, haga click en **FINISH**.

8\. Verifique que la política de almacenamiento
**vSAN-VM-Custom-Policy-FTT0** se haya creado y aparezca en la

lista.

Es posible que deba desplazarse por la lista de **VM Storage Policies**.

## Actividad \# 3

### Asignar la política personalizada a una máquina virtual

Crear una segunda máquina virtual y aplica tu nueva política de
almacenamiento de vSAN.

#### 1\. En el menú principal, selecciona **Inventory** y dar click en el
ícono **Hosts & clústeres**.

#### 2\. Clonar una máquina virtual desde Photon-01.

1)  En el panel de navegación, dar click con el botón derecho en
    Photon-01 y seleccionar **Clone**, click **Clone to Virtual
    Machine**.

2)  En la página **Select a name and folder**, ingresa Payload-02 en el
    cuadro de texto **Virtual machine name,** seleccionar **Lab VMS**
    como ubicación y haz click en **NEXT**.

3)  En la página **Select a compute resource**, expande SA-Datacenter y
    SA-Compute-02, seleccionar sa-esxi-05.vclass.local y dar click en
    NEXT.

4)  Es posible que se vea una advertencia de compatibilidad para el host
    ESXi. Esta advertencia se puede ignorar de forma segura.

5)  En la página **Select storage**, seleccionar **Datastore Default**
    en el menú desplegable **VM Storage Policy**.

6)  Seleccione **OPSCALE-Datastore** de la lista de datastores y haga
    click en **NEXT**.

7)  En la página **Select clone options**, seleccione solamente **Power
    on virtual machine after creation** y haga click en **NEXT**.

8)  En la página **Ready to complete**, haga click en **FINISH**.

9)  Supervise el panel Tareas recientes para verificar que la tarea
    Clonar máquina virtual se complete correctamente.

#### 3\. Verifique que su nueva máquina virtual esté incluida en el panel de
navegación y esté encendida.

Si no ve la máquina virtual incluida y encendida, haga click en el ícono
**Update**

### 4\. Asigne la política de almacenamiento _vSAN-VM-Custom-Policy-FTT0 a Payload-02_


En el panel de navegación, haga click con el botón derecho en la
VMPayload-02 y seleccione **VM Policies**, seleccionar **Edit VM Storage
Policies**..

Seleccione **vSAN-VM-Custom-Policy-FTT0** en el menú desplegable **VM
storage policy**. Haga click en **OK**.

Supervise el panel Tareas recientes para verificar que la tarea
**Reconfigure virtual machine** se complete correctamente.

5\. En el panel de navegación, seleccionar Payload-02.

6\. En la pestaña **Summary**, revise el recuadro **Related Objects** y
el recuadro **VM Storage Policies**.

Es posible que deba desplazarse hacia abajo en el panel derecho para ver
estos recuadros. Revise la configuración

## Actividad \# 4

### Hacer que la máquina virtual cumpla con la configuración preestablecida

Migre la máquina virtual Payload-02 desde el datastore **VMFS**
compartido al almacén de datos **vSAN** para

hacerla compatible con su política de almacenamiento.

### 1\. Migre la máquina virtual Payload-02 al datastore vSAN para garantizar su cumplimiento.

a\. En el panel de navegación, haga click con el botón derecho en
Payload-02 y seleccione **Migrate**.

b\. En la página **Select a migration type**, haga click en **Change
storage only** y haga click en **NEXT**.

c\. En la página **Select Storage**, deje seleccionada la opción **Keep
existing VM storage policies** en el menú desplegable **VM Storage
Policy**.

d\. En la lista de almacenes de datos, seleccione **vsanDatastore** y
haga click en **NEXT**.

Tenga en cuenta que **vsanDatastore** es el único almacén de datos que
aparece como compatible.

e\. En la página **Ready to complete**, haga click en **FINISH**.

f\. Supervise el panel Tareas recientes hasta que la tarea se complete
correctamente.

### 2\. En el panel derecho, observe el recuadro **VM Storage Policies y haga click en _Check Compliance_


Es posible que el cliente vSphere haya actualizado automáticamente el
estado de cumplimiento. Si es así,

no es necesario hacer click en **Check Compliance**.

### 3\. Verifique que el estado de cumplimiento de Payload-02 cambie a _compliant_.

### 4\. En el panel de navegación, haga click con el botón derecho en
Payload-02 y seleccione **Power**, seleccione **Power off** y haga click
en **Yes** en la ventana emergente confirmar el apagado
