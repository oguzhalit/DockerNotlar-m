DockerFile
docker file'da image'ımızın icinde barındırmak istedikerimizi
barındırıyoruz.docker file'a uygulamayı nasıl dagıtıcagımızı söyleriz.
Dockerfile içersine yazdıgımız
FROM nginx:alpine #ile hangi dagıtımda hangi uygulamayı kullanacagımız belirtir
COPY . /usr/share/nginx/html # bulundugumuz dizindeki dosyaları konteynır içinde /usr/share/nginx/html içersine atarız.dosyayı kaydedeip kapatır.
Docker cli ekrarnına geliriz.
docker build -t webserver:v1 . #diyerek bulundugumuz dizin içersinde
ki docker file'u build ederek tag veririz.
docker images ile kontrol ettigimizde vermigiz tag'e ait image'ı görebiliriz.
şimdi uygulamamızı yayına alalım.
docker run -d -p 80:80 webserver:v1 #komutu ile çalıştırırız.
