---
permalink: "/pwa-series-service-workers-los-bsicos-de-la-experiencia-offline/"
cover: img.jpg
title: "PWA Series: Service Workers, los básicos de la experiencia offline"
description: "[ English version here!]"
category: PWA
img: https://miro.medium.com/max/1200/0*UR5vMuq_mAotNLQX.jpeg
author: Laura Morinigo
authorImg: https://miro.medium.com/fit/c/96/96/1*rZUWIujvpL0YX4iV8KTKTg.jpeg
tags: [Progressive Web App, Pwa, Web Development, Programación, JavaScript]
---

# PWA Series: Service Workers, los básicos de la experiencia offline

[ English version here!]

En artículos previos, estuvimos explicando [qué son las Progressive Web Apps](https://medium.com/samsung-internet-dev/pwa-gu%C3%ADa-del-manifest-file-92c7cdac25ad) y las características que posee una PWA: HTTPS, [un archivo manifest](https://medium.com/samsung-internet-dev/pwa-gu%C3%ADa-del-manifest-file-92c7cdac25ad) y los denominados service workers, los cuales veremos a continuación.

![](https://cdn-images-1.medium.com/max/4000/0*UR5vMuq_mAotNLQX.jpeg)

## La experiencia offline

Aunque algunos dispositivos y apps son diseñados para que se utilicen bajo un escenario ideal que implica buena conexión de datos, no nos sorprende encontrar, que en general, estas no son las condiciones normales con las que un usuario se encuentra.

*“Por favor recuerden poner sus dispositivos en modo avión, este vuelo cuenta con acceso a wifi para los miembros executive platinum VIP y sino son miembros pueden adquirir 5 minutos de conexión a cambio de la pequeña suma de la hipoteca de su casa”. *Si han viajado en avión en algun momento estas palabras les sonarán conocidas, o simplemente sin ir más lejos, llegar a un lugar con mala conexión o viajar en subterráneo son algunos de los casos que puede hacer que el usuario pierda conectividad, ni hablar de cuando disponemos de un plan de datos limitado para nuestros celulares y recibimos el mensaje *“Agregue saldo a su cuenta para poder seguir navegando”* . Estas situaciones traen como consecuencia que las web apps deben ser rápidas y confiables para los usuarios sin importar la calidad de la red. Para esto están disponibles estrategias que podemos utilizar y los denominados “service workers” tienen un papel importante en todo esto.

Antes de ir de lleno en definiciones de service workers, recuerden que primero, necesitamos aplicar *HTTPS*. Además de hacer que nuestro sitio sea seguro, tener habilitado HTTPS hace que nuestra web tenga acceso a muchas propiedades de los browsers modernos, como por ejemplo: geolocation, pago y también a los service workers.

## Y qué es un service worker?

Un service worker es un script que permite interceptar y controlar los requests de la red y el almacenamiento del cache del browser. Gracias a los service workers, los programadores web pueden crear sitios web con una experiencia offline. Cabe aclarar que no tiene acceso al DOM, su rol es diferente del de un script normal de javascript.

Como los service workers tienen acceso al manejo de los requests, pueden llegar a ser muy poderosos (y peligrosos), especialmente si son usados con mala intención por ejemplo inyectando un script o queriendo reemplazar el sitio entero. Esto es uno de los motivos por lo cuales usar HTTPS es muy importante, para prevenir ataques de terceros.

## Cómo puedo implementar un service worker?

Para instalar un service worker se necesitan seguir los siguientes pasos:

**1- Registrar**

Antes de instalar un service worker, el browser debe de chequear si ya existe, para hacer esto llamamos al evento “register”.



Revisemos este pedazo de código, la primera parte es chequear si una propiedad llamada “serviceworker” que pertenece al objeto “navigator” existe, de ser así significa que no hay necesidad de registrarlo. De todas maneras, podemos llamar al método registrar el cual va a invocar a nuestro service worker, que como puedes ver, es un archivo llamado “serviceworker.js” el que contiene el código para instalar y mantener la funcionalidad del mismo.

**2- Instalar**

En nuestro script del service worker llamado “serviceworker.js” implementamos el resto de la funcionalidad.

La primera parte es el evento *install*, acá podemos indicar qué archivos son los que se van a guardar en la caché, el contenido que se agrega al array “urlsToCache” serán agregados de forma inmediata cuando la página lo requiera.



**3- Fetch**

Ya tenemos nuestros archivos en la caché, estos pueden ser imágenes, scripts o lo que sea que te parezca importante manejar de manera offline. Hay diferentes estrategias para elegir si se debe almacenar un archivo o cargarlo directamente con la red. Nosotros debemos elegir cuidadosamente y ser responsables a la hora del manejo de archivos ya que los recursos disponibles son limitados.

Una vez que se tienen los recursos cacheados, debemos indicar qué hacer con ellos al service worker. Hay un evento denominado* fetch* que nos permite hacer esto.

Fetch es un evento que se ejecuta cada vez que cualquier documento se busque en la cache de un service worker, como cuando alguna página se carga y se necesite un recurso como un script o una imagen, o se realiza una llamada a un API. Se puede agregar un evento fetch que escucha al service worker, y entonces llamar al método respondWith() para manejar tus request-response de la red y hacer algo con eso, como por ejemplo algún mensaje que el usuario está offline o cargar imágenes offline.

El ejemplo siguiente es una estrategia de cache simple, si el archivo está en la cache del service worker, lo devuelve de allí inmediatamente, sino lo obtendrá de la red.



**4- Activate**

Necesitas manejar los recursos cacheados, por ejemplo, los viejos archivos que no existen más o incluir archivos nuevos. Esta es una buena forma de hacerle mantenimiento a tu web app ya que los browsers tienen una relación complicada con el espacio de almacenamiento.



## Pasos siguientes

Estos son los pasos básicos para crear un service worker y comenzar a experimentar alrededor de los recursos offline en la web. Hay diferentes herramientas que nos permiten realizar estos pasos de manera simple, por ejemplo, con [PWA builder ](https://www.pwabuilder.com/)se puede elegir un template de service worker, setear parámetros y luego guardar el archivo generado.

Existen varios temas relacionados para entender aún mejor: estrategias de caching, ciclo de vida de un service worker, etc… Vamos a hablar de esto en los próximos artículos. Por lo pronto recomendamos chequear el sitio de [MDN](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps) para aprender más acerca de este tema.

## En las noticias de Samsung Internet…

Si te gustaría aprender más de PWA o si estas interesado en temas de tecnologías (en especial web) o si tenés algo para compartir con nosotros, estamos haciendo oficinas virtuales para continuar interactuando socialmente (pero online) con la comunidad, seguir hablando de la web y más alrededor del mundo tech. Podes chequear la nueva página de [meetup](https://www.meetup.com/Samsung-Internet-Meetup/) para nuestros siguientes eventos.

Además si querés compartir algo en lo que estás trabajando, y te gustaría tener un espacio para mostrarlo, te estamos buscando como invitado especial! Hicimos [este formulario](https://docs.google.com/forms/d/e/1FAIpQLScV-hhmM2MGVP2WIij5WlArxic6KEl9sYnBkHf21oNXEIUjxA/viewform) para que puedas participar. Cada oficina virtual es una oportunidad para conectar con audiencia de todos lados del mundo y aprender.

PD: Estamos planeando realizar esto también en español!! No dudes en aplicar.

Sigamos conectados (virtualmente) 🎉



By Laura Morinigo on April 3, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/pwa-series-service-workers-los-b%C3%A1sicos-de-la-experiencia-offline-14592542c738)
