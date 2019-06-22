---
layout: post
title: 【TUTORIAL】Personalizando de ⓪ a ①⓪⓪ el BASH Prompt en Linux®
date: 2019-06-22 00:00:00 +0100
permalink: /personalizar-bash-prompt-linux/
comments: true
pic: https://res.cloudinary.com/gligan/image/upload/photo-1545465270-b28c72a628f9.jpg
thumb: https://res.cloudinary.com/gligan/image/upload/w_300/photo-1545465270-b28c72a628f9.jpg
---

<center style="display:block">![Customized Linux Prompt](https://res.cloudinary.com/gligan/image/upload/v1561211648/Screenshot_from_2019-06-22_15-53-07.png)</center>

Si te aburre el típico *prompt* de Linux, no pasa nada, en este artículo verás como modificarlo para que se adapte a tí.

## ¿Cómo 📐 personalizo 📐 mi Linux Prompt?

Antes de cambiarlo tienes que saber que el *prompt^1^* tendrás que saber que este, está guardado en una variable que puedes ver escribiendo:

```bash
echo $PS1
```
Y deberías ver algo parecido a esto ---si no lo has tocado antes---

![BASH Command: echo $PS1](https://res.cloudinary.com/gligan/image/upload/v1561212520/Screenshot_from_2019-06-22_16-07-56.png)

Para hacer esto tendremos que ir al archivo `~/.bashrc`  y tendremos que ir al final del archivo y allí tendremos que que escribir lo siguiente:
```bash
export PS1 = "<...>"
```

Dentro de `<...>` tendrás que poner... lo que te apetezca, aquí tienes unas chuletas:

- `\u` mostrará el nombre de usuario.
- `\h` mostrará el nombre del dispositivo.
- `\w` mostrará el nombre del directorio actual.
- `\` con esto podrás escribir cualquier otro caracter, por ejemplo: `\$` mostrará un simbolo de dólar (`$`).

Incluso puedes añadir emojis ---como ❖, ღ, ✨, ❃, ✙, ⚡, etc.--- aunque yo pienso que no tiene ningún valor pero cada uno tiene sus gustos.

Te aconsejo que mires [esta página](http://ezprompt.net/) o [este otro](http://bashrcgenerator.com/), son unos generadores muy intuitivos con los que podrás tener facilmente un BASH prompt personalizado.

![Customized BASH prompt](https://res.cloudinary.com/gligan/image/upload/v1561213138/Screenshot_from_2019-06-22_16-18-30.png)

El siguiente código es mi BASH prompt personalizado, recuerda; para editarlo tienes que abrir el archivo localizado en `~/.bashrc` y tendrás que añadir al final el siguiente código:

```bash
# Git branch and stat customization
function parse_git_branch() {
    BRANCH=`git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/\1/'`
    if [ ! "${BRANCH}" == "" ]
    then
        STAT=`parse_git_dirty`
        echo " git(${BRANCH}${STAT})"
    else
        echo ""
    fi
}

# get current status of git repo
function parse_git_dirty {
    status=`git status 2>&1 | tee`
    dirty=`echo -n "${status}" 2> /dev/null | grep "modified:" &> /dev/null; echo "$?"`
    untracked=`echo -n "${status}" 2> /dev/null | grep "Untracked files" &> /dev/null; echo "$?"`
    ahead=`echo -n "${status}" 2> /dev/null | grep "Your branch is ahead of" &> /dev/null; echo "$?"`
    newfile=`echo -n "${status}" 2> /dev/null | grep "new file:" &> /dev/null; echo "$?"`
    renamed=`echo -n "${status}" 2> /dev/null | grep "renamed:" &> /dev/null; echo "$?"`
    deleted=`echo -n "${status}" 2> /dev/null | grep "deleted:" &> /dev/null; echo "$?"`
    bits=''
    if [ "${renamed}" == "0" ]; then
        bits=">${bits}"
    fi
    if [ "${ahead}" == "0" ]; then
        bits="*${bits}"
    fi
    if [ "${newfile}" == "0" ]; then
        bits="+${bits}"
    fi
    if [ "${untracked}" == "0" ]; then
        bits="?${bits}"
    fi
    if [ "${deleted}" == "0" ]; then
        bits="x${bits}"
    fi
    if [ "${dirty}" == "0" ]; then
        bits="!${bits}"
    fi
    if [ ! "${bits}" == "" ]; then
        echo " ${bits}"
    else
        echo ""
    fi
}

# Custom BASH Prompt.
export PS1="█ \[\033[01;32m\]\u\[\033[00m\]\[\033[01;14m\]\`parse_git_branch\`\[\033[00m\]\[\033[02;00m\] \[\033[01;34m\]\w\[\033[00m\]\[\033[02;00m\]\n█ "
```

Con esta personalización tendrás el nombre del usuario, ver en que rama y estado de un proyecto git estás y el directorio en el que estás situado.

Si tu también tienes una personalización y la quieres compartir la puedes dejar abajo ---tanto código como enlace--- en los comentarios para que todos podamos verla, seguro que será un gran aporte.
