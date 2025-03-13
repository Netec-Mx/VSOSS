# Práctica 18. Creando una máquina Virtual cifrada

## Objetivos de la práctica:

- Crear una Máquina virtual cifrada.
- Confirmar que la máquina virtual está cifrada con un proveedor de llaves standard.

## Duración aproximada:
- 40 minutos.

## Instrucciones

## **Actividad \# 1**

### **Crear una Máquina virtual cifrada**

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
> Click en **Login**
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

User: `administrator@vsphere.local>`

Password: `VMware1!`

Dar clic en **Login.**

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar la vista **VMs and Templates.**

Click derecho en **Lab VMs**, seleccionar **New Virtual Machine.**

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega el asistente **New Virtual Machine**

En la página **Select a creation** **type**, click en **Create a new
virtual machine**

click **NEXT**.

<img src="./media/image7.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select a name and folder**

Introducir el nombre de la máquina virtual **VM-cifrada** en el campo
**Virtual machine name**.

Seleccionar la ubicación **Lab VMs**

click en **NEXT**

<img src="./media/image8.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En la página **Select a compute resource** expandir la lista
**SA-Datacenter** y seleccionar **SA-Compute-02,** expandir la lista y
seleccionar el host **sa-esxi-06.vclass.local**

Click en **NEXT**.

<img src="./media/image9.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En la página **Select** **storage**, seleccionar **Encrypt this virtual
machine**, automáticamente se activa la política de almacenamiento
**Management Storage Policy - Encryption**

Seleccionar el datastore **vsanDatastore**, click en **NEXT**.

<img src="./media/image10.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Select compatibility** click en **NEXT**

<img src="./media/image11.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En la página **Select a guest OS**, seleccionar en la opción **Guest OS
Family:** **Linux**

En la opción **Guest OS Version** seleccionar **VMware Photon OS
(64bit),** click en **NEXT**.

<img src="./media/image12.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En la página **Customize hardware**, configurar la máquina virtual con
los siguientes parámetros en su hardware virtual:

**1 CPU**

**1 GB de memoria**

**1 disco de 2 GB**

**Red VM Network**

En la opción de **CD/DVD Drive**, seleccionar **Datastore ISO File**,
seleccionar el archivo el datastore **OPSCALE-Datastore**, click en el
folder **ISO**, seleccionar el archivo **photon-3.0-a0f216d.iso**

Click en **OK**.

<img src="./media/image13.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Expandir la sección **New CD/DVD Drive**, activar la opción **Connect At
Power**, Click en **NEXT**.

<img src="./media/image14.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En la página **Ready to complete**, click en **FINISH**.

<img src="./media/image15.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que aparece en la lista la máquina **VM-cifrada** en el folder
**Lab VMs**

<img src="./media/image16.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

## **Actividad \# 2**

### **Confirmar que la máquina virtual está cifrada con un proveedor de llaves standard**

Seleccionar la máquina virtual **VM-Cifrada** en el inventario

En la pestaña **Summary**, revisar las especificaciones en la sección
**Virtual Machine Details**

Verificar que la máquina está cifrada

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />
