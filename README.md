# Giriş

## Kurulum

```

```

### Docker içinde en çok kullanılan komutlar.

```
-docker version => docker versiyon bilgisi döner
-docker info => O an sistemde çalışan docker bilgilerini vermek için kullanılır.
-docker => docker cli’da kullanabileceğimiz komutları listelemek için kullanılır.

-docker image —help => help komutu image’in altında ki diğer seçenekleri kullanımı hakkında bilgi vermek için kullanılır.
-docker image rm —help => image altında rm seçeceği altında kullanılabilecek seçenekleri göstermek için kullanılır.
-docker container ls -a => Sistem kullanılan container’ları listelemek için kullanılır -a demek tümünü göster demek -a yok ise sadece çalışan container görüntülenir.

-docker ps ile docker container ls aynıdır
-docker ps -a ile docker container ls -a aynıdır


-docker container rm -f [id] bu komut çalışan container silmenizi sağlar
-docker container prıne => sistemde çalışan stop haldeki tüm containerları siller


```


### Docker Volume Nedir ?
Container içindeki dataları loglamaları kalıcı hale getirmek için kullandığımız yapıdır. Container'lar sürekli olarak silindiği için volume'lar üzerinden logları yönetebiliriz.

#### Yeni bir tane volume oluşturmak için

```
docker volume create first-volume
```

### Docker Compose Nedir?
