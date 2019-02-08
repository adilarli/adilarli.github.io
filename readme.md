# Ghost Wordpress’i Tahtından indirebilir mi ? 👻

Wordpress anketlere göre dünya genelinde CMS’ler arasında %60'lık bir orana
sahipken tüm siteler arasında %30'luk bir oranla bütün ekosistemi domine ediyor.
Bu rakamlar bize tahtından kolay kolay inmeyeceğini sadece küçük sallantılar
olacağını bize net bir şekilde
gösteriyor.[*](https://w3techs.com/technologies/overview/content_management/all)

![](https://cdn-images-1.medium.com/max/800/1*__xEgvYGZn4xKUwYKVAQxg.png)

Benim bu yazıyı yazma sebebime gelecek olursak geçtiğimiz haftalar yine mevcut
işlerden sıkıldığım bir anda farklı bir şeyler ile uğraşmak istedim. 2012
yılından bu yana ne zaman bu boşluğa düşsem adilarli.com’u biraz kurcalarım. Bu
sefer biraz daha farklı bir tecrübe için wordpress’den başka bir alt yapıya
geçmek istedim fakat ne kullanacağım hakkımda hiç bir fikrim yoktu. Farklı
projeler için bir çok cms’i inceleyip, kurup hatta bencmarklara kadar
araştırdım. Kurulumu bitirdikten sonra bir süre hiç dokunmayacağımı bildiğim
için lightweight bir yapı seçip hızlı bir şekilde sonuçlandırmak istiyordum (
Olmadı ).

[Ghost](https://ghost.org/)** son dönemlerde beni en çok etkileyen işlerden biri
oldu.**

![](https://cdn-images-1.medium.com/max/800/1*guR2mLJUI4y_ZxKpuYw5Xw.gif)

> Eski wordpress takımından [@johnonolan](https://medium.com/@johnonolan)
> tarafından 2012'de geliştirilmeye başlanmış. 2013 Yılında ilk release için
KickStarter’da 25.000 sterlinlik bir kitle fonlama talebinde bulunmuş ve 9
saatte hedef rakama ulaşmış hatta bununlada kalmayıp kalan 29 Günde yaklaşık
olarak 200.000 Sterlin daha toplamış. Bu sürede önemli destekçileri arasında
Seth Godin, Leo Babauta, Darren Rowse, Tucker Max, WooThemes, Envato ve
Microsoft gibi büyük şirketler olmuş.
[*](https://www.kickstarter.com/projects/johnonolan/ghost-just-a-blogging-platform)

![](https://cdn-images-1.medium.com/max/600/1*xJOu6US8I4p7okdobdxs2A.png)

Biraz inceleme sonrasında ghost’u kullanmak konusunda kesin karar verdim. Sırada
nasıl kullanacağıma karar vermek vardı. [Ghost Pro](https://ghost.org/pricing/)
36$’lık fiyatı ile Güncel kur göz önünde bulundurulunca ilk dakikadan elendi :)
. Bir sonraki seçenek Cloud servislerden birini seçip onun üzerinden
ilerlemekti. Digital Ocean’da One-click applications seçenekleri arasında mevcut
dakikalar içerisinde kurulumu bitirebilirsiniz. Fakat yoğun bir trafik almayacak
bir sayfa için bir droplet kullanmak resmen teknoloji israfı olacaktı. O sırada
bir ampül yandı ve bunu github.io üzerinde host etmenin çok kolay olacağını
farkettim. Çok sık güncelenmeyen bir sayfa olduğu için static dosyaları github
repo’ya commitlersem, SSL dahil tamamen Free olarak host edebilirdim. Tabikii
benim gibi başka düşünenler de olmuş ve Ghost için python kullanarak bir static
file generator yazmışlar adınıda “ Ghost Buster ” koymuşlar. İsmi için bile
kullanılmaya değer.

![](https://cdn-images-1.medium.com/max/800/1*K1MCut8qHZ7EhHH74ThadQ.png)
<span class="figcaption_hack">Tercih eden markalardan bazıları</span>

# Ghost Github Pages’de nasıl yayınlanır ?

![](https://cdn-images-1.medium.com/max/800/1*3XiiM4LkVSDAYbttjl-RmA.jpeg)

### Kurulum

Ghost ve Buster için yeteri kadar döküman var, ancak kurulum esnasında bu işlemi
daha kolaylaştıracak birkaç adım olduğunu gördüm, sizinle onları paylaşacağım.

* Node, diğer projeleriniz için daha eski veya daha yeni node sürümlerini
çalıştırabilmek için nvm (node sürüm yöneticisi) kullanmanız gerekebilir.
* Python ve pip (Python paket yöneticisi).

![](https://cdn-images-1.medium.com/max/800/1*ztvLIhgC--yeuI0Xm7Mv2A.png)
<span class="figcaption_hack">Ghost Feature Diagram</span>

**Ghost Kurulum**<br> Öncelikle, npm kullanarak Ghost CLI araçlarını kurmamız
gerekiyor, eğer nvm kullanıyorsanız, bunu çalıştırmadan önce v6.5.0 veya önceki
sürümlerinin seçtiğinizden emin olun:

    npm install -g ghost-cli

Sonrasında Ghost’u kuracağınız dizine gidin :

    ghost install local

Bütün bağımlıkları sorunsuz olarak indirip sonrasında kurulumda bir hata
almazsanız Ghost blogunuzu ve sunucunuzu local olarak başlatır. Daha sonra http:
//localhost:2368 adresinde ulaşabilir, okuyabilir, düzenleyebilir, silebilir ve
yeni yazılar oluşturabilirsiniz.

Adınızı, blog bilgilerinizi ve blog yayınlarınız hakkındaki diğer verileri
ayarlamak için kontrol paneline (http://localhost:2368/ghost ) adresinden
ulaşabilirsiniz.

**Sonuç;**

**Buster Kurulum**Blogumuzu yerel olarak çalıştırdığımıza göre, statik sayfaları
ve asetleri yakalamak için bir yola ihtiyacımız var. Yerel olarak çalışan Ghost
blogunuzda bulabildiği tüm sayfaları etkili bir şekilde çalıştırır ve sayfaları
statik HTML olarak kaydeder. Ayrıca, CSS ve JS asetleri, blogunuzdaki sayfalarda
pathleri de günceller.

Buster kurulumu için ;

    pip install buster

Kurulum hata almadan tamamlanınca aşağıdaki komutu çalıştırıyoruz ;

    buster setup

Özel bir tanımlamaya ihtiyacınız yoksa enter ile bu işlemi tamamlayabilirsiniz.

İlk dosyaları oluşturmak yada Ghost’da bir değişiklik yaptığımızda, yeni bir
içerik eklediğimizde generate komutunu çalıştırmak yeterli olacaktır ;

    buster generate --domain=

Buster, tüm blog sitenizi /static adındaki bir klasöre static dosyalar olarak
oluşturur. Artık bu klasörü her hangi bir web sunucusunda barındırarak sitenizi
yayınlayabilirsiniz.

**Github Pages Kurulum** Github üzerinde yayınlamak için tek yapmanız gereken
ilgili komutu çalıştırmak;

    buster deploy

Gerekli cname ayalarını tamamladığınız zaman github pages üzerinde kendi
domaininiz ile ssl olarak sayfayı yayınlayabilirsiniz

<span class="figcaption_hack">github pages custom domain ve ssl ayarları</span>

### Extra

Docker’da çalıştırmak için örnek dockerfile ;

    FROM ghost:lastest

    MAINTAINER Adil Arlı <
    >

    RUN apt-get update && apt-get install -y — no-install-recommends \
     nano \
     python \
     python-pip \
     git \ 
     && \
     apt-get clean && \
     rm -rf /var/lib/apt/lists/*
    RUN pip install — upgrade setuptools
    RUN pip install buster

