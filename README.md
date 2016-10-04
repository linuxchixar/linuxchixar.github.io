# Pasos para tener el sitio corriendo localmente en GNU/Linux

Prerequisitos:
* Ruby >=2.0.0
* Bundler
* Jekyll

Antes que nada probamos si tenemos una versión de Ruby mayor a 2.0.0 instalada

    ruby --version
    
Si no tenemos la versión correcta (o no tenemos Ruby) lo instalamos.

## Instalando Ruby
La manera más fácil de tener la última versión es mediante RVM (https://rvm.io/):

1. Importar la key de RVM. **Importante**. Ir a https://rvm.io/ y usar la key que aparece allí en la sección "Install RVM" 

    ```gpg --keyserver hkp://keys.gnupg.net --recv-keys {key}```
2. Instalar RVM junto con Ruby:

    ```\curl -sSL https://get.rvm.io | bash -s stable --ruby```

3. Correr el script que nos pide RVM:
     
     ```source /home/{miusuario}/.rvm/scripts/rvm```


4. Listar las versiones de Ruby que tenemos para elegir cuál usar:
     
    ```rvm list```

5. Tomar nota de la versión más nueva y escribir:

    ```rvm use {version_mas_nueva}```


Si este comando nos tira un error del tipo RVM is not a function, selecting rubies with 'rvm use ...' will not work, hacemos:

    /bin/bash --login
    

Y luego nuevamente 

    rvm use {version_mas_nueva}
    

### Instalando Bundle
Si no lo hicimos ya, elegir la versión de Ruby a usar

    rvm use {version_mas_nueva}
    
Instalar bundler:

    gem install bundler
    
### Instalando Jekyll

    bundle install
    
Esto va a leer nuestro ```Gemfile``` e instalar todas las dependencias necesarias
    
## Corriendo la web localmente
 

1. Forkear el repo desde github

2. Clonar el repo forkeado a nuestra máquina

3. Correr RVM para usar la versión correcta de Ruby (ver pasos 4 y 5 de la sección "Instalando Ruby")

4. Copiar archivo de configuración para los seteos locales:

    ```cp _config.yaml _config_local.yml```
    
    
5. Editar _config_local.yml, cambiamos el valor de ```url``` por ```http://127.0.0.1:4000```

6. Correr el servidor de Jekyll con nuestra configuración local

    
    ```jekyll serve --config _config_local.yml```
    
    
7. En el browser ingresar a ```http://127.0.0.1:4000/linuxchixar-web/```

Ya tenemos el sitio corriendo localmente.



Para info más genérica sobre cómo correr un sitio de github pages con Jekyll ver https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/
