Docker Networks
Bir ag kartı olustuaralım.
#docker network create backend-network
backend-network adında bir ag olusturduk.
olusturdugumuz kartı 
#docker network ls  ile görebilriz.
şimdi oluşturdugumuz ag ile bir konteynır çalıştıralım.
#docker run -d --name=redis --net=backend-network redis

agların haberleşmesi
linkle konteynırları bagladıgımızda cat /etc/hosts dosyasını kontrol ettigiizde
baglantıların hosts üzerinden yapıldıgını görmüştük.
Dns sunucusu aracılıgıyla iletişim kurdukları için 
/etc/resolv.conf dosyasında degişim oldugunu görebiliriz.
#docker run --net=backend-network alpine cat /etc/resolv.conf
konteynırlar diger konteynırlara erişmek istediginde dns server'da bilinenlere
erişim yapabilecek. ping atacak.kontrol için.
#docker run --net=backend-network alpine ping -c1 redis

konteynırlarda birden fazla network baglantısı desteklenir.
#docker network create frontend-network bir ag dha olusturalım
bu agı bir konteynıra baglayalım.
#docker network connect frontend-network redis
bunu redis'e baglayalım.

#docker run -d -p 3000:3000 --net=fronted-network webserver/node-example
web sunucumuzla aynı aga baglı oldugu için redisle iletişim sorun çıkarmayacaktır.

#alias kullanarak konteyner baglama
#docker network create frontend-network2
#dockere network connect --alias db frontend-network2 redis
#docker run --net=frontend-network2 alpine ping -c1 db
#docker network inspect frontend-network ile ip adreslleri ile ilgili detayı bilgi ögreneiblirz.
#docker network disconnect frontend-network redis ile aradaki baglantıyı koparabilriz.
