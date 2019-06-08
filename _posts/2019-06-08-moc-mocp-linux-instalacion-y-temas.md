---
layout: post
title: MOC - El REPRODUCTOR de Música para Linux. Instalación y Temas.
date: 2019-06-08 00:00:00 +0100
permalink: /moc-mocp-linux-instalacion-y-temas/
comments: true
pic: https://res.cloudinary.com/gligan/image/upload/moc-mocp-linux-instalacion-y-temas.jpg
thumb: https://res.cloudinary.com/gligan/image/upload/w_300/moc-mocp-linux-instalacion-y-temas.jpg
---

¿Te gusta la música, la terminal y Linux? Si es así, te aseguro que te encantará MOC, un reproductor de audio *super*liviano con el que podrás... escuchar música.

Si sabes como se usa VIM te resultará muy fácil, ya que está basado en este. Ah! Y por cierto MOC significa *Music On Console*.

![MOC player in Elementary Terminal](https://res.cloudinary.com/gligan/image/upload/v1560032749/Screenshot_from_2019-06-08_22-35-38.png)
*Captura de pantalla de MOC*

## Instalación de MOC.

Para instalar MOC es muy sencillo, simplemente escribe:
```bash
sudo apt install moc
```

Y después para ejecutarlo, escribe `mocp`. Y ya está.

Si no sabes como usar MOC aquí tienes una *chuleta*:

|Tecla| Significado |
|-:|:-|
|**`Espacio`** | pausar/reanudar la reproducción |
|**`s`**	|(*stop*) parar la reproducción|
|**`<`** y **`>`**|bajar/subir el volumen en un 1%|
|**`,`** y **`.`**	|bajar/subir el volumen en 5%|
|**`Tab`**| cambiar entre paneles|
|**`C`**|(*Clear*) limpiar la lista de reproducción|
|**`o`**|reproducir desde una url|
|**`a`** | añadir a la lista de reproducción|
|**`z`**|añadir el archivo a la cola de reproducción|
|**`n`** | (*next*) siguiente archivo|
|**`b`**|(*back*) archivo previo|

Aquí te dejo un vídeo para que puedas ver cómo funciona MOC:
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/m8pvj4QQU9w" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Si tienes alguna otra duda puedes presionar la tecla `h` dentro de MOC para ver todos los comandos disponibles.

## Cómo Personalizo MOC con los Temas.

Tienes (en la teminal) que dirigirte a la carpeta de MOC (`cd ~/.moc/`) y si no existe crear un archivo llamado ***config*** (`nano config` o `touch config` y editarlo con tu editor preferido).

Cuando estés allí simplemente tendrás que escribir lo siguiente:
```bash
Theme = NOMBRE_DEL_TEMA
XTermTheme = NOMBRE_DEL_TEMA
```
Tendrás que cambiar `NOMBRE_DEL_TEMA` por el tema que te plazca, para eso dirígete a MOC con `mocp` y presiona `T` (en mayúsculas), saldrá un menú y elige el tema que te guste y ese mismo nombre lo tendrás que ponder en vez  de `NOMBRE_DEL_TEMA`.

Así de trivial es cambiar un tema de MOC.

Espero que este artículo te haya gustado, si es así o tienes alguna pregunta puedes comertarla y la responderé (lo intentaré 😊).
