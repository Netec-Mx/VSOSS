> # **VMware vSphere**
>
> ## **Operación, Escalamiento y Seguridad**
>
> ### **Versión 8**
>
> #### **Guía de uso de laboratorio**

## **Laboratorio \# 14**

## **Monitoreo del desempeño de un Máquina Virtual**

Actividades por realizar:

1.  Establecer afinidad de CPU

2.  Establecer contención en dos VMS

3.  Explorar las opciones de gráficas de desempeño

## **Actividad \# 1**

### **Establecer afinidad de CPU**

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

Abrir una instancia de Firefox, seleccionar el shortcut de **vCenter**

**Apagar DRS**

En la vista de **Hosts & Clusters** (1), click en el cluster
**Production Cluster** (2), click en la pestaña **Configure** (3), click
en **vSphere DRS** (4), Click en **EDIT** (5)

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en **vSphere DRS** (1), **OK** (2)

<img src="./media/image7.png" style="width:2.91043in;height:2.46145in"
alt="A screenshot of a computer screen Description automatically generated" />

El servicio está deshabilitado

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Migrar la VM Linux_02, click en la VM (1), en el menú contextual
seleccionar Migrate (2)

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Change compute resource only** (1), **NEXT** (2)

<img src="./media/image10.png" style="width:3.89573in;height:2.39811in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el host **ESXi_01** (2), **NEXT** (3)

<img src="./media/image11.png" style="width:3.89298in;height:2.37594in"
alt="A screenshot of a computer Description automatically generated" />

Click en **NEXT** (1)

<img src="./media/image12.png" style="width:3.88459in;height:2.37577in"
alt="A screenshot of a computer Description automatically generated" />

Aceptar el resumen **FINISH** (1)

<img src="./media/image13.png" style="width:3.88834in;height:2.39026in"
alt="A screenshot of a computer Description automatically generated" />

Con el host **ESXi_01** seleccionado (2), click en la pestaña **VMS**
(3), se pueden observar las dos VMs residiendo en el host **ESXI_01**
(4)

<img src="./media/image14.png" style="width:6.5in;height:3.65625in" />

Para crear afinidad de CPU

Con ambas máquinas apagadas realizar el siguiente procedimiento

Click en la VM **Linux_01** (1), en el menú contextual seleccionar
**Edit Settings** (2)

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Expandir la sección de CPU (1), en el campo **Scheduling Affinity**
establecer el cpu físico **0** (3) Click en **OK** (4)

<img src="./media/image16.png" style="width:2.91424in;height:2.75936in"
alt="A screenshot of a computer Description automatically generated" />

Realizar la misma operación en la VM **Linux_02**

## **Actividad \# 2**

### **Establecer contención en dos VMS**

Encender ambas máquinas virtuales **Linux_01** y **Linux_02**

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image18.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para ambas Máquinas Virtuales en la pestaña de **Summary** dar click
**LAUNCH WEB CONSOLE**

Usar el password `VMware 1!`

<img src="./media/image19.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Click en el ícono de **Apps** (1)

<img src="./media/image20.png" style="width:6.5in;height:3.65625in" />

Ejecutar la aplicación **Terminal** (1)

<img src="./media/image21.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ejecutar los comandos para iniciar el script cpubusy.pl

`cd Desktop`

`chmod +x cpubusy.pl`

`perl ./cpubusy.pl`

<img src="./media/image22.png" style="width:6.5in;height:3.65625in" />

## **Actividad \# 3**

### **Explorar las opciones de gráficas de desempeño**

En la vista de **Hosts & Clusters** (1), click en el Host ESXi_01 (2),
click en la pestaña **Monitor** (3), En la sección **Performance** click
en **Overview** (4),

En ambas VM tendremos una aplicación que hace alta utilización de CPU
con afinidad de CPU en CPU físico 0

<img src="./media/image23.png" style="width:6.5in;height:3.65625in" />

Hay que asegurar tener gráficas en tiempo real, esto lo podemos ver al
ver **Real-Time** a la izquierda de **Chart-Options** (5)

Dar click en **Chart-Options** (5)

<img src="./media/image24.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega la caja de diálogo para determinar que métrica se despliega
en la gráfica, en este caso seleccionar **CPU** (1)

De esta métrica seleccionar **Readiness** (2) y **Usage** (3), se puede
filtrar en la gráfica la información del **cpu 0** y **cpu 1** (4)

<img src="./media/image25.png" style="width:3.89948in;height:2.72893in"
alt="A screenshot of a computer Description automatically generated" />

En la sección **Performance Chart Legend** se pueden resaltar la gráfica
de un objeto como **CPU 0** o **CPU 1**

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Con la aproximación del mouse a una gráfica se despliega la información
relacionada

<img src="./media/image27.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

En esta gráfica se muestra el comportamiento de uso del cpu 0, de
tiempos de espera de uso de cpu físico

<img src="./media/image28.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Para las máquinas Linux_01 la gráfica de **CPU ready** muestra
contensión, es decir, tiene tiempo de espera para uso del cpu físico en
competencia con la VM **Linux_02**

<img src="./media/image29.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la VM2 se muestra de igual manera contensión

<img src="./media/image30.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Retornar las VMs a su estado anterior

Apagar las VMs

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Eliminar la afinidad de CPU, en ambas VMs al dar Edit Settings (3)

<img src="./media/image32.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Expandir la sección de **CPU** y eliminar el **cpu 0** en el campo
**Scheduling Affinity** (2), **OK** (3)

<img src="./media/image33.png" style="width:2.89937in;height:2.7662in"
alt="A screenshot of a computer Description automatically generated" />
