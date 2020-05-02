Bütün konteyner image'ları base image ile baslar.
Docker registry'lerden bu imagalar çekilerk kullanılabilir
FROM image-name:tag #ile base image belirleriz.
base image'i belirledik.şimdi hangi komutlar ile başlayacagı ve neler
yapabilcegine bakalım.2 ana komut kullanacagız
COPY ve RUN
RUN konteynırda herhangi bir komut çalıstırmamıza izin verir.
pket indirmek ve build etmek için bunu kullanabiliriz.
image'e dahil edileceginden gereksiz kullanımlardan kaçınmak önemlidir.
COPY konteynıra çalışma alanımızı kopyalamak için kullanılır.
EXPOSE ile docker'ın hangi porttan baglnacagını belirleriz.
CMD ile dockerfile'da commandlar çalıştırabilriz.arg'man gerektrien komutları
bir dizi şeklinde belirterek çalıştıabiliriz.
CMD ve ENTRYPOİNT farklarını arastır.
