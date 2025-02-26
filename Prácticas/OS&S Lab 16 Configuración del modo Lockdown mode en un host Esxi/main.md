> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> ### Versión 8
>
> #### Guía de uso de laboratorio

## **Laboratorio \# 16**

### **Configuración del modo Lockdown mode en un host Esxi**

Actividades por realizar:

1.  Activar el servicio de SSH

2.  Habilitar y probar el modo Lockdown mode

3.  Deshabilitar el Modo Lockdown mode

## **Actividad \# 1**

### **Activar el servicio de SSH**

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

Para activar el servicio SSH

En la vista de **Hosts & Clusters** (1), click en el host **ESXi_01**
(2), click en la pestaña **Configure** (3), en la sección **System**,
click en **Services** (4), click en **SSH** (5) click en **Start** (6)

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El servicio está activo

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que se acepta una conexión con **PuTTY** usando la cuenta de
root, establecer como host

**sa-esxi-01.vclass.local** (1) y conexión con **SSH** (2)

<img src="./media/image8.png" style="width:4.81074in;height:4.70839in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la alerta de conexión con SSH

<img src="./media/image9.png" style="width:5.0246in;height:3.70156in"
alt="A screenshot of a computer Description automatically generated" />

Se logra conexión con la cuenta de

User: `Root`

Password: `VMware1!`

<img src="./media/image10.png" style="width:6.5in;height:4.11042in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 2**

### **Habilitar y probar el modo Lockdown mode**

Enseguida activar el modo de protección Lockdown Mode

En la vista de **Hosts & Clusters** (1), click en el host **ESXi_01**
(2), click en la pestaña **Configure** (3), en la sección **System**,
click en **Security Profile** (4), observar que está deshabilitada la
protección (5), click en **EDIT** (6)

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar modo **NORMAL** (1) click en **OK** (2)

<img src="./media/image12.png" style="width:5.2434in;height:4.22523in"
alt="A screenshot of a computer Description automatically generated" />

Se activa la protección (1), notar que la lista de **Exception User**
está vacía

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que no se acepta una conexión con **PuTTY** usando la cuenta
de root, establecer como host

**sa-esxi-01.vclass.local** (1) y conexión con **SSH** (2)

<img src="./media/image14.png" style="width:4.69113in;height:4.83153in"
alt="A screenshot of a computer Description automatically generated" />

Se deniega la conexión con la cuenta de

User: `Root`

Password: `VMware1!`

<img src="./media/image15.png" style="width:4.125in;height:1.72917in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image16.png" style="width:6.5in;height:4.11042in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 3

## Deshabilitar el Modo Lockdown mode

Para des-habilitar la protección click en **EDIT** (1)

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en **Disable** (1), **OK** (2)

<img src="./media/image18.png" style="width:6.2612in;height:5.07637in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra el nuevo estado

<img src="./media/image19.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Apagar el servicio de SSH

En la vista de **Hosts & Clusters** (1), click en el host **ESXi_01**
(2), click en la pestaña **Configure** (3), en la sección **System**,
click en **Services** (4), click en **SSH** (5) click en **STOP** (6)

<img src="./media/image20.png" style="width:6.5in;height:3.65625in" />

Aparece la advertencia de apagado de SSH, OK (1)

<img src="./media/image21.png" style="width:6.51448in;height:2.09761in"
alt="A screenshot of a computer Description automatically generated" />

El servicio se ha detenido
