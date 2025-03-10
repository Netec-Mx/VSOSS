> # **VMware vSphere**
>
> ## **Manejo de Host Profiles en Vsphere**
>
>### **Versión 12**
>
> #### **Guía de uso de laboratorio**

## **Laboratorio \# 12**

### **Manejo de Host Profiles en Vsphere**

#### **Actividades por realizar:**

1\. Configuración de un cluster con una imagen única

2\. Configurar un cluster con perfiles de configuración

3\. Retornar un host a una configuración específica

4\. Revisar el documento de configuración

## **Actividad \# 1**

### **Configuración de un cluster con una imagen única**

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

En un cluster se realizará una conversión de uso de **configuraciones
base** (baselines) al uso de **perfiles de servidor**, para que los
hosts estén **homologados**.

Iniciaremos esto revisando la configuración inicial del cluster

En la vista de **Hosts & Cluster, click** en el **cluster
SA-Compute-01**,

Click en la pestaña **Configure**

En la sección **Desired State**, clic en **Configuration**

Se nota que el cluster está actualmente trabajando con **configuraciones
base** (baselines)

Vea el mensaje desplegado

Click en la pestaña **Updates**

<img src="./media/image6.png"
style="width:6.50069in;height:3.65347in" />

Revise los mensajes desplegados

Para configurar el cluster para que trabaje con configuraciones basadas
en imágenes

click en **MANAGE WITH A SINGLE IMAGE**

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a computer screen Description automatically generated" />

Click en el botón **SETUP IMAGE MANUALLY**.

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Del menú desplegable **ESXi Version** seleccionar la versión **8.0 U2 –
22380479**

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Dar click en **VALIDATE**.

Esperar a que se despliegue que la imagen es válida

En la sección **Convert to image**, click en el botón **SAVE** y esperar
a que se verifique el cumplimiento

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Click en **FINISH IMAGE SETUP**

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega un comentario del proceso.

Click en **YES, FINISH IMAGE SETUP**.

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a message Description automatically generated" />

Se tendrá que verificar que los hosts cumplen con la configuración

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a message box Description automatically generated" />

## **Actividad \#2**

### **Configurar un cluster con perfiles de configuración**

El propósito de usar perfiles de configuración es controlar, monitorear
y en su caso retornar un host a una configuración específica.

Dar click en la pestaña **Configure** seleccionando el cluster
**SA-Compute-01**

En la sección **Desired State click** en **Configuration**

Para hacer que el cluster use una configuración usando perfiles de
configuración, click en **CREATE CONFIGURATION**.

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

En la etapa **Create configuration**, click en **IMPORT FROM REFERENCE
HOST** para establecer cual será la configuración a utilizar en el
perfil

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el host **sa-esxi-01.vclass.local,** click en **IMPORT**.

<img src="./media/image16.png" style="width:8in;height:6.in"
alt="A computer screen shot of a computer Description automatically generated" />

Click en **CLOSE**

<img src="./media/image17.png" style="width:width:8in;height:6.in"
alt="A screen shot of a computer Description automatically generated" />

Click en **NEXT**.

<img src="./media/image18.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

En la sección **Validate configuration**, esperar a que se termine el
proceso de validación, click en **NEXT**.

<img src="./media/image19.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la etapa **Pre-check and apply**, esperar a que termine el proceso de
pre-verificación para la aplicación, click en **FINISH AND APPLY**.

<img src="./media/image20.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en **CONTINUE**.

<img src="./media/image21.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a message Description automatically generated" />

Click en GO **TO CONFIGURATION**.

<img src="./media/image22.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la configuración obtenida como referencia

<img src="./media/image23.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 3**

### **Retornar un host a una configuración específica**

En este caso, se mostrará como cambiar la configuración de un host para
que ya no cumpla la configuración del perfil del cluster y como corregir
el incumplimiento a la misma aplicando un proceso de reparación.

El cambio de configuración será en la red

Agregar un puerto **VMkernel** al host

En la vista de **Hosts & Clusters**

Seleccionar el host **sa-esxi-02.vclass.local**.

Click en la pestaña **Configure**

En la sección **Networking** click en **VMkernel adapters**

Click en ADD **NETWORKING**.

<img src="./media/image24.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el paso **Select Connection Type** dejar seleccionada la opción
**VMkernel Network Adapter,** click en **NEXT**.

<img src="./media/image25.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En el paso **Select target device** seleccionar la opción **Select an
existing standard switch**

Enseguida seleccionar el Switch **vSwitch0,** click en **NEXT**.

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En el paso **Add Networking** dejar las opciones de default, click en
**NEXT**.

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En el paso **IPV4 Settings,** dejar seleccionada la opción **Obtain IPv4
settings automatically**, click en **NEXT**
<img src="./media/image28.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Revisar la configuración final, click en **FINISH**.

<img src="./media/image29.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aparecerá un adaptador adicional tipo vmk, verificar si es **vmk1,
vmk2,** o **vmk3,** este podría ser diferente según el estado del
laboratorio.

<img src="./media/image30.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Con el propósito de verificar si el host cumple con la configuración del
perfil

Seleccionar en la vista de **Hosts & Clusters** el cluster
**SA-Compute-01**

click en la pestaña **Configure**

En la sección Seleccionar **Desired State** click en **Configuration**.

Click en la pestaña **Compliance,** click en **CHECK COMPLIANCE**.

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega el estado del host **sa-esxi-02.vclass.local** que no
cumple con la configuración del perfil.

<img src="./media/image32.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En este punto, para retornar el host a su configuración inicial
establecida en el perfil del cluster

Click en **REMEDIATE**.

<img src="./media/image33.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Se realizará una verificación del proceso

Expandir cada host para ver detalles

Click en **NEXT**

Verificar la información del posible impacto del proceso

<img src="./media/image34.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en **REMEDIATE**.

<img src="./media/image35.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Observe el panel de tareas.

Como parte del proceso el host puede reiniciarse.

Se ejecutará un segundo proceso de verificación del cumplimiento de la
configuración

<img src="./media/image36.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a white and black screen Description automatically generated" />

El host ha regresado a la configuración inicial definida en el cluster

Seleccionar el host **sa-esxi-02.vclass.local**

Verificar que el proceso eliminó el adaptador kernel que se le agregó
anteriormente.

<img src="./media/image37.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

## **Actividad \# 4**

### **Revisar el documento de configuración**

Es posible ver la configuración establecida en el cluster en un archivo
tipo **JSON**

Seleccionar el cluster **SA-Compute-01**

Click en la pestaña **Configure**, en la sección **Desired State** click
en **Configuration**.

En la sección de configuración, Click en la pestaña **Settings**

Click the **EXPORT** para abrir un menú desplegable, seleccionar
**Cluster**

**Configuration.**

<img src="./media/image38.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en **DOWNLOAD**.

<img src="./media/image39.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Abra el folder **Downloads**.

Revisar los detalles del archivo, click en **Save**.

En la barra de tareas de Linux click en **Files**.

Click en **Downloads**.

<img src="./media/image40.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Abrir con click derecho el archivo
**export-settings-config-xxxxxxxxxx.json,** click en **Open with Text
Editor**.

<img src="./media/image41.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Esto despliega el archive tipo **JSON**, para su revisión, y posible
edición si se desea importar y aplicar al cluster

<img src="./media/image42.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />
