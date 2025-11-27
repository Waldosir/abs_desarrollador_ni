# ABC para desarrollador nuevo ingreso

Este es un programa de Sistema de Gestión de Citas Médicas

## Arquitectura de referencia

Para este programa me enfoqué en una arquitectura de capas:

- Capa Frontend: Es la capa visual. Esta es la que conecta al usuario con la aplicación, y con la cual el usuario interactúa. Esta solo tiene acceso a la capa Backend
- Capa Backend: Es la capa de la lógica. Esta es la que procesa las solicitudes, transforma los datos, valida la información y tiene comunicación entre la capa Frontend y la capa DB
- Capa DB: Es la capa de almacenamiento de datos. Se encarga de guardar información, modificar, o borrar información de la capa backend, o transmitir la información hacia la capa backend.
Razón de utilizar esta arquitectura: Es la más sencilla para la separación de responsabilidades, para un escalamiento a mediano y/o largo plazo, y también permite que el equipo de desarrollo vaya integrando funcionalidades en una de las capas sin afectar a la otra capa siempre y cuando el tipo de respuesta y el canal de comunicación usado sea el adecuado y pactado.

A su vez también se implementó una arquitectura de Microservicios: En este se divide en servicios, los cuales son aplicaciones independientes y pueden ser utilizados en conjunto en una sola capa para una aplicación más robusta.

## Modelo de datos

### Diagrama DB

![Diagrama de Arquitectura base de datos](docs/Diagrama_DB.drawio.svg)

## Diagrama Backend

![Diagrama de Arquitectura backend](docs/Diagrama_Clases_Backend.drawio.svg)

**Nota:** Alergias fue una clase considerada a implementar que por cuestiones de tiempo no fue implementada.

## Diagramas en Drive

<https://drive.google.com/drive/folders/10YdpXJMfVKXjnoY-oSdB1sE5eX9Km_tc?usp=sharing>

**Nota:** Por demoras de tiempo no se realizó un diagrama para el Frontend en digital. Se hicieron muchos borradores en fisico.

## Tecnologías usadas

Se usaron 3 tecnologías:

- Front-end: Vite React
  - Es el front end que sé utilizar, sin embargo también existe Angular para ello.
  - No se utilizó javascript vanilla, dado que el DOM puede complicarse y es más sencillo la funcionalidad de componentes que te da React.
- Back-end: Java Springboot
  - Java es un lenguaje utilizado en lo empresarial, el cual incluye herramientas de seguridad, tipado y actualizaciones, y permite tener control sobre lo que se tiene que hacer y el cómo declarar tipos, variables y la Java Virtual machine para usarse en cualquier computadora que lo tenga si la versión es la misma o mayor, y este es utilizado con un framework llamado spring. Pese a ello, la configuración del framework no es sencilla, por lo que para hacerlo más sencillo para iniciar se creó springboot que viene con configuraciones por defecto para utilizarse como microservicio. Se requirió tiempo para una lectura del framework para usarse en lo básico. Además existe Spring security, un .jar para su uso y posible deploy rápido mediante spring cloud o uso de Docker
  - No se utilizó python por rapidez y falta de tipado, pero fue considerado
  - No se utilizó javascript, pese a la existencia de typescript, porque requería tiempo para su lectura y al final ofrece mejores tecnologías java con springboot
- Base de datos: Postgresql
  - Esta base de datos relacionales no solo es de código libre y que puede ser utilizado sin pagar, sino que también es muy robusta, pudiendo guardar y procesar miles de millones de datos más rápidamente que otras bases de datos como MariaDB o MySQL.
  - Microsoft SQL es de pago, y MySQL también, por ello fueron descartadas.

## Correr proyecto

### Descargar proyecto con submodulos

- Haz un clone del repositorio con todos los submodulos: `git clone --recurse-submodules https://github.com/Waldosir/abs_desarrollador_ni`

### Correr en docker

Es requerido docker para correr este proyecto

En la raiz del proyecto ejecuta este comando: `docker compose -f docker-compose.yml up --build`

Con ello tres servicios se inician: la base de datos postgresql 15, el backend java con spring boot y el front end vite react.

Sustituir los .env_example en las carpetas ProyectoCPL_backend,ProyectoCPL_Frontend y en la raiz del proyecto y sustituir las variables de entorno.

**Nota**: Este proyecto no funciona en local. Solo funciona en Docker.

## URL Importantes

Para entrar en el front es mediante este link: <http://localhost:3000/>

Para enviar peticiones al backend es mediante este link: <http://localhost:8050>