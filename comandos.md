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

## Ver historial de confirmacion

    Mostrar historial completo
    git log

    Mostrar diferencias entre las confirmacione
    git log -p

    Mostrar las ultimas dos confirmaciones
    git log -2

    Mostrar solo algunas estadisticas
    git log --stat

    Modificar Formato de salida
    git log --pretty=nombredeformato
    Hay varias opciones en este: oneline, short, full, fuller. Tambien esta format que te premite crear tu propio formato

|Opción|Descripcion de la salida|
|:------:|:------------------------:|
|%H|hash de la confirmacion|
|%h|hash de la confirmacion abreviado|
|%T|hash del arbol|
|%t|hash del arbol abreviado|
|%P|hashes de las confirmaciones padre|
|%p|hashes de las confirmaciones padre abreviados|
|%an|nombre del autor|
|%ae|dirección de correo del autor|
|%ad|fecha de autoria (el formato respeta la opcion --date)|
|%ar|fecha de autoria, relativa|
|%cn|nombre del confirmador|
|%ce|dirección de correo del confirmador|
|%cd|fecha de confirmacion|
|%cr|fecha de confirmacion, relativa|
|$s|asunto|

    Mostrar ramificaciones y uniones
    git log --graph

| Opción | Descripción |
| :---------------: | :--------------------------------------------------------- |
| -p | Muestra el parche introducido en cada confirmación |
| --stat | Muestra estadísticas sobre los archivos modificados en cada confirmación |
| --shortstat | Muestra solamente la línea de resumen de la opción --stat |
| --name-only | Muestra la lista de archivos afectados |
| --name-status | Muestra la lista de archivos afectados indicando además si fueron añadidos modificados o eliminados |
| --abbrev-commit | Muestra solamente los primeros caracteres de la suma SHA-1 en vez de los 40 caracteres de que se compone |
| --relative-date | Muestra la fecha en formato relativo (por ejemplo “2 weeks ago” (“hace 2 semanas”)) en lugar del formato completo |
| --graph | Muestra un gráfico ASCII con la historia de ramificaciones y uniones |
| --pretty | Muestra las confirmaciones usando un formato alternativo Posibles opciones son oneline short full fuller y format (mediante el cual puedes especificar tu propio formato) |

    Limitar salida del historial
    git log -<n>

| Opción | Descripción |
| :------------------: | :--------------------------------------------------------- |
| -(n) | Muestra solamente las últimas n confirmaciones |
| --since y --after | Muestra aquellas confirmaciones hechas después de lafecha especificada |
| --until y --before | Muestra aquellas confirmaciones hechas antes de la fechaespecificada |
| --author | Muestra sólo aquellas confirmaciones cuyo autor coincidecon la cadena especificada |
| --committer | Muestra sólo aquellas confirmaciones cuyo confirmadorcoincide con la cadena especificada |
| -S | Muestra sólo aquellas confirmaciones que añaden o eliminen código que corresponda con la cadena especificada |

## Deshacer confirmaciones

    git commit --amend
    Agregar cosas que olvidaste en la anterior confirmacion
    ej:
    git commit -m 'confirmacion inicial'
    git add archivoOlvidado
    git commit --amend
    Aparecera con el mismo nombre de la confirmacion anterior y con el cambio de ahora

## Deshacer archivo preparado

    git reset HEAD nombreArchivo
    Solo quita de preparado el archivo, no afecta el contenido de este

## Deshacer modificacion de archivo

    git checkout -- nombreArchivo
    Este si cambia los datos de un archivo, regresandolos a una version anterior

## Repositorio remoto

    Donde estas en tu repositorio
    git remote

    direccion web del repositorio
    git remote -v

    añadir repositorio remoto
    git remote add [nombre] [url]

    traer informacion de repositorios vinculados
    git fetch [nombre] 

    descargar y fusionar remoto
    git pull [nombreRemoto] [nombreRama]

    Enviar remotos
    git push [nombreRemoto] [nombreRama]

    Informacion de remoto
    git remote show [nombreRemoto]

    renombrar remoto
    git remote rename [nombreRemoto] [nuevoNombreRemoto]

    eliminar remoto
    git remote rm [nombreRemoto]

## Etiquetado

    listar etiquetas
    git tag

    listar etiquetas especificas
    git tag -l 'vX*'
    ej: git tag -l 'v1.8.5*' Te trae todas las versiones de la 1.8.5

    etiquetas anotadas
    git tag -a vX -m 'nombreVersion'

    etiquetas ligeras (temporales)
    git tag vX-lw

    etiquetado tardio
    git log --pretty=oneline
    git tag -a vX [los 7 caractares inciales del que quieres etiquetar] -m 'vX'

    informacion de etiqueta
    git show vX

    compartir etiquetas
    git push [nombreRemoto] [etiqueta]

    compartir todas las etiquetas
    git push [nombreRemoto] --tags

    sacar etiqueta
    git checkout -b [nombreNuevaRama] [etiquetaExistente]