# Proyecto1-Toptel
Aplicación Geolocalización:
 Alejandro Velasquez Uribe –  avelas61@eafit.edu.co
 Keila Andrea Martines Lagares -kmartin5@eafit.edu.co
Creación de máquinas en Aws:
1)	Se crea una nueva estancia en Amazon EC2 (con las opciones free para no recibir cargos de pago)
2)	Se tiene que crear una Key y asociarla con la estancia.
3)	Descargar la key.pem
4)	Para conectarnos en Linux ejecutamos el siguiente comando:
Ssh -i “tu_key.pem” centos @<dominio o ip>
Para conectarnos en Windows necesitamos una consola, la cual puede ser Windows bash o Putty.
Para conectarnos por putty tenemos que generar el archivo key con puttyGen, y cuando la tengamos nos conectamos seleccionando la clave y conectándonos a centos @<dominio o ip>
Requisitos para Centos 7:
Instalar Docker.
Instalar Nginx.
Instalar Node.
Instalar cerbot-auto.

Atributos de calidad:
Disponibilidad:
Bueno, a la hora de la disponibilidad vamos a hacer un Load balancer con Amazon web service para así asegurar que se repartan de manera correcta las cargas de nuestro servicio web
 
Además de generar una conexión entre el DCA y las estancias de amazon, por si en un caso exagerado y casi imposible amazon se caiga, que el DCA soporte nuestra maquina
Esto se está logrando por medio de Docker Swarm
 

Seguridad
Generación de certificados ssl válidos para asegurar una conexión segura a la aplicación, mediante let’sencrypt con el software cerbot.




