# Documento 1


## 1.  Definición del equipo, proyecto y aplicación

### a. Miembros del equipo y asignaciones de QA

**QA:** Disponibilidad.      **Encargado:** Alejandro Velasquez Uribe
**QA:** Seguridad            **Encargado:** Keila Martínez Lagares

### b. Selección de la aplicación basada en Proyecto 1

Aplicación seleccionada:

Geolocation GPS (Proyecto 1 - Tópicos de telemática)


### c. Descripción de la aplicación

La aplicación consiste en un sistema que permita registrar a un usuario, permitir su acceso a la aplicación, mostrar su ubicación GPS en tiempo real, guardar su posición y generar rutas basadas en estas.

### d. Requisitos Funcionales:

* El sistema debe poder crear usuarios nuevos.
* El sistema debe generar una sesión única a cada usuario.
* El sistema debe permitir almacenar la posición geográfica del usuario en su sesión.
* El sistema debe poder mostrar las posiciones guardadas.
* El sistema debe poder generar una ruta con las posiciones.

## 2. Detalles técnicos del diseño e implementación funcional para el proyecto 2

La aplicación estará distribuida en tres (3) nodos de un cluster generado con
docker swarm, en los cuales solo el principal contará con los servicios de NGNIX y MongoDB

## 3. Aplicación desplegada en el Data Center Académico (DCA)

https://kmartin5.dis.eafit.edu.co

## 4. Definición de Tecnología v1 - Infraestructura TI:

* Servidores: DCA, instancias EC2 micro con Centos 7 en Amazon Web Service (AWS)
* Software Base: NodeJS, MongoDB, JMeter, LetsEncrypt, Auth0, Open VPN, Docker Services, Google Maps API
* Redes: NGINX

## 5. Marco-referencia-v1

### Disponibilidad (confiabilidad y recuperación)

El principal objetivo de este QA es permitir soportar las fallas de tal modo que el servicio ofrecido por dicho sistema continúe siendo compatible con sus especificaciones.

De igual forma implica que una falla se vuelve amenaza cuando esta afecta a los servidores del sistema, de tal modo que las especificaciones del sistema dejan de funcionar.

Estrategias y tácticas:

* **Detección de fallas**
* **Recuperación de fallas**
  * **Reparation and repair**
  * **Reintroducción**
* **Prevención de fallas**

### Rendimiento

### Seguridad
