#PASO A PASO Node.js/Heroku
Como desplegar una app Node.js en un PaaS como [Heroku], comentado paso a paso.

[Heroku]:http://www.heroku.com

### ![GitHub](http://www.grails48.com/static/images/github-logo3.png)
Creamos un nuevo repositorio remoto en [GitHub] para nuestra app.

[GitHub]:https://github.com/

### ![Git](http://git-scm.com/images/logo@2x.png)
Iniciamos el control de versiones del directorio local de nuestro proyecto, agregamos todos los archivos,
guardamos, lo enlazamos con nuestro repositoiro remoto en GitHub y subimos los cambios.
``` sh
cd web-app
git init
git add .
git commit -m "first commit"
git remote add origin http://github.com/juanfegc/web-app.git
git push -u origin master
```

### ![Node.js](http://nodejs.org/images/logos/nodejs.png)
Creamos un archivo **package.json** para declarar todas las dependencias de la app y las instalamos con npm.
``` sh
npm init
npm install express logfmt --save
```
Creamos un **Procfile** para indicar como ejecutar nuestra web-app en heroku, con el contenido siguiente:
``` javascript
web: node app.js
```

### ![Heroku](http://www.treasuredata.com/img_logos/heroku.png)
Necesitamos instalar la herramienta [Heroku toolbelt] para poder usar el cliente heroku en la linea de comandos.

[Heroku toolbelt]:https://toolbelt.heroku.com/

``` sh
heroku login
heroku create
```

Probamos la app localmente en [http://localhost:5000] antes de subirla a Heroku
[http://localhost:5000]:http://127.0.0.1:5000

```
foreman start
```
Guardamos todos los cambios en Git/GitHub antes de desplegar
```sh
git add .
git commit -m "first deployment"
git push -u origin master
```
Desplegamos nuestra app en Heroku.
``` sh
heroku create
git push heroku master
```
(opcional) renombramos el nombre del servicio web que heroku nos asignó por defecto.
``` sh
heroku apps:rename newname
```
Abrimos la app en nuestro navegador
``` sh
heroku open
```

**realizado por J.Fernando Godoy Caba**
