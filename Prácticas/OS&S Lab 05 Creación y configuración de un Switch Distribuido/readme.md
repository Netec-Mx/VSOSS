> # VMware vSphere
>
> ## Operación, Escalamiento y Seguridad
>
> **Versión 8**
>
> **Guía de uso de laboratorio**

## Laboratorio \# 5

### Creación y configuración de un Switch Distribuido

> Revisión 1.1 2024

## Laboratorio \# 5

### Creación y configuración de un Switch Distribuido

#### Actividades a realizar:

1.  Crear un Switch distribuido

2.  Configuración del Switch distribuido

3.  Integración de Hosts al Switch distribuido, migración de VMs

4.  Verificar configuración del Switch distribuido

## Actividad \# 1

### Crear y configurar un Switch distribuido

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionando el acceso rápido de
**vCenter**.

Para crear un Switch distribuido click en la vista de redes (1), click
en el **datacenter Production Datacenter** (2), presionar el botón
derecho, en el menú contextual seleccionar **Distributed Switch**, click
en **New Distributed Switch** (4)

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de Nombre y ubicación establecer como nombre: **vds
Production** (2), **NEXT** (3)

<img src="./media/image2.png" style="width:3.95573in;height:3.29644in"
alt="A screenshot of a computer Description automatically generated" />

En el paso para selección de la versión de Switch dejar la versión por
default **Esxi 8.0** (2), aceptar (3)

<img src="./media/image3.png" style="width:3.96615in;height:3.28568in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de configuración de especificaciones dejar los campos con
opciones de **default** y asignar el nombre **dps-SA-Production** al
**port group**. (2), aceptar (3)

<img src="./media/image4.png" style="width:4.84409in;height:4.03038in"
alt="A screenshot of a computer Description automatically generated" />

Revisar la configuración del Switch, aceptar (3)

<img src="./media/image5.png" style="width:4.26302in;height:3.5506in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 2

### Configuración del Switch distribuido

En la vista de redes, seleccionar el **Production Datacenter** y
expandir el switch **vds Production**

Observar el port group **dps-SA-Production**

<img src="./media/image6.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Click en el port group **dpg-SA-Production** (1), presionar el botón
derecho y seleccionar **Edit Settings** (2)

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la caja de diálogo siguiente

<img src="./media/image8.png" style="width:4.32945in;height:2.7908in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar un **Uplink** a la vez y mover hacia abajo a la sección de
**Standby uplinks** con el botón **MOVE DOWN** para terminar con la
configuración siguiente, sólo el **uplink 3** (3) queda activo, los
otros están inactivos (4), aceptar las opciones de **monitoring** y
**micellaneous** con valores de default.

<img src="./media/image9.png" style="width:4.4401in;height:2.88361in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 3

### Integración de Hosts al Switch distribuido, migración de VMs

Para administrar los hosts en la vista de red seleccionar el Switch
distribuido (1), presionar botón derecho, click en **Add and Manage
Host** (2)

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En la opción de seleccionar tareas, click en **Add Host** (2), **NEXT**
(3)

<img src="./media/image11.png" style="width:4.77344in;height:3.59329in"
alt="A screenshot of a computer Description automatically generated" />

En el paso para seleccionar host, click en **SELECT ALL** (2), **NEXT**
(3)

<img src="./media/image12.png" style="width:4.28906in;height:3.24063in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de administrar tarjetas de red físicas, seleccionar la
**vmnic 3** que dejamos como activas en ambos **ESXis**, se ve la lista
de **Related Host** (3) incluyendo al **ESXi-01** y **ESXi-02**

<img src="./media/image13.png" style="width:4.33073in;height:3.24405in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **uplink 3** (1) de la lista desplegable

<img src="./media/image14.png" style="width:4.70052in;height:3.5515in"
alt="A screenshot of a computer Description automatically generated" />

El resultado es el siguiente, **NEXT** (4)

<img src="./media/image15.png" style="width:4.67969in;height:3.51843in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de **administración** de adaptadores **VMkernel** click en
**Assign port group** (2) y seleccionar el port group **dpg
SA-Production** (5)

Click en **ASSIGN** (4), **NEXT** (5)

<img src="./media/image16.png" style="width:4.37261in;height:3.25781in"
alt="A screenshot of a computer Description automatically generated" />

El resultado es el siguiente:

<img src="./media/image17.png" style="width:4.86719in;height:3.68182in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de migrar **VMs**, click en **Migrate virtual machine
networkin**g (2), click en **configure per network adapter** (3), click
en **ASSIGN PORT GROUP** (5)

<img src="./media/image18.png" style="width:4.70052in;height:3.52539in"
alt="A screenshot of a computer Description automatically generated" />

Revisar la configuración, **FINISH** (3)

<img src="./media/image19.png" style="width:4.42969in;height:3.33453in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 4

### Verificar configuración del Switch distribuido

Para explorar la configuración final click en el Switch distribuido (1),
click en la pestaña **Configure** (2), en la sección de **Settings**
(3), click en **Topology** (4), observe las **VMS** (6) y las **vmnics**
asociadas de cada Host (5)

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Otra vista de la configuración está al seleccionar el **Switch** (1),
click en la pestaña **Configure** (2), en la sección de **Settings**
click en **Properties** (3), verifique **Uplinks** (4), **MTU** (5),
**CDP** (6)

<img src="./media/image21.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Siga inspeccionando, click en el port group (1), click en **Configure**
(2), en la sección de **Settings** Click en **properties** (4), observar
**port binding** y **port Allocation** (5)

<img src="./media/image22.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Para revisar que las **VMs** están controladas por el **Switch** click
en el **port Group** (1), click en la pestaña **VMs** (2), ver la lista
de **VMs** (3)

<img src="./media/image23.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Click en el port group (1), Click en pestaña **Ports** (2), se muestra
lista de hosts asociados (3), **VMs** (4) y estado de uplinks (5)

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />
