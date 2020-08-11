---
title: Cómo instalar vagrant en ubuntu 20.04
date: 2020-08-10 09:45:47 -05:00
modified: 2020-08-10 09:45:47 -05:00
tags: [vagrant]
description: Tutorial de instalación de vagrant en ubuntu 20.04
---

# Instalar Vagrant en Ubuntu 20.04

Vagrant necesita un proveedor para la creación de máquinas virtuales, para este tutorial instalaremos virtualbox en una máquina (host) con ubuntu 20.04.

Para instalar vagrant simplemente ejecutarémos los siguientes comandos

```bash
sudo apt update
sudo apt install virtualbox
```

Ahora una vez tenemos instalado virtualbox, procedemos a instalar vagrant cuya última versión para el tiempo en que se escribe este post es la 2.2.9

Descargamos entonces el instalador de vagrant

```bash
curl -O https://releases.hashicorp.com/vagrant/2.2.9/vagrant_2.2.9_x86_64.deb
```

y una vez descargado lo instalamos

```bash
sudo apt install ./vagrant_2.2.9_x86_64.deb
```

Verificamos la versión 

```bash
vagrant --version
```

y con esto ya tenemos instalado vagrant en nuestra máquina.

## Primeros pasos

Aprovechando la instalación vamos a crear nuestra primera máquina con vagrant, para esto creamos un directorio de trabajo

```bash
mkdir mi_primera_maquina
cd mi_primera_maquina/
```

Crearémos una máquina o en términos de vagrant un **box** con ubuntu 18.04, el catálogo de todas las **boxes** que podemos crear está en [https://app.vagrantup.com/boxes/search](https://app.vagrantup.com/boxes/search)

```bash
vagrant init "hashicorp/bionic64"
```

el comando init nos crea el archivo de configuración Vagrantfile, es ahí donde especificamos la creación de nuestras boxes. Dentro del archivo encontramos lo siguiente

```bash
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
```

Esta linea inicia la configuración de nuestras máquinas virtuales en la versión 2 de Vagrantfile. Luego en el archivo podemos observar lo siguiente:

```bash
# Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/bionic64"
```

config.vm.box nos indica cuál imagen vamos a utilizar.

Limpiando un poco el Vagrantfile puede quedar de la siguiente forma

```bash
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
end
```

Ahora creamos nuestra máquina virtual con el siguiente comando

```bash
vagrant up
```

Para entrar a la máquina ejecutamos

```bash
vagrant ssh
```

Detenemos la máquina y la eliminamos

```bash
vagrant halt
vagrant destroy
```

En próximos post configuraremos un entorno de desarrollo con Vagrant. No olviden ver la documentación oficial para tener más detalle de cada uno de los comandos.