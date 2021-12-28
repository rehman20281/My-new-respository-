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
Openresty








