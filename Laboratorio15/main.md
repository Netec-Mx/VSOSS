# Práctica 15. Manejo de alarmas 

## Objetivos de la práctica:

- Establecer una alarma para monitorear una condición.
- Disparar la alarma de condición.
- Establecer una alarma para monitorear un evento.
- Disparar la alarma de evento.
- Desactivar las alarmas.

## Duración aproximada:
- 40 minutos.

## Instrucciones

## **Actividad \# 1**

**Establecer una alarma para monitorear una condición**

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
> Dar clic en **Login.**
>
Seleccionar en esta interfaz el primer pod de trabajo **vPodProd001a** (1).
>
> <img src="./media/image2.png" style="width:6.5in;height:3.65625in"
> alt="A screenshot of a computer Description automatically generated" />

Al entrar, en la siguiente interfaz proporcionar:

> Usuario: `student01`
>
> Contraseña: `VMware1!`

Dar clic en **OK.**

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

Dar clic en **Login.**

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Abrir una instancia de Firefox y seleccionar el shortcut de **vCenter.**

En la vista de **Hosts & Clusters** (1), escoger la VM **Linux-CPU-01**
(2). En el menú contextual, seleccionar **Alarms** (3), **New Alarm** y
**Definition**(4).

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Se despliega el asistente de alarmas.

En el campo **Alarm Name**, establecer **Linux_01_CPU_High_Usage** (2).
**NEXT** (3).

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a white box Description automatically generated" />

Seleccionar del menú desplegable **IF** (2) y escoger **VM CPU USAGE** (3).

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Establecer las siguientes condiciones:

**Métrica : VM CPU Usage (2),**

**Operador: Is above (3)**

**Umbral: 35% (4)**

**Tiempo: 30 Sec (5)**

**Acción: Show as Warning (6)**

**NEXT** (7).

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a white box Description automatically generated" />

En el paso **Reset Rule** (1), observar la regla presente y avanzar.
**NEXT** (2); la misma indica que la norma para poner la alarma en un estado normal, es que la condición ya no se cumpla.

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra el resumen de la alarma, aceptarla con **CREATE** (2).

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Si se desea administrar las alarmas, y en este caso verificar la
existencia de la alarma recién creada.

En la vista de **Hosts & Clusters** (1), seleccionar el clúster
**SA-Compute-02** (2) y hacer clic en la VM **Linux-CPU-01** (3). Dirigirse a la
pestaña **Configure** (4) y en la sección de **Settings**, seleccionar **Alarm
definitions** (5), dar clic en la alarma **Linux_01_CPU_High_Usage** (6).

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Encender la VM **Linux-CPU-01.**

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Observar que la VM no tiene alta utilización de CPU en la gráfica de
desempeño.

En la vista de **Hosts & Clusters** (1), seleccionar el clúster
**SA-Compute-02** (2) y hacer clic en la VM **Linux_01** (3). Dirigirse a la
pestaña **Monitor** (4) y en la sección de **Performance** seleccionar
**Advanced**, ver que la gráfica se muestra en tiempo real **Real-Time**
(6). Verificar que la gráfica se refiere a **CPU usage in %** (7).

El uso de CPU está alrededor de 3% (8).

<img src="./media/image14.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

## **Actividad \# 2**

### **Disparar la alarma de condición**

Con la VM **Linux-CPU-01** seleccionada, en la pestaña de **Summary**,
dar click **LAUNCH WEB CONSOLE.**

Usar el password `VMware1!`, si es necesario.

<img src="./media/image16.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ejecutar el comando para iniciar el **script cpubusy.pl**.

`./Desktop/cpubusy.pl`

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se dispara la alarma. Observar con la VM **Linux-CPU-01** seleccionada (3)
en la pestaña de resumen (5).

<img src="./media/image18.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a computer screen Description automatically generated" />

Observar la gráfica avanzada de desempeño.

En la vista de **Hosts & Clusters**, elegir el clúster
**SA-Compute-02** y seleccionar la VM **Linux-CPU-01** (1). Dirigirse a la pestaña de **Monitor** (2) y en la sección de **Performance** seleccionar
**Advanced** (3). Ver que se muestra la gráfica en tiempo real **Real-Time**
(6). Verificar que la gráfica se refiere a **CPU usage in %
aproximadamente de 90** **%** (7).

<img src="./media/image19.png" style="width:6.5in;height:3.65625in" />

En la sección de Alarmas disparadas podemos ver también la alarma
listada.

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Datacenter-02** (2) y seleccionar la VM **Linux-CPU-01** (3). Dirigirse a la pestaña **Monitor** (4) y en la sección de **Issues and Alarms**
seleccionar **Triggered Alams** (5). Ver que se lista la alarma (6).

<img src="./media/image20.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a white screen Description automatically generated" />

En la lista de eventos también está listado el disparo de la alarma.

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2) y seleccionar la VM **Linux-CPU-01** (3). Dirigirse a la
pestaña **Monitor** (4) y en la sección de **Tasks and Events** (4) seleccionar **Events** (5). Ver que se lista la alarma (6).

<img src="./media/image21.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Una opción para apagar la alarma es:

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** y seleccionar la VM **Linux_01** (2). Dirigirse a la
pestaña **Monitor** (3), en la sección de **Issues and Alarms**
seleccionar **Triggered Alams** (4). Seleccionar la alarma y dar clic en
**RESET TO GREEN** (5).

<img src="./media/image22.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Alternativamente se puede:

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** y seleccionar la VM **Linux-CPU-01** (2). Dirigirse a la
pestaña **Summary** (3), hacer clic en Actions (4) y dar clic en **RESET TO
GREEN** (5).

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Apagar en la VM la aplicación de **cpubusy.**

<img src="./media/image24.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2) y seleccionar la VM **Linux-CPU-01** (3). Dirigirse a la
pestaña **Monitor** (4) y en la sección de **Performance** seleccionar
**Advanced**. Ver que la gráfica se muestra en tiempo real **Real-Time**
(6). Verificar que la gráfica se refiere a **CPU usage in %
aproximadamente de 3%** (7).

<img src="./media/image25.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 3**

### **Establecer una alarma para monitorear un evento**

En la vista de **Hosts & Clusters** (1), elegir el clúster
**Production Cluster** y seleccionar la VM **Linux_01** (2). Dirigirse a la
pestaña Configure (3), en la sección de **Settings** seleccionar **Alarm
definitions** (5). **ADD** (6).

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de **Nombre y objetivo**, establecer en el campo **Alarm Name**: **VM_Suspended** (2) y dejar en **Target Type** Virtual Machine (3). **NEXT** (3).

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de **Alarm Rule 1**, en la lista desplegable de **IF** (2), seleccionar **Power and Connection State** (3).

<img src="./media/image28.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la lista desplegable de **IF**, seleccionar **VM suspended** (2)

<img src="./media/image29.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Especificar que cuando se dispare la alarma se muestre una advertencia
(3), **NEXT** (4).

<img src="./media/image30.png"
style="width:6.50069in;height:3.65347in" />

En el paso de **Reset Rule 1**, especificar que la alarma se anule cuando la VM se reinicie (3). **NEXT** (4).

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

<img src="./media/image32.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aceptar el resumen de la configuración de la alarma (1). **CREATE** (2).

<img src="./media/image33.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Tarea \# 4**

### **Disparar la alarma de evento**

Procedamos a suspender la **VM Linux_01**.

En la vista de **Hosts & Clusters** (1), elegir la **VM Linux-CPU-01**
(2) y en el menú contextual seleccionar **POWER** (3). Seleccionar **Suspend**
(4).

<img src="./media/image34.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Se muestra la advertencia de que se suspenderá la VM. **YES** (1).

<img src="./media/image35.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Se dispara inmediatamente la alarma.

<img src="./media/image36.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Iniciar la VM para que se anule la alarma.

En la vista de **Hosts & Clusters** (1), elegir la **VM Linux_01**
(2) y en el menú contextual seleccionar **POWER** (3). Dar clic en **Power On**
(4)

<img src="./media/image37.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

La alarma desaparece.

<img src="./media/image38.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

## **Tarea \# 5**

### **Desactivar las alarmas**

En la vista de **Hosts & Clusters** (1), elegir la **VM Linux-CPU-01**
(2). Dirigirse a la pestaña **Configure**(3) y seleccionar **Alarm
Definitions** (4), en la alarma a eliminar (5), dar clic en **DELETE** (6).

<img src="./media/image39.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la advertencia de eliminación. **OK** (1).

<img src="./media/image40.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
