# Amazon S3 - AWS Elastic Block Store (EBS)

## Indicaciones

1.  Las respuestas deben ser explicadas, solo colocar resultados sin ninguna referencia no puntúa en las preguntas de la evaluación.
    
2.  Realiza una copia de este documento y coloca todas tus respuestas y sube a tu repositorio personal de GitHub en formato Markdown. Presenta capturas de pantalla del procedimiento y las explicaciones necesarias. No puntúa si solo se hace la presentación de imágenes.
    
3.  De preferencia, adiciona un video adicional explicando los pasos realizados. Utiliza el sandbox de AWS usado en la práctica anterior.
    
4.  Sube a la plataforma de Blackboard el enlace de GitHub donde están todas tus respuestas. No olvides colocar tu nombre y apellido antes de subir el enlace de tus respuestas a la plataforma.
    
5.  Cualquier evidencia de copia elimina el examen. Se informará de la situación a la coordinación.

## S3

En este laboratorio, se estudiará el almacenamiento de Amazon S3. Utilizarás los comandos `aws s3` y `s3api` para administrar datos en Amazon S3. Amazon S3 es un almacenamiento de objetos accesible a través de Internet.

### Parte 1: Operaciones básicas con S3

Suponga que su directorio actual es `/home/aws_user` (puedes cambiarlo). Envíe las siguientes instrucciones y responde las preguntas que siguen.

1.  Enumere todos los buckets propiedad del usuario a través del siguiente comando `ls`. `aws s3 ls`

¿Cuál es la salida?

**![](https://lh6.googleusercontent.com/hVqaNKbMvHEN37EZj7p0GONbgvPXB9eSHcLs9OsWItvtphdaLUZcYdQ6Xtuvc7EDUQqg2A9xwivQvCMzyAESisTSDgtyBGoO9DAS_mMJrFugt6Rh0WtFHCAdH07bmG-8j06_t8ixqylDPzfzK9zo9a4)**
No sale nada aun porque no se ha creado el bucket.


2.  Haz un bucket a través del siguiente comando `mb`.

`aws s3 mb s3://tu_nombre_de_usuario`

¿Cuál es la salida?
**![](https://lh6.googleusercontent.com/KpG_S5drB4gJ0zD-TbSC1ujQD7p07OY6RJWO7E9ARWxRbrdUxgAXzhSunsR9di5mBM72eB7f54IZkVlW6MkdRt7FLMxmoe4xFMAIW4VIRZfUBix4m20_QEuDuoBbLAdd2mzhAGc0kAqHBVeV0BtJc4c)**
Mi usuario es rubenrojasramos

3.  Enumera el contenido del bucket a través del siguiente comando `ls`.

`aws s3 ls s3://tu_nombre_de_usuario`

¿Cuál es la salida?
**![](https://lh6.googleusercontent.com/KpG_S5drB4gJ0zD-TbSC1ujQD7p07OY6RJWO7E9ARWxRbrdUxgAXzhSunsR9di5mBM72eB7f54IZkVlW6MkdRt7FLMxmoe4xFMAIW4VIRZfUBix4m20_QEuDuoBbLAdd2mzhAGc0kAqHBVeV0BtJc4c)**
4.  Crea un directorio llamado "páginas web" (`mkdir webpages`) y cambia a ese directorio (`cd webpages`). Crea un archivo HTML simple llamado "hello.html" con el siguiente contenido.

html
bod
h1>Amazon S3</h1
Hello World!
/body
/html
 **![](https://lh5.googleusercontent.com/XStsZkNpX9jQBrTB39EGacDPGAoDoBgOz1-2tyzElAeK0Mm7mRm1h4v1vy9M9hTiG9YaoJYku4noWlhCNC1zRn-zd09sMAkTxgIUy7zbYUW5R1P7Q9Gv_KqSDRucykuSMUrNG-688IZNoJwT0nE4NuY)**
Carga el archivo en tu bucket S3 y hazlo público con el siguiente comando: `aws s3 cp hello.html s3://tu_nombre_de_usuario --acl public-read`

¿Cuál es la salida?

**![](https://lh5.googleusercontent.com/0IY4_IGNyF8LZrxFK1rdpx7yBwbHRx2iRfX_SE-cB5-fU0ep_RWCxr4Z7NOBLykpNqaObrO8rkmlF3IeBsTEX2g10kBkob11MpqZsobmC3owKypM5k_xVPDKtCXQK4oDTGT1UOhYtwX7owiu8sua8cA)**

5.  Dado que se puede acceder a tu objeto S3 a través de Internet, probémoslo. En el navegador web de tu máquina virtual (o cualquier otro navegador), accede a la URL `http://s3.amazonaws.com/tu_nombre_de_usuario/hello.html`. ¿Qué ves en el navegador?
**![](https://lh3.googleusercontent.com/PGsDdThAKsqPB6NnJfSTt568IZX8UKmrQcY1BhRfCX4wMWLT0rJ2ADw1oag90779p57oNN8cRv_fNzY4cTQMPmVRGfQERtXvGQF9UdVd-aMXpvH_xxk8sQhkd7_-BtzwG3K70X27JZJ1Q8qCYiVXMnc)**


### Parte 2: Alojamiento de sitios web estáticos con S3

6.  Podemos usar el bucket como almacenamiento para sitios web estáticos. Experimentemos con eso aquí. Crea dos archivos HTML en el directorio actual llamados "index.html" y "error.html". El contenido de los dos archivos se muestra a continuación.

index.html:
error.html:
**![](https://lh5.googleusercontent.com/WoyAAlvL-iM-quiGXXb0C0gxsJN5pEdd_mudPDaJFQck7mTv83zkd1niGwc1jwIBXX_mNXHIAtqGKUFd11m5r07fWso1JtWKD-U_YHVzZg355HuL8Bl3mgmhf0AFjInJ1LSS0tFPbQgwgHJm1Bmask8)**
7.  Ejecuta el siguiente comando para sincronizar los archivos HTML en tu bucket S3:
    
    `aws s3 sync . s3://tu_nombre_de_usuario --acl public-read`
    
   ¿Cuál es la salida?
**![](https://lh5.googleusercontent.com/bRHCDfesZ9hUsjXX9nlcs8yw_YT_nUD5oItim5S8vwxA7LNC6VjSIRzOsdIW20P8uccG4YUGmUg_dONeteo0N2NK2Vma5cnwGiQYfmchpr5sv9pGGGAH4WEDyLbE28PM4VFfd4bHMXVNHT5qlX0GdQQ)**

    
    
8.  Ahora, vamos a configurar el bucket S3 para que funcione como un sitio web estático. Ejecuta el siguiente comando:
    
    `aws s3 website s3://tu_nombre_de_usuario/ --index-document index.html --error-document error.html`
    
    
9.  Ahora, en tu navegador web, accede a la URL `http://tu_nombre_de_usuario.s3-website-us-east-1.amazonaws.com`. ¿Qué ves en el navegador? 
11.  Podemos definir reglas de redirección y agregar metadatos a los objetos en el bucket utilizando el comando `aws s3api put-object`. Ejecuta el siguiente comando para hacerlo:

`aws s3api put-object --bucket tu_nombre_de_usuario --key hello.html --website-redirect-location http://www.nku.edu/~haow1 --acl public-read --metadata redirection_creator=aws_user` 

**![](https://lh3.googleusercontent.com/NkY-cD0ys1V0FdhzLmIw4ZEvGshuSNTPP7zScX-EkgYUmJCmD4PimOcIcJZy1Fg76oDy7EtUIsSKqrYgDnJOp9pxdsPjTvXJN45b4Ohxo0BVz1rYdAcj4ryb9tw6BiNRbFuPEsAxHnX_9XcD26830H0)**
**![](https://lh5.googleusercontent.com/zf2cye23CCCsocc90B1YRaakHgVpViOEUMweKiaDrxFdm1eDKSOw8xAhmzn-MHNKHdTwgo8xPBkwG-z81Clv3XREjuJp1rToSAl9bjEq8dOJWe9zxCz6GGnKpMYh3sMYKm8c1XM1JoqBg2QW16UpPMU)**
Después de ejecutar este comando, si accedes a la siguiente URL en tu navegador: `http://tu_nombre_de_usuario.s3-website-us-east-1.amazonaws.com/hello.html`, verás que el navegador redirige automáticamente a `http://www.nku.edu/~haow1`. Esto sucede porque hemos configurado una regla de redirección para el objeto `hello.html` en el bucket.
**![](https://lh4.googleusercontent.com/UM9EAjZ_3NnJ1qxBmFFTMtW5O_V4jgjs4vnr3FFGgcudAxAbizyp8mpP0ZthL7AmoyqGbdE4TAaaslVckUrcnpuai7s5ijD-3q7KusEIyg_9bxjRI7r-3xobOONAHku5MG25-X4a6FExLoDsw49UQQE)**
8.  Para recuperar los metadatos de un objeto, podemos usar el subcomando `head-object`. Ejecuta la siguiente instrucción:

`aws s3api head-object --bucket tu_nombre_de_usuario --key hello.html` 

**![](https://lh5.googleusercontent.com/FIAShSHWYaVkFH0KkEYmWOO9bsmOScX0jSn-YvkeikE-xja-rd4h55PJVmgP3wrTaUDG0OByiERpEnBYm3oxKRY5f17Im3gnDpIutf64YYthqZWsAcupzMqxjX22MhglSQJYY8tMAwC1fm_69RlU36o)**
La salida de este comando proporcionará información sobre los metadatos del objeto `hello.html` en el bucket especificado.

### Parte 3: Limpieza

Podemos eliminar objetos usando el comando `rm`. Elimina tu página de índice de la siguiente manera:

`aws s3 rm s3://tu_nombre_de_usuario/index.html` 

Esto eliminará el archivo `index.html` del bucket especificado. 

El comando `aws s3 rb s3://tu_nombre_de_usuario --force` se utiliza para eliminar un bucket de S3 de forma recursiva y forzada. La opción `--force` indica que se deben eliminar todos los objetos dentro del bucket antes de eliminar el bucket en sí. La salida del comando mostrará mensajes indicando si el bucket y los objetos se eliminaron correctamente. Si hay algún error, se mostrará un mensaje de error correspondiente.
**![](https://lh5.googleusercontent.com/5BqKbfbXjg-5aAzHYBvBCHF7tcv38XNlOC2vb4cgeFVYl6Dx_8JFvDgeoJpbUKy8D9kFZj6nw4j45lpYGShShwr7WeyleuD_v1-PE7lfI7kmYzUn_RLwg4GODYRd0V8nx1F8SaYo61WgGz1BpZE6e4I)**
### Parte 1. Crea un nuevo volumen de EBS

1.  El comando `aws ec2 create-volume --size 1 --region us-east-1 --availability-zone us-east-1c` se utiliza para crear un nuevo volumen de Amazon EBS.
**![](https://lh3.googleusercontent.com/Q7RRQVvtSuM1jAy7cdZq6mq89mEIXDfoLvEwb40MTYAbAWZcbBzyjVMxs216qETDryikRhsqa-xc0_EXdYEPv4X0ThmZi3lnZeqEcUGtkRehjyAg8nPzmv8DMsyIUQG2e5m4NE_lM-LrNqLoro2i32k)**
2.  El comando `aws ec2 describe-volume-status --volume-ids volume_id` se utiliza para obtener información sobre el estado de un volumen de EBS específico. Debes reemplazar `volume_id` con el ID del volumen que deseas consultar.

**![](https://lh6.googleusercontent.com/XX7UY42wvl1gCdXo42fV84apVe51YpTQpvNNEHa33lG8XGc1olY8pJtz3EOoBGBrGdUpOC8ZYWVScLbPUVNPEU9T5iVXdrhDd4EQyIAtbOT_YWN-w4LNv9DciUNruPcpSJaIasihtgcgCURlG2zaiic)**

3.  Para crear una instancia de EBS, se utiliza el comando `aws ec2 run-instances` junto con varias opciones para configurar la instancia. Ten en cuenta que algunos valores en el comando, como `ami-d9a98cb0`, `tu_nombre_de_usuario-key`, `tu_nombre_de_usuario`, `us-east-1c`, `volume_id` e `id_instance`, deben reemplazarse con los valores adecuados según tu entorno.
**![](https://lh5.googleusercontent.com/g0b2b48FXqebKZB9nI2Ly3dD9KKSF4V5gScq6Pm6VFzAH1rC7FMGdXP5PGdYCIBOE0EyHn1ApWhrErWfRWOkEorVtNQ_xEa2P1oh9vTxf8VDXMrw5frH5Ovp2Kv_wPA1DCKuVa5Tkic7d-go1CleqS0)**

4.  Ahora, adjunta el volumen de EBS a la instancia. Esto lo colocas en el directorio /dev/sdf en tu instancia EC2.

`aws ec2 attach-volume --volume-id volume_id --instance-id id_instance --device /dev/sdf`

¿Cuál es la salida?
**![](https://lh3.googleusercontent.com/nvFa_sR-Qs0KU_nTFeq8qfiL_Eb3wlAjiYBxv_QuRgxXPbKSoVcbqoERnbSmvO88T8PVrIT1IDrVyUt6nm6kJA7gTUbvvqcZvOoxQhe07EQCLJhJwbxoqJfd-RM3T4FjFHT5bGyJRuthDQdDn_Py9KA)**

 Se utiliza para adjuntar el volumen de EBS creado anteriormente a la instancia de EC2. Aquí, `volume_id` y `id_instance` deben reemplazarse con los IDs correspondientes del volumen y la instancia respectivamente.
La salida de este comando mostrará información sobre la operación de adjuntar el volumen a la instancia.

5. Inicia sesión en la instancia EC2 a través de ssh. En tu instancia EC2, cambie a root. Ahora queremos crear un sistema de archivos en el volumen de EBS (el volumen de EBS es básicamente un dispositivo de almacenamiento en blanco). Luego necesitamos montar el volumen para que sea accesible. Utiliza los siguientes comandos desde tu EC2. Ten en cuenta que, según el controlador del dispositivo de bloque del kernel, el dispositivo puede estar conectado con un nombre diferente al que ha especificado. Por ejemplo, si especificas un nombre de dispositivo de /dev/sdf, el kernel podría cambiar el nombre de tu dispositivo a /dev/xvdf, en la mayoría de los casos, la letra final sigue siendo la misma. Ejecuta lsblk en tu terminal para ver tus dispositivos de disco disponibles y tus puntos de montaje (si corresponde) para ayudarte a determinar el nombre de dispositivo correcto que debe usar. Suponga que el kernel cambia el nombre del dispositivo a /dev/xvdf.

¿Cuál es la salida?

La salida del comando `mkfs -F /dev/xvdf` será el resultado del formateo del dispositivo `/dev/xvdf` con un sistema de archivos. No proporcionas el sistema de archivos específico en tu pregunta, por lo que la salida mostrará detalles sobre el sistema de archivos creado.

La salida del comando `df` mostrará información sobre el sistema de archivos montado en el directorio `/data`. Mostrará el tamaño total, el espacio utilizado y el espacio disponible para el sistema de archivos montado.

### Parte 2. Instantáneas de EBS

5. Crea un archivo llamado aws_user.txt y escribe lo que desees en el archivo. Ahora, veremos cómo crear una copia de seguridad de todo tu volumen de EBS. El primer paso es asegurarte de que todos los datos en memoria se hayan escrito en el volumen (disco), ya que es posible que el archivo creado aún no se haya guardado en el disco. Para forzar que esto suceda, usamos el comando sync (sincronización). En la ventana de tu terminal para su instancia EC2, ejecuta las siguientes instrucciones.

root@ip-10-45-185-154:/data# sync

Abre una segunda ventana de terminal en tu máquina virtual. Emite el siguiente comando.

aws ec2 create-snapshot --volume-id volume_id

--description "Esta es mi instantánea de volumen".
**![](https://lh6.googleusercontent.com/zOwAJv88Z8AFGQU1UuwNOg_Gtn_kfQe3T_Zu_zZx7_rpCTFLrxXb83Wk-vrnORK4FiDVHK2denf5_72EzSffnPuT9x2CpdpUhlDM1_x1KaQYwsD5afKhx1XR0wyrSdPqABfrimEEo7_FCG2LH2et9vo)**
donde volume_id es el id obtenido del paso 1. ¿Cuál es el resultado? Puedes verificar el estado de tu instantánea usando las siguientes instrucciones.

aws ec2 describe-snapshots --snapshot-id snapshot_id
**![](https://lh6.googleusercontent.com/NJMRy_VoeNf6evo0FR6ehNiA0k1OvKKZGqig8rW-EmzSgFgksNLlfNYmGPErmGCsp2o5_BZr5_xl-2VUe3nNSxXPeAwbJ6AqbmOeDFHL-jS3wvFnsfSVW-GF9zUvpGagFstjlr-ffb6OzvDO_6PvSX0)**

El snapshot_id debe ser parte de la salida de la instrucción de creación de instantáneas que acaba de ejecutar. ¿Cuál es el resultado del comando describe-snapshot? Continúa repitiendo este comando hasta que vea que el estado de la instantánea cambia a "completado", lo que significa que se ha realizado una copia de seguridad del volumen.

El resultado del comando `aws ec2 create-snapshot --volume-id volume_id --description "Esta es mi instantánea de volumen"` será la creación de una instantánea del volumen de EBS especificado. El comando retornará información sobre la instantánea recién creada, incluyendo su ID.

Para verificar el estado de la instantánea, puedes ejecutar el comando `aws ec2 describe-snapshots --snapshot-id snapshot_id`, donde `snapshot_id` debe ser reemplazado por el ID de la instantánea que obtuviste en el paso anterior. La salida de este comando proporcionará detalles sobre la instantánea, incluyendo su estado actual.

Es posible que inicialmente el estado de la instantánea sea "pending" (pendiente), lo que indica que la creación de la instantánea está en progreso. Puedes repetir el comando `describe-snapshots` varias veces hasta que el estado cambie a "completed" (completado), lo que significa que la copia de seguridad del volumen ha sido realizada exitosamente.

6. Dada una instantánea, podemos usarla para crear un nuevo volumen. Ejecuta el siguiente comando. Utiliza el ID de instantánea del paso 5.

`aws ec2 create-volume --region us-east-1 --availability-zone us-east-1c --snapshot-id snapshot_id` 
**![](https://lh5.googleusercontent.com/1aBxax8b-vLU8zB6WvxbpAW88w7KGC67K5lWiOH48T5S4YpLZKgci8h1_OGqZp6ihX09-jc-sDbp91Nm9ElH1SiwEeEr7-M9m38gtxzpYErgxdXLTSlZ2-bHyb8gbcyyeva7QSUvm4CPttt8FhhFcqE)**

¿Cuál es la salida? Comprueba el estado del volumen. ¿Qué comando ejecutaste para verificar el estado? ¿Cuál es la salida?

`aws ec2 describe-volumes --volume-ids volume_id` 

![](https://lh3.googleusercontent.com/4Wlgs5EjvVeUw0stZ0j0yhTxRH9KVBA1TL5SLPfRTKZiTm_PNKNntzB6cphT_gByE3hzpfBA57DoZmHu9O4nPqMdmq4lz7tJ6XCMAhrRjDhnzO7rqVK4prhq91qYRXTW3XHpo6YypL4nTrWdzfYRj34)**

7. Repite el comando de adjuntar volumen del paso 3 para adjuntar este nuevo volumen. El ID de volumen será el que se devolvió al obtener el estado 6, mientras que el ID de instancia es el de tu instancia EC2 que obtuvo en el paso 3.


`aws ec2 attach-volume --volume-id volume_id --instance-id instance_id --device /dev/sdg` 

**![](https://lh3.googleusercontent.com/Rp4BYi9Ka6bD4zBWfVGmRWN5MJ33Nu3iZsaSc5RG5BzsRxsmmPLVhXFUKUUSmrv0oPXe_paLKdAJ7zVAAWAO8F5tzB3efm5HfoWjQDr80xic02etEihrkSJM_qxws9JdVKAnXyr3gVALMAJkoU27n_0)**
8. Vuelve a la ventana de la terminal en la que se tiene ssh en tu instancia EC2. Desde ese terminal, crea un punto de montaje llamado /data2 y monte el nuevo volumen allí. ¿Qué comandos se ejecutó para lograr ambas tareas? Cambia el directorio de su instancia EC2 a /data2. Viste el archivo aws_user.txt

cat aws_user.txt


10. Ahora queremos desmontar nuestros volúmenes, para lo cual usamos el comando umount. Luego separaremos los volúmenes de la instancia EC2 y los destruiremos. Los siguientes son los comandos a ejecutar. Ten en cuenta que los primeros tres comandos están en su instancia EC2 y el resto está en tu VM.

root@ip-10-45-185-154:/data3# cd /

root@ip-10-45-185-154:/# unmount /dev/xvdf

root@ip-10-45-185-154:/# unmount /dev/xvdg

Ahora desconecta y elimina el primer volumen, cuyo volume_id obtuvo en el paso 1. Espera unos 10 segundos después de desconectar antes de intentar eliminar.

aws ec2 detach-volume --volume-id volume_id 
aws ec2 delete-volume --volume-id volume_id`
**![](https://lh4.googleusercontent.com/0wRFxNy9V48ZpzV4e30_HI0cMXYNNgZC0S56BNmgGupO3Emt369BkpNwc8UG0eeiZYx7ut_qT-WrzLko4KT9naHBC8dFi_F14Yi2G2LmEj8TXOJzlR26wow5wVipfiq4wOdewR-BfFlX5V92CkUSA3c)**
10. Elimina la instantánea con lo siguiente usando su snapshot_id del paso 5. 
aws ec2 delete-snapshot --snapshot-id snapshot_id.}

![](https://lh4.googleusercontent.com/QvJWTGiO5aNPzA2bZ9a5-qCAI6FuQaGayvUAgG33Un__QAm8HhQsSuh4mv-YVS9IFcLYP6cLwwZsZN5aCVCX5NdGz_nji-ExHXliUC6qLsgpoZRlIBO_v1TLTVZ1ywyrr1WzjosNePb4PuE1eDOYwao)**
12. Cambie a la terminal. De lo que aprendiste en la parte 1, crea dos volúmenes de 1 GB en la zona de disponibilidad us-east-1c. ¿Qué comandos ejecutaste? ¿Cuáles son las salidas? Adjunta ambos volúmenes a tu instancia EC2, haciendo que aparezcan como /dev/sdh1 y /dev/sdh2, respectivamente. ¿Qué comandos ejecutaste? ¿Cuáles son las salidas?

`aws ec2 create-volume --region us-east-1 --availability-zone us-east-1c --size 1` 

La salida de cada comando será información sobre los volúmenes creados, incluyendo sus IDs.

Luego, para adjuntar los volúmenes a tu instancia EC2 y asignarles los nombres de dispositivo `/dev/sdh1` y `/dev/sdh2`, respectivamente, puedes ejecutar los siguientes comandos:

`aws ec2 attach-volume --volume-id volume_id1 --instance-id instance_id --device /dev/sdh1
aws ec2 attach-volume --volume-id volume_id2 --instance-id instance_id --device /dev/sdh2` 

12. Cambia al terminal de la instancia EC2. Usaremos el programa mdadm de Linux para configurar los volúmenes en una configuración RAID. Instala mdadm de la siguiente manera.

apt-get update
Cambia al terminal de la instancia EC2. Usaremos el programa mdadm de Linux para configurar los volúmenes en una configuración RAID. Instala mdadm de la siguiente manera.

apt-get update
apt-get install mdadm

Escribe "y" y presiona enter cuando se te solicite, seleccione "No configuration" cuando se te solicite y presiona enter. Ahora ejecutamos mdadm para crear un arreglo RAID 0 en los dos volúmenes. Ejecuta lo siguiente. Donde vea "renamed_/dev/sdh1" y "renamed_/dev/shd2", usa los nombres que se te proporcionó AWS en el paso 11.

mdadm --create /dev/md0 --level 0 --metadata=1.1

--raid-devices 2 renamed_/dev/sdh1 renamed_/dev/sdh2

¿Cuál es la salida?

sudo mdadm --create /dev/md0 --level 0 --metadata=1.1 --raid-devices 2 /dev/sdh1 /dev/sdh2


13. Ahora, podemos comprobar el estado de la matriz RAID 0. Emite lo siguiente. mdadm --detail /dev/md0

¿Cuál es la salida? Tenemos que agregar un sistema de archivos al arreglo RAID 0. Entonces queremos montarlo. Haz lo siguiente.

mkfs /dev/md0

mkdir /data3

mount /dev/md0 /data3

El comando df de Linux muestra información sobre los sistemas de archivos montados. ¿Cuál es la salida?

Luego, para agregar un sistema de archivos al arreglo RAID 0 y montarlo en el directorio `/data3`, ejecuta los siguientes comandos:

`sudo mkfs /dev/md0
sudo mkdir /data3
sudo mount /dev/md0 /data3`

14.  Para detener el arreglo RAID 0, separar y eliminar ambos volúmenes de EBS, puedes ejecutar los siguientes comandos:

`cd /
sudo umount /dev/md0
sudo mdadm --stop /dev/md0`

14. Finalizamos este laboratorio deteniendo el arreglo RAID 0, separando y eliminando ambos volúmenes de EBS y luego finalizando la instancia EC2. Para detener el arreglo RAID 0, haz lo siguiente desde su instancia EC2.

cd /

unmount /dev/md0

mdadm --stop /dev/md0

Para detener el arreglo RAID 0, separar y eliminar ambos volúmenes de EBS, puedes ejecutar los siguientes comandos:

`cd /
sudo umount /dev/md0
sudo mdadm --stop /dev/md0`

Ahora, cambia a tu terminal. Separa y elimina ambos volúmenes de EBS. ¿Qué comandos ejecutaste? ¿Cuáles son las salidas? Finaliza tu instancia EC2. ¿Qué comando ejecutaste? ¿Cuál es la salida?

aws ec2 detach-volume --volume-id volume_id1
aws ec2 delete-volume --volume-id volume_id1
aws ec2 detach-volume --volume-id volume_id2
aws ec2 delete-volume --volume-id volume_id2
**![](https://lh5.googleusercontent.com/UuI0x1k9RpkTZeksoCXKvyob-EMG44_gizeqUHFXe5pz2BpyF-4tmqn7jlT6NNERP9xQgXJNG5Hpu86U-eXkGLW3krrtaLAZSu-eRVHXBjOFatKEhOMD1aabtzp3TCU17j4-c6ZxKzz5_wTCjGWoPDE)**
Estos comandos detendrán el arreglo RAID 0 y lo separarán. Luego, puedes utilizar los comandos de AWS CLI para separar y eliminar ambos volúmenes de EBS. Reemplaza `volume_id1` y `volume_id2` con los IDs de los volúmenes correspondientes:


`aws ec2 detach-volume --volume-id volume_id1
aws ec2 delete-volume --volume-id volume_id1
aws ec2 detach-volume --volume-id volume_id2
aws ec2 delete-volume --volume-id volume_id2` 

Finalmente, para finalizar tu instancia EC2, ejecuta el siguiente comando:

`aws ec2 terminate-instances --instance-ids instance_id`

**![](https://lh5.googleusercontent.com/0jjJNOZJCpJJOCFM8KoQ5kpHpsWLI2OLMenJow2mhXAk1r8UJ8G1ReG-yiPIlG8QtC4emgsin2F2aOJq8tdjypG7OPTufUGy9R08JTqFbCLXK-pkXKcMbleS1V0pwcOi8PbJ5ghqabQnfm2vWkSsKLc)**
