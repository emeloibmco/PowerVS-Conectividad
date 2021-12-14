# PowerVS-Conectividad
<p align="center">
<img width="500" alt="autoscale" src=https://github.com/emeloibmco/PowerVS-Conectividad/blob/main/Imagenes/escenario.png>
</p>

## Índice  📰
1. [Pre-Requisitos](#Pre-Requisitos-pencil)
2. [Activar el VRF(Virtual Routing Forwarding)](#Activar-el-VRF-(Virtual-Routing-Forwarding))
3. [Referencias](#Referencias-mag)
4. [Autores](#Autores-black_nib)
<br />

## Pre Requisitos :pencil:
* Contar con una cuenta en <a href="https://cloud.ibm.com/"> IBM Cloud</a>.
* Contar con un grupo de recursos específico para el despliegue de los recursos
<br />

## Crear un Power Systems Virtual Server
Para crear y configurar un servidor virtual Power Systems, tenga en cuenta los siguientes pasos:

1. Desde el catálogo busque Power Systems Virtual Server y haga click sobre el icono.
2. Esto lo llevara a una pestaña de configuración, aquí ingrese la siguiente información:
  * ```Select a location: ``` Seleccione la ubicación donde desea desplegar el servidor.
  * ```Service name: ``` Asígnele un nombre el servidor.
  * ```Select a resource group: ``` Seleccione el grupo de recursos con el cual quiere desplegar el servidor.
  * ```Tags :``` Asígnele etiquetas al servidor si lo considera necesario.
3. Luego de esto de click en el botón ```Crear```.

<p align="center">
<img width="500" alt="autoscale" src=https://github.com/emeloibmco/PowerVS-Conectividad/blob/main/Imagenes/PSVS.gif>
</p>

## Crear una SSH key
1. Para crear una SSH key es necesario obtener primero una llave publica, a continuación, se muestra una de las opciones en las que se puede generar el par de llaves SSH para esto tenga en cuenta los siguientes pasos:
   * Acceda al *IBM Cloud Shell* e ingrese el siguiente comando: 
   ```
   ssh-keygen -t rsa -C "user_id" 
   ```
   * Al colocar el comando anterior, en la consola se pide que especifique la ubicación, en este caso oprima la tecla Enter para que se guarde en la ubicación sugerida. Posteriormente, cuando se pida la ```Passphrase ```coloque una contraseña que pueda recordar o guárdela, ya que se utilizará más adelante.
   * Muévase con el comando 
   ```cd .ssh``` a la carpeta donde están los archivos ```id_rsa.pub``` y ```id_rsa```. Estos archivos contienen las claves públicas y privadas respectivamente.
   * Copie el valor de la clave pública, utilice el comando: 
   ```
   cat id_rsa.pub
   ```
   
4. Una vez obtenida la llave publica en la Lista de recursos, seleccione su servicio de Servidor virtual de Power Systems.
5. Siga la ruta ```SSH keys > Create SSH key```.
6. Ingrese un nombre para la llave y pegue la llave publica creada anteriormente. 


## Crear una subred
Tenga en cuenta los siguientes pasos para crear una subred en el servidor virtual creado anteriormente:
1. En la Lista de recursos, seleccione su servicio de Servidor virtual de Power Systems.
2. Siga la ruta ```Subnets > Create subnet```
3. Esto abrirá una ventana de configuración, aquí ingrese la siguiente información:
  * ```Name```: Ingrese un nombre distintivo para la subred.
  * ```CIDR```: Ingrese el valor exacto de una dirección o un rango de direcciones IP.
4. De click sobre el botón ```Crear```. 

## Crear una Virtual Server instance

Para esto tenga en cuenta los siguientes pasos:
1. En la Lista de recursos, seleccione su servicio de Servidor virtual de Power Systems.
2. Siga la ruta ```Virtual server instances > Create instance```
3. Esto lo llevara a una pestaña de configuración, aquí ingrese la siguiente información:
  * ```Instance name```: Ingrese un nombre distintivo para la instancia.
  * ```Number of instances```: Seleccione el numero de instancias que desee.
  * ```VM pinning```: Seleccione la opción que desee para controlar el movimiento de las VM durante desastres y otros eventos de reinicio.
  * ```SSH key```: Seleccione la llave SSH creada anteriormente.
  * ```Operating system```: Seleccione el sistema operativo que desee.
  * ```Image```: Seleccione la versión de la imagen que desee.
  * ```Tier```: Seleccione el storage tier que necesite según su aplicación.
  * ```Machine Type```: Seleccione el tipo de maquina según su aplicación.
  * ```Core type```: Seleccione el tipo de core que desee.
  * ```Attached storage volumes (optional)```: Cree un volumen de almacenamiento de 20GB en el Tier que selecciono
  * ```Public networks```: Seleccione la opción ```OFF``` para no permitir acceso a la interfaz mediante redes publicas
  * ```Private networks```: De click sobre ```Attach existing``` y seleccione la subred privada creada anteriormente.
4. De click sobre ```Crear```.




## Activar el VRF (Virtual Routing Forwarding) 
Para realizar la conexión entre PowerVS y el Firewall Juniper es importarte activar el VRF. Para solicitar la activación del VRF en la cuenta de IBM Cloud, el administrador debe añadir un caso. Para generar dicha solicitud siga los pasos que se muestran a continuación:

1. Acceda a ```Manage / Administrar``` > ```Account / Cuenta``` y luego haga clic en  ```Account settings / Configuración de la cuenta```. 
2. Busque la sección de ```Virtual Routing and Forwarding```  y de click en ```Create case / Crear caso```.
3. En la descripción del caso, ingrese a ```Category / Categoria```, seleccione ```Account / Cuenta ``` y en subtopic ingrese Other / Otro, por último de click en Next / Siguiente.
4. A continuación en ```Details / Detalles``` ingrese:

* ```Subject```: Enable VRF in the account
* ```Description```: Texto guía -> Please, your help to enable (ON) Virtual Router Forwarding in this account (<Número de cuenta IBM Cloud>). We require to enable VRF to enable connectivity to PowerVS resources. Thanks in advance for your help, let me know if any additional information is required.
*  ```Severity```: Severity 2 - Significant business impact.

Revise que sus configuraciónes hayan quedado correctas y de click en Next / Siguiente.

5. Finalmente de clik en ``` Submit case / Enviar caso```.

La habilitación se verá reflejada en las próximas horas.

<p align="center">
<img width="500" alt="autoscale" src=https://github.com/emeloibmco/PowerVS-Conectividad/blob/main/Imagenes/vrf.gif>
</p>

## Referencias :mag:
* <a href="https://cloud.ibm.com/docs/schematics?topic=schematics-about-schematics">Acerca de IBM Cloud Schematics</a>

<br />

## Autores :black_nib:
Equipo IBM Cloud Tech Sales Colombia.
<br />
