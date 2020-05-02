#Bir uygulmayı dockerize etmeye çalıştıgımızda,o uygulamanın bagımlılıklarını
barındıran bir base image secmemiz lazım.
bizim nodejs için sececegimiz docker image node:10-alpine.
WORKDIR calistma dizini tanımlamak için kullanırız.
bunun için mkdir komutunda calisma dizini olusruuyoruz.

FROM node:10-alpine
RUN mkdir -p /src/app
WORKDIR /src/app

seklinde bir calisma dizini tanımlanım image olusturulur.

önceki uygulamamızda bir server image olusturmusturduk.
#bu bölümde bagımlılıklara ihtiyac duyan bir uygulama çalıştırcagız.

COPY package.json /src/app/package.json

RUN npm install


COPY . /src/app

EXPOSE 3000

CMD [ "npm", "start" ]

Docker environment variables çalış
-e parametresi ile env tanımlayabiliriz.

DockerFileOptimizasyonu konusunda araştır.
https://www.digitalocean.com/community/tutorials/how-to-optimize-docker-images-for-production

https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

https://medium.com/@esotericmeans/optimizing-your-dockerfile-dc4b7b527756
https://medium.com/better-programming/optimizing-docker-image-creation-fa06bb42733d




