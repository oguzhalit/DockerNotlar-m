Dockerda hassas bilgilerinizin yanlışlıkla image'larınızın içinde unutabilirisiniz.
bunu çözmek için dockerignore kullanabiliriz.
'
$ cat Dockerfile
FROM alpine
ADD . /app
COPY cmd.sh /cmd.sh
CMD ["sh", "-c", "/cmd.sh"]
$ cat
.dockerignore  Dockerfile     cmd.sh         passwords.txt
'
docker build -t password .
docker run password ls /app
password dosyamız erişilebilir olcak.

bunu engellemek için
echo passwords.txt >> .dockerignore
yönlendirmesinden sonra tekrar build işlemini gerçekleştiriri.
docker build -t nopassword .
docker run nopassword ls /app #ile password dosyası görülmez olur.
Paroları run komutu ile çalıştırmak gerekiyorsa kopyaladıkdan sonra silmeniz gerek.
image'ın sadece son durumu korunur.

Docker Build Bağlamına gönderilmesini istemediğimiz dosyaları hariç tutmak için kullanabiliriz.
echo big-temp-file.img >> .dockerignore
daha küçük boyutlarda dosya oluşturmaya ve optimizasyona yara.

dockerignore hassas ayrıntıların image'e dahil edilmesini engeller.
