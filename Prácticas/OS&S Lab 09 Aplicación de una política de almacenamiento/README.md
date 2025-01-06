> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> ### Versión 8
>
> #### Guía de uso de laboratorio

## Laboratorio \# 9

> ### Aplicación de una política de almacenamiento
>
> Revisión 1.1 2024

## Laboratorio \# 9

> ### Aplicación de una política de almacenamiento

#### Actividades por realizar:

> 1\. Agregar almacenes de datos para que los use el almacenamiento
> basado en políticas
>
> 2\. Use vSphere Storage vMotion para migrar el almacenamiento de
> máquinas virtuales

## Actividad \# 1

**Agregar almacenes de datos para que los use el almacenamiento basado
en políticas**

### 1.- Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: VMware1!`

### 2\. En el menú principal, seleccione **Inventory** y haga click en el
ícono **Storage**.

### 3\. Cree un almacén de datos denominado ds-gold.

1)  En el panel de navegación, haga click con el botón derecho en
    **SA-Datacenter** y seleccione **Storage**, click **New Datastore**.
    Aparece el asistente **New datastorage**.

2)  En la página **Type**, deje **VMFS** seleccionado y haga clic en
    **NEXT**.

3)  En la página **Name and device Selection**, ingrese **ds-gold** en
    el cuadro de texto **Name**.

4)  En el menú desplegable **Select a host**, seleccione ESXi host
    **sa-esxi-04.vclass.local**

5)  En la lista LUN, seleccione LUN 7 con la descripción de entrada
    FreeNAS ISCSI Disk (naa..) y capacidad 8.00 GB, y haga clic en
    **NEXT**.

6)  Las unidades locales están etiquetadas como **VMware local Disk**.
    No seleccione estas unidades.

7)  En la página **VMFS version**, deje **VMFS 6** seleccionado y haga
    clic en **NEXT**.

8)  En la página **Partition configuration**, mantenga los valores
    predeterminados y haga clic en **NEXT**.

9)  En la página **Ready to complete** para terminar, revise la
    configuración y haga clic en **NEXT**.

En el panel de Tareas recientes, verifique que la tarea se haya
completado.

Verifique que el almacén de datos **ds-gold** aparezca en el panel de
navegación.

### 4\. Cree un datastore llamado **ds-silver**.

1)  En el panel de navegación, haga clic con el botón derecho en
    SA-Datacenter y seleccione **Storage**, click en **New datastore**.
    Aparece el asistente **New datastore**.

2)  En la página **Type**, deje **VMFS** seleccionado y haga clic en
    **NEXT**.

3)  En la página **Name and device selection**, ingrese **ds-silver** en
    el campo **Name**.

4)  En el menú desplegable **Select a host**, seleccione ESXi host
    sa-esxi-04.vclass.local.

5)  En la lista LUN, seleccione LUN 8 con la descripción de entrada
    FreeNAS ISCSI Disk (naa..) y capacidad 12.00 GB, y haga clic en
    **NEXT**.

6)  Las unidades locales están etiquetadas como **local VMware Disk**.
    No seleccione estas unidades.

7)  En la página **VMFS version**, deje **VMFS 6** seleccionado y haga
    clic en **NEXT**.

8)  En la página **Partition configuration**, mantenga los valores
    predeterminados y haga clic en **NEXT**.

9)  En la página **Ready to complete**, revise la configuración y haga
    clic en **FINISH**.

10) En el panel Tareas recientes, verifique que se haya completado la
    tarea.

11) Verifique que el almacén de datos **ds-silver** aparezca en el panel
    de navegación

## Actividad \# 2

### Use vSphere Storage vMotion para migrar el almacenamiento de máquinas virtuales

Utilice **vSphere Storage vMotion** para migrar la máquina virtual
Photon-01 al almacén de datos **ds-gold**.

1\. En el menú principal, seleccione **Inventory** y haga clic en el
icono **Hosts & clústeres**

2\. En el panel de navegación, haga clic con el botón derecho en
Photon-01 y seleccione **Migrate**.

Aparece el asistente de migración.

3\. En la página **Select a migration type**, haga clic en **Change
storage only** y haga click en **NEXT**.

4\. En la página **Select storage**, seleccione el almacén de datos
**ds-gold**, deje todas las demás configuraciones con sus valores
predeterminados y haga clic en **NEXT**.

5\. En la página **Ready to complete**, haga clic en **NEXT**.

6\. En el panel Tareas recientes, supervise la tarea de migración hasta
su finalización.

7\. Verifique que la migración se haya realizado correctamente.

Es posible que deba actualizar vSphere Client para ver que la migración
se haya completado.

a\. En el panel de navegación, seleccione Photon-01.

b\. En el panel derecho, haga clic en la pestaña **Datastores** y
verifique que el almacén de datos **y** **Ready to complete** esté en la
lista.
