# Install dan Konfigurasi Web Server Apache

## Instal Web Server Apache
```
sudo apt update
sudo apt install apache2
```
## Periksa Pengaturan Web Server
```
sudo service apache2 status

hostname -I
```


## Manajemen Proses Web Server Apache
* perintah dijalankan ketika menggunakan VirtualBox
```
sudo systemctl stop apache2
sudo systemctl start apache2
sudo systemctl restart apache2
sudo systemctl reload apache2
sudo systemctl disable apache2
sudo systemctl enable apache2
```

## Setup Virtual Hosts  
file project apache2 ada di direktori `/var/www/html`
```
sudo mkdir -p /var/www/example.lokal/html
sudo chown -R $USER:$USER /var/www/example.lokal/html
sudo chmod -R 755 /var/www/example.lokal
nano /var/www/example.lokal/html/index.html
```
isi file `index.html`
```
<html>
    <head>
        <title>Selamat Datang di situs Saya!</title>
    </head>
    <body>
        <h1>Pengaturan Server di Situs Saya telah berhasil!!!</h1>
    </body>
</html>
```


## Mengatur file konfigurasi  
File konfigurasi apache2 default berada di `/etc/apache2/sites-available/000-default.conf`.  
Coba buat file konfigurasi baru `/etc/apache2/sites-available/example.lokal.conf`, lalu isi file konfigurasi seperti berikut:
```
<VirtualHost *:80>
    ServerAdmin admin@example.lokal
    ServerName example.lokal
    ServerAlias www.example.lokal
    DocumentRoot /var/www/example.lokal/html
   ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```


## Mengaktifkan file konfigurasi
```
sudo a2ensite example.lokal.conf
```


## Menonaktifkan file konfigurasi default `000-default.conf`
```
sudo a2dissite 000-default.conf
```


## Cek file konfigurasi
```
sudo apache2ctl configtest
```


Jika berhasil akan muncul pesan `Syntax OK`  
## Restart service apache2
```
sudo systemctl restart apache2
```

# Coba akses pada browser
---

# Setting Hosts di Windows
File hosts ini digunakan untuk konfigurasi penamaan DNS pada VM yang kita punya. Nantinya kita bisa mengakses VM tanpa harus ketik IP Address dari VM, cukup panggil nama Domain saja.  
File config hosts berada di 
```
C:\Windows\System32\drivers\etc
```

