> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> ### Versión 8
>
> ### Guía de uso de laboratorio

## Laboratorio \# 15

> ### Manejo de Alarmas
>
> Revisión 1.1 2024

## Laboratorio \# 15

> ### Manejo de Alarmas

#### Actividades por realizar:

1.  Establecer una alarma para monitorear una condición

2.  Disparar la alarma de condición

3.  Establecer una alarma para monitorear un evento

4.  Disparar la alarma de evento

5.  Desactivar las alarmas

## Actividad \# 1

### Establecer una alarma para monitorear una condición

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña:  `VMware1!`

Abrir una instancia de Firefox, seleccionar el shortcut de **vCenter**

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), en el menú
contextual seleccionar **Alarms** (4), **New Alarm** **Definition**(5)

<img src="./media/image1.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega el asistente de alarmas

En el campo **Alarm Name** establecer **Linux_01_CPU_High_Usage** (2),
**NEXT** (3)

<img src="./media/image2.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar del menú desplegable **IF** (2), **VM CPU USAGE** (3)

<img src="./media/image3.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Establecer las siguientes condiciones:

**Métrica : VM CPU Usage (2),**

**Operador: Is above (3)**

**Umbral: 35% (4)**

**Tiempo: 30 Sec (5)**

**Acción: Show as Warning (6)**

Click en **NEXT** (7)

<img src="./media/image4.png" style="width:6.5in;height:3.65625in" />

En el paso **Reset Rule** (1), observar la regla presente y avanzar
**NEXT** (2) la misma establece que la regla de establecer la alarma en
un estado de normal es que la condición ya no se cumpla.

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra el resumen de la alarma, aceptarla **CREATE** (1)

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Si se desea administrar las alarmas, y en este caso verificar la
existencia de la alarma recién creada

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), Click en la
pestaña Configure (4), en la sección de **Settings** seleccionar **Alarm
definitions** (5), click en la alarma **Linux_01_CPU_High_Usage** (6)

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Encender la VM **Linux_01**

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Observar que la VM no tiene alta utilización de cpu en la gráfica de
desempeño

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), Click en la
pestaña **Monitor** (4), en la sección de **Performance** click en
**Advanced**, ver que la gráfica se muestra en tiempo real **Real-Time**
(6), verificar que la gráfica se refiere a **CPU usage in %** (7)

El uso de cpu está alrededor de 10% (8)

<img src="./media/image9.png" style="width:6.5in;height:3.65625in" />

## Actividad \# 2

### Disparar la alarma de condición

Con la VM Linux_01 seleccionada, en la pestaña de **Summary** dar click
**LAUNCH WEB CONSOLE**

Usar el password `VMware 1!`

<img src="./media/image10.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Click en el ícono de **Apps** (1)

<img src="./media/image11.png" style="width:6.5in;height:3.65625in" />

Lanzar la aplicación Terminal para emitir comandos en línea

<img src="./media/image12.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Emitir los siguientes comandos:

`ls`

`cd Desktop`

`Chmod +x cpubusy.pl`

`perl ./cpubusy.pl`

Se ejecuta una aplicación que realiza “N” operaciones matemáticas por
segundos.

Observar la estadística después de varios minutos al estabilizarse.

<img src="./media/image13.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se dispara la alarma, observar con la VM **Linux_01** seleccionada en la
pestaña de resumen (5)

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Observar la gráfica avanzada de desempeño

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), Click en la
pestaña **Monitor** (4), en la sección de **Performance** click en
**Advanced**, ver que la gráfica se muestra en tiempo real **Real-Time**
(6), verificar que la gráfica se refiere a **CPU usage in %
aproximadamente de 60** **%** (7)

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la sección de Alarmas disparadas podemos ver también la alarma
listada

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), Click en la
pestaña **Monitor** (4), en la sección de **Issues and Alarms** (4)
click en **Triggered Alams** (5), ver que se lista la alarma (6)

<img src="./media/image16.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la lista de eventos también está listado el disparo de la alarma

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), Click en la
pestaña **Monitor** (4), en la sección de **Tasks and Events** (4) click
en **Events** (5), ver que se lista la alarma (6)

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Una opción para apagar la alarma es

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), Click en la
pestaña **Monitor** (4), en la sección de **Issues and Alarms** (4)
click en **Triggered Alams** (5), Seleccionar la alarma y dar click en
**RESET TO GREEN** (6)

<img src="./media/image18.png" style="width:6.5in;height:3.65625in" />

Alternativamente se puede

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), Click en la
pestaña **Summary** (4), en click en Actions (4) click en **RESET TO
GREEN** (5)

<img src="./media/image19.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Apagar en la VM la aplicación de cpubusy

<img src="./media/image20.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), Click en la
pestaña **Monitor** (4), en la sección de **Performance** click en
**Advanced**, ver que la gráfica se muestra en tiempo real **Real-Time**
(6), verificar que la gráfica se refiere a **CPU usage in %
aproximadamente de 10%** (7)

<img src="./media/image21.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 3

### Establecer una alarma para monitorear un evento

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la VM **Linux_01** (3), Click en la
pestaña Configure (4), en la sección de **Settings** seleccionar **Alarm
definitions** (5), click **ADD** (6)

<img src="./media/image22.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Establecer en el campo **Alarm Name**: **VM_Suspended** (2), dejar en
**Target Type** Virtual Machine (3), **NEXT** (3)

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la lista desplegable de **IF,** en la sección de **Power and**
**Connection State** (1)

<img src="./media/image24.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **VM suspended** (2)

<img src="./media/image25.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Especificar que cuando se dispare la alarma se muestre una advertencia
(3), **NEXT** (4)

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Especificar que la alarma se anule (2) cuando la VM se reinicie (2),
**NEXT** (4)

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aceptar el resumen de la configuración de la alarma (1), **CREATE** (2)

<img src="./media/image28.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 4

### Disparar la alarma de evento

Procedamos a suspender la **VM Linux_01**

En la vista de **Hosts & Clusters** (1), click en la **VM Linux_01**
(2), en el menú contextual seleccionar **POWER** (3), Click **Suspend**
(4)

<img src="./media/image29.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la advertencia de que se suspenderá la VM, Click **YES** (1)

<img src="./media/image30.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se dispara inmediatamente la alarma

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Iniciemos la VM para que se anule la alarma

En la vista de **Hosts & Clusters** (1), click en la **VM Linux_01**
(2), en el menú contextual seleccionar **POWER** (3), Click **Power On**
(4)

<img src="./media/image32.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

La alarma desaparece

<img src="./media/image33.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 5

### Desactivar las alarmas

En la vista de **Hosts & Clusters** (1), click en la **VM Linux_01**
(2), click en la pestaña **Configure**(3), click en **Alarm
Definitions** (4), en la alarma a eliminar(5), click **DELETE** (6)

<img src="./media/image34.png" style="width:6.5in;height:3.65625in" />

Se muestra la advertencia de eliminación, click **OK** (1)

<img src="./media/image35.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
