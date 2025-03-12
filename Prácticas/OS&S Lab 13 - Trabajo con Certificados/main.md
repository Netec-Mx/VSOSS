# Práctica 13. Trabajo con certificados 

## Objetivos de la práctica:

- Examinar el certificado SSL de una máquina virtual.
- Generar una solicitud de firma de certificado.
- Reemplazar un certificado SSL de la máquina por un certificado de CA pregenerado.

## Duración aproximada
- 30  minutos.

## **Actividad \# 1**

### **Examinar el certificado SSL de una máquina virtual**

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

Click en **Login**

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El certificado SSL de vCenter se utiliza para proteger la comunicación y
garantizar la confidencialidad e integridad de los datos que se
intercambian entre los componentes de vCenter y otras entidades en la
infraestructura de VMware.

En el menú principal, seleccionar **Administration** (2).

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la sección **Certificates**, seleccionar **Certificates Managment**
(2). En la sección **Machine SSL Certificate** (3), seleccionar
**VIEW DETAILS** (4).

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la información del certificado que sería similar a la que se
muestra.

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Registrar la siguiente información del certificado para compararla en el
futuro.

Valid from: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Valid Until: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Thumbprint:
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

La huella digital del certificado (**Thumbprint**), también llamada **hash
de certificado**, es única y cambia con cada certificado generado.

Al terminar de revisar el certificado SSL de máquina, dar clic en **BACK
TO.**

**CERTIFICATE MANAGEMENT** (1)

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Dar clic en **VIEW DETAILS** (2) para el primer certificado en la sección
**Trusted Root Certificates** (1).

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Observar que el certificado fue emitido por **CA,** que indica que
VMware CA emitió el certificado. 
> CA se refiere a la VMCA en vCenter

Dar clic en **BACK TO CERTIFICATE MANAGEMENT.**

## **Actividad \#2**

### **Crear una solicitud de firma de certificado**

Utilizar **vSphere Certificate Manager** para crear una solicitud de
firma de certificado (**CSR**) que usará para solicitar un certificado
personalizado firmado por la autoridad de certificación (CA) del
controlador de dominio para el laboratorio.

Generar la solicitud de firma de certificado (**Certificate signing
request CSR**) (1).

En el recuadro **Machine SSL Certificate** (2), seleccionar **Actions**
(3). Hacer clic en **Generate Certificate Signing Request (CSR)** (4).

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ingresar los detalles necesarios para finalizar la solicitud de firma de
certificado.

| **Campo:**        | **Introducir**         |
|-------------------|------------------------|
| Organization      | **Netec**              |
| Organization Unit | **Educacion**          |
| Country           | Seleccionar **México** |
| State/Province    | **CDMX**               |
| Locality          | **Benito J**           |
| Email Address     | **admin@netec.com.mx** |

Dejar todos los demás campos como predeterminados.

**NEXT** (1).

<img src="./media/image12.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Hacer clic en **FINISH** (1) para cerrar el asistente.

<img src="./media/image13.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

La generación de la CSR de vCenter en esta actividad es sólo para fines
de prueba.

## Actividad # 3
### Reemplazar un certificado SSL de máquina con un certificado CA pregenerado

Importar y reemplazar el certificado autofirmado (**self-signed
certificate)** de VMware CA con un certificado firmado por una entidad
certificadora externa mediante vSphere Client.

En el menú principal (1), seleccionar **Administration** (2). En la
sección **Certificates** (3) elegir **Certificate Management** (4). 
En la sección **Machine SSL Certificate** (5), hacer clic en **ACTIONS**
(6) y después en **Import and Replace Certificate** (7).

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Se iniciará el asistente.

En la página **Choose apropriate option** (1) seleccionar **Replace with
external CA certificate (requires private key)** (2). **NEXT** (3).

<img src="./media/image15.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En el campo **Machine SSL Certificate** (2) hacer clic en **BROWSE FILE** (3).

<img src="./media/image16.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la carpeta **/Desktop/Class Materials and Licenses/linux_CA**, seleccionar **ca_vcsa.crt** (4). **OPEN** (5).

<img src="./media/image17.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Después de seleccionar este archivo, el cuadro de texto se completará
con la información del certificado firmado por la entidad encargada de la certificación.

En el cuadro **Chain of trusted root certificates**, hacer clic en
**BROWSE FILE** (3).

<img src="./media/image18.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la carpeta **/Desktop/Class Materials and Licenses/linux_CA**,

seleccionar **RootCA.crt** (4). **OPEN** (5).

<img src="./media/image19.png" style="width:6.19419in;height:3.5298in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Después de seleccionar este archivo, el cuadro de texto se completará
con la información del certificado raíz.

En el cuadro **Private Key,** hacer clic en **BROWSE FILE.**

En la carpeta **/Desktop/Class Materials and Licenses/linux_CA**, seleccionar el archivo **vmca_issued_key.key**, click en **OPEN**.

Después de seleccionar este archivo, el cuadro de texto se llenará con
la información de la Clave privada.

Clic en **NEXT**.

<img src="./media/image20.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **System Backup** (1), seleccionar la opción de verificación
**Backup acknowledgment** (2). **NEXT** (3).

<img src="./media/image21.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

En la página **Review** (1), dar clic en **FINISH** (2).

<img src="./media/image22.png" style="width:6.19419in;height:3.5298in"
alt="A screenshot of a computer Description automatically generated" />

Después de unos segundos, debería aparecer un cuadro de mensaje que
indique que se ha cambiado el certificado.

Dar clic en **UPDATE**.

En una nueva pestaña de **Firefox**, abrir el menú y seleccionar **Settings**.

Alternativamente, puede abrir una nueva pestaña del navegador Firefox e
ingresar:

`about:preferences` en el **campo de dirección**.

Buscar la sección de **Cookies**

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Clear data** y anular la selección de **Cookies and Site
Data**. Dar clic en **Clear**.

<img src="./media/image24.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Esta acción borrará la memoria caché web de su navegador Firefox.

1. Reiniciar el navegador Firefox.

2. Verificar el reemplazo del certificado.

Con vSphere Client, iniciar sesión en la instancia de vCenter
**sa-vcsa-01.vclass.local** usando sus credenciales de laboratorio de vCenter.

Si recibe el mensaje de **Warning: Potential Security Risk Ahead** en su
session de Firefox, dar click en **Advanced.**

<img src="./media/image25.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Dar click en **Accept the Risk and Continue** para pasar a la página de
inicio de sesión de vCenter.

Si no es posible iniciar sesión en vCenter después de que se hayan
reiniciado los servicios, intentar iniciar sesión con una nueva ventana
privada de Firefox.

En el menú principal, seleccionar **Administration** (2). Elegir
**Certificate Management** en la sección **Certificates** (4). En el recuadro **Machine SSL Certificate**, hacer clic en **VIEW DETAILS**.

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Registrar la siguiente información del certificado y comparar las fechas
válidas y la huella digital con la información del certificado recopilada en una tarea anterior.

Valid from: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Valid until: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Thumbprint:
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

<img src="./media/image27.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

### IMPORTANTE:

### Las fechas válidas y la huella digital del certificado actual deben ser diferentes a las del certificado anterior.
