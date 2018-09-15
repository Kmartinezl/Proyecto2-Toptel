# Proyecto1-Toptel

**GEOLOCATION GPS:**
------------------------------------------------------------------------------------

- Alejandro Velasquez Uribe – avelas61@eafit.edu.co
- Keila Andrea Martínez Lagares – kmartin5@eafit.edu.co

-------------------------------------------------------------------------------------
**Creación de máquinas en Aws:**
1) Se crea una nueva estancia en Amazon EC2 (con las opciones free para no recibir cargos de pago)
2)	Se tiene que crear una Key y asociarla con la estancia.
3)	Descargar la key.pem

--------------------------------------------------------------------------------------
**Conexión a la máquina:**

- **Linux:**
_ssh -i “key.pem” centos@dominio_o_ip_

- **Windows:**
Para conectarnos en Windows necesitamos una consola, la cual puede ser Windows bash o PuTTY.
Para conectarnos por PuTTY tenemos que generar el archivo key con PuTTYgen, luego nos conectamos seleccionando la clave y conectándonos a centos@dominio_o_ip

------------------------------------------------------------------------------------------------
**Requisitos para Centos 7:**
- Docker.
- Nginx.
- Nodejs.
- Mongo
- cerbot-auto.

-----------------------------------------------------------------------------------------------
**Instalación de Docker:**

 source: https://docs.docker.com/install/linux/docker-ce/centos/

  - $ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
  - $ sudo yum install docker-ce
  - $ sudo systemctl start docker
  - $ sudo systemctl enable docker

 instalar docker-compose: https://docs.docker.com/compose/install/

  - $ sudo curl -L https://github.com/docker/compose/releases/download/1.20.1/docker-compose-`uname -s`-`uname -m` -o             /usr/local/bin/docker-compose

  - $ sudo chmod +x /usr/local/bin/docker-compose

------------------------------------------------------------------------------------------------
**Descargar Proyecto:**
  - $ cd /tmp/
  - $ mkdir app
  - $ cd app
  - $ git clone https://github.com/Kmartinezl/Proyecto1-Toptel
  - $ cd Proyecto1-Toptel
 
 ---------------------------------------------------------------------------------------------------
**Creación de contenedores en Docker:**

1. Contenedor de Mongo:

  - $ docker pull mongo
  - $ docker run --name mongo-server -p 27017:27017 -v $(pwd)/data:/data/db -d mongo:latest

2. Contenedor de Nodejs+app:

  - $ cd Proyecto1-Toptel
  - $ docker image build -t <docker_user>/artnode:<version>
  - $ docker image push <docker_user>/artnode:<version>
  - $ docker run --name nodeapp --link mongo-server:mongo -p 3000:3000 -d <docker_user>/artnode:<version>
 
3. Contenedor de Nginx:

 - $ docker pull nginx
 - $ docker run --name webapp --link nodeapp:node -p 80:80 -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro -d nginx:latest

-------------------------------------------------------------------------------------------------
**Atributos de calidad:**
----------------------------------------------------------------------------------------

 **Disponibilidad:**
 
**Analisis:**
  Implementación de un Load balancer con Amazon web service para así asegurar que se repartan de manera correcta las cargas    de nuestro servicio web.
 
   Además de generar una conexión entre el DCA y las estancias de Amazon, para que el DCA soporte nuestra app web, por si se llega el casos en que Amazon llega a caerse. Esto lo hacemos por medio de Docker Swarm.
  
  Control y monitoreo ademas de mucha versatilidad a la hora de desplegar nuevas maquinas usando herramientas brindads por Jenkins

**Balanceador de cargas con AWS:**

  

 **Seguridad:**

  - Generación de un dominio propio (geolocationp2.tk)
  - Generación de certificado ssl válido, por medio de Let's Encrypt, con el fin de garantizar una conexión segura a nuestra     aplicación.

  **Generar certificado:**
 
   - $ apt-get install certbot
   - $ certbot certonly
  
  
  _A continuación debe aparecer en consola el siguiente mensaje:_
  
  ------------------------------------------------------------------------------------
  
   How would you like to authenticate with the ACME CA?
   
  -------------------------------------------------------------------------------
     1: Place files in webroot directory (webroot)
     2: Spin up a temporary webserver (standalone)
   
  -------------------------------------------------------------------------------
   Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 
  
  ---------------------------------------------------------------------------------
  _[Digite "1"]_
  
  ---------------------------------------------------------------------------------------
   Please enter in your domain name(s) (comma and/or space separated)  (Enter 'c'
   to cancel)geolocationp2.tk
   
   Obtaining a new certificate
   
   Performing the following challenges:
   
   http-01 challenge for geolocationp2.tk


   Select the webroot for geolocationp2:
   
  -------------------------------------------------------------------------------
     1: Enter a new webroot
   
  -------------------------------------------------------------------------------
   Press 1 [enter] to confirm the selection (press 'c' to cancel): 1
  
  ------------------------------------------------------------------------------------------------
  _A continuación se debe ingresar la raíz del sitio Web (se supone que el servicio Web ya se encuentra funcionando).          Seleccionar "1" y luego especificar la ruta a la raíz del sitio Web (home/centos/app/Proyecto1-Toptel)_
  
  
   **[Mensaje en consola]**
  
  ---------------------------------------------------------------------------------------------------------
   Input the webroot for geolocationp2.tk: (Enter 'c' to cancel):/var/www/linuxito.com/
   Waiting for verification...
   Cleaning up challenges
   Generating key (2048 bits): /etc/letsencrypt/keys/0003_key-certbot.pem
   Creating CSR: /etc/letsencrypt/csr/0003_csr-certbot.pem


   IMPORTANT NOTES:
   
   
    - Congratulations! Your certificate and chain have been saved at
      /etc/letsencrypt/live/geolocationp2.tk/fullchain.pem.
      
      Your cert will expire on 2018-10-08. To obtain a new or tweaked
      version of this certificate in the future, simply run certbot
      again. To non-interactively renew *all* of your certificates, run
      "certbot renew"
    - If you like Certbot, please consider supporting our work by:

      Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
      Donating to EFF:                    https://eff.org/donate-le
  
  
  _El certificado se ha generado con éxito y ha quedado almacenado en el siguiente directorio:_
  
         etc/letsencrypt/live/geolocationp2.tk/
  
  
 _[Para visualizar la app, ingrese el siguiente dominio en su browser: **geolocationp2.tk**]_ 


