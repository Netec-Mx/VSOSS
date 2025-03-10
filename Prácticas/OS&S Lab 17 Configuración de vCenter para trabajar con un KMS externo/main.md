> # **VMware vSphere**
>
>## **Operación, Escalamiento y Seguridad**
>
> ### **Versión 8**
>
> #### **Guía de uso de laboratorio**

## **Laboratorio \# 17**

### **Configuración de vCenter para trabajar** **con un KMS externo**

#### Actividades por realizar:

1.  Configurar un KMS en vCenter

2.  Establecer confianza entre un KMS y vCenter

## **Actividad \# 1**

### **Configurar un KMS en vCenter**

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
> Contraseña: `mVMware1!`

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

Seleccionar la vista de **Host y& clusters**

Click en **sa-vcsa-01.vclass.local**, click en la pestaña **Configure**.

En la sección **Security** click en **Key** **Providerr**

Click en **ADD**

Seleccionar **Add Standard Key Provider**

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el asistente establecer la siguiente configuración relativa al KMS

**Name**: **sa-kms-01.vclass.local**

**KMS**: **sa-kms-01.vclass.local**

**Address**: `172.20.10.193`

**Port**: `5696`

Click en **ADD KEY PROVIDER**

<img src="./media/image7.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

En la cuadro de diálogo **Make vCenter Trust Key Provider** Click en
**TRUST**

<img src="./media/image8.png" style="width:2.54629in;height:3.22089in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que el servidor **sa-kms-01.vclass.local** se ha agregado a la
lista de proveedores KMS

Seleccionar el servidor y verificar el estado de desconectado

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \#2**

### **Establecer una relación de confianza del KMS con el vCenter Server**

En la Sección **Key** **Providers**, click sobre el proveedor KMS
**sa-kms-01.vclass.local**.

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Click en la lista desplegable **ESTABLISH TRUST** y seleccionar **Make
KMS trust vCenter**.

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Se despliega el asistente **Make KMS trust vCenter**

En la Página **Choose a method**, seleccionar la opción **KMS
certificate and private key**

click en **NEXT**.

<img src="./media/image12.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Upload KMS Certificate**, en la sección **KMS**
**Certificate**, click en **UPLOAD** **A FILE**

<img src="./media/image13.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el archivo **/Downloads/KMS Keys/root_certificate.pem**

Click en **Open**.

<img src="./media/image14.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer Description automatically generated" />

En la sección **KMS Private Key**, click en **UPLOAD A FILE**

Seleccionar el archivo **/Downloads/KMS Keys/root_key.pem**

click en **Open**.

<img src="./media/image15.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer Description automatically generated" />

Click en **ESTABLISH TRUST**.

<img src="./media/image16.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

Confirmar que se ha establecido confianza entre el **KMS** and
**vCenter**

<img src="./media/image17.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />
