Deploy sebuah project yang telah Kami sediakan ke Heroku menggunakan heroku-cli sertakan screenshot dan deskripsikan step by step-nya atau record menjadi video.

Clone app dari repository yang telah disediakan
```
git clone https://github.com/sgnd/todo-app.git
```
Lalu pergi ke directory todo-app
```
cd todo-app
```
Buat heroku app dengan buildpack
```
heroku create leon-todo --buildpack mars/create-react-app
```
Edit file <code>package.json</code> untuk installasi nodejs dengan versi yang spesifik
```
"engines": {
      "node": "10.x"
   }
```
Push repository ke heroku
```
git add .
git commit -m "push pertama"
git push heroku master
```
Tunggu beberapa saat, jika sudah selesai buka app yang sudah berhasil dideploy dengan perintah <code>heroku open</code>

Berikut dokumentasi video. <a href="https://github.com/ledleledle/dw-devops-2/raw/main/soal-07/07-video.mkv">Video Deploy Heroku</a>