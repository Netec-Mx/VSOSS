# Práctica 11. Respaldo del vCenter Server 

## Objetivos de la práctica_

- Acceso a la consola de administración del vCenter Server.
- Examinar las opciones para respaldos programados e inmediatos.
- Lanzar un proceso de respaldo del vCenter Server.
- Visualizar la opción de restauración de un backup con la aplicación Install.

## Duración aproximada
- 30 minutos.

## Instrucciones

## **Actividad \# 1**

### **Acceso a la consola de administración del vCenter Server**

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

Dar clic en **Login.**

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Abrir una instancia de Firefox. Seleccionar el shortcut de la VAMI o escribir el URL en el browser.

<https://sa-vcsa-01.vclass.local:5480> (1),

Notar que el acceso es a la vista de administración del vCenter Server
(2).

Proporcionar el user:
[**administrator@vsphere.local**](mailto:administrator@vsphere.local) 
Proporcionar password: `VMware 1!` (3). 
**LOGIN.** (4)

<img src="./media/image6.png" style="width:5.86297in;height:4.84605in"
alt="A screenshot of a computer Description automatically generated" />

En la interfaz de administración dar clic en **Backup** (1).

<img src="./media/image7.png" style="width:6.5in;height:3.65625in" />

## **Actividad \# 2**

### **Examinar las opciones para respaldos programados e inmediatos**

En el panel derecho se muestran dos opciones:

**CONFIGURE** para establecer una programación recurrente de backups (1).

**BACKUP** **NOW** para iniciar un proceso inmediato de respaldo (2).

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Configure.**

Se muestran opciones de programación recurrente. Entre los datos relevantes
están: el datastore en donde se realiza la copia (1), el user y password
del datastore (2), la programación (3) y los datos (4) a proteger.

<img src="./media/image9.png" style="width:5.81758in;height:4.28373in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 3**

### **Lanzar un proceso de respaldo del vCenter Server**

Para realizar un respaldo inmediato.

Establecer **nfs://172.20.10.15/msnt/NFS-POOL** (1) en el **Backup location** 

(2)
Username: `root`

Password: `VMware1!`

Seleccionar en **Data** la opción de **Stats, Events, and Tasks (3). START (4)

<img src="./media/image10.png" style="width:5.81244in;height:4.03032in"
alt="A screenshot of a computer Description automatically generated" />

Vigilar el proceso de backup del vCenter Server Appliance.

## **Actividad \# 4**

### **Visualizar la opción de restauración de un backup con Install**

Para un proceso de restauración es importante recordar que éste se lleva a cabo desde la aplicación de instalación del vCenter.

Ejecutar la aplicación Installer del ISO. 

<img src="./media/image11.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la aplicación, usar la opción **Restore** (1).

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
