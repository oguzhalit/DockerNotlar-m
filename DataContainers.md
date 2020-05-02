Yapılandırma dosyalrımızı saklamak için bir image yapalım.

#docker create -v /config --name dataContainer busybox

verileri depolamak ve yönetmek için data container'lar kullanılır.

konteynırı olusturdukdan sonra dosyalırımızı konteynıra yollamak için
docker cp komutunu kullanabiliriz.

#docker cp config.conf dataContaienr:/config/

şimdi dataContainer'ımızı yapılandıralım.dockerda mount islemi için 
--volumes-from <container> opsiyonunu kullanıcagız.
Ubuntu konteynır çalıştırıp dataContainer'ımıza referenas vercez.

#docker run --volumes-from dataContainer ubuntu ls /config

eger ubuntu içide /config dosyası mevcutsa üzerine yazar.
Birden çok birimi bir kapsayıcıyla eşleyebilirsiniz.

dataContainerımızı taşımak istersek başka bir makinede kullanmak istersek
export import ile gerçekleştirebiliriz.
docker export dataContainer > dataContainer.tar
docker import dataContainer.tar
