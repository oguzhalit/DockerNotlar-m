Docker Log
 docker logs image_adi ile logları inceleyeiliriz.
 veya docker run -d --name deneme --log-driver=syslog redis logları baglayabiliriz.
 dcker logları syslog'a yönlendirelecektir.
 docker inspect --format '{{.HostCOnfig.LogConfig }}' redis-syslog ile lgları nereye bastıgını görebilriiz.
 EnsuringUptime
 docker run -d --name restart-always --restart=always scrapbook/docker-restart-example
 hata olursa otomatik olarak kendini yeniden başlatır
 farklı kullanımlar ile istedigimiz kadar tekrar başlatabiliriz.
 docker run -d --name restart-3 --restart=on-failure:3 scrapbook/docker-restart-example
 farklı kullanımlar ile denyebiliriz.
 
 docker ps --format 'table {{.Names}}\t{{.Image}}'
 ile calisan imageları görebiliriz.
 
 docker ps -q | xargs docker inspect --format '{{ .Id }} - {{ .Name }} - {{ .NetworkSettings.IPAddress }}'
 calisan makinelerin ipleri hakkında bilgi alabiliriz.
