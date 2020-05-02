Containerİmage
container imageları tar dosyları olarak dışarı aktarılabilir.
tar dosyası acıldıgında layerlar görülür.
docker save image_adı > redis.tar ile tar olarak aktarılaiblir.
manifest.json dosyasında layerlar ve repo hakkında bilgi verir.
tar -xvf layer.tar ilede layetların içindekileri görebilriz.
Create Empty Image
tar cv --files-from /dev/null | docker import - empty
içerini kontrol ettgimizde tamamen boş bir image oldugu için çalışmayacak
Creating image with dockerfile
busybox docker image oluştururken işimize yarayacak.
busybox'ı kök dosya sistemi oluşturmak için kullanacagız( temel Unix araçlarının sistemde yüklü olması gerekmektedir.İşte BusyBox paketinde bu araçların tümü son derece rafine bir şekilde bulunmaktadır. )
 Projenin temel hedefi, 1.44 MB'lık tek bir disket içerisine temel bir Linux kök dosya sistemini ve Linux kurulum uygulamasını sığdırmak idi.  Linux kurulum süreci, 2 disket ile başlıyordu. Birinci diskette Linux çekirdeği yer alıyordu. Kök dosya sistemi ise 2. disket üzerinden okunuyordu.rootfs and main binaries
./busybox-static busybox diyerek bi rootfs olursuturuyoruz
echo Deneme > busybox/release #sürüm bilgisini giriyoruz.
tar -C busybox -c . | docker import - busybox olusturdugumuz tar'ı import ederek image oluşturuyoruz

docker run busybox cat /release dedeigimizde 
deneme yazısı ekrana gelcektir.
