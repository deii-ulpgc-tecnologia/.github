# **La guía del desarrollador web galáctico 🚀**

Bienvenidos a la guía definitiva de la DEII para entender de una vez por todas el mapa general del desarrollo web. Pero no cualquier desarrollo web, sino el desarrollo web **GALÁCTICO.**

Pero tranquilo astronauta, sabemos que no quieres marearte en tu primer viaje a si que vamos a ir, como dice fonsi, des pa ci to.

el único objetivo de esta guía es que cuando la termines tengas un mapa en la cabeza de como funciona el desarrollo web y puedas comenzar a trabajar.

Comencemos pues!

3, 2, 1... Despegue!!!!!!!


# Índice

#### 1. Infraestructura: Los pilares de todo
#### 2. Diseño: Cómo crear experiencias únicas
#### 3. Frontend: Convertir una experiencia única en una aplicación real
#### 4. Backend: Dónde ocurre la magía.
#### 5. Sistemas: linux uwu


# Infraestructura

### El modelo cliente/servidor

cliente/servidor

concepto:

SSR

CLIENTE <-> SERVER

cliente/servidor -> http tradicional petición devuelves html

problemas: aplicaciones cada vez mas interacción, tarda mucho en devolver html ejemplo 
Ejemplos: google, pagina universidad (requiren poca interaccion mantienen el esquema tradicional)

CSR

CLIENTE - -> SERVER 1 -> http -> el server que antes enviaba html al cliente ahora en un formato que otro programa pueda leer JSON, el front se descarga entero de una.
    |
    --> SERVER 2

Problemas: el seo es una mierda. La araña de google solo ve un html en blanco porque no interpreta js
Ejemplos: dashboards de métricas, videojuegos, aplicaciones web (whatsapp imaginate que cada vez que envias un mensaje por ella se recargara la página)

HIBRID: CSR + SSR

CLIENTE <-> server 1 <-> server 2 -> 
    |--------------------|

SSR nuevo modelo servidor/servidor/cliente -> el cliente pide la intefaz de una, y la interfaz se encarga de comunicarse con el servidor para devolverle la información como se la devuelve? JSON, javascript object notation, en que lenguaje esta la intefaz programada? javascript

PROBLEMA SOLUCIONADO: FALTA DE INTERACCIÓN, FALTA DE SEO
ejemplos: netflix quiere que puedas bajar el volumen sin que recargues la página, y también quiere que cuando busques una serie concreta aparezca en el navegador. 

# Producto 

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


# Frontend

lenguajes:

framework: coge tu código y lo transforma en javascript, html y css tradicional. encambio la libreria la llamas

html: etiquetas, es un arbol se llama DOM. 
css: define estilos para esas etiquetas.
javascript: introducción, paradigma funcional es6, (!yuju existen clases pero no son objetos! prototype), parece concurrente pero es single threaded surprise motherfucker (event loop). 

nosotros usaremos next implementa react como librería.

# Backend

python: 
https:
lenguaje: de verdad herencia (!puto self) y programacion funcional (lambdas) en armonia perfecta, si lo necesitas metes c++
postgres
ORM

# Sistemas

nginx (Servidor front)
django (Servidor back)
postgres ( Servidor db )

docker ( Virtualización, el contenedor, la imagen, ventajas, inconvenientes )
    - Envuelve toda la infraestructura
    - Aporta un entorno estándarizado para el desarrollo

Diagrama de infraestructura

CI/CD
DevOps

