# V2parcial2_2do50

---1 RabbitMQ
● Explique qué es RabbitMQ y cuándo se debe utilizar una cola frente a un
exchange tipo fanout.
 RabbitMQ se puede entender como un sistema de gestion de colas de mensajes , para sistemas distribuidos
 dentro de RabbitMQ tenemos un exchange como un componente que recibe mensaje de productoes, donde uno de los tipos de exchange que exite es el fanout, como tal fanout tiene caracteristicas  especiales como enrutamiento de mensajes de las colas asociadas a este sin importar la ruta(routing) o clave(key) del mensaje.

● ¿Qué es una Dead Letter Queue (DLQ) y cómo se configura en RabbitMQ?

UN DLQ se entiende como la cola que almacena mensajes  que no pudieron ser procesados dentro del segmento de procesamiento de mensajes de un sistema, donde dichas colas  permiten guardar mensajes  que no se pueden entregar por uno que otro error ademas de que puedan presentar un escenario donde e la cola de destino esta llena.
para la configuracion dentro de rabbitMQ se crea un exhcange y se vincula a una cola principal, despues se puede especificar dentro de los argumentos de la cola que los mensajes se enruten a DLQ.


● Diferencia entre un volumen y un bind mount con ejemplos.

Un volumen se entiende como una forma de compartir datos  dentro de Docker con la maquina,un volumen ofrece mas flexibilidad dado que funcionan como directorios de archivos y pueden almacenar datos persistentes , ejemplos de los mismos pueden ser archivos con datos persistentes compartidos entre aplicaciones en un formato correspondiente.

Un bind por otro lado se entiende como la forma de enlace de informacion en un esquema de archivos a un sistema host y que tienen una ubicacion especifica, este tipo de archivos permiten permiten una persistencia de mas archivos, pero requiere permisos para evitar conflictos dentro de una aplicacion, ejemplo de estos son los archivos que permiten compartir datos cuando se el contenedor se reinicia o elimina.

●Función de Traefik en una arquitectura de microservicios.

Traefik nos sirve dentro de una arquitectura de microservicios como una especie de puente , ya que permite la relación entre los mismos, como tal es un proxy inverso o en su definicion un balanceador de carga  para facilitar el enrutamiento y trafico a los diferentes  microservicios que pueda tener una app.

● ¿Cómo se puede asegurar un endpoint usando certificados TLS automáticos
en Traefik?

Para asegurar un endpoint utilizando certificados TLS automáticos en Traefik, es necesario configurar Traefik para utilizar un solucionador de certificados (como Let's Encrypt), asociar este solucionador a un enrutador y, finalmente, configurar la TLS para ese enrutador. se siguen como tal se siguen varios pasos como la configuracion de un solucionador de certificados, confirguracion de enrutador, habilitacion de TLS y posteriormente la ejecución de pruebas de accesp al endpoint dado


----------paso a paso del codigo
EL desarrollo del codigo se enmarca desde aqui: 
la estructura que se maneja dle projecto es la siguiente : 

jhona@jhona:~/Descargas/microservices_project$ tree
.
├── api
│   ├── Dockerfile
│   └── main.py
├── docker-compose.yml
├── traefik
│   └── traefik.yml
└── worker
    ├── Dockerfile
    └── worker.py

para correr inicialmente dirigete a V2parcial2_2do50/microservices_project

ejecuta el comando docker compose up -d --build

accesos a API  Y RABBITMQ desde : 
API: http://localhost/api/docs

RabbitMQ: http://localhost/monitor
http://localhost:15672/#/


●implementación del docker- compose con servicios :  api,worker,rabbitmq,traefik ver imagenes en carpeta /evidences : "2.1_1" ;"2.1_2";"2.1_3";"2.1_4" y "2.1_5"

●implementacipn de api productora de mensajes endpoint  POST/message ver imagenes en carpeta /evidences -->"2.2"
●creación del worker consumidor ver imagenes en carpetta /evidences -->"2.3"


●Configuracion de traefik ,ver imagenes en carpeta /evidences -->"2.4"

●Extra bonus,ver imagenes en carpeta /evidences -->"2.5"
