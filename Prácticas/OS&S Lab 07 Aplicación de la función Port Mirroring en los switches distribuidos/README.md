> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> ### Versión 8
>
> #### Guía de uso de laboratorio

## Laboratorio \# 7

> ### Aplicación de la función Port Mirroring en los switches distribuidos
>
> Revisión 1.1 2024

## Laboratorio \# 7

### Aplicación de la función Port Mirroring en los switches distribuidos

#### Actividades a realizar:

1.  Establecer las condiciones para realizar la captura de tráfico

2.  Configurar el switch distribuido para la captura de tráfico

3.  Realizar la captura de tráfico, comprobar la funcionalidad

4.  Retornar la configuración inicial del switch distribuido desde un
    respaldo

## Actividad \# 1

### Establecer las condiciones para realizar la captura de tráfico

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionando el acceso rápido de
**vCenter**.

Verificar que las VMs **Linux_01** y **Linux_02** están conectadas al
port group del switch distribuido y operando en el mismo servidor.

En la vista de **Hosts & Clusters** (1), click en la máquina
**Linux_01** (2), en el menú contextual seleccionar **Edit Settings**
(3)

<img src="./media/image1.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El port group es **dpg-SA-Production**, y está en estado de
**connected** (1), **OK** (2)

<img src="./media/image2.png" style="width:5.57832in;height:4.61933in"
alt="A screenshot of a computer Description automatically generated" />

Inspeccionar que la VM **Linux_02** tiene esa misma condición

En la vista de **Hosts & Clusters** (1), click en la máquina
**Linux_02** (2), en el menú contextual seleccionar **Edit Settings**
(3)

<img src="./media/image3.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

El port group es **dpg-SA-Production**, y está en estado de
**connected** (1), **OK** (2)

<img src="./media/image4.png" style="width:6.48036in;height:5.3413in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que están operando en el mismo host **ESX1_01**

En la vista de **Hosts & Clusters** (1) seleccionar el **Host
Esxi_01**(2), click en la pestaña **VMs** (3) y confirmar que están en
el mismo host (4)

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Encender ambas VMs y entrar a las consolas, usar el password  `VMware1!`

<img src="./media/image6.png" style="width:6.5in;height:3.52083in"
alt="A screenshot of a computer Description automatically generated" />

En ambas VMs, activar la vista de aplicaciones (1)

<img src="./media/image7.png" style="width:6.5in;height:3.65625in" />

Ejecutar en ambas VMs la aplicación **Terminal** (1)

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Con los comandos

`Ip add` (1)

`Ip route` (3)

Identificamos la dirección IP `172.20.10.208` (2) de la **VM
Linux_01** y su default **Gateway** `172.20.10.10` (4)

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

También comprobamos que el ping (1) al **default gateway** es exitoso (2).

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

De forma similar en la **VM Linux_02** averiguamos la IP
`172.20.10.201` (2) y el mismo default gateway `172.20.10.10` (4)

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Adicionalmente hacemos ping a la **VM Linux_01**(1) con dirección
`172.20.10.208`, con resultado exitoso (2)

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En esta preparación la **Linux_02** será el destino de la captura de
tráfico que se configurará en el Switch distribuido

Para esto en el SO de la **VM Linux_02** usaremos el comando para
capturar tráfico de ICMP

`sudo tcpdump -nn icmp`

Se emite el comando y al esperar un tiempo se ve que no se recibe
tráfico, así estará hasta recibir trafico de ICMP en su puerto

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la **VM Linux_01** emitir el comando **ping 172.20.10.10** (1) con
resultado exitoso (2)

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="Screens screenshot of a computer Description automatically generated" />

## Actividad \# 2

### Configurar el switch distribuido para la captura de tráfico

El tráfico que se genera en el **VM Linux_01** se reflejará en el puerto
de la **VM** **Linux_02** en una sesión de mirroring que se establecerá
en el switch

En la vista de **Network** (1) seleccionar el switch **vds Production**
(2), click en la pestaña **Configure** (3), en la sección de
**Settings** seleccionar **Port Mirroring** (4), click en **NEW** (5)

<img src="./media/image15.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Dejar seleccionada la opción **Distributed Port Mirroring** (2),
**NEXT** (3)

<img src="./media/image16.png" style="width:6.30922in;height:3.43951in"
alt="A screenshot of a computer Description automatically generated" />

Esta es la vista del paso **Edit Properties**

<img src="./media/image17.png" style="width:6.26938in;height:3.44765in"
alt="A screenshot of a computer Description automatically generated" />

Configurar en **Status** la opción **Enabled** (2), adicionalmente en la
opción **Normal I/O on destination Ports** establecer **Allowed** (3),
**NEXT** (4)

<img src="./media/image18.png" style="width:6.37535in;height:3.55931in"
alt="A screenshot of a computer Description automatically generated" />

En la selección del puerto origen establecer el host **ESXI_01** con la
**VM Linux_01** (2), **NEXT**(3)

<img src="./media/image19.png" style="width:6.38073in;height:3.54021in"
alt="A screenshot of a computer Description automatically generated" />

En la selección del puerto destino establecer el host **ESXI_01** con la
**VM Linux_02** (2), **NEXT**(3)

<img src="./media/image20.png" style="width:6.41678in;height:3.52976in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega la configuración, aceptar **FINISH** (1)

<img src="./media/image21.png" style="width:6.35098in;height:3.54229in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 3

### Realizar la captura de tráfico, comprobar la funcionalidad

Ya se tiene una sesión de mirroring y en la **VM Linux_02** se empieza a
recibir paquetes de ICMP lo que inicia la captura observar el origen y
destino de los paquetes (1)

<img src="./media/image22.png" style="width:6.5in;height:3.65625in" />

Para retornar a las condiciones iniciales antes de la captura, terminar
el proceso en la **VM** **Linux_02**, se muestra la cantidad de paquetes
capturados

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Terminar el ping en la **VM Linux_01**

<img src="./media/image24.png" style="width:6.5in;height:3.52083in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 4

### Retornar la configuración inicial del switch distribuido desde un respaldo

Terminar la sesión de mirroring en el switch retornando el switch a su
configuración original respaldada en un archivo en un laboratorio
anterior

En la vista de **Network** (1) seleccionar el switch **vds Production**
(2), en el menú contextual seleccionar **Settings** (3), click en
**Restore Configuration** (4)

<img src="./media/image25.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Click en la opción **BROWSE** (1) para buscar el archivo de respaldo

<img src="./media/image26.png" style="width:6.05942in;height:3.19803in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el archivo de **Backup** (1), **Abrir** (2)

<img src="./media/image27.png"
style="width:6.30463in;height:3.5317in" />

Aparece el nombre de archivo de respaldo (1), dejar la opción **Restore
Distributed switch and all port groups,** **NEXT** (3)

<img src="./media/image28.png" style="width:6.33698in;height:3.49307in"
alt="A screenshot of a computer Description automatically generated" />

Aceptar la configuración, **FINISH** (1)

<img src="./media/image29.png" style="width:6.26587in;height:3.40847in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que el Switch está en las condiciones iniciales sin una sesión
de mirroring

En la vista de **Network** (1) seleccionar el switch **vds Production**
(2), click en la pestaña **Configure** (3), en la sección de
**Settings** seleccionar **Port Mirroring** (4)

Ya no se ven sesiones operando (5)

<img src="./media/image30.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
