> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> ### Versión 8
>
> **Guía de uso de laboratorio**

## Laboratorio \# 3

### Administración de pools de recursos

> Revisión 1.1 2024

### Administración de pools de recursos

#### Actividades a realizar:

1.  Revisar el inventario actual

2.  Revisar desempeño de VMs sin condiciones de contención

3.  Creación de condiciones de contención

4.  Revisar desempeño de VMs con condiciones de contención

5.  Creación de pools de recursos

6.  Revisar el desempeño utilizando pools de recursos

## Actividad \# 1

### Revisar el inventario actual

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionando el acceso rápido de
**vCenter Server**.

Considerar el inventario actual

Un vCenter Server (**sa-vcsa-01.vclass.local**), un Datacenter
(**Production Datacenter**), un cluster (**Production Clusters**)

<img src="./media/image1.png" style="width:6.5in;height:3.52083in"
alt="A screenshot of a computer Description automatically generated" />

En el host **ESXi_01** se tienen las VMs encendidas **Linux_01** y
**Linux_02** (1)

<img src="./media/image2.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el host **ESXi_02** se tienen las VMs encendidas **Linux_03** y
**Linux_04** (1)

<img src="./media/image3.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Observar la configuración de los vCPUs de una VM encendida, click en la
VM **Linux_01**, en el menú contextual seleccionar **Edit Settings** (2)

<img src="./media/image4.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Al expander el campo de **vCPU** se tienen los siguientes campos
disponibles

<img src="./media/image5.png" style="width:3.16132in;height:2.75561in"
alt="A screenshot of a computer Description automatically generated" />

Si se apaga la VM entonces se tendrá acceso al campo **Scheduling**
**Affinity** (1)

<img src="./media/image6.png" style="width:2.89583in;height:2.6875in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 2

### Revisar desempeño de VMs sin condiciones de contención

Observar la capacidad de cómputo de las VMs con la configuración actual;
para esto accesar la consola de cada una de las VMs y ejecutar una
aplicación para medir el desempeño, a manera de ejemplo, click en la
**VM Linux_01** (1), en la pestaña **Summary** click en **LAUNCH WEB
CONSOLE** (2)

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Accesar con el password `VMware1!`

<img src="./media/image8.png" style="width:6.5in;height:3.52083in"
alt="A screenshot of a computer Description automatically generated" />

Click en el botón de aplicaciones (1)

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en la aplicación **Terminal** (1)

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la aplicación Terminal emitir los siguientes comandos

`CD Desktop`

`chmod +x cpubusy.pl`

`perl ./cpubusy.pl`

Entonces se lanza una aplicación que realizar cálculos matemáticos; la
medida del desempeño es el tiempo en segundo que le toma hacer un ciclo
de cálculos

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Esperar algunos minutos para que se estabilice el cálculo, con las 4 VMs
encendidas el promedio que se observa es similar al que muestra la VM
**Linux_01**

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 3

### Creación de condiciones de contención

Establecer una primera condición de contención al reunir todas las VMs
en un solo host **ESXi_01**.

En la vista **Hosts & Clusters** (1), seleccionar el cluster
**Production Cluster (**2), seleccionar el host **Esxi_02** (3), click
en la pestaña **VMs** (4), seleccionar las **VMs Linux_03**,
**Linux_04**, en el menú contextual seleccionar **Migrate** (6)

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el paso **Select a Migration type** (1), seleccionar **Change compute
resource only** (2), click **NEXT** (3).

<img src="./media/image14.png" style="width:4.21966in;height:2.31786in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el host destino **ESXi_01** (3), **Next** (4)

<img src="./media/image15.png" style="width:4.2562in;height:2.33418in"
alt="A screenshot of a computer Description automatically generated" />

Establecer la red **dpg-SA-Production** (2), **NEXT** (3)

<img src="./media/image16.png" style="width:4.24993in;height:2.31322in"
alt="A screenshot of a computer Description automatically generated" />

En el paso **Select vMotion Priority** (1), seleccionar **Schedule
vMotion with High priority** (2), **NEXT** (3).

<img src="./media/image17.png" style="width:4.24924in;height:2.33854in"
alt="A screenshot of a computer Description automatically generated" />

Al seleccionar el host **ESXi_01**, se podrá observar todas las VMs
concentradas.

El recurso de CPU ahora se comparte con 4 VMs.

<img src="./media/image18.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Proceder a observar las consolas de las VMs se nota un aumento en el
número de segundos para terminar un ciclo en todas las VMs.

VMs **Linux_01, Linux_02:**

<img src="./media/image19.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

VMs **Linux_03, Linux_04:**

<img src="./media/image20.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Un segundo mecanismo de contención es asignar afinidad

Apagar las 4 VMs, en la vista de **Hosts & Clusters** (1), seleccionar
el cluster **Production Cluster** (2), click en la pestaña **VMs** (3),
seleccione las 4 VMs (4), en el menú contextual seleccionar **Power**
(5), **Shutdown Guest OS** (6)

<img src="./media/image21.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Confirmar el apagado múltiple **YES** (1)

<img src="./media/image22.png" style="width:4.91814in;height:2.12826in"
alt="A screenshot of a computer Description automatically generated" />

En cada una de las 4 VMs establecer afinidad de CPU con el CPU físico 0,
a manera de ejemplo

En la vista de **Hosts & Clusters**, seleccionar el cluster **Production
Cluster**, click en **Linux_01** (3), en el menú contextual click en
**Edit Settings** (4).

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la pestaña **Virtual Hardware** (1), expander la sección **vCPU**
(2), escribir **0** en el campo **Scheduling Affinity** (4), **OK** (5).

<img src="./media/image24.png" style="width:3.15263in;height:2.76656in"
alt="A screenshot of a computer Description automatically generated" />

Repetir la misma operación en las 4 VMs.

Encender todas las VMS.

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **VMs** (3), seleccionar
todas las VMs (4), en el menú contextual seleccionar **Power** (5),
click en **Power On** (6)

<img src="./media/image25.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 4

### Revisar desempeño de VMs con condiciones de contención

Encender todas las VMs

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **VMs** (3), seleccionar
todas las VMs (4), en el menú contextual seleccionar **Power** (5),
click en **Power On** (6)

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Accesar de nuevo a las consolas de las VMs y ejecutar los comandos en la
aplicación Terminal

`CD Desktop`

`chmod +x cpubusy.pl`

`perl ./cpubusy.pl`

Después de minutos de espera observar las consolas de las VMS, se nota
un incremento proporcional del tiempo requerido para cada ciclo similar
en cada una de las 4 VM

Las VMS están en un solo Host utilizando ahora un sólo CPU físico

VMs **Linux_01** y **Linux_02**:

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

VMS **Linux_03** y **Linux_04**:

<img src="./media/image28.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 5

### Creación de pools de recursos

Con el propósito de ver la aplicación de los pools de recursos

Activar DRS en el Cluster, esto es totalmente necesario para incluir un
pool de recursos en el cluster.

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **Configure** (3), en la
sección de Servicios seleccionar **vSphere DRS** (4), click en **EDIT**
(5)

<img src="./media/image29.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Observar que al activar el servicio (1), tenemos varias opciones de
operación **Manual** , **Partially Automated** y **Fully Automated**.
(2)

Seleccionar **Manual** (2), **OK** (3)

<img src="./media/image30.png" style="width:3.1821in;height:2.65696in"
alt="A screenshot of a computer Description automatically generated" />

Se crearán dos pools, uno con alta prioridad de asignación de recursos y
otro con baja prioridad de recursos para incluir VMs en cada uno de
ellos y observar los resultados

Creación de pool con **alta prioridad** de asignación de recursos

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), en el menú contextual seleccionar **New
Resource Pool** (3)

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Al ingresar a la definición de pools en vCPUs y Memoria podrá observar
los campos siguientes, en **Shares** se tienen las opciones **Low**,
**Normal**, **High** (1) y **Custom** (2)

<img src="./media/image32.png" style="width:3.16667in;height:2.41146in"
alt="A screenshot of a computer Description automatically generated" />

Para este primer pool establecer las opciones **Name**
**Production_High_Priority** (1), CPU **Shares**, **Custom 1000000**
(2), **Reservation 1000** (3) y activar **Expandable** (4), **OK** (5)

<img src="./media/image33.png" style="width:3.15103in;height:2.37005in"
alt="A screenshot of a computer Description automatically generated" />

Se incluye en el inventario del cluster el Pool, observar los parámetros
establecidos

<img src="./media/image34.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Crear un segundo pool, en la vista de **Hosts & Clusters** (1), click en
el cluster **Production Cluster** (2), en el menú contextual seleccionar
**New Resource Pool** (3)

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Llenar la caja de diálogo del Pool

Para este primer pool establecer las opciones **Name**
**Production_Low_Priority** (1), CPU **Shares**, **Custom 100** (2),
**Reservation 0** y desactivar **Expandable** (3), **OK** (4)

<img src="./media/image35.png" style="width:3.16655in;height:2.40642in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra en el inventario el segundo Pool, observar los parámetros
establecidos

<img src="./media/image36.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Enseguida arrastrar en el inventario las VMs **Linux_01** y **Linux_02**
sobre en el pool de **alta prioridad**. (1)

Arrastrar en el inventario a las VMs **Linux_03** **y Linux_04** sobre
el pool de **baja prioridad** (2), el resultado se muestra enseguida

<img src="./media/image37.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 6

### Revisar el desempeño utilizando pools de recursos

Para que tengan efecto los parámetros reiniciar las VMS, accesar a sus
consolas, y emitir los comandos

`CD Desktop`

`chmod +x cpubusy.pl`

`perl ./cpubusy.pl`

Después de varios minutos observar el desempeño de las VMs

Se puede observar **alto desempeño** en las VMs **Linux_01** y
**Linux_02**

<img src="./media/image38.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se puede observar **bajo desempeño** en las VMs **Linux_03** y
**Linux_04**

<img src="./media/image39.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Los resultados anteriores es el resultado de la utilización de pools de
recursos.

Restaurar las VMs a una operación normal,

Apagar las VMs

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **VMs** (3), seleccionar
todas las VMs (4), en el menú contextual seleccionar **Power**, click en
**Shut Down Guest OS** (5)

<img src="./media/image40.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aceptar la operación múltiple (**yes**)

<img src="./media/image41.png" style="width:6.5in;height:3.52083in"
alt="A screenshot of a computer Description automatically generated" />

Eliminar en sus especificaciones la afinidad de cpu

En la vista de **Hosts & Clusters** (1), click en la VM **Linux_01**
(2), en el menú contextual seleccionar **Edit Settings** (3)

<img src="./media/image42.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Eliminar afinidad de CPU, en el campo de **Scheduling Affinity** borrar
**0** (2), **OK** (3)

<img src="./media/image43.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Repetir la operación para las VMs **Linux_02**, **Linux_03** y
**Linux_04**

Poner RDS en operación totalmente automática,

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **Configure** (3), Click
en **vSphere RDS** (4), click en **EDIT** (6)

<img src="./media/image44.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Configurar **Automatic level** en **Fully Automated** (2).

<img src="./media/image45.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
