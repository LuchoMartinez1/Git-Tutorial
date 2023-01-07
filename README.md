# Tutorial Git
1. Creamos un repositorio nuevo en github vacío.

![](img/1.png)

2. Creamos un proyecto nuevo en intellij y trabajamos en él (ésta vez lo hice sin iniciar un repositorio de Git).

![](img/2.png)

3. Creamos una carpeta para guardar las capturas del tutorial y poder tener las imágenes para este README.md.

![](img/3.png)

4. Inicializamos un repositorio de Git en local y vemos el estado del repositorio.

```bash
git init
```

![](img/4.png)

5. El siguiente paso es ignorar en el "working directory" las carpetas que no nos interesan subir: .idea/ y out/. Para esto creo un nuevo documento con el nombre .gitignore.

![](img/5.png)

En él añadiremos las carpetas (".../") o archivos ("*.txt") que no queremos que sean trackeadas cada vez que pusheamos, ya que sino tendríamos que hacerlo de forma manual cada vez que querramos hacer un commit con el siguiente comando (antes de commitear):

```bash
git rm -r --cached .idea/
```

![](img/6.png)

Ahora nos toca ver el estado del repo tras haber modificado el .gitignore.

![](img/7.png)

6. Como vemos en el paso anterior, añado también este README creando un documento de texto al cual también le cambio la extensión y le llamo README.md y voy editando en Visual Studio Code.

7. Ahora si estamos listos para commitear:
    - Lo primero es añadir los cambios del working directory al staging área:
    ```bash
    git add .
    ```
    - Commiteamos, siempre con mensaje

    ```bash
    git commit -m "subiendo proyecto con README y .gitignore"
    ```

8. Nos olvidamos de cambiar el README.md en el commit anterior, esto se soluciona con el siguiente comando (para cualquier cambio):

```bash
git commit --amend --no-edit
```
Si no quiero cambiar el mensaje del commit que quiero añadir o modificar algo.

```bash
git commit --amend -m "..."
```
Si le quiero cambiar el mensaje.

9. Para verificar que el cambio se ha realizado sobre el mismo commit, o ver el historial de commits del proyecto tenemos el siguiente comando:

```bash
git log --oneline
```
    Esta es un log antes del amend:
    ![](img/8.png)

    Luego del amend:
    ![](img/9.png)

    Como vemos, cambia el hash del commit.    

10. Pusheamos el proyecto por primera vez.

    1. Sincronizar con el repo remoto.

    ```bash
    git remote add origin (URL github)
    ```
    2. subirlo:

    ```bash
    git push -u origin master
    ```

11. Ahora simularemos que otra persona se implica en el proyecto y hace modificaciones.

   - Lo primero que tenemos que hacer es clonar el proyecto desde github a su local:
    ```bash
    git clone https://github.com/LuchoMartinez1/Git-Tutorial.git
    ```

   - Creamos una rama para hacer un cambio o desarrollar en Intellij:

    ```bash
    git checkout -b change-code
    ```
        "chekout" para salir de master y "-b" (branch) para crear la rama nueva. 

   - Modificamos el código tal como se ve en el commit.

   - Nos preparamos para hacer merge a master.

   ![](img/9.png)

   - Realizamos el merge sin conflictos.

   ```bash
    git merge change-code
   ```

   - Por último avanzo en este README y pusheo ambas ramas, en este caso no hace falta añadir el remoto ya que se sincroniza al hacer el clone.

   ```bash
    git push -u origin --all
   ```