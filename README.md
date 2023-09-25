# Workshop01 - Bookworm con Vagrant

## Instalacion de VirtualBox

El primer requerimeintop para instalar Bookworm es una maquina virutal es un _"hypervisor"_, para eso vamos a utilizar VirtualBox.

- [Descargar VirtualBox](https://www.virtualbox.org/wiki/Downloads "Click aqui para descargar")

## Instalacion de Vagrant

El segundo requerimiento es _"Vagrant"_. Que es un software para crear y mantener entornos de desarrollo virtuales portatiles.

- [Descargar Vagrant](https://developer.hashicorp.com/vagrant/downloads?product_intent=vagrant "Click aqui parar descargar")

## Configuracion del VBoxnet en VirtualBox'

Antes de aprovisionar nuestra maquina _"Bookworm"_, debemos asegurarnos de que ecista al menos un red del tipo `Host-only`, la cual permitira la comunicacion entre la maquina anfitriona y las maquinas virtuales

![Configuracion de una VBoxNet](./images/Vboxnet.png) 

## Aprovisionar la maquina virtual

Para aprovisionar nuestra primer maquina virtual debe,os crear la estrctura de directorios que albergara los archivos de configuracion de Vagrant

```
cd ~
mkdir -p ISW811/VMs/webserver
cd ISW811/VMs/webserver
```

Luego debemos crear el archivo Vagrant o _"Vagrantfile"_.

```
vagrant init debian/bookworm64
```

Ahora a configurar la IP de la interfaz de red `Host-only` para esto debemos descomentar y editar la linea 35 del archivo _"Vagrantfile"_ detro del VS Code con el comando

```
code Vagrantfile
```

Ahora estamos listos para lanzae el aprovisionamiento de la maquina

```
vagrant up
```

Luego comprobamos que tenemos comunicaion con la maquina virtual

```
ping 192.168.56.10
```

Finalmente nos conectamos a la maquina virtual

```
vagrant ssh
```

## Instalar programas en la maquina virtual

Para instalar programas en **Debian Bookworm** debemos actualizar la lista de paquetes elegibles

```bash
Sudo apt-get update
```

A partir de este punto podemos utilizar el comando apt-get install para instalar cualquier programa disponible en los repositiprios de Debian

```
sudo apt-get install apache2 vim vim-nox
```

## Visualizar la pagina por defecto de Apache

Para visualziar la pagina por defecto de Apache simplemente debemos abrir la url ``http://192.168.56.10`` desde un navegador (O la IP que se haya configurado en nuestra maquina)

<div style="page-break-after: always;"></div>

## Apagar la maquina virtual
Finalmente cuando terminemos de manipular nuestra maquina debemos salir y apagarla

```bash
exit
vagrant halt
```

## Crear el tar.gz

Para finalizar debemos crear el archivo tar.gz con las evidencias de la realizacion del Workshop, debemos ubicarnos en el directorio padre y lanzar el siguiente comando 

```
tar cvfz Workshop01.tar.gz Workshop01
```

Tar es el programa que nos permite crear un archivo empaquetado y comprimido. Los parametros cvfz tienen el siguiente significado.
- c - Compress
- v - Verbose
- f - File
- z - Zip# Workshops-ISW811
# Workshops-ISW811
# Workshops-ISW811
