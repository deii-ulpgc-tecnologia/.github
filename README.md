# GUÍA INTRODUCTORIA AL DESARROLLO WEB

## Índice

    - Infraestructura: ¿Cómo funcionan las páginas web?
        - El modelo [cliente/servidor](#el-model-clienteservidor)
    - Diseño: UI/UX.
    - Frontend: ¿Cómo se construyen las interfaces de usuario?
    - Backend: Dónde ocurre la mágia.
    - Sistemas: linux uwu.


## Infraestructura

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

## DESIGN

figma

## FRONT

lenguajes:

framework: coje tu código y lo transforma en javascript, html y css tradicional. encambio la libreria la llamas

html: etiquetas, es un arbol se llama DOM. 
css: define estilos para esas etiquetas.
javascript: introducción, paradigma funcional es6, (!yuju existen clases pero no son objetos! prototype), parece concurrente pero es single threaded surprise motherfucker (event loop). 

nosotros usaremos next implementa react como librería.

## BACKEND

python: 
https:
lenguaje: de verdad herencia (!puto self) y programacion funcional (lambdas) en armonia perfecta, si lo necesitas metes c++
postgres
ORM

## SISTEMAS

nginx (Servidor front)
django (Servidor back)
postgres ( Servidor db )

docker ( Virtualización, el contenedor, la imagen, ventajas, inconvenientes )
    - Envuelve toda la infraestructura
    - Aporta un entorno estándarizado para el desarrollo

Diagrama de infraestructura

CI/CD
DevOps

