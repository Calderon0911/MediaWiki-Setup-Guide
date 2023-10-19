# MediaWiki-Setup-Guide
Guía de instalación de MediaKiki. 

## 1. Preparativos
Antes de instalar MediaWiki, necesitarás configurar un servidor web, PHP y una base de datos. En este ejemplo, utilizaremos Apache, PHP y MariaDB:

# a. Instalar Apache, PHP y módulos necesarios

```bash
sudo apt update
sudo apt install apache2 libapache2-mod-php php php-mysql php-xml php-mbstring
```
```bash
sudo apt install php-intl
```
# b. Instalar MariaDB

```bash
sudo apt install mariadb-server
```
```bash
sudo mysql_secure_installation
```
establece una contraseña de root si se te solicita y responde "Y" a las demás preguntas para asegurar tu servidor MariaDB.

## 2. Configurar la base de datos para MediaWiki

Inicia sesión en MariaDB:
```bash
sudo mysql -u root -p
```
```bash
CREATE DATABASE mediawiki;
GRANT ALL PRIVILEGES ON mediawiki.* TO 'mediawikiuser'@'localhost' IDENTIFIED BY 'admin';
GRANT ALL PRIVILEGES ON mywiki.* TO 'mediawikiuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
Guardar el nombre 'mediawikiuser' y la contraseña 'admin', ya que se te solicitara mas adelante.

## 3. Descargar e instalar MediaWiki

Vamos a descargar la última versión de MediaWiki y colocarla en el directorio de Apache:

```bash
cd /tmp
```
```bash
wget https://releases.wikimedia.org/mediawiki/1.36/mediawiki-1.36.0.tar.gz
```
```bash
tar -xvzf mediawiki-1.36.0.tar.gz
```
```bash
sudo mv mediawiki-1.36.0 /var/www/html/mediawiki
```

## 4. Configurar MediaWiki

Seguimos las instrucciones para finalziar la instalacion. 
Recordatorio, en la seccion de base de datos ingresar el usuario y contraseña que añadieron en la base de datos.

![image](https://github.com/Calderon0911/MediaWiki-Setup-Guide/assets/69009908/ab9f372e-df68-426a-bf4c-2b87044bcfa2)

## 5 Finalizacion de instalacion.

Cuando terminemos la configuracion de MediaWiki se nos descargara un archivo 'LocalSetting.php'. Cuando tengan este archivo lo transferimos a nuestro servidor y lo colocamos en la carpeta donde se encuentre la configuracion de MediaWiki.
En mi caso lo realice de la siguiente manera: 


Descargamos el siguiente programa en su maquina: 

```bash
https://winscp.net/eng/download.php
```
![image](https://github.com/Calderon0911/MediaWiki-Setup-Guide/assets/69009908/e2097df1-5ba3-41a5-a4e4-53f3098d822c)

y conectamos a nuestro servidor por medio de SFTP para la transferencia del archivo LocalSetting.php. 

![image](https://github.com/Calderon0911/MediaWiki-Setup-Guide/assets/69009908/fed6eeee-dd17-4d4d-b55d-2c0b63417bf0)

![image](https://github.com/Calderon0911/MediaWiki-Setup-Guide/assets/69009908/edcc598b-ca58-4ce8-b9e4-22d8042e55f4)

![image](https://github.com/Calderon0911/MediaWiki-Setup-Guide/assets/69009908/f33d9acf-4d32-4587-9a0d-96033030090b)


Si lo desean pueden usar otro medio de transferencia como TFTP.

En mi caso guarde el archivo .php en mi usuario en el directorio /home/marioc/

Luego lo movi al directorio de MediaWiki con el siguiente comando: 

```bash
sudo mv LocalSettings.php /var/www/html/mediawiki/
```


### Luego de realizar esto podemos ingresar a su MediaWiki

Podemos ingrear a su pagina MediaWiki con el siguiente Link:

```bash
http://'Su direccion IP'/mediawiki/
```

![image](https://github.com/Calderon0911/MediaWiki-Setup-Guide/assets/69009908/fe017985-d00c-48ee-84f7-0aece64f3a23)

## FIN

