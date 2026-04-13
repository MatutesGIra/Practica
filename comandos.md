# Comandos de Git

## Inicializar un proyecto en git

    git init

## Clonar Repositorio

    Clonar Repositorio
    git clone [URL] 
    Ej: git clone https://github.com/libgit2/libgit2

    Clonar repositorio con nombre especifico
    git clone [URL] nombre
    Ej: git clone https://github.com/libgit2/libgit2 mylibgit

## Status de los archivos

    Normal
    git status

    Abreviacion
    git status -s
    git status --short

## Crear o editar Archivos, configurar .gitignore

    Crear archivos
    echo 'My Project' > README
    
    Modificar archivos
    echo "echo Hola mundo 2" >> archivo1.sh

    Configurar ignorados
    echo "*jpg" >> .gitignore

## .gitignore

    ignora los archivos terminados en .a
    *.a

    pero no lib.a, aun cuando había ignorado los archivos terminados en .a en la línea anterior
    !lib.a

    ignora unicamente el archivo TODO de la raiz, no subdir/TODO
    /TODO

    ignora todos los archivos del directorio build/
    build/

    ignora doc/notes.txt, pero no este: doc/server/arch.txt
    doc/*.txt

    ignora todos los archivos .txt del directorio doc/
    doc/**/*.txt

## Status precisos

    lo que esta sin preparar
    git diff

    lo que esta preparado hasta ahora
    git diff --cached

    compara cambios preparados
    git diff --staged

## Confirmar cambios

    Confirmar directamente y crear una version
    git commit -m 'Nombre de commit'

    Añadir todos los archivos rastreados y confirmar
    git commit -a -m 'Nombre de commit'

## Eliminar archivos

    Eliminar directamente
    rm Archivo

    Eliminar archivo con status visible
    git rm Archivo

    Eliminarlo del area de preparados, mas no del directorio
    git rm --cached Archivo

## Cambiar nombre de archivos

    git mv nombre nombreNuevo