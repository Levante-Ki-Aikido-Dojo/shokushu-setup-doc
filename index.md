# Instalar aplicaciones

Estas instrucciones suponen que se instala en Windows.

## Git
- Navegar a <https://gitforwindows.org>
- Descargar instalador
- Ejecutar instalador
- Elegir "Next" en cada diálogo
- Ejecutar en el terminal (cambiando `<tu nombre>` y `<tu email>`):
```console
> git config --global user.name "<tu nombre>"
> git config --global user.email "<tu email>"
```
- Opcional: Abrir archivo en `C:\Users\<tu usuario>\.gitconfig` y entrar siguiente contenido abajo:
```
[core]
	commentchar = ";"
[init]
	defaultBranch = main
[push]
	autoSetupRemote = true
[remote "origin"]
	prune = true
```

## Visual Studio Code
- Navegar a <https://code.visualstudio.com/Download>
- Descargar instalador
- Ejecutar instalador
- Opcionalmente elegir "Crear un acceso directo en el escritorio"
- Abrir Visual Studio Code y instalar los siguientes extensiones:
  - GitLens - Git supercharged
  - Code Spell Checker
  - Spanish - Code Spell Checker

## Latex
- Navegar a <https://mirror.ctan.org/systems/texlive/tlnet/install-tl-windows.exe>
- La descarga del instalador empieza automáticamente
- Ejecutar instalador
- Si el SmartScreen impide la instalación, elegir "Más información" y después "Ejecutar de todas formas"
- Revisar las opciones del instalador y elegir "Instalar". AVISO: este proceso tarda unas dos horas.
- Cambiar el template del español en `C:\texlive\2023\texmf-dist\tex\generic\babel-spanish\spanish.ldf`:
Cambiar líneas 143 y 144 de
  ```
  \SetString{\bibname}{Bibliograf\'{\i}a}%
  \SetString{\chaptername}{Cap\'{\i}tulo}%
  ```
  a
  ```
  \SetString{\bibname}{Bibliografía}%
  \SetString{\chaptername}{Capítulo}%
  %  \SetString{\bibname}{Bibliograf\'{\i}a}%
  %  \SetString{\chaptername}{Cap\'{\i}tulo}%
  ```

# Acceso repositorio

## Crear certificado SSL
- Ejecutar aplicación Git bash
- En el terminal (cambiando `<tu email>` y `<tu usuario>`):
  - ```console
    > ssh-keygen -t ed25519 -C "<tu email>"
    ```
  - Pulsar "Entrar" para aceptar donde guardar el archivo
  - Pulsar "Entrar" dos veces para guardar sin contraseña
  - ```console
    > ssh-add /c/Users/<tu usuario>/.ssh/id_ed25519
    ```
  - Si no encuentra el SSH agent primero entrar:
  - ```console
    > eval `ssh-agent -s`
    > ssh-add /c/Users/<tu usuario>/.ssh/id_ed25519
    ```

## Crear cuenta GitHub
- Navegar a <https://github.com>
- Elegir "Sign up"
- Seguir instrucciones
- Desde la nueva cuenta navegar a Settings -> SSH and GPG keys
- Elegir "New SSH key"
- Elegir un título y bajo "Key" copiar y pegar el contenido de `C:/Users/<tu usuario>/.ssh/id_ed25519.pub`
- Elegir "Add SSH key"
- Pasar el nombre y email de tu cuenta para recibir acceso al repositorio

## Clonar repositorio
- Primero asegúrate de que tu cuenta tiene acceso al repositorio de los shokushu
- Abrir el terminal
- Navegar a la carpeta deseada
- ```console
  > git clone git@github.com:pbrandwijk/shokushu.git
  ```
- Entrar "yes" si el sistema avisa que es una llave desconocida
- Ahora descarga el repositorio en la carpeta

## Abrir proyecto en Visual Studio Code
- Abrir Visual Studio Code
- Navegar a File -> Open folder
- Elegir la carpeta `shokushu`
- Confirmar Trust folder

## Crear archivo PDF
- Arrancar VS code y abrir carpeta del repositorio
- Abrir el terminal del VS code
- ```console
  > cd libro
  > pdflatex shokushu.tex
  ```
