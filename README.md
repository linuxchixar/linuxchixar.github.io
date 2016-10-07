# Pasos para correr el sitio localmente en GNU/Linux

Prerequisitos:
* [Ruby](https://www.ruby-lang.org) >= 2.0.0
* [Bundler](https://bundler.io)
* [Jekyll](https://jekyllrb.com)

Antes que nada probamos si tenemos una versión de Ruby mayor a 2.0.0 instalada:

```bash
ruby --version
```

Si no tenemos la versión correcta *(o no tenemos Ruby)* lo instalamos.

## Instalando Ruby

La manera más fácil de tener la última versión es mediante RVM (https://rvm.io):

1. Importar la key de RVM. **Importante**. Ir a https://rvm.io y usar la key que aparece allí en la sección "Install RVM" 

     ```bash
     gpg --keyserver hkp://keys.gnupg.net --recv-keys {key}
     ```

2. Instalar RVM junto con Ruby:

     ```bash
     curl -sSL https://get.rvm.io | bash -s stable --ruby
     ```

3. Correr el script que nos pide RVM:
     
     ```bash
     source ~/.rvm/scripts/rvm
     ```

4. Listar las versiones de Ruby que tenemos para elegir cuál usar:
     
     ```bash
     rvm list
     ```

5. Tomar nota de la versión más nueva y escribir:

     ```bash
     rvm use {version_mas_nueva}
     ```

Si este comando nos tira un error del tipo *RVM is not a function, selecting rubies with 'rvm use ...' will not work*, hacemos:

```bash
/bin/bash --login
```

Y luego nuevamente:

```bash
rvm use {version_mas_nueva}
```    

### Instalando Bundle

Si no lo hicimos ya, elegir la versión de Ruby a usar:

```bash
rvm use {version_mas_nueva}
```

Instalar bundler:

```bash
gem install bundler
```
    
### Instalando Jekyll

```bash
bundle install
```

Esto va a leer nuestro `Gemfile` e instalar todas las dependencias necesarias.

## Corriendo la web localmente
 

1. [Forkear el repo desde github.](https://github.com/linuxchixar/linuxchixar-web#fork-destination-box "Click para Forkear")

2. Clonar el repo forkeado a nuestra máquina.

3. Correr RVM para usar la versión correcta de Ruby *[(ver pasos 4 y 5 de la sección "Instalando Ruby")](https://github.com/juancarlospaco/linuxchixar-web/blob/master/README.md#instalando-ruby)*.

4. Copiar archivo de configuración, para editarlo con los ajustes locales:

     ```bash
     cp _config.yml _config_local.yml
     ```
    
5. Editar `_config_local.yml`, cambiamos el valor de `url` por `http://127.0.0.1:4000` *(En linea 20 aprox.)*

6. Correr el servidor de Jekyll con nuestra configuración local.

     ```bash
     bundle exec jekyll serve --config _config_local.yml
     ```

7. En el browser ingresar a [http://127.0.0.1:4000/linuxchixar-web/](http://127.0.0.1:4000/linuxchixar-web/)

Ya tenemos el sitio corriendo localmente. *Happy Hacking !.*



Para info más genérica sobre cómo correr un sitio de github pages con Jekyll ver:
- https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll
