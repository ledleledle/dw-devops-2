Install aplikasi web server di komputer kamu, kemudian install php di web server tersebut (dilarang menggunakan aplikasi seperti xampp, lampp).

Pada praktek ini saya menggunakan Distro **Arch Linux** dan text editor **nano**.

1. Perbarui repository
<code>pacman -Sy</code>
2. Install nginx dan php-fpm php
<code>pacman -S nginx php-fpm</code>
3. Start nginx dan php-fpm
<code>systemctl start nginx.service php-fpm.service</code>
4. Edit konfigurasi nginx agar nginx dapat menjalankan php.
<code>nano /etc/nginx/nginx.conf</code>

Cari dan edit beberapa baris
```
location / {
      root /usr/share/nginx/html;
      index index.html index.htm index.php
}

...

location ~ \.php$ {
      fastcgi_pass   unix:/var/run/php-fpm/php-fpm.sock;
      fastcgi_index  index.php;
      root   /usr/share/nginx/html;
      include        fastcgi.conf;
 }
```
6. Restart nginx
<code>systemctl restart nginx.service</code>
7. Buat file **info.php**, untuk melakukak cek pada web server php.
<code>nano /usr/share/nginx/html/info.php</code>

Isi file **info.php** dengan perintah php. Misal :
```
<?php
phpinfo();
?>
```
8. Buka browser lalu buka halaman <a href="localhost">localhost</a> atau <a href="127.0.0.1">127.0.0.1</a> dan <a href="localhost/info.php">localhost/info.php</a>

Berikut video installasi yang saya lampirkan. <a href="https://github.com/ledleledle/dw-devops-2/raw/main/soal-06/06-video.mkv">Video Installasi Web Server</a>
