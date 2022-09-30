# Banco Familiar | El Banco Nunca te Pide

Landing Page Desarrollado para la campaña de prevención de Phising del **Banco Familiar**.

Proyecto desarrollado en Winter CMS.


## Guia de Instalación

El proyecto en WinterCMS puede ser instalado de varias maneras. Ver la [documentación](https://wintercms.com/install) para más información.


### Requerimientos del Sistema

1. Un servidor web (Apache, Nginx, IIS, Lighttpd)
2. Un servidor de base de datos (MySQL/MariaDB, PostgreSQL, SQL Server or SQLite)
3. Version del PHP 7.2 o mayor
4. Las siguientes extensiones PHP deben estar instaladas y habilitadas:
   - Curl
   - GD
   - Mbstring
   - OpenSSL
   - PDO (and a relevant driver for your database server)
   - SimpleXML
   - Zip
5. Composer 2

### Antes de empezar

Antes de empezar a instalar se debe importar la BD, se puede omitir este paso, pero eso implica que la mayoria de la
información debe cargarse desde el CMS.

1. Crear una base de datos nueva en mysql.
2. Crear o asignar un usuario y contraseña existente a la base datos recientemente creada.
3. Importar la base de datos existente en la base datos recientemente creada.


Código de referencia para creación de DB
```mysql
CREATE DATABASE db_familiar;
GRANT ALL PRIVILEGES ON 'db_familiar'.* TO 'existing_user'@'localhost';
FLUSH PRIVILEGES;
```


Código de referencia para importar
```shell
mysqldump  db_familiar < db_familiar_prod.sql
```


### Instalación

1. Una vez realizado los pasos previos posicionarse en la carpeta pública del servidor web y clonar el repositorio
2. Ejecutar el comando
```shell
composer i --no-dev
```
3. Copiar el archivo .env-example
```shell
cp .env-example .env
```
4. Editar el archivo .env con los datos de la base de datos
```
APP_DEBUG=true # Aqui debe estar FALSE al estar en producción
APP_URL=http://dev.familiar-landing.com # Aqui debe ir la url a utilizarse
APP_KEY=base64:RDOFRK+qZ6E3U2iNb5iVC1dbJqLkaAWpTPo8H8v3PMk=

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=fv_familiar_dev # Aqui debe ir el nombre de la base de datos
DB_USERNAME=root # Aqui debe ir el nombre del usuario con permisos sobre la DB
DB_PASSWORD= ## Aqui debe ir el password de la DB

...

LINK_POLICY=detect # Este puede ir 'force' o 'detect'
ENABLE_CSRF=true
```

5. Luego de completar la configuración de las variables de entorno ejecutar el siguiente comando en la raíz del proyecto,
esto realizara la migración de la base de datos y generara una contraseña para el user admin que mostrará en la pantalla,
en caso de no utilizar una base de datos existente:

```shell
php artisan winter:up
```
6. Para actualizar el framework ejecutar el sgt. comando:
```shell
php artisan winter:update
```

## Enlaces de Interés

- **Backend:** `/backend`
- **Configuración del CMS:** `/backend/cms/themeoptions/update/familiar-landing-theme`

## Equipo de desarrollo

Este proyecto fue desarrollado por este increíble grupo de trabajo.

<table>
  <tr>
    <td align="center"><a href="https://github.com/the-fgx"><img src="https://avatars.githubusercontent.com/u/59941436?v=4" width="100px;" alt="Fabio Garcete"/><br /><sub><b>Fabio Garcete</b></sub></a></td>
    <td align="center"><a href="https://github.com/fershio20"><img src="https://avatars.githubusercontent.com/u/69645075?v=4" width="100px;" alt="Fernando Vera"/><br /><sub><b>Fernando Vera</b></sub></a></td>
    <td align="center"><a href="https://github.com/RoKrypto"><img src="https://avatars.githubusercontent.com/u/19767431?v=4" width="100px;" alt="Rodrigo Mendoza"/><br /><sub><b>Rodrigo Mendoza</b></sub></a></td>
  </tr>
</table>




