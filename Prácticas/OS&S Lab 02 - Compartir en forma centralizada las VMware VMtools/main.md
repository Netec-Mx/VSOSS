# Práctica 2. Compartir en forma centralizada los VMware VMtools

## Objetivos de la práctica:
- Ver el valor por default de la ubicación de las VMtools.
- Modificar la variable avanzada de ubicación de las VMtools.
- Usar una API para actualizar el Symlink del SO que apunta a las VMtools.
- Realizar la reconfiguración normal de servicios.

## Duración aproximada:
- 50 minutos.

> Versión 8


## Instrucciones

## **Actividad \# 1**

### **Ver el valor por default de la ubicación de las VMtools**

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
Seleccionar en esta interfaz el primer pod de trabajo **vPodProd001a** (1)

> <img src="./media/image2.png" style="width:6.5in;height:3.65625in"
> alt="A screenshot of a computer Description automatically generated" />

Al entrar, en la siguiente interfaz proporcionar:

> Usuario: `student01`
>
> Contraseña: `VMware1!`

Dar clic en **OK**.

<img src="./media/image3.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Se obtiene acceso al escritorio remoto.
>
> <img src="./media/image4.png" style="width:6.5in;height:2.85276in"
> alt="A screenshot of a computer Description automatically generated" />

Abrir una instancia del browser Firefox con acceso directo al **vSphere
Client login interface**.

User: `administrator@vsphere.local`

Password: `VMware1!`

Dar clic en **Login**.

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En cada host existe una variable avanzada que apunta a un datastore, que
por default es un disco local en el que residen las **VMtools**.

La variable avanzada **UserVars.ProductLOckerLocation** tiene como valor
de default el directorio **/locker/packages/vmtoolsRepo/** en el disco
interno del servidor.

Para verificarlo:

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2) y seleccionar el host **Esxi-04**(3). Dirigirse a la
pestaña **Configure** (4), en la sección de **System** (5), seleccionar
**Advanced System Settings** (6). Dar clic en **EDIT** (7).

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se mostrará la caja de diálogo siguiente. Dar clic en el filtro (1) para
que se muestre un campo en donde se puede establecer el nombre de una
variable (2).

<img src="./media/image7.png" style="width:6.19021in;height:5.33639in"
alt="A computer screen with a computer screen Description automatically generated" />

Escribir el nombre de la variable a investigar. Basta con escribir
**User.Vars.pl** para que se filtre de la lista la variable requerida.

<img src="./media/image8.png" style="width:6.75124in;height:5.71189in"
alt="A computer screen with a white box Description automatically generated" />

La variable avanzada **UserVars.ProductLOckerLocation** (1) tiene como
valor de default el directorio.

**/locker/packages/vmtoolsRepo/** (2)

<img src="./media/image9.png" style="width:7.19779in;height:6.08309in"
alt="A screenshot of a computer Description automatically generated" />

## **Actividad \# 2**

### **Modificación de la variable avanzada de ubicación de las VMtools**

Modificaremos el valor de esa variable emitiendo comando en el host con
un comando ESXi.

Para esto, activar los servicios de **ESXi Shell** y SSH en el host
**ESXi_04**.

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2) y seleccionar el host **ESXi-04** (3). Dirigirse a la
pestaña **Configure** (4), en la sección **System** (5), dar clic en
**Services** (6). Observar el estado de los servicios **ESXi** **Shell**
(8) y **SSH** (10).

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Elegir el servicio **ESXi Shell** (1) y dar clic en **START** (2).

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Elegir el servicio **SSH** (1) y dar clic en **START** (2).

<img src="./media/image12.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Los servicios ya están activos (1).

<img src="./media/image13.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En el desktop ejecutar la aplicación **Remmina** (1).

<img src="./media/image14.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Proporcionar el password `VMware 1!` En la caja de autenticación.

<img src="./media/image15.png" style="width:6.52258in;height:4.65913in"
alt="A screenshot of a computer Description automatically generated" />

Dar doble clic en **SA-ESXI-04**.

<img src="./media/image16.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega la línea de comandos en el host.

<img src="./media/image17.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Enseguida, emitir el comando **ls** para mostrar los directorios, entre
ellos examinar el directorio **productLocker** que aloja actualmente las
**VMtools**.

`cd productLocker`

`ls`

Se muestran dos directorios asociados con las VMtools a saber:
**vmtools** y **floppies**

<img src="./media/image18.png" style="width:8in;height:6.in"
alt="A computer screen shot of a black screen Description automatically generated" />

Examinemos ambos directorios que copiaremos a un datastore y
compartiremos para todos los host ESXi.

`cd vmtools`

`ls`

Se muestran los archivos listados en la siguiente imagen:

`cd ..`

`cd floppies`

`ls`

`cd ..`

`ls`

Se muestran los archivos listados en la siguiente imagen:

<img src="./media/image19.png" style="width:8in;height:6.in"
alt="A screenshot of a computer Description automatically generated" />

Enseguida, establecer en un datastore **compartido** un directorio en
donde se copiarán las **VMtools** y se actualizarán constantemente para
compartirlas con todos los hosts ESXi en el datacenter.

Emitir los comandos:

`mkdir /vmfs/volumes/OPSCALE-Datastore/VMtoolsShare`

`cp -r \* /vmfs/volumes/OPSCALE-Datastore/VMtoolsShare`

`cd /vmfs/volumes/OPSCALE-Datastore/VMtoolsShare`

`ls`

<img src="./media/image20.png" style="width:8in;height:6.in"
alt="A screenshot of a computer Description automatically generated" />

Examinar las copias de los dos directorios.

`cd VMtools`

`ls`

`cd ..`

`cd floppies`

`ls`

`cd ..`

<img src="./media/image21.png" style="width:8in;height:6.in"
alt="A screenshot of a computer Description automatically generated" />

Con el siguiente comando modificamos el valor de la variable avanzada
del host.

**UserVars.ProductLOckerLocation** al valor deseado en un datastore
compartido al que tienen acceso todos los hosts ESXi en el datacenter
**/vmfs/volumes/OPSCALE-Datastore /VMtoolsShare**.

**esxcli system settings advanced set -o /UserVars/ProductLockerLocation
-s /vmfs/volumes/OPSCALE-Datastore/VMtoolsShare**

El nuevo valor se comprueba con el comando:

`esxcli system settings advanced list -o
/UserVars/ProductLOckerLocation`

Observar los resultados:

<img src="./media/image22.png" style="width:8in;height:6.in"
alt="A screenshot of a computer Description automatically generated" />

Si se retorna a la interfaz del vCenter y se examina el valor se ve
actualizado.

Para verificarlo:

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2) y seleccionar el host **Esxi-04** (3). Dirigirse a la
pestaña **Configure** (4) y en la sección de **System** (5), seleccionar
**Advanced System Settings** (6). Dar clic en **EDIT** (7).

<img src="./media/image23.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Abrir la lista y escribir:

`USerVars.Pro` para desplegar la variable.

<img src="./media/image24.png" style="width:7.75192in;height:6.67617in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra que el punto en donde están la VMtools es:

**/vmfs/volumes/OPSCALE-Datastore/VMtoolsShare**

<img src="./media/image25.png" style="width:7.85394in;height:6.67978in"
alt="A screenshot of a computer Description automatically generated" />

Dar clic **OK**.

## **Actividad \# 3**

### **Uso de una API para actualizar el Symlink del SO que apunta a las VMtools**

Para que este nuevo valor de variable avanzada entre en operación, es
necesario reiniciar el Host ESXi. Sin embargo, cuando se requiere no
interrumpir el servicio, se tiene la alternativa de modificar en el
Sistema operativo del Host el Symlink asociado. (Shortcut en el SO).
Esto se puede hacer con un comando Esxcli o con una llamada de una API.

Observar que en la salida del comando que usamos anteriormente, la variable
avanzada está actualizada pero el Symlink es **/productLocker -\>
/locker/packages/vmtoolsRepo**; no coinciden.

<img src="./media/image26.png" style="width:8in;height:6.in"
alt="A screenshot of a computer Description automatically generated" />

Para hacer uso de una API para ajustar este último valor, seleccionar en
el inventario el host **ESXi-04**. Observar de la URL en el browser el
número de host, en este caso es 22.

<img src="./media/image27.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Abrir una nueva ventana usando el \# de host 22 en el URL siguiente, a
manera de ejemplo (sustituya según sea su caso).

[**https://sa-vcsa-01.vclass.local/mob/?moid=host-22&method=updateProductLockerLocation**](https://sa-vcsa-01.vclass.local/mob/?moid=host-22&method=updateProductLockerLocation)

<img src="./media/image28.png" style="width:10.01837in;height:6.07399in"
alt="A screenshot of a computer Description automatically generated" />

**Proporcionar:**

User: `administrator@vpshere.local`

Password: `VMware1!`

Se muestra la interfaz del api correspondiente para ajustar el
**Symlink** de **UpdateProductLockerLocation_Task** (1), en ella,
determinar el valor.

**/vmfs/volumes/OPSCALE-Datastore/VMtoolsShare** (2), dar click en **Invoke
Method** (3).

<img src="./media/image29.png" style="width:8in;height:6.in"
alt="A screenshot of a computer Description automatically generated" />

Se ejecuta el Method correspondiente (1)

<img src="./media/image30.png" style="width:8in;height:6.in"
alt="A screenshot of a computer Description automatically generated" />

Con la llamada a la API ahora el **symlink** está actualizado.

<img src="./media/image31.png" style="width:6.27416in;height:2.85247in"
alt="A screenshot of a computer Description automatically generated" />

Estas operaciones se tendrían que realizar en cada host, ya sea
manualmente o con un script para automatizar el proceso.

## **Actividad \# 4**

### **Reconfiguración normal de servicios**

Finalmente, cerrar los procesos de ESXi y SSH.

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2) y seleccionar el host **ESXi-04** (3). Dirigirse a la
pestaña **Configure** (4) y en la sección **System** (5), seleccionar
**Services** (6). Dar clic en **ESXi Shell** (7). **STOP** (8).

<img src="./media/image32.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

En la vista de **Hosts & Clusters** (1), elegir el clúster
**SA-Compute-02** (2) y seleccionar el host **ESXi-04** (3). Dirigirse a la
pestaña **Configure** (4) y en la sección **System** (5), seleccionar
**Services** (6). Dar click en **SSH** (7). **STOP** (8).

<img src="./media/image33.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Ahora lucen apagados ambos servicios (1).

<img src="./media/image34.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
