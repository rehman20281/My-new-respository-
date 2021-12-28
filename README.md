# RGF-ADMIN Configuration with Composer, PHP8.0, laravel8, doctrine/orm:2.10.3, Docker   
### ``` About Composer ```

##### Step 1

First, update the package manager cache by running:
``` $ sudo apt update ```

Next, to run the following command for installation required packages:
``` $ sudo apt install php-cli unzip ```

You will be incited to affirm establishment by composing Y and afterward ENTER.

Once the prerequisites are installed, you can proceed to installing Composer.

##### Step 2 Downloading and Installing the Composer
Writer gives an installer script which is written in PHP [https://getcomposer.org/installer]. 
We'll download it, and confirm that it's not debased, and afterward use it to install the Composer.

Now, make sure you are in home directory, then retrieve the installer using curl:
``` 
$ cd ~

```
then
```
$ curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php

```

Then, we'll check that the downloaded installer matches the SHA-384 hash for the most recent installer found on the Composer ***`Public Keys/Signatures`*** ***https://composer.github.io/pubkeys.html***. To work with the confirmation step, To facilitate the verification step, you can use the following command to programmatically obtain the latest hash from the Composer page and store it in a shell variable:
```
$ HASH=`curl -sS https://composer.github.io/installer.sig`
```
if you want to verify SHA code you can run
```
echo $HASH
```
This will show you like that code 
```
e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a 
```

Now execute the following PHP code, as provided in the Composer download page, to verify that the installation script is safe to run:
``` 
$ php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" 
```

After that you will see this message :***```Installer verified```***

***NOTE***
If the output says _***Installer corrupt***_, you’ll need to download the installation script again and double check that you’re using the correct hash. Then, repeat the verification process. When you have a verified installer, you can continue.

Install composer globally
``` 
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

You’ll see output similar to this:
```
All settings correct for using Composer
Downloading...

Composer (version 1.10.5) successfully installed to: /usr/local/bin/composer
Use it: php /usr/local/bin/composer
```

After completion this step you will type 
```
$ composer
 
    ______
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 2.1.14 2021-11-30 10:51:43
```
### ***NOTE***
``` 
When this output will display on the screen it means composer has been installed successfully 
```

### ``` About PHP8.0, laravel8, doctrine/orm:2.10.3 ```

> It contains numerous new features and optimizations including  union types, named arguments, attributes, constructor property promotion, match expression, nullsafe operator, JIT, and improvements in the type system, error handling, and consistency. 
_https://www.php.net/releases/8.0/en.php_



` composer.json` 
``` 
"require": {
        "php": "^7.4|8.x",
 }

```

### ``` Doctrine/orm ```

> Latest version of  __doctrine/orm__ was already configured we have just run composer update after this its fetch latest version , so in this configuration we did not work much time.

``` 
    "laravel-doctrine/orm": "1.7.*",
```
``` composer update ```



### ``` Docker ``` 
I hope you have knowledge about docker and it`s containers and images 

First of all you need to build container which are required for your configuration 
here I am telling you about my own requirement 
openresty 
php8.0 
mongodb 
mysql 
redis 
mailcatcher 
laravel8

These are container which are configured by our team 

now these containers ready for running 

Step 1
go to renegade-docker
``` 
$ cd projects/renegade-docker
```
then 
run this command
``` 
$ docker-compose up --build openresty php8.0 mongodb mysql redis mailcatcher laravel8
```

`docker-compose up --build `
This command build all containers if its image will not found in our directory it will download from ***Docker hub*** 

when you run this command after its running proccess you will see like that  
***NOTE***: docker can start the process in the container and attach the console to the process’s standard input, standard output 
``` 
Successfully built d4c72264f3a5
Successfully tagged renegade-docker_openresty:latest
Starting renegade_redis        ... done
Starting renegade_mailcatcher  ... done
Starting renegade-docker_app_1 ... done
Starting renegade_mysql        ... done
Starting renegade_mongodb      ... done
Starting renegade_workspace    ... done
Starting renegade_php8         ... done
Starting renegade_laravel8     ... done
Starting renegade_hhvm         ... done
Recreating renegade_openresty  ... done
Attaching to renegade_redis, renegade_mailcatcher, renegade_mongodb, renegade_mysql, renegade_php8, renegade_laravel8, renegade_openresty
```



if you want to see how many containers are running or proccess mode you will type this command

```
$ docker ps

CONTAINER ID   IMAGE                         COMMAND                  CREATED         STATUS         PORTS                                                                                         NAMES
73a450fdf99e   renegade-docker_openresty     "/usr/local/openrest…"   7 minutes ago   Up 7 minutes   0.0.0.0:80->80/tcp, :::80->80/tcp, 0.0.0.0:443->443/tcp, :::443->443/tcp                      renegade_openresty
b9eb1ff7b05b   renegade-docker_mongodb       "docker-entrypoint.s…"   6 hours ago     Up 7 minutes   0.0.0.0:27017->27017/tcp, :::27017->27017/tcp                                                 renegade_mongodb

```


ps stand for proccess state 

if you want to see how many containers are running and how many are exit you will type this command

```
$ docker ps -a

ONTAINER ID   IMAGE                         COMMAND                  CREATED         STATUS                      PORTS                                                                                         NAMES
73a450fdf99e   renegade-docker_openresty     "/usr/local/openrest…"   7 minutes ago   Up 7 minutes                0.0.0.0:80->80/tcp, :::80->80/tcp, 0.0.0.0:443->443/tcp, :::443->443/tcp                      renegade_openresty
b0328766b188   renegade-docker_mailcatcher   "mailcatcher -f --ip…"   3 hours ago     Exited (0) 3 hours ago                                                                                                    reverent_rosalind
8830a58023f4   renegade-docker_mailcatcher   "mailcatcher -f --ip…"   3 hours ago     Created                                                                                                                   vibrant_knuth
b9eb1ff7b05b   renegade-docker_mongodb       "docker-entrypoint.s…"   6 hours ago     Up 7 minutes                0.0.0.0:27017->27017/tcp, :::27017->27017/tcp                                                 renegade_mongodb
97d805390232   5b21bb72cfd7                  "/bin/sh -c 'mv /etc…"   7 hours ago     Exited (1) 7 hours ago                                                                                                    exciting_hofstadter
5d226c217840   5b21bb72cfd7                  "/bin/sh -c 'mv /etc…"   7 hours ago     Exited (1) 7 hours ago           
```
-a = all

#### Step 2 
you goto inside php8 container 

```
$ docker-compose exec php8.0 bash 
```
it will show you like that
```
root@bea7dd095762:/# 
```
`Now you are in PHP8.0 container`
`if you want to test that you are inside or not in container 
you can run `
``` 
root@bea7dd095762:/# php -v
PHP 8.0.0 (cli) (built: Dec  1 2020 03:14:26) ( NTS )
Copyright (c) The PHP Group
Zend Engine v4.0.0-dev, Copyright (c) Zend Technologies
```

now go to inside your project
``` 
root@bea7dd095762:/# cd srv/renegade-admin
root@bea7dd095762:/srv/renegade-admin# php artisan serve
```

