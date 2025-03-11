# Práctica 8. Exploración de la configuración de un datastore vSAN

## Objetivos de la práctica:
- Revisar la configuración de un datastore de vSAN.
- Revisar la política por default de almacenamiento en vSAN.
- Revisar una VM en el datastore de vSAN.

## **Actividad \# 1**

### **Revisar la configuración de un datastore de vSAN**

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
> Dar clic en **Login**
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
Client login interface**.

User: `administrator@vsphere.local`

Password: `VMware1!`

Dar clic en **Login**.

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que **VSAN** está habilitado en el clúster.

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2). Dirigirse a la pestaña **Configure** (3), en la
sección de configuración, seleccionar **Quickstart**. Revisar que
**vSAN** aparece como un servicio activo.

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Revisar que Hosts pertenecen al clúster de **vSAN**.

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2). Dirigirse a la pestaña **Summary** (3). Desplazarse entre las secciones y checar que en la sección de **Cluster Resources** (4) el número de hosts que están relacionados en el cluster de **vSAN** (5).

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Dar clic en la pestaña de **Hosts** (1) para ver el nombre de los host ESXi
en el clúster (2).

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Revisar la configuración de grupos de discos en el clúster de **vSAN**.

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2) y dirigirse a la pestaña **Configure** (3).

En la sección de **vSAN** (4) dar clic en **Disk Managment (5)**.

En cada host seleccionar **VIEW DISK** (6) y (7)

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Expandir el grupo de discos **Disk group** para ver sus detalles.

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Identificar la configuración del puerto VMkernel que se usa para accesar
la red de **vSAN**.

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2) y seleccionar el host **ESXI_04** (3) Dirigirse a la
pestaña **Configure** (4), en la sección de **Networking** (5)
seleccionar **Vmkernel Adapters** (6).

En la lista de puertos VMkernel, expandir el **vmk2** (7) para revisar
sus detalles.

Dar clic en la pestaña de **Properties** (8) para el puerto **vmk2**.

Verificar que aparece el servicio **vSAN** activo para este puerto (9).

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ver la capacidad de almacenamiento del clúster de vSAN.

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2). Dirigirse a la pestaña **Summary** (3).

Desplazarse entre las secciones para hallar el apartado de **vSAN**
que muestra la capacidad de almacenamiento (4).

Para ver el uso del espacio de vSAN dar clic en **VIEW CAPACITY** (5).

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la pestaña **MONITOR,** seleccionar **Capacity Usage**, ver en
**Capacity Overview** el espacio libre y ocupado en **vSAN**.

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 2**

### **Revisar la política por default de almacenamiento en vSAN**

Desde el menú principal (1), seleccionar **Policies and Profiles** (2).

<img src="./media/image14.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer Description automatically generated" />

En el panel de navegación verificar que políticas de almacenamiento están activas para VMs (1).

En el panel derecho desplazarse en la lista de políticas y seleccionar
**vSAN Default Storage Policy**.

En la pestaña de reglas ver la especificación para esta política de
almacenamiento.

La misma política de RAID 1 (mirroring) (3), es la política por
default de vSAN.

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Tarea \#3**

### **Revisar una VM en el datastore de vSAN**

Para tener la certeza de que una VM está almacenada en un datastore de
vSAN.

En la vista de **Datastores** (1) seleccionar el datastore
**vsanDatastore** (2). Dirigirse a la pestaña de **VMs** (3).

En la misma aparece la **VM Photon-03**.

<img src="./media/image16.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Dar clic en la **VM Photon-03** y observar que la VM está seleccionada
en el inventario en la sección izquierda (1) Dirigirse a la pestaña
**Monitor** (2) y en la sección de **vSAN** (3), elegir **Physical disk
placement** (4). En la sección de la derecha aparecen los componentes
del objeto **VM Photon-03** ubicados en los servidores del clúster
**ESXI-06, ESXI-05 y ESXI-04** (5).

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />
