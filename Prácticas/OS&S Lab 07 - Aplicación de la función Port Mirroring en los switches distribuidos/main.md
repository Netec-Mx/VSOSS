# Práctica 7. Aplicación de la función Port Mirroring en los switches distribuidos

## Objetivos de la práctica:
- Establecer las condiciones para realizar la captura de tráfico.
- Configurar el switch distribuido para la captura de tráfico.
- Realizar la captura de tráfico y comprobar la funcionalidad.
- Retornar la configuración inicial del switch distribuido desde un respaldo.

## Duración aproximada: 
- 40 minutos.

## Instrucciones

## **Actividad \# 1**

### **Establecer las condiciones para realizar la captura de tráfico**

Utilizar la liga de acceso proporcionada por su instructor.

A manera de ejemplo:
[**https://vlabs.v2s.us/lab**](https://vlabs.v2s.us/lab)

<img src="./media/image1.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Utilizar el usuario y contraseña que le proporcione su instructor.

A manera de ejemplo

> Usuario: `student01a`
>
> Contraseña: `Arn0224!`
>
Dar clic en **Login**.
>
Seleccionar en esta interfaz el primer pod de trabajo **vPodProd001a** (1).
>
> <img src="./media/image2.png" style="width:6.5in;height:3.65625in"
> alt="A screenshot of a computer Description automatically generated" />

Al entrar, en la siguiente interfaz proporcionar:

> Usuario: `student01`
>
> Contraseña: `VMware1!`

Dar lick en **OK**.

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

Para este ejercicio se utilizarán las VMS **Linux01** y **Linux02,** que
están en el **cluster SA-Compute.**

Encender la **VM Linux01.**

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Encender la **VM Linux02.**

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a computer screen Description automatically generated" />

La VM Linux01 se utilizará como destino para la operación de Port
Mirroring.

Verificar que las VMs **Linux01** y **Linux02** están conectadas al port
group del switch distribuido y operando en el mismo servidor.

En la vista de **Hosts & Clusters** (1), seleccionar la máquina **Linux01**
(2) y en el menú contextual elegir **Edit Settings** (3).

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

El port group es **dpg-SA-Production**, y está en estado de
**connected** (3). **CANCEL** (4).

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Inspeccionar que la VM **Linux02** tenga esa misma condición.

En la vista de **Hosts & Clusters** (1), seleccionar la máquina **Linux02**
(2) y en el menú contextual elegir **Edit Settings** (3).

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El port group es **dpg-SA-Production**, y está en estado de
**connected** (2). **CANCEL** (3).

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Verificar que están operando en el mismo host **sa-esxi-06**.

En la vista de **Hosts & Clusters** (1) seleccionar el **sa-esxi-06**
(2). Dirigirse a la pestaña **VMs** (3) y confirmar que están en el mismo
host (4).

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Entrar a las consolas de ambas máquinas, al seleccionarlas, dirigirse a la pestaña
**Symmary**, y dar clic en **LAUNCH WEB CONSOLE**.

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

En cada una de ellas proporcionar como user: `root` y el password
`VMware1!`.

<img src="./media/image14.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Con los comandos

`ip add` (1).

`ip route` (3).

Identificamos la dirección IP `172.20.11.116` (2) de la **VM Linux01**
y su default **Gateway** `172.20.11.2` (4).

> NOTA: Es posible que en el Laboratorio se encuentren por su implementación direcciones IP diferentes, por ejemplo, de la red 172.20.10.0 /24, ajustar los comandos según las salidas de estas instrucciones en las dos VM Linux01 y Linux02.

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Hacemos ping a la dirección del default Gateway `172.20.11.2`

<img src="./media/image16.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

De forma similar en la **VM Linux02** averiguamos la IP
`172.20.11.115` (2) y default Gateway

`ip add` (1)

`ip route` (3)

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ping al default Gateway `172.20.11.2`

<img src="./media/image18.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Adicionalmente hacemos ping a la **VM Linux01**(1) con dirección
`172.20.11.116`, con resultado exitoso (2)

<img src="./media/image19.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En esta preparación la **Linux02** será el destino de la captura de
tráfico que se configurará en el Switch distribuido

Para esto en el SO de la **VM Linux02** usaremos el comando para
capturar tráfico de ICMP

`sudo tcpdump -nn icmp`

Se emite el comando y al esperar un tiempo se ve que no se recibe
tráfico, así estará hasta recibir tráfico de ICMP en su puerto

<img src="./media/image20.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la **VM Linux01** emitir el comando `ping 172.20.11.2` (1) al
default Gateway con resultado exitoso (2)

<img src="./media/image21.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la VM2 no se ven cambios

<img src="./media/image22.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 2**

### **Configurar el switch distribuido para la captura de tráfico**

El tráfico que se genera en el **VM Linux01** se reflejará en el puerto
de la **VMLinux_02** en una sesión de mirroring que se establecerá en el
switch

En la vista de **Network** (1) seleccionar el switch **vds Production**
(2), click en la pestaña **Configure** (3), en la sección de
**Settings** seleccionar **Port Mirroring** (4), click en **NEW** (5)

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Dejar seleccionada la opción **Distributed Port Mirroring** (2),
**NEXT** (3)

<img src="./media/image24.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

En el paso **Edit Properties,** configurar

Configurar en **Status** la opción **Enabled** (2), adicionalmente en la
opción **Normal I/O on destination Ports** establecer **Allowed** (3),
**NEXT** (4)

<img src="./media/image25.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la selección del puerto origen establecer el host **sa-esxi-06** con
la **VM Linux01** (2), **NEXT**(3)

<img src="./media/image26.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la selección del puerto destino establecer el host **sa-esxi-06** con
la **VM Linux02** (2), **NEXT**(3)

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega la configuración, aceptar **FINISH** (1)

<img src="./media/image28.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

## **Actividad \# 3**

### **Realizar la captura de tráfico, comprobar la funcionalidad**

Ya se tiene una sesión de mirroring y en la **VM Linux02** se empieza a
recibir paquetes de ICMP lo que inicia la captura observar el origen y
destino de los paquetes (1)

<img src="./media/image29.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Para retornar a las condiciones iniciales antes de la captura, terminar
el proceso en la **VM** **Linux02**, se muestra la cantidad de paquetes
capturados

<img src="./media/image30.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Terminar el ping en la **VM Linux01**

<img src="./media/image31.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 4**

**Retornar la configuración inicial del switch distribuido desde un
respaldo**

Terminar la sesión de mirroring en el switch retornando el switch a su
configuración original respaldada en un archivo en un laboratorio
anterior

En la vista de **Network** (1) seleccionar el switch **vds-Production**
(2), en el menú contextual seleccionar **Settings** (3), click en
**Restore Configuration** (4)

<img src="./media/image32.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

Click en la opción **BROWSE** (1) para buscar el archivo de respaldo

<img src="./media/image33.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Seleccionar el archivo de **Backup** (2), **OPEN** (2)

<img src="./media/image34.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Aparece el nombre de archivo de respaldo (1), dejar la opción **Restore
Distributed switch and all port groups,** **NEXT** (3)

<img src="./media/image35.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Aceptar la configuración, **FINISH** (1)

<img src="./media/image36.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que el Switch está en las condiciones iniciales sin una sesión
de mirroring

En la vista de **Network** (1) seleccionar el switch **vds-Production**
(2), click en la pestaña **Configure** (3), en la sección de
**Settings** seleccionar **Port Mirroring** (4)

Ya no se ven sesiones operando (5)

<img src="./media/image37.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />
