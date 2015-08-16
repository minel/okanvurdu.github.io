---
layout: post
title: PostgreSQL'de Rolleri Yönetme
date: '2015-02-22 20:11:20'
---

Uygulamalarımız için yaptığımız veritabanı bağlantı ayarlarında genellikle şu 3 temel bilgiyi vermemiz beklenir:

* Veritabanı servisimizin adresi
* Bu serviste oturum açabilmek için kullanıcı adı ve parola
* Bağlantının sağlanacağı veritabanının adı

Bu noktada dikkatimizi çekmesi gereken husus; nasıl ki farklı her uygulama için yeni bir veritabanı oluşturuyorsak, bu uygulamaya ait veritabanı kullanıcıları oluşturmak da "olsa güzel olur" diyebileceğimiz tarzda bir durum.
<!--more-->

Birden fazla uygulamayı yürütürken tek bir kullanıcı kullanmak elbette mümkün fakat herhangi bir veritabanına sadece onunla ilgili uygulama üzerinden erişimi denetlemek çok daha sağlıklı ve güvenli bir harekettir.

Bu blog yazısında bir PostgreSQL rolünü nasıl kullanılabilir hale getirebiliriz onu irdeleyeceğiz.

> Öncelikle bu işlemi `Ubuntu 14.04.1 LTS` yüklü bir sunucuda gerçekleştirdiğimi belirtmek isterim.

* İlk olarak bir Terminal (ya da kendi kabuk programınız) penceresi açalım.
* PostgreSQL kurulumunda (bilgisayarınızda yüklü değilse [şuraya](http://blog.okanvurdu.com/hizlica-postgresql-kurulumu/) gidebilirsiniz) otomatik olarak "postgres" adlı bir kullanıcı sisteminize tanımlanmaktadır. Şimdi `su - postgres` komutunu yürüterek bu kullanıcıya geçiş yapalım.
* Şimdi ise `psql` komutunu yürüterek PostgreSQL'in kabuk üzerinde çalışır hale getirilmiş programcığını çalıştıralım.

Buraya kadar olan adımlar PostgreSQL komutu çalıştırmak için hazırlık yaptığımız adımlardı. Artık rol tanımlamak için tüm saha şartları hazır.

* Bir rol tanımlamadan önce sistemimizde hangi roller tanımlı onları görmekte fayda var. Bunun için `\du` komutunu yürütünüz. Şuna benzer bir çıktı almalısınız:

![\du komutu yürütüldüğünde karşılaşılacak çıktı](/img/posts/psql-command-running.png)

Gördüğünüz gibi karşımıza tanımlı roller ve yapabilecekleri işleri (yetkilerini) içeren bir liste geldi. Buradaki `postgres` rolü kurulumla birlikte gelen varsayılan roldür. Bu rol ile benim daha önceden oluşturmuş olduğum rol arasındaki yetkisel farkları gözlemleyebilmektesiniz.

Şimdi `test` adını verdiğimiz ve `test*2015!` parolasına sahip bir rolü nasıl oluşturabiliriz birlikte inceleyelim.

{% highlight sql %}
CREATE ROLE test LOGIN PASSWORD 'test*2015!' CREATEDB;
{% endhighlight %}

Yukarıda yazmış olduğum komut tam olarak bu işi yapmak için uygundur. Burada dikkat etmeniz gereken nokta satır sonuna noktalı virgül (;) koymanız gerektiğidir. Aksi halde PostgreSQL yazdığınız komutun bitmediğini, yazmaya devam edeceğinizi düşüneceği için komutun çıktısını göremeyeceksiniz.

Şimdi bir de komutu yürütüp çıktısını inceleyelim:

![Komutun çıktısı](/img/posts/after-running-command.png)

Komutu yürüttükten hemen ardından varolan rolleri görmemizi sağlayan `\du` komutunu bir kez daha yürüttüm.

Gördüğünüz gibi `test` kullanıcımız `CREATEDB` yetkisi ile birlikte rollerimiz arasında yerini aldı.

Buraya kadar her şey yolunda. Peki bu kullanıcının yetkilerine nasıl müdahale edeceğiz?

Bunun için anahtar kelime `ALTER`. Tahminimce `ALTERATION (Değişiklik)` kelimesinin kısa bir hali.

Aslında SQL sözdiziminde (syntax) `ALTER` değiştirilmek istenen her ögenin başında yer alır. Özetle `ALTER` rolleri yeniden yapılandırmaktan daha geniş bir kapsama sahiptir. (tabloları, alanları yeniden yapılandırmak vb.)

{% highlight sql %}
ALTER ROLE test NOLOGIN;
{% endhighlight %}

Bir üst satırda `test` isimli kullanıcımızın LOGIN yetkisini elinden almak için gerekli komutu hazır hale getirdik. Şimdi yine bu komutu yürüterek çıktısını gözlemleyelim:

![Rolü yeniden yapılandırdıktan sonra](/img/posts/alter-role-command.png)

Gördüğünüz gibi artık `test` rolünün yanında *"Cannot login"* yani *"Giriş yapamaz"* yazıyor.

Kısacası bir yetki, yukarıda gördüğünüz şekilde değiştirilebiliyor. Yetkiler üzerinde yapabileceğiniz değişiklikleri içeren resmi dökümana [şuradan](http://www.postgresql.org/docs/9.0/static/sql-alterrole.html) erişmeniz mümkün.

Son olarak oluşturduğumuz rolü ortadan kaldırmayı da inceliyoruz.

{% highlight sql %}
DROP ROLE test;
{% endhighlight %}

Haydi, hemen yürütelim şunu!

![Rolü ortadan kaldırdıktan sonra](/img/posts/drop-role-command.png)

Artık `test` isimli rolümüze veda etmiş olduk.

Üstten bir bakacak olursak, bu yazı sonunda;

* Bir rol oluşturmak
* Rolü değiştirmek
* Rolü ortadan kaldırmak

bilgilerine sahip olduk.

Yazıyı burada noktalarken aklınızda yer eden soruları hemen aşağıda tartışabileceğimizi bilmenizde fayda var.

Görüşmek üzere!
