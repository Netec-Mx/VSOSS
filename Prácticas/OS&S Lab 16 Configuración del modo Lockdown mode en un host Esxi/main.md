# Práctica 16. Configuración del modo Lockdown mode en un host ESXi

## Objetivos de la práctica: 

- Activar el servicio de SSH.
- Habilitar y probar el modo Lockdown mode.
- Deshabilitar el Modo Lockdown mode.

## Duración aproximada:
- 20 minutos.

## Instrucciones

## **Actividad \# 1**

### **Activar el servicio de SSH**

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
>  Dar clic en **Login.**
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

Click en **Login**

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para activar el servicio SSH

En la vista de **Hosts & Clusters** (1), escoger el host **sa-esxi-01**
(2). Dirigirse a la pestaña **Configure** (3) y en la sección **System**,
dar clic en **Services** (4). Seleccionar **SSH** (5) dar clic en **Start** (6).

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

El servicio SHH está activo.

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a black and white screen Description automatically generated" />

En el escritorio ejecutar la aplicación **Remmina.**

Verificar que se acepta una conexión con **Remmina** usando la cuenta de
root, establecer como host **sa-esxi-01.vclass.local** (1).

<img src="./media/image8.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen with a white and black box Description automatically generated" />

Se logra la conexión con el Host **sa-esxi-01.vclass.local**.

<img src="./media/image9.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 2**

### **Habilitar y probar el modo Lockdown mode**

Enseguida, activar el modo de protección Lockdown Mode.

En la vista de **Hosts & Clusters** (1), escoger el host **sa-esxi-01**
(2). Dirigirse a la pestaña **Configure** (3) y en la sección **System**,
seleccionar **Security Profile** (4). Observar que está deshabilitada la
protección (5). Seleccionar **EDIT** (6).

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a message Description automatically generated" />

Seleccionar modo **NORMAL** (1). **OK** (2).

<img src="./media/image11.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

Se activa la protección (1), notar que la lista de **Exception User**
está vacía.

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Verificar que no se acepta una conexión con **Remmina** usando la cuenta
de **root**.

Activar Reminna.

**sa-esxi-01.vclass.local** (1).

<img src="./media/image13.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Se deniega la conexión con la cuenta de:

User: `Root`

Password: `VMware1!`

<img src="./media/image14.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 3**

### **Deshabilitar el Modo Lockdown mode**

Para des-habilitar la protección, hacer clic en **EDIT** (1).

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Seleccionar **Disable** (1) **OK** (2).

<img src="./media/image16.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra el nuevo estado.

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Apagar el servicio de SSH.

En la vista de **Hosts & Clusters** (1), escoger el host **sa-esxi-01**
(2). Desplazarse a la pestaña **Configure** (3) y en la sección **System**,
seleccionar **Services** (4). Hacer clic en **SSH** (5) y en **STOP** (6).

<img src="./media/image18.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aparece la advertencia de apagado de SSH. **OK** (1).

<img src="./media/image19.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

El servicio se ha detenido.

<img src="./media/image20.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
