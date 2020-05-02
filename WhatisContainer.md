#Processler#
Konteynırlar izole edilmiş processlerdir.
ppid
docker top contiar_name
pgrep dockerd
pstree
/proc/Program_pid/env
docker exec -it db env
#Namespaces#
unshare ilede kendi namaspace ortamını yaratabiliriz.
sudo unshare --fork --pid --mount-proc bash komutu ile.
Bir programın hangi namespaceleri kullandıgını görmek için
ls -lha /proc/program_pid/ns/ #burdan ogrendigimiz ile bilgi ile   |
komutunu kullanarak görebiliriz.                                   |
nsenter komutunu ilede ns'ler hakkında bilgi elde edinebiliriz.    |
docker exec -it con_adi sh ile girip bir dosya yaratalim           |
asagıdaki komut ile dosya içerigini okumaya çalışalım              |
nsenter --target $DBPID --mount --uts --ipc --net --pid ps aux   <-- bu komutu kullanara docker exec gibi çalıştırabiliriz.
nsenter komutu ile konteynıra komut yollayabilirz.
2 konteynırımız olsun bunları birbirine baglamak istedigimizde --net=container:c_adı seklinde diger konteynıra baglayarak acabiliriz.
Orn:

docker run -it --name ornek -d alpine #bir makine acalim.

docker run -it --name ornek2 --net=container:ornek -d alpine #ikinci makine ile birinci makinelerin agları birbirine bagladık.

ls -lha /proc/$pidornek/ns/
ls -lha /proc/$pidornek2/ns/ 

2 komutun cıktısını karşılaştırdıgımız. benzerlikler oldugunu görecegiz.

#Chroot#
https://www.cyberciti.biz/faq/unix-linux-chroot-command-examples-usage-syntax/
Yeni bir filesystem oluşturur, gördügü ve çalıştıgı dizini degiştirir.
Chrooting apache
Güvenli bir çalışma alanı ve test ortamı oluşturmak için chroot'a başvurulabilir.
Bir konteynırıda chroot ile izole çalıştırabiliriz. | 
                                                  <-|
docker pull image_adi                      #izole etmek istedigimiz image indirelim
docker run -it --name img_isim -d img_adi  #imagei calistirarlim
mkdir img_adi                              #chroot ortamono olusturalim
docker export img_isim > root.tar          #imagecımızı dışarı çıkartalım

for i in dev sys proc; do mount --rbind /$i ./$i; done

#gerekli dosyaları mount ederek sistemimizi çalıştıralım.

chroot . /bin/sh

artık izole docker ortamızın elimizde
#Cgroups(ControlGroups)#
Tüketilen kaynakların sınırlandrılması için kullanılır.
cat /proc/pid_id/cgroup
ls /sys/fs/cgroup
bununla ilgili bilgiler bu komutlar ile eldi edilebilir.
cat /sys/fs/cgroup/cpu,cpuacct/docker/$DPID/cpu.shares
docker stats db --no-stream
-----------------------------------------------------------
Docker'a biraz veri yazarak degişimi görelim
echo 8000000 > /sys/fs/cgroup/memory/docker/$DPID/memory.
limit_in_bytes

cat /sys/fs/cgroup/memory/docker/$DPID/memory.limit_in_bytes

degişime bakalm
------------------------------------------------------
#Seccomp / AppArmor #
AppArmor sistemin hangi bölümlerine erişilebilceginin tanılayan bir uygulama profilidir.
cat /proc/Pıd/attr/current
Seccomp hangi sistem çagrılarnın kullanılabilecegine dair sınırlama yapar.Çekirdek modülleri kurma ve izinleri degiştirme gibi özellikleri engelleyebilir.sistem çagrlarının engelleyebilir.
cat /proc/Pıd/status  | grep Seccomp
0 disabled 1 strict 2 filtering
#Capabilities#
işlemlerin ve kullanıcıların izinleri ile ilgilenir.
sistem saati,makine adı,sistem çagrıları  gibi durumları kapsar
cat /proc/pid/status | grep ^Cap ile görüntülerişlemlerin ve kullanıcıların izinleri ile ilgilenir
capsh --decode=00000000a80425fb ile neler kullandıgı görülebilir.
bitmask olarak saklanır.
