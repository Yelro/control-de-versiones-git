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

![](https://i.stack.imgur.com/y9KUV.png)

**git status** permite obtener un reporte
```
C:\Maestria\1mer-repo>git status
```
![](https://i.stack.imgur.com/rNEcQ.png)

**git add** añade una modificación presente en el directorio de trabajo

```
C:\Maestria\1mer-repo>git add index.js
C:\Maestria\1mer-repo>git status
```
![](https://i.stack.imgur.com/C78iD.png)

**git commit** permite documentar los cambios que se realizan en un repositorio

```
C:\Maestria\1mer-repo>git commit -m "1mer commit"
```
**git log** muestra todas las commits en el historial del repositorio (*salir = tecla q*)
```
C:\Maestria\1mer-repo>git log
```
![](https://i.stack.imgur.com/RaCaB.png)

Se crea un archivo index2.js con la función concatenateStrings y en index.js se agrega la función subtract

**git diff** permite comparar cambios en archivos, ramas y commit

```
C:\Maestria\1mer-repo>git diff
```
![](https://i.stack.imgur.com/UXV2a.png)

**add .** agrega todos los cambios
```
C:\Maestria\1mer-repo>git add .
```
**commit**
```
C:\Maestria\1mer-repo>git commit -m "agregar index2.js"
``` 




