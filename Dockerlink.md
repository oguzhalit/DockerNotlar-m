#How links work
redis serverımızaa baglı makineler oluşturmak istersek link ler ile baglamamız
gerekir.
#docker run --link redis-server:redis alpine env
calısan docker serverımıza alpine makinesini baglarız.
env ekledigimiz için enviroment variablesı görebiliriz.

#docker run --link redis-server:redis alpine cat /etc/hosts
Docker, konteynerin HOSTS dosyasını kaynak konteynırımız için orijinal, takma ad ve karma kimliğinden oluşan üç adla güncelleyecektir. Kapsayıcı ana bilgisayar girdisini aşağıdakileri kullanarak çıktı alabilirsiniz

/etc/hosts dosyasında güncelleme yapıldıgını göreceksiniz.

baglantının başarı ile gerçekleştigini anlamak için ping atmayı deneyebiliriz.
#docker run --link redis-server:redis alpine ping -c 1 redisi
link oluşturuldugunda diger konteynırlar ile haberleşme konusnda sorun olmadıgını görebilriz.
#konteynırlar arasın baglantı olusturma konusunda biraz egzersiz yap
