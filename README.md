# Giriş

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

build: Belirtilen image’ı build edip yükler.

```

### Container
Docker Daemon tarafından Linux çekirdeği içerisinde birbirinden izole olarak çalıştırılan process’lerin her birine verilen isimdir. Virtual Machine (Sanal Makina) analojisinde Docker’ı Hypervisor’e benzetirsek fiziksel sunucu üzerinde halihazırda koşturulmakta olan her bir işletim sisteminin (sanal sunucunun) Docker’daki karşılığı Container’dır. Container’lar milisaniyeler içerisinde başlatılabilir, istenen herhangi bir anda duraklatılabilir (Pause), tamamen durdurulabilir (Stop) ve yeniden başlatılabilirler.

### Image ve Dockerfile

Docker Daemon ile çalıştırılacak Container’ların baz alacağı işletim sistemi veya başka Image’ı, dosya sisteminin yapısı ve içerisindeki dosyaları, koşturacağı programı (veya bazen çok tercih edilmemekle birlikte programları) belirleyen ve içeriği metin bazlı bir Dockerfile (yazımı tam olarak böyle, ne dockerfile ne DockerFile ne de DOCKERFILE) ile belirlenen binary’ye verilen isimdir.

Docker, koşturulacak Container’ların iskeletini oluşturan her bir Image’ın bir Dockerfile ile tanımlanmasını gerekli kılar. Bu Dockerfile içerisinde Image’ın hangi Image’ı baz aldığı (miras aldığı), hangi dosyaları içerdiği ve hangi uygulamayı hangi parametrelerle koşturacağı açık açık verilir. 

### Docker Daemon (Docker Engine)

Docker ekosistemindeki Hypervisor’ün tam olarak karşılığıdır. Linux Kernel’inde bulunan LXC’nin yerini almıştır. İşlevi Container’ların birbirlerinden izole bir şekilde, Image’larda tanımlarının yapıldığı gibi çalışmaları için gerekli yardım ve yataklığı yani ortamı sağlamaktır. Container’ın bütün yaşam döngüsünü, dosya sistemini, verilen CPU ve RAM sınırlamaları ile çalışması vb bütün karmaşık (işletim sistemine yakın seviyelerdeki) işlerin halledildiği bölümdür.

### Docker CLI (Command-Line Interface) - Docker İstemcisi

Kullanıcının Docker Daemon ile konuşabilmesi için gerekli komut setini sağlar. Registry’den yeni bir Image indirilmesi, Image’dan yeni bir Container ayağa kaldırılması, çalışan Container’ın durdurulması, yeniden başlatılması, Container’lara işlemci ve RAM sınırlarının atanması vb komutların kullanıcıdan alınarak Docker Daemon’e teslim edilmesinden sorumludur. Bu blog’un ilerleyen bölümlerinde sık sık Docker CLI’ı kullanarak Docker’ı tanımaya devam edeceğiz.

### Docker Registry

Zaten bir teknoloji harikası olan Docker’ı daha da kullanılabilir ve değerli kılan bir özellik bütün açık kaynak sistemler gibi paylaşımı özendirmesi, adeta işin merkezine koymasıdır. DockerHub‘da topluluğun ürettiği Image’lar ücretsiz ve sınırsız indirilebilir, oluşturulan yeni Image’lar gerek topluluk ile gerekse kişisel veya şirket referansı için açık kaynaklı (ücretsiz) veya kapalı kaynaklı (ücretli) yüklenebilir ve sonradan indirilebilir. Cloud’da hizmet veren DockerHub’ın yanında Image’larını kendi Private Cloud’unda tutmak isteyenler için Docker’ın sunduğu Private Registry hizmeti de vardır.

Sözün özü Container’lar Image’lardan oluşturulur. Image’larsa ortak bir eforun sonucu olarak meydana gelir ve Docker Registry’lerde tutulur. Örnek olarak, Ubuntu’nun üreticisi Canonical DockerHub’da Official Repository’ler tutmakta ve Ubuntu versiyonlarını bu repository‘lerde yayınlamaktadır. Ubuntu Image’ını kullanarak bir Container oluşturmak isteyen kişiler direkt olarak bu Image’ı kullanabilirler. İkinci bir kullanım senaryosu olarak, sağlanan bu Ubuntu Image’ını kullanarak başka bir işlev gerçekleştiren, örneğin Nginx ile statik web server hizmeti veren, bir Image yaratıp bunu DockerHub’da yayınlamak, yani hem kendi hem de başkalarının kullanımına sunmak verilebilir.
### Docker Repository

Bir grup Image’ın oluşturduğu yapıdır. Bir repository’deki değişik Image’lar Tag’lanarak etiketlenir böylece değişik versiyonlar yönetilebilir. İlerleyen bölümlerde Image versiyonlama konusunda örnekler vereceğiz.


### Docker Volume Nedir ?
Container içindeki dataları loglamaları kalıcı hale getirmek için kullandığımız yapıdır. Container'lar sürekli olarak silindiği için volume'lar üzerinden logları yönetebiliriz.

#### Yeni bir tane volume oluşturmak için

```
docker volume create first-volume
```

### Docker Compose Nedir?
Docker Compose , container içinde çalışabilen uygulamaların, tek bir komutla ayaklandırılıp durdurulabilmesine olanak sağlayan “yml” tabanlı bir dosyadır. “version”,”services”,”networks” ve “volumes” olarak tanımlanan 4 ana parçacıktan oluşur.

### Docker Bind Mount Nedir ?

Volume kavramının yetenekleri kısıtlanmış hali olarak tanımlanabilmektedir. Sadece runtime zamanında kullanılabilmektedir. Ve aslında host üzerinde bulunan bir alanın containera bağlanması anlamına gelmektedir.

