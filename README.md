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

![](https://i.stack.imgur.com/rqary.png)

**git add** y **git commit**

```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar gitignore"

```
Además, en VS CODE creamos una **carpeta**: **logs**, con un **archivo**: **sabado21.log**, y fuera de la carpeta creamos también un **archivos**: **secrets.yml**

Posteriormente en el archivo **.gitgnore** le coloco **/logs** que ignora cualquier cosa dentro de la carpeta, y **secrets,yml** que ignorara este archivo 

![](https://i.stack.imgur.com/1Z7Z1.png)

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
![](https://i.stack.imgur.com/xE6Nl.png)

Se ingresa en la carpeta hooks **cd .git/hooks** y con **dir** nos muestra el directorio

```
C:\Maestria\1mer-repo>cd .git/hooks
C:\Maestria\1mer-repo\.git\hooks>dir
```
![](https://i.stack.imgur.com/90wO0.png)

Abrir el archivo ****pre-commit.sample**

```
C:\Maestria\1mer-repo\.git\hooks>more pre-commit.sample
```
![](https://i.stack.imgur.com/78WeA.png)

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

Se abre el *archivo pre-commit* en el **Editor de Texto vim**

```
C:\Maestria\1mer-repo\.git\hooks>vim pre-commit    
```
Si *no se reconoce el comando*, se puede **descargar el Editos de Text Vim** y *editarlo directamente* en él (en Linux no suele haber problemas con ello)

[link de descarga](https://github.com/vim/vim-win32-installer/releases)

Presionar **i** para *insertar la salida*: **echo “vamos a hacer un commit”** ->**Esc**->**:wq**

![](https://i.stack.imgur.com/YKprN.png)

Volver a la carpeta **1mer-repo**

En VS CODE al archivo index2.js se *agrega la función* **getFirstCharacter**

**git add** y **git commit**

```
C:\Maestria\1mer-repo>git add .
C:\Maestria\1mer-repo>git commit -m "Agregar traer primer caracter"
```
Se observa el *mensaje* del pre-commit *"vamos a hacer un commit"* antes de la acción de ejecutarse el commit de "Agregar traer primer caracter"

![](https://i.stack.imgur.com/vhZKL.png)

Si se agrega **-n** al final del commit *no se ejecutan los hooks* (el mensaje de pre-commit)

```
C:\Maestria\1mer-repo>git commit -m "Agregar traer primer caracter" -n
```


