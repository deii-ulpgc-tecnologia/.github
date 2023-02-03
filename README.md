# **La guía del desarrollador web galáctico 🚀**

Bienvenidos a la guía definitiva de la DEII para entender de una vez por todas el mapa general del desarrollo web. Pero no cualquier desarrollo web, sino el desarrollo web **GALÁCTICO.**

Pero tranquilo astronauta, sabemos que no quieres marearte en tu primer viaje a si que no vamos a ir, como dice fonsi, des pa cito.

el único objetivo de esta guía es que cuando la termines tengas un mapa en la cabeza de como funciona el desarrollo web y puedas comenzar a trabajar.

# Índice

1. [Infraestructura: El mapa](#infraestructura-el-mapa)
2. [Diseño: Cómo crear experiencias únicas](#diseño-cómo-crear-experiencias-únicas)
3. [Frontend: Convertir una experiencia única en una aplicación real](#frontend-de-un-diseño-único-a-código-escalable)
4. [Backend: Dónde ocurre la magia](#backend-dónde-ocurre-la-magia)
5. [Sistemas: Linux uwu](#sistemas-linux-uwu)

<br>

# Infraestructura: El mapa

Buenas aspirante. Antes de poder embarcarte en tu viaje a través de la galaxia para 
convertirte en el desarrollador web definitivo vas a tener que familiarizarte con los
protocolos de seguridad de la nave ¿No pensarías que puedes subirte a una nave espacial
sin tener ni pajorera idea, no?

A continuación vamos a atravesar una nebulosa conceptual que describe el desarrollo web
desde el comienzo a hasta las técnicas modernas y que se utilizarán para desarrollar la página web de la delegación.


## El modelo cliente/servidor 
<br>

La forma más básica de realizar cualquier tipo de comunicación en internet es 
siguiendo el modelo cliente/servidor. En primer lugar, el **cliente** realiza una
petición y, posteriormente, el **servidor** le responde.

```
Cliente               Servidor
   |     Solicitud       |
   | ----------------->  |
   |                     |
   |     Respuesta       |
   | <-----------------  |
```

El punto a recordar es que la interacción siempre la inicia el cliente mientras que
el servidor espera pacientemente una solicitud.

## HTTP

Ahora que hemos hablado de la principal forma en que dos máquinas se envían mensajes 
deberíamos hablar del formato de estos.


El protocolo [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) es, 
de forma muy reducida, el formato con el que se envían todos los mensajes a través de
internet. Ejemplos del uso de HTTP son envíar un formulario de inicio de sesión o el código fuente de una página web (HTML, del que hablaremos más adelante).

Un mensaje HTTP está formado por dos partes.
- **La cabecera del mensaje** contiene metadatos como el 
[tipo de mensaje](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods)
 o el formato de los datos enviados (JSON, CSV, HTML, etc).
- **La carga del mensaje**, o payload, son los datos que se quieren envíar. No todos 
los mensajes HTTP requieren de este campo de forma que es opcional.

Es importante mencionar que el protocolo HTTP sigue el modelo cliente/servidor de
forma que todas las comunicaciones comienzan con una solicitud, HTTP Request, (Por 
ejemplo: GET, que se utiliza para solicitar infomación o PUT, que se suele utilizar 
para actualizar información) y terminan con una respuesta, HTTP Response, que 
contiene un código numérico indicando éxito o, en caso de fallo, la razón del error. 

Tanto la solicitud como la respuesta podrían incluir un payload, por ejemplo:
- La solicitud podría contener la información de inicio de sesión.
- La respuesta podría contener la información del usuario que ha iniciado sesión.

## La página web tradicional

En un principio, las páginas web eran [estáticas](https://en.wikipedia.org/wiki/Static_web_page). 
El cliente, en este caso un navegador web, solicitaba al servidor una página web y 
este responde con el código que representa la página (HTML) que el navegador puede 
utilizar para generar la vista que finalmente se entiende por la página. 

Se les llama estáticas porque el código HTML se aloja en el servidor de la misma
forma en la que se va a envíar al usuario y todos los clientes reciben la exacta 
misma copia.

```
Cliente               Servidor
Firefox                Google
   |     Solicitud       |
   | ----------------->  |
   |                     |
   |     Página web      |
   | <-----------------  |
```

Ahí se quedaba la cosa, nada de aplicaciones en tiempo real como WhatsApp Web.

## Páginas webs dinámicas: Renderización

Con el tiempo surgió la necesidad de personalizar las páginas webs en función del 
cliente para mostrar, por ejemplo, la lista de la compra de un usuario en particular.
Para conseguir este objetivo el código HTML se escribe de forma genérica 
(Con variables, bucles, condicionales, etc.) y, posteriormente, se transforma en una 
página estática a partir de los datos correspondientes (Como el usuario o el catálogo de una tienda).

Algunas de las tecnologías que permiten seguir este modelo son 
[JavaServer Pages](https://en.wikipedia.org/wiki/Jakarta_Server_Pages), 
[PHP](https://en.wikipedia.org/wiki/PHP), 
[Angular](https://angular.io/) 
y, la que nosotros utilizaremos, [Next](https://nextjs.org/).

A este proceso se le conoce como renderizado, en el contexto del desarrollo web, y existen
varias formas de realizarlo:

### Server Side Rendering (SSR)

El proceso de renderización se lleva a cabo en el servidor. Bastante sencillo, ¿No?

```
Cliente               Servidor
   |     Solicitud       |
   | ----------------->  |
   |                     |
   |               Renderización
   |                     |
   |     Página web      |
   | <-----------------  |
```

Después de recibir la solicitud el servidor transforma el HTML genérico en uno 
personalizado para el cliente en cuestión y, una vez completado el proceso, devuelve
la página estática. Ejemplos de SSR son JavaServer Pages y PHP.

**Ventajas**:
- El cliente recibe todo el HTML generado lo que facilita un mejor ranking en la 
página de búsquedas de google ([SEO](https://en.wikipedia.org/wiki/Search_engine_optimization)). 
Y esto no es poca cosa.

**Desventajas**: 
- La carga computacional de renderización puede saturar al o los servidores.
- Hace falta refrescar la página cada vez que se desea actualizar el contenido. Las 
solicitudes recurrentes saturan a la red y los servidores, más aún si el HTML generado
es extenso.

### Client Side Rendering (CSR)

Bueno pues lo mismo pero al revés, ¿No? Ciertamente la idea es la misma aunque no es 
tan trivial darle la vuelta, al fin y al cabo, ¿Como puede el cliente renderizar una 
página web que no conoce? 

La respuesta a esto es [Javascript](https://en.wikipedia.org/wiki/JavaScript): En 
lugar de responder con un archivo HTML el servidor devolverá código javascript capaz
de construir la página por sí mismo.

```
   Cliente               Servidor
      |     Solicitud       |
      | ----------------->  |
      |     JavaScript      |
      | <-----------------  |
      |                     |
Renderización               |
      |                     |
```

Un ejemplo de CSR es Angular.

**Ventajas**:
- Permite actualizar el contenido de la página sin necesidad de refrescar. Esto lo 
conviene en la opción idónea para aplicaciones altamente interactivas, imagina que 
tuvieras que refrescar la página para ver cada mensaje que te llega nuevo a Whatsapp 
Web.
- Libera carga del servidor.

**Desventajas**:
- Tiene muy mal [SEO](https://en.wikipedia.org/wiki/Search_engine_optimization) 
puesto que el HTML está vacío en un principio lo que le dificulta a google posicionar
tu página.

### Hybrid Rendering 

Como el nombre indica, consiste en hacer las dos cosas a la vez. Una parte de la 
página se renderizará en el servidor y otra en el cliente.

```
   Cliente               Servidor
      |     Solicitud       |
      | ----------------->  |
      |                     |
      |               Renderización 
      |                     |
      |  HTML y JavaScript  |
      | <-----------------  |
      |                     |
Renderización               |
      |                     |
```

Este acercamiento nos permite escoger a voluntad, para cada caso, la solución que 
mejor se adapte. Por ejemplo la gran parte de la página es poco interactiva y su 
contenido no cambia a menudo de forma que la renderizamos en el servidor, sin embargo,
la aplicación tiene un chat de atención al cliente, esta parte que es altamente 
interactiva la renderizamos en el cliente.

De esta forma obtenemos un mejor [SEO](https://en.wikipedia.org/wiki/Search_engine_optimization) 
sin la necesidad de sacrificar toda interactividad.

## El verdadero mapa

He de admitir que hasta ahora he estado mintiendo, bueno más bien he ocultado parte 
de la verdad. Por la imagen que se ha pintado hasta el momento parece que hay dos 
agentes que interactuan: el cliente y el servidor, sin embargo, en realidad son cinco agentes
los interactuan en una página web moderna.


### 1. El cliente
Este sigue siendo el navegador web del usuario que quiere acceder a la página. Nada ha
cambiado.
<br>


### 2. El servidor de frontend
Frontend de aquí en adelante, es el servidor que hemos estado viendo hasta ahora. Se encarga de devolver el HTML (SSR) o el javascript (CSR) al cliente cuando este se conecta por primera vez
a la página web.
<br>


### 3. El servidor de backend
Backend de aquí en adelante, es el servidor que hemos estado ocultando hasta ahora. 
En pocas palabras es el encargado de generar el contenido de la página web. 
Abstrae la lógica de negocio haciendo de interfaz entre la base de datos y el 
frontend. El frontend (SSR) o el cliente (CSR) se comunican con este servidor para
obtener la infomación necesaria para renderizar la página.
<br>


### 4. Base de datos 
Se trata de una máquina que ejecuta un [DBMS](https://en.wikipedia.org/wiki/Database#Database_management_system) y a la cual solo se debería poder acceder 
a través del backend por motivos de seguridad.
<br>

### 5. Servidor de imágenes
Se trata de un servidor de archivos estáticos. Aunque en realidad este tipo de 
servidores se pueden utilizar para almacenar cualquier tipo de archivo lo normal 
es utilizarlos para almacenar las imágenes a las que la página web hace referencia
a través de URLs.
<br>

----

A continuación se muestran los **verdaderos diagramas de los diferentes modelos de 
desarrollo web**. Se utiliza como ejemplo un cliente cualquiera y el servidor la delegación. Los contenedores representan las máquinas físicas mientras que los 
componentes dentro de estas representan procesos. 

### SSR 

![SSR Diagram](./assets/ssr-diagram.png)

### CSR 
![CSR Diagram](./assets/csr-diagram.png)

Los pasos 3. y 7. pueden llevarse a cabo multiples veces
a medida que haga falta actualizar información.

### Hybrid Rendering 
![Hybrid Diagram](./assets/hybrid-diagram.png)

Los pasos 10. y 11. pueden llevarse a cabo multiples veces
a medida que haga falta actualizar información.

----
Para desarrollar la página web utilizaremos **Next**, que implementa el modelo de 
Hybrid Rendering de modo que nuestro *setup* final corresponderá con el último 
diagrama.

# Diseño: Cómo crear experiencias únicas

figma

# Frontend: De un diseño único a código escalable

lenguajes:

framework: coje tu código y lo transforma en javascript, html y css tradicional. encambio la libreria la llamas

html: etiquetas, es un arbol se llama DOM. 
css: define estilos para esas etiquetas.
javascript: introducción, paradigma funcional es6, (!yuju existen clases pero no son objetos! prototype), parece concurrente pero es single threaded surprise motherfucker (event loop). 

nosotros usaremos next implementa react como librería.

# Backend: Dónde ocurre la magia

python: 
https:
lenguaje: de verdad herencia (!puto self) y programacion funcional (lambdas) en armonia perfecta, si lo necesitas metes c++
postgres
ORM

# Sistemas: Linux uwu

Vaya o eres muy curioso/a o definitivamente eres el pibe de sistemas. 

Bienvenidos al corazon de la máquina. El explorador espacial definitivo es capaz de
reparar los motores y asegurarse de que todo está bien engrasado. 

A continuación se describen las principales tecnologías que se utilizarán para 
facilitar el desarrollo y despliegue de este proyecto.

## Docker

[Docker](https://www.geeksforgeeks.org/containerization-using-docker/) es la columna
vertebral de toda nuestra infraestructura. Cada uno de los servidores que tenemos 
que poner a disposición del público se creará en un contenedor de docker distinto. 
Y tú te preguntarás: ¿Qué es un contenedor de docker? 

En pocas palabras, se trata de una máquina virtual muy eficiente que solo debe 
ejecutar un único proceso. Dispondremos entonces de tantos contenedores como 
servicios queremos desplegar, ejecutanto cada uno de ellos el servicio en cuestión.

### Imágenes

Una imagen de docker es, muy burdamente, una ISO que quemas en un pen para 
instalar un OS. Para ser más específicos se trata de un archivo compuesto por 
distintas capas que todas juntas cumplen con los requisitos necesarios para ejecutar
un cierto programa.

Una imagen de docker sirve para crear contenedores. Estos se instanciarán y 
ejecutarán el programa especificado en su imagen. Una imagen puede estar relacionada
con muchos contenedores pero un contenedor solo está relacionado con una imagen.

Las capas que componen una imagen se especifican en el proceso de creación.


### El Dockerfile

Este fichero describe como crear una imagen. Consiste en una secuencia de [órdenes 
de docker](https://docs.docker.com/engine/reference/builder/). Algunos comandos
específicos crean capas dentro del fichero de la imagen, por ejemplo: RUN, COPY y 
ADD. La estructura por capas reduce el tiempo de reconstrucción en la imagen puesto 
que solo hay volver a construir la capa que se quiere cambiar y las que estén por 
encima.

Para aprender más sobre docker usa este [enlace](https://docs.docker.com/get-started/).

### Desarrollo y Producción

Pero, ¿cómo encaja docker en nuestro proyecto? Docker tiene dos funciones principales.

En primer lugar, se encargará de proporcionar un entorno de desarrollo homogéneo para
todos los participantes. De esta manera se establece un entorno estándar que soluciona
problemas de compatibilidad de versiones entre las herramientas que utilicemos. Este 
*setup* permitirá, además, abstraer la complejidad del entorno de desarrollo al resto 
de colaboradores teniendo que ejecutar un único comando para tener todo listo y 
funcionando.

En segundo lugar, compondrá la infraestura de producción. ¿Que significa producción?
Simplemente es el término que se utiliza para referirnos a la aplicación desplegada 
y lista para el cliente final. En esta etapa docker nos permitirá aislar todos los 
servicios necesarios para desplegar la aplicación. La virtualización nos permite 
hacer mejor uso de los recursos del servidor de la delegación. El aislamiento nos 
ofrece seguridad adicional, en caso de que una de las aplicaciones 
fueran vulneradas el atacante solo tendría acceso al contenedor. 

A continuación se vuelve a mostrar el diagrama visto en [Infraestructura: El mapa](#infraestructura-el-mapa) para el modelo de *Hybrid Rendering*.

![hybrid-rendering](./assets/hybrid-diagram.png)

En producción cada uno de los componentes pertenecientes a DEII Server será un 
contenedor de docker.

### Dockerhub

[Dockerhub](https://hub.docker.com/) es un servicio que docker pone a disposición de 
sus usuarios para almacenar y compartir imágenes de docker. Lo utilizaremos para 
almacenar tanto las imágenes de desarrollo como producción de forma que sean 
fácilmente accesibles y los colaboradores no tengan que construir sus imágenes.

Para aprender más sobre dockerhub puedes visitar la guía oficial 
[aquí](https://docs.docker.com/docker-hub/)

----

## Servicios

En este punto hablaremos sobre los programas concretos que utilizaremos para 
desplegar la infraestructura tanto en desarrollo como en producción. En este momento
aún no se ha decidido que aplicación se utilizará para el Image Server así que no se 
contempla.

### Frontend

En el entorno de desarrollo usaremos el servidor de desarrollo de Next que permite
editar el código fuente y ver los cambios en tiempo real sin necesidad de compilar.

En producción utilizaremos [nginx](https://www.nginx.com/) como servidor web. Un 
servidor web es un programa capaz servir el HTML y JavaScript al cliente cuando un 
cliente realiza un HTTP Request.

### Backend

En el entorno de desarrollo usaremos el servidor de desarrollo de 
[Django](https://www.djangoproject.com/) que permite editar el código fuente y ver 
los cambios en tiempo real sin necesidad de compilar.

En producción utilizaremos alguna de las opciones disponibles para desplegar Django.
En principio nos quedará un contenedor capaz de responder a las solicitudes 
necesarias para que la página web funcione (Carga de noticias, dudas frequentes, etc.).

### Data Base

Para la base de datos utilizaremos el [contenedor oficial](https://hub.docker.com/_/postgres) 
de [PostGres](https://www.postgresql.org/) tanto en desarrollo como en producción.
Por supuesto la base de datos de producción no será accesible para los desarrolladores
con el fin de garantizar la integridad de la información sino que trabajarán con una
copia local de la misma.

PostGreSQL o PostGres es DBMS como podría ser MySQL o Oracle DataBase. 

## Continuos Integration and Continuos Deployment (CI/CD)

[CI/CD](https://en.wikipedia.org/wiki/CI/CD) es el proceso de automatizar la 
intergración del código en desarrollo y el proceso de despliegue con el objetivo
de detectar defectos tempranamente, aumentar la productividad y obtener ciclos de 
lanzamiento más cortos.

Para lograr estos objetivos los cambios incrementales aportados por un desarrollador
son compilados, procesados a través de una batería de tests que garantice la 
funcionalidad y finalmente desplegados. Todo de forma automática.

Aunque en el futuro se debe alcanzar un ciclo de CI/CD adecuado para la delegación 
actualmente no es una prioridad y lo iremos construyendo en función de nuestras 
necesidades.
