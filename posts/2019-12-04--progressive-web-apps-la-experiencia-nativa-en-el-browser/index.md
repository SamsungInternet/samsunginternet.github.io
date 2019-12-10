---
permalink: "/progressive-web-apps-la-experiencia-nativa-en-el-browser/"
cover: img.jpg
title: "Progressive Web Apps: la experiencia nativa en el browser"
description: "No hace mucho tiempo, cada vez que quería instalar una app en mi querido y viejo Android lo tenía que pensar dos veces, la probabilidad de que me aparezca el mensaje “Insuficiente espacio en el disco” era bastante alta… Esto además de haber sido una señal de que ya era hora de comprar un celular nuevo (😅), fue una especie de recordatorio que aparte de developer también soy usuario y que de la misma forma puede haber una gran cantidad de usuarios que por no tener el último dispositivo del mercado o incluso por encontrarse en una región con mala conectividad, no pueden sacarle provecho a ciertas aplicaciones nativas. Hacer que los usuarios bajen tu app del store y que luego continúen usándola es una tarea que tiene sus complicaciones. En cambio si por el otro lado haces productos para la web, tenes la ventaja de llegar a billones de personas sin la necesidad de que instalen nada, pero aún asi debemos lidiar con la retención de usuario, visibilidad, etc."
category: Web
img: https://miro.medium.com/max/886/1*B_fxWrWzgdsK6qedoBAtnw.png
author: Laura Morinigo
authorImg: https://miro.medium.com/fit/c/96/96/1*rZUWIujvpL0YX4iV8KTKTg.jpeg
tags: [Web, Desarrollo Web, Coding, Tecnologia, JavaScript]
---

# Progressive Web Apps: la experiencia nativa en el browser

No hace mucho tiempo, cada vez que quería instalar una app en mi querido y viejo Android lo tenía que pensar dos veces, la probabilidad de que me aparezca el mensaje “Insuficiente espacio en el disco” era bastante alta… Esto además de haber sido una señal de que ya era hora de comprar un celular nuevo (😅), fue una especie de recordatorio que aparte de developer también soy usuario y que de la misma forma puede haber una gran cantidad de usuarios que por no tener el último dispositivo del mercado o incluso por encontrarse en una región con mala conectividad, no pueden sacarle provecho a ciertas aplicaciones nativas. Hacer que los usuarios bajen tu app del store y que luego continúen usándola es una tarea que tiene sus complicaciones. En cambio si por el otro lado haces productos para la web, tenes la ventaja de llegar a billones de personas sin la necesidad de que instalen nada, pero aún asi debemos lidiar con la retención de usuario, visibilidad, etc.

Hasta acá me gustaría pensar que en su mayoría estamos de acuerdo en que si los usuarios están satisfechos con el producto y vemos que usan nuestra app periódicamente estamos cumpliendo gran parte de nuestros objetivos como programadores. Entonces que pasaría si podemos combinar algunas características de las aplicaciones nativas para ayudar a atraer y retener usuarios como push notifications o acceso a la app desde un ícono *todo desde el browser*? **Habemus Progressive Web Apps!**

![](https://cdn-images-1.medium.com/max/2000/1*bLpfKRlT34ZpGkanf0-oyg.png)

Las Progressive Web Apps o PWA es un concepto cuyo nombre fue creado por Frances Berriman y Alex Russel para describir a aquellas apps que utilizan funcionalidades de los browsers modernos y que se contruyen utilizando sólo tecnologías web ❤, es decir HTML, CSS y Javascript.

**La evolución del browser**

Pero si quiero hacer una de estas web-apps, tengo acceso al hardware del móvil desde el browser? Sí! Además de poder utilizar servicios como la cámara y el GPS, actualmente muchos navegadores modernos incluyendo Samsung Internet brindan acceso a por ejemplo autenticación mediante huellas dactilares y próximamente Web-XR.

![Web XR, Instalacion de WebAPK para PWA, seguridad biométrica para navegación privada y antitracking son algunas de las caracteristicas que brinda Samsung Internet](https://cdn-images-1.medium.com/max/2122/1*aAxPuds6QgnFgr42BUQgOA.png)*Web XR, Instalacion de WebAPK para PWA, seguridad biométrica para navegación privada y antitracking son algunas de las caracteristicas que brinda Samsung Internet*

**Técnicamente hablando….**

Para los programadores construir una PWA se traduce a incluir lo siguiente en la web:

* *HTTPS*: La web tiene que estar en una red segura. Ofrecer un sitio seguro además de ser una buena práctica también confirma que tu web-app es de confianza, en especial si los usuarios necesitan hacer transacciones que requieren cierta capa de seguridad. Además muchas de las características de una PWA funcionan solamente si utilizas HTTPS ya que sino puede traerte problemas por ejemplo a la hora de utilizar service workers. La buena noticia es que actualmente es bastante simple tener un certificado SSL lo cual ahorra tiempo y recursos, así que ya sabes cuál es el primer paso para construir tu PWA: usa HTTPS.

* *Service Worker: *Un service worker es un script que permite interceptar y controlar la manera en la que el navegador maneja los diferentes requests y el caching. Gracias a los service workers, los desarrolladores web pueden crear sitios seguros, confiables y experiencias offline.

* *Manifest File: *Es un archivo JSON que controla como aparece tu app y se asegura que las progressive web apps puedan ser descubiertas. Describe el nombre de la app, la URL, los iconos y los detalles necesarios para transformar el website en un formato parecido al de una app nativa. En los celulares Samsung también existe soporte para instalar PWAs usando WebAPK el cual nos da una experiencia aún más parecida al de una app.

Veamos un ejemplo, aquí tenemos Pigment, una Progressive Web App creada por Samsung Internet que convierte los formatos de los colores entre Hexa, HSL, RGB y CMYK que funciona offline! La primera vez que visitas la página podrás encontrar un botón al lado de la URL para comenzar a instalarla. Luego de la instalación podrás ver el ícono en tu home screen como si fuese una app nativa!!

![](https://cdn-images-1.medium.com/max/2000/1*B_fxWrWzgdsK6qedoBAtnw.png)

**Entonces deber**í**a de construir una PWA?**

* *Si ya tenes una app nativa: *construir una PWA no significa que vaya a reemplazar tu app nativa, ambas pueden coexistir tranquilamente, es más, estás agregando una experiencia multiplataforma y con esto la opción al usuario de acceder desde la pc. Hay varios ejemplos en el mercado como Pinterest o Tinder que luego de costruir una PWA aumentaron sus ganancias y mejoraron considerablemente la experiencia de usuario. Para saber más estadísticas de PWA recomiendo [pwastats.com](https://www.pwastats.com/).

* *Si ya tenes un website: *Definitivamente sí! Además de agregar las características de una app nativa para aumentar la retención de los usuarios, la mayoría de las funcionalidades citadas anteriormente son buenas practicás para la web, usando https para asegurarse que es un sitio seguro para el usuario, cachear los archivos correctos para mejor el rendimiento o setear los íconos correctos deberían de ser prioridades.

**Próximos Pasos**

Estamos en un muy buen momento para aportar productos a la web y esperamos ver muchas PWAs interesantes. Para ayudar a los developers a ganar más visibilidad, Samsung anunció recientemente la posibilidad de publicar tu PWA en el Galaxy Store!!!

Si ya tenés una PWA y te interesa publicarla o si tenés feedback de lo que te gustaría ver en el Galaxy Store (actualmente sólo disponible para el mercado de US), podés escribir a [pwasupport@samsung.com](mailto:pwasupport@samsung.com).

**Crea tu primera PWA**

Vendrán más articulos acerca de este tema, pero si mientras tanto querés empezar a construir tu primera PWA podés chequear nuestro [codelab](https://glitch.com/~samsunginternet-pigment-starterkit) donde te explicamos paso a paso cómo hacerlo, esperamos el feedback de la comunidad y cómo les resulta trabajar con esta tecnología!!



By Laura Morinigo on December 4, 2019.

[Canonical link](https://medium.com/samsung-internet-dev/progressive-web-apps-la-experiencia-nativa-en-el-browser-9b17aa0196fb)
