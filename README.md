# **Control de versiones y GIT**
Tarea 1 de la materia de controlador de versiones de la maestría Diseño web y desarrollo de app.
## Introducción al control de versiones
* Sistema que registra cambios en un conjunto de archivos
* Registra un historial de cambios
* Ayuda con la colaboración en equipos
* Facilita reversión de cambios
* Gestión de ramas
* Facilita la implementación de CI/CD
* Código abierto
### Descargar e instalar Git
[link de descarga](https://git-scm.com/downloads "Git para windows")

O si ya está instalado, solo se lo ***Actualiza***
```
C:\windows\system32>git update-git-for-windows
```
Verificar si se ha instalado Git
```
C:\Windows\system32>git --version
```
### Configurar Git 

Setear nombre y email
```
C:\Windows\system32> git config --global user.email "doctorX@gmail.com"
C:\Windows\system32> git config --global user.name "Doctor"
```
Revisar la configuración
```
C:\windows\system32>git config --list
```
### Creación de repositorio local

Crear una carpeta en C:\ e *inicializarla*
```
C:\Maestria\1mer-repo>git init
```
En *Visual Studio CODE*, se crea un archivo con una función

![](https://i.stack.imgur.com/axZqQ.png)

**git status** permite obtener un reporte
```
C:\Maestria\1mer-repo>git status
```
![](https://i.stack.imgur.com/siR6E.png)

**git add** añade una modificación presente en el directorio de trabajo

```
C:\Maestria\1mer-repo>git add index.js
C:\Maestria\1mer-repo>git status
```
![](https://i.stack.imgur.com/oO1Cr.png)

**git commit** permite documentar los cambios que se realizan en un repositorio

```
C:\Maestria\1mer-repo>git commit -m "1mer commit"
```
**git log** muestra todas las commits en el historial del repositorio (*salir = tecla q*)
```
C:\Maestria\1mer-repo>git log
```
![](https://i.stack.imgur.com/W1f1u.png)

Se crea un archivo index2.js con la función concatenateStrings y en index.js se agrega la función subtract

**git diff** permite comparar cambios en archivos, ramas y commit

```
C:\Maestria\1mer-repo>git diff
```
![](https://i.stack.imgur.com/OWTfK.png)

**git add .** agrega todos los cambios
```
C:\Maestria\1mer-repo>git add .
```
**git commit**
```
C:\Maestria\1mer-repo>git commit -m "agregar index2.js"
``` 
## TRABAJO EN EQUIPO CON GIT
* **Branches** o **ramas**: Lineas de desarrollo independientes. Rama main o master

* **git branch** permite crear una rama nueva

* **git checkout** permite desplazarte entre las ramas creadas por git branch

* **git checkout** acepta el argumento **-b**, que creará la nueva rama y cambiará a ella al instante

* **git merge** se utiliza para combinar dos ramas

* **conflictos** de fusión suceden cuando fusionas ramas que tienen confirmaciones de cambios contrapuestas

Ejemplo **git merge**

![](https://i.stack.imgur.com/YoTXH.png)

Se crea un nuevo **branch**
```
C:\Maestria\1mer-repo>git checkout -b Orley/Tarea1-Multiplicacion
``` 
En index.js se crea la función multiply 

**git add** y **git commit**
```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar Multiplicacion"
```
**HEAD**: Puntero de Git para especificar branch/commit actual

**git log**

![](https://i.stack.imgur.com/1qSs9.png)

Se cambia al **branch master** (main)
```
C:\Maestria\1mer-repo>git checkout master
```
Se crea un nuevo **branch** que realice otra tarea
```
C:\Maestria\1mer-repo>git checkout -b Desarrollador2-Dividir
``` 
En index.js se crea la función divide

**git add** y **git commit**

```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar Division"
```
Con **git log** vemos que esta rama contiene el commit de División, y los 2 commits de **master**

![](https://i.stack.imgur.com/O76EN.png)

Cambiar al **branch master** (main)

```
C:\Maestria\1mer-repo>git checkout master
```
**git branch** permite ver las branchs que tenemos

```
C:\Maestria\1mer-repo>git branch
```
![](https://i.stack.imgur.com/LvFFJ.png)

Ahora con **git merge** se unirá un branch dentro de otro. 
Unir el **branch mater** con la **branch Orley/Tarea1-Multiplicacion**

```
C:\Maestria\1mer-repo>git merge Orley/Tarea1-Multiplicacion
```

Con **git log** apreciamos como el *commit de Agregar Multiplicacion* se ha unido a **master**

![](https://i.stack.imgur.com/GHyzW.png)

Ahora se unirá **branch mater** con **branch  Desarrollador2-Dividir**

```
C:\Maestria\1mer-repo>git merge Desarrollador2-Dividir
```
![](https://i.stack.imgur.com/RGG8h.png)

**Nota**: se produce un **conflicto** en index.js porque 2 desarrolladores han tocado las mismas líneas de código y no puede unir automáticamente

En **VS CODE** se *muestra el conflicto*, que se *soluciona* cerrando con corchete la función multiply y haciendo un espacio entre funciones

![](https://i.stack.imgur.com/6IOex.png)

**git add**

```
C:\Maestria\1mer-repo>git add index.js
```
**git commit** para mostrar el Editor de Texto
```
C:\Maestria\1mer-repo>git commit
```
#### Editor de Texto
* **i** - permite insertar
* **Esc** - pasa a guardar y cerrar

**Guardar y cerrar**

* **:w** – Permite guardar el fichero
* **:q** – Salir. Si el fichero ha sido modificado pero no se ha guardado, nos advertirá y no podremos salir usando este comando
* **:q!** – Salir, descartando posibles cambios no guardados que se hayan realizado en el fichero
* **:wq** – Hace el guardado del archivo y después sale

No insertar nada solo **guardar y salir** (**Esc**->**:wq**)

![](https://i.stack.imgur.com/NGT1u.png)

Con **git log** se aprecia que el **conflicto** se ha solucionado, y el *commit de Agregar División* se ha unido a **master**

![](https://i.stack.imgur.com/oWdqY.png)

### Etiquetas y versionado semántico

**Etiquetas** (tags) son punteros fijos a un commit en especial
* git tag nombre
* git tag (lista)
* git tag -d nombre

**Versionado semántico** es una convención en la nomenclatura para nombrar
versiones. X.Y.Z.
* X: Cambios mayores: API, modificaciones importantes
* Y: Se agregan nuevas características, retrocompatibles con versiones anteriores
* Z: Cambios menores: bug fixes, parches

Con **git checkout** y el **ID de un commit** en particular, permite desplazarse a él, en este caso se usa el commit de “agregar index2.js”

```
C:\Maestria\1mer-repo>git checkout 4d6c5eb76025493013850f7fd2d8b49969b3e376
```

En este Commit agregaremos un **git tag**, le pondremos de versión 0.0.1

```
C:\Maestria\1mer-repo>git tag 0.0.1
```
En **git log** se ve la etiqueta añadida

![](https://i.stack.imgur.com/kMBjo.png)

Se cambia al **branch master** (main)

```
C:\Maestria\1mer-repo>git checkout master
```
### Gitignore y gestión de archivos binarios y sensibles

* .gitignore es in archivo de texto plano con patrones para ignorar archivos
* Builds, archivos para subir, archivos sensibles con contraseñas, logs

![](https://i.stack.imgur.com/VMdsN.png)

En VS CODE crearemos el archivo .gitignore

![](https://i.stack.imgur.com/PX772.png)

**git add** y **git commit**

```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar gitignore"

```
Además, en VS CODE creamos una **carpeta**: **logs**, con un **archivo**: **sabado21.log**, y fuera de la carpeta creamos también un **archivos**: **secrets.yml**

Posteriormente en el archivo **.gitgnore** le coloco **/logs** que ignora cualquier cosa dentro de la carpeta, y **secrets,yml** que ignorara este archivo 

![](https://i.stack.imgur.com/JlKhP.png)

**git add** y **git commit**

```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar longs y secrets a gitgnore"

```
### Hooks de Git y automatización de tareas
* Hooks son scripts que se ejecutan en respuesta a acciones en un repositorio git: antes de commit, antes de push
* Se encuentran en .git/hooks

Con **dir** y el modificador **/a:h** comprobamos si existe la carpeta oculta .git/hooks (Linux = **ls -la**)

```
C:\Maestria\1mer-repo>dir /a:h
```
![](https://i.stack.imgur.com/3D1Fi.png)

Se ingresa en la carpeta hooks **cd .git/hooks** y con **dir** nos muestra el directorio

```
C:\Maestria\1mer-repo>cd .git/hooks
C:\Maestria\1mer-repo\.git\hooks>dir
```
![](https://i.stack.imgur.com/OU5l5.png)

Abrir el archivo ****pre-commit.sample**

```
C:\Maestria\1mer-repo\.git\hooks>more pre-commit.sample
```
![](https://i.stack.imgur.com/7BE0V.png)

Se copia (**copy**) el pre-commit.sample al archivo pre-commit (Linux copiar = cp)

```
C:\Maestria\1mer-repo\.git\hooks>copy pre-commit.sample pre-commit
```
Volver a la carpeta **1mer-repo**

En **index2.js** se crea la función **toUpperCase**

**git add** y **git commit**

```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar toUpperCase"
```
Volvemos a la carpeta hooks **cd .git/hooks** y con **dir** nos muestra el archivo **pre-commit** recién creado

Se abre el *archivo pre-commit* en el **Editor de Texto Vim**

```
C:\Maestria\1mer-repo\.git\hooks>vim pre-commit    
```
Si *no se reconoce el comando*, se puede **descargar el Editos de Text Vim** y *editarlo directamente* en él (en Linux no suele haber problemas con ello)

[link de descarga](https://github.com/vim/vim-win32-installer/releases)

Presionar **i** para *insertar la salida*: **echo “vamos a hacer un commit”** ->**Esc**->**:wq**

![](https://i.stack.imgur.com/YLbhg.png)

Volver a la carpeta **1mer-repo**

En VS CODE al archivo index2.js se *agrega la función* **getFirstCharacter**

**git add** y **git commit**

```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar traer primer caracter"
```
Se observa el *mensaje* del pre-commit *"vamos a hacer un commit"* antes de la acción de ejecutarse el commit de "Agregar traer primer caracter"

![](https://i.stack.imgur.com/qoEp3.png)

Si se agrega **-n** al final del commit *no se ejecutan los hooks* (el mensaje de pre-commit)

```
C:\Maestria\1mer-repo>git commit -m "Agregar traer primer caracter" -n
```
## Git Avanzado

### Git Rebase
* git rebase sirve para reorganizar y modificar la historia del proyecto.
* A diferencia de merge, se puede modificar el historial
* git rebase
* git rebase -i HEAD~n
* git rebase -i branch

![](https://i.stack.imgur.com/yo5Ez.png)

Se crea el branch orley/tarea-2-get-char

```
C:\Maestria\1mer-repo>git checkout -b orley/tarea-2-get-char
```
En VS CODE se crea la función getOneCharacter en index2.js

**git add** y **git commit**
```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit –m “Agregar traer un caracter”

```
Se cambia al **branch main** (master)
```
C:\Maestria\1mer-repo>git checkout main
```
Crear **función power** en index.js 

**git add** y **git commit**
```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar potencia"
```
Se cambia al **branch orley/tarea-2-get-char**
```
C:\Maestria\1mer-repo>git checkout orley/tarea-2-get-char
```
Con **git log** vemos, que *no tiene el commit de “Agregar potencia”* porque se izó luego de crear la rama

![](https://i.stack.imgur.com/41VRq.png)

Estando en la *branch* de **orley/tarea-2-get-char**, hacer **rebase**, sé lo hace contra la *branch* **main** (master) que se desea actualizar

```
C:\Maestria\1mer-repo>git rebase main
```
Con **git log**, vemos la actualización realizada

![](https://i.stack.imgur.com/faeQ9.png)

En index2.js se crea la función getTwoCharacter

**git add** y **git commit**

```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar traer 2 caracteres"
```
Se crea nuevamente en index2.js la función makeCapitalized
```
**git add** y **git commit**

C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar hacer capitalizado"
```
![](https://i.stack.imgur.com/eMIIM.png)

Hacer **git rebase -i** contra el *ID del commit “Agregar potencia”* de main, para que el Editor de Texto muestre los 3 últimos commit

```
C:\Maestria\1mer-repo>git rebase -i 590a6829c22eb1e59652b5c030f45fde06ea78b3
```
También se puede obtener el mismo resultado con **git rebase -i HEAD~n** colocando el *número de commit* que se desea
```
C:\Maestria\1mer-repo>git rebase -i HEAD~3
```
**Nota**: cada uno de estos comandos se pueden usar para realizar diferentes acciones

![](https://i.stack.imgur.com/P0C8A.png)

Presionar **i** para *insertar* **r** -> **Esc** -> **:wq**

Se *cambia la descripción* de un commit con la letra **r**
En este caso se cambiará: "Agregar traer **2** caracteres" por "Agregar traer **dos** caracteres"  

![](https://i.stack.imgur.com/esOcu.png)

Presionar **i** para *insertar* **dos** -> **Esc** -> **:wq**

Nos lleva al commit seleccionado y se procede a cambiar la descripción: 2-dos

![](https://i.stack.imgur.com/rPPoT.png)

Con **git log**, se aprecia que el commit ya está modificado

![](https://i.stack.imgur.com/bWEbB.png)

### Git stash

Es una estructura de datos en pila, lo que hace es guardar los cambios temporales o no definitivos sin necesidad de hacer commit 
* git stash
* git stash pop
* git stash list
* git stash apply stash@{n}
* git stash pop stash@{n}

En VS CODE, en index2.js se realiza la **función getInitials3** y se la *deja incompleta* 

![](https://i.stack.imgur.com/hsJQF.png)

Se me pide que cambie a la **branch main** (master), y para no llevar esos cambios se los *guarda en una pila temporal* **git stash**, donde guarda temporalmente, pero deja la branch tal como estaba

```
C:\Maestria\1mer-repo>git stash
```
Si vamos a **git status** *no hay ninguna función*, pero lo *podemos ver dentro de la* **pila**

Donde lo guarda en la posición 0, y lo saco del commit “funcione con strings” el cual es un trabajo en progreso (WIP)

```
C:\Maestria\1mer-repo>git stash list
```
![](https://i.stack.imgur.com/6sHWo.png)

Si hacemos **git stash pop** me trae y borra los últimos cambios que están dentro de la pila

Es decir, *retorna* la **función getInitials3** incompleta, pero lo borra de la pila
```
C:\Maestria\1mer-repo>git stash pop
```
![](https://i.stack.imgur.com/gxAnv.png)

Volver hacer **git stash**

```
C:\Maestria\1mer-repo>git stash
```
Con **git stash list** se aprecia que la posición del stash, en este caso 0

**git stash apply stash@{n}** aplica el número del cambio que queramos, pero no lo borra

```
C:\Maestria\1mer-repo>git stash apply stash@{0}
```
**git stash pop stash@{n}** elimina algo de la pila
```
C:\Maestria\1mer-repo>git stash pop stash@{0}
```
**git checkout -- .** una forma de eliminar los cambios de forma definitiva

```
C:\Maestria\1mer-repo>git checkout -- .
```
Con **git status** se ve que ya no hay nada

![](https://i.stack.imgur.com/rSxyO.png)

Pero como se aplicó **git stash apply stash@{n}** aún se conserva en la lista

![](https://i.stack.imgur.com/Sz3TE.png)

Pero si hago **git stash pop** que lo saca y lo borra, me quedo sin nada en la lista, no hay forma de recuperarlo por CMD

```
C:\Maestria\1mer-repo>git stash pop
```



























