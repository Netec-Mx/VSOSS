# Práctica 17. Configuración de vCenter para trabajar con un KMS externo

## Duración aproximada:

- Configurar un KMS en vCenter.
- Establecer confianza entre un KMS y vCenter.

## Duración aproximada:
- 40 minutos.

## Instrucciones

## **Actividad \# 1**

### **Configurar un KMS en vCenter**

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
> Dar clic en **Login.**
>
Seleccionar en esta interfaz el primer pod de trabajo **vPodProd001a** (1).
>
> <img src="./media/image2.png" style="width:6.5in;height:3.65625in"
> alt="A screenshot of a computer Description automatically generated" />

Al entrar, en la siguiente interfaz proporcionar:

> Usuario: `student01`
>
> Contraseña: `mVMware1!`

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

Seleccionar la vista de **Host & clusters** (1), escoger **sa-vcsa-01.vclass.local**. Dirigirse a la pestaña **Configure**. En la sección **Security** dar clic en **Key Providerr.** Hacer clic en **ADD** y 
seleccionar **Add Standard Key Provider.**

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el asistente establecer la siguiente configuración relativa al KMS

**Name**: **sa-kms-01.vclass.local**

**KMS**: **sa-kms-01.vclass.local**

**Address**: `172.20.10.193`

**Port**: `5696`

Hacer clic en **ADD KEY PROVIDER** (5).

<img src="./media/image7.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

En la cuadro de diálogo **Make vCenter Trust Key Provider**, hacer clic en
**TRUST.**

<img src="./media/image8.png" style="width:2.54629in;height:3.22089in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que el servidor **sa-kms-01.vclass.local** se ha agregado a la
lista de proveedores KMS.

Seleccionar el servidor y verificar el estado de desconectado.

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \#2**

### **Establecer una relación de confianza del KMS con el vCenter Server**

En la Sección **Key Providers**, dar clic sobre el proveedor KMS
**sa-kms-01.vclass.local**.

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Dar clic en la lista desplegable **ESTABLISH TRUST** y seleccionar **Make
KMS trust vCenter** (1).

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Se despliega el asistente **Make KMS trust vCenter**

En la página **Choose a method** (1), seleccionar la opción **KMS
certificate and private key** (2). **NEXT** (3).

<img src="./media/image12.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Upload KMS Certificate** (1), dar clic en **UPLOAD A FILE** (2) en la sección **KMS Certificate**.

<img src="./media/image13.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el archivo **/Downloads/KMS Keys/root_certificate.pem**

Click en **Open**.

<img src="./media/image14.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer Description automatically generated" />

En la sección **KMS Private Key**, hacer clic en **UPLOAD A FILE.**
Seleccionar el archivo **/Downloads/KMS Keys/root_key.pem** (1). Dar clic en **Open** (2).

<img src="./media/image15.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer Description automatically generated" />

**ESTABLISH TRUST** (1).

<img src="./media/image16.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

## Resultado esperado

Confirmar que se ha establecido confianza entre el **KMS** and
**vCenter.**

<img src="./media/image17.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />
