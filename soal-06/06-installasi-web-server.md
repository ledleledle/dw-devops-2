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
5. Cari dan edit beberapa baris
```
location / {
			root /usr/share/nginx/html;
			index index.html index.htm index.php
}

location ~ \.php$ {
      fastcgi_pass   unix:/var/run/php-fpm/php-fpm.sock;
      fastcgi_index  index.php;
      root   /usr/share/nginx/html;
      include        fastcgi.conf;
 }
```

6. Restart nginx
<code>systemctl restart nginx.service</code>