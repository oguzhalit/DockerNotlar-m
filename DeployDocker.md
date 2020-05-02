DockerHub'a giris
bütün konteynerlar docker image'ını baz alarak başlar.
docker search image_name ile docker imagelarını arayabiliriz.
aradıgımızda bircok image oldugunu görürüz.Official olan sürümü genelde tercih edilmesi gerekir.
Docker image'ını arkada planda çalıştırmak için -d parametresini kullanırız.
docker run -d redis olarak çalıştırdıgımızda bir cıktı üretmez
docker ps ile kontrole ettigimizde arka planda çalıştıgını görüürüz.
docker inspect ile konteynırımız hakkında daha detaylı bilgi alabiliriz.
docker logs ile konyeynıırımızın cıktılarını görürüz.
Konteynırımız çalışıyor ama biz ona şuanda erişemiyoruz.bunun için
konteynırı çalıştırırken cıkıs portunu belitmemiz gerek.
docker run -d --name RedisHostPort -p 6379:6379 redis:latest
6379'portunu localimizdeki 6379 yönlendirerek erişim vermiş olduk(mapping)
Konteynırlarda Çalışırken Kalıcı Veriler
konteynırlar stateless olarak tasarlanmıştır.içinde veri barındırmak cok mantıklı degildir.o yüzden bazı dizinleri konteynırımıza baglarız.
bu sekilde konteynır içine degil local makinemizde verileri kullanabiliriz.
bu saye veerilerimizi kaypetmeden konteynırları degiştirebiliriz.
Konteynırda kullandıgımız programların nelerelde verileri sakladıgını bulup 
kendi lokalimizi map'lememiz sorunu çözecektir.
docker run -d --name deneme -v "$PWD/data:/data" redis
ile bulundugumuz dizinde ki data klasörünü konteynırdaki redis'e baglyarak 
çıktıları kendi localimize alabiliriz.
Konteynıra erişim.
şimdiye kadar konteynırlar hep arkaplanda çalıştır peki onlara erişmek
istedigimizde ne yapacagız.
docker run ubuntu ps #dedigimizde konteynırımız ps komutunu çalıştırıp kapanacaktır.
docker run -it ubuntu bash #komutu ile interactive bir tty oluşturup bash ile
termial ekrarnına giriş yapmış olacagız.
