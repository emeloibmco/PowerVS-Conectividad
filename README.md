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
