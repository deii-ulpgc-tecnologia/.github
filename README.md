# **La guía del desarrollador web galáctico 🚀**

Bienvenidos a la guía definitiva de la DEII para entender de una vez por todas el mapa general del desarrollo web. Pero no cualquier desarrollo web, sino el desarrollo web **GALÁCTICO.**

Pero tranquilo astronauta, sabemos que no quieres marearte en tu primer viaje a si que vamos a ir, como dice fonsi, des pa ci to.

el único objetivo de esta guía es que cuando la termines tengas un mapa en la cabeza de como funciona el desarrollo web y puedas comenzar a trabajar.

Comencemos pues!

3, 2, 1... Despegue!!!!!!!


# Índice

1. [Infraestructura: El mapa](#infraestructura-el-mapa)
2. [Producto: Del problema a la solución](#producto-del-problema-a-la-solución)
3. [Frontend: Del prototipo a una aplicación real](#frontend-del-prototípo-a-una-aplicación-real)
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
cliente/servidor

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

Un ejemplos de CSR es Angular.

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

## La Imagen Real

He de admitir que hasta ahora he estado mintiendo, bueno más bien he ocultado parte 
de la verdad. Por la imagen que se ha pintado hasta el momento parece que hay dos 
agentes que interactuan: el cliente y el servidor, sin embargo, en realidad son cinco agentes
los interactuan en una página web moderna.


### El cliente
Este sigue siendo el navegador web del usuario que quiere acceder a la página. Nada ha
cambiado.
<br>


### El servidor de frontend
Frontend de aquí en adelante, es el servidor que hemos estado viendo hasta ahora. Se encarga de devolver el HTML (SSR) o el javascript (CSR) al cliente cuando este se conecta por primera vez
a la página web.
<br>


### El servidor de backend
Backend de aquí en adelante, es el servidor que hemos estado ocultando hasta ahora. 
En resumidas cuentas es el encargado de gestionar la lógica de negocio y hacer de 
interfaz con la base de datos. En resumidas cuentas es quien genera el contenido de 
la página web. El frontend (SSR) o el cliente (CSR) se comunican con este servidor 
para obtener la infomación necesaria para renderizar la página.
<br>


### Base de datos 
Se trata de una máquina que ejecuta un [DBMS](https://en.wikipedia.org/wiki/Database#Database_management_system) y a la cual solo se debería poder acceder 
a través del backend por motivos de seguridad.
<br>

### Servidor de Imágenes
Se trata de un servidor de archivos estáticos. Su objetivo es contener las imágenes 
que puedan ser referenciadas desde la página web a través de una URL.
<br>


A continuación se muestran los **verdaderos diagramas de los diferentes modelos de 
desarrollo web**. Se excluye el servidor de imágenes pero este sería accedido, 
siempre por el cliente, para cada imagen que se incluya en la página web.


### SSR 
```
          HTML                Contenido de la página              Información en crudo
Cliente <------> Frontend <---------------------------> Backend <---------------------> DB
```

### CSR 
```
          Javascript
Cliente <------------> Frontend 
   ^
   | Contenido de la página             Información en crudo
   |------------------------> Backend <----------------------> DB
```

### Hybrid rendering 

# Producto: Del problema a la solución

## Aterrizaje en el planeta producto:

Bueno viajero, que tal ha ido tu primer expedición? Tienes un poco cara de mareado. Pero bueno, tranquilo que has aterricado en el planeta más alucinante de todos. El planeta **Producto**. 

Te noto aturdido, te estarás preguntando ¿Qué es producto? Producto es todo y nada, es el infinito y el cero. Uhum Uhum... vale me dejo de tonterías. Producto es el area de una empresa que se encarga de ser intermediario entre el equipo de desarrollo y el equipo de negocio. Transforma las ideas locas de una empresa en prototipos viables listos para programar, midiendo el impacto real de los mismos una vez entregados al cliente final. 

Las funciones que realizan los perfiles de producto son:
- Identificación de problemas (pains) de nuestro cliente
- Ideación de funcionalidades que solventen esos problemas
- Priorización de esas funcionalidades.
- Diseño de un prototipo que cumpla con las especificaciones.
- Testeo y evaluación del rendimiento de nuestro prototipo.
- Delivery final al equipo de desarrollo.

Este proceso sigue el llamado "Design Double Diamond"

Dentro de producto como os podreis imaginar hay varios roles: (estos roles suelen ser variables al igual que su función, dependen mucho de la empresa)
- Product Manager
- Product Designer
- Product Marketer
- Business Analyst
- Chief Product Officer
...

nosotros nos centraremos en dos de ellos, el Product Manager y el Product Designer.

## Product Manager:

El Product Manager se encarga de la primera fase del diseño: decidir que se va a hacer y priorizarlo.

Hay dos reglas que todo Product Manager debe marcarse en la sangre:

1. No creer nada hasta que no lo pruebes (A.K.A Lean Startup).
2. Tomar decisiones en base a datos (A.K.A Data Driven Decisions o en su abreviación DDD).

Su primer labor será hacer research del sector en el que se mueve, encontrando y verificando los problemas reales del cliente. Para esto puede apoyarse de metodologías como Lean Startup. Qué por cierto es la metodología que ha llevado Silicon Valley a donde esta ahora mismo. Esta se basa en el ciclo hipótesis, test y aprendizaje descrito en la imagen posterior. Pero bueno podríamos estar hablando días sobre esto.

Su segunda función es idear funcionalidades que solventen los problemas encontrados, priorizandolas según su importancia. Una heurística, muy sencilla, pero popular, para hacer esto es usar la matriz effort/value que nos permite en muy poco tiempo identificar aquellas que aporten mas valor con el mínimo esfuerzo (Principio de Pareto). El output de esta fase deberá de ser un Product Roudmap, que se puede crear con Jira, Product Board o cualquier otro software pero la idea es que todo el equipo sepa que funcionalidades se van a desarrollar a largo plazo y que prioridades tienen. Mas tarde estas funcionalidades se convertiran en epics que el equipo de desarrollo tendrá que implementar.

Aquí terminá el trabajo del Product Manager y comienza el del Product Designer, aunque oviamente el Product Manager seguirá al tanto de todo el ciclo de desarrollo para comprobar que este yendo todo de la mejor manera posible.

.- imagen product roadmap
.- imagen effort value

## Product Designer:

El product designer se encarga de: definir una funcionalidad y diseñar un prototipo final de la misma. Este prototipo será el entregable que el equipo de desarrollo cogerá y realizará la implementación. P.D: No cambies un prototipo final al no ser que quieras que algún frontend tire tu ordenador por la ventana un martes por la mañana.

Las fases de este proceso son 4:
1. Research e Inspiración: donde se tratará de buscar aplicaciones con funcionalidades parecidas, diseños ya echos por otros... (Dribbble es la herramienta que mas se usa para esta fase)
2. Crear Wireframes: Los wireframes son el esqueleto de nuestro diseño, nos indican la posición de los elementos, los CTAs (call to actions), información contenida dentro de los mismos pero sin ningún tipo de estilo.
3. Pasar los Fireframes a Mockups: es decir darle estilo a estos Mockups a través del sistema de diseño de nuestra organización
4. Protipar: craer un prototipo que el equipo de desarrollo usará para comenzar a trabajar.

- foto wireframe
- foto mockup
- video wireframe a mockup

las principales subcategorias del mismo son:
- UX Designer: Encargados de desarrollar los wireframes.
- UI Designer: Encargados de pasar los wireframes a mockups.

--foto ciclo lean startup


# Frontend: Del prototípo a una aplicación real

lenguajes:

framework: coge tu código y lo transforma en javascript, html y css tradicional. encambio la libreria la llamas

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

nginx (Servidor front)
django (Servidor back)
postgres ( Servidor db )

docker ( Virtualización, el contenedor, la imagen, ventajas, inconvenientes )
    - Envuelve toda la infraestructura
    - Aporta un entorno estándarizado para el desarrollo

Diagrama de infraestructura

CI/CD
DevOps

