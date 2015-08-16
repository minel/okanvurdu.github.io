---
layout: post
title: Jekyll "is_post" kontrolü
date: '2015-08-16 20:11:00'
---

Merhaba, bu yazımda blogumu Ghost'tan Jekyll'e göç ederken karşılaştığım bir problem ve çözüm önerisinden bahsedeceğim.

Unutmadan; bunun bir çözüm yolu olduğunu ve daha efektif çözümler üretilebileceğini belirtmek lazım. Şimdilik gayet kullanışlı.

Ghost ile birlikte kullandığım temayı fazlasıyla sevdiğimden dolayı Jekyll'da da kullanmak istedim. Sonrasında bu işin oluru (aslında eforu) nedir diyerekten her ikisinin de tema düzenlerini inceledim. Gördüğüm kadarıyla arada uçurum yoktu, fakat yine de değişmesi gereken bir hayli kısım mevcuttu.

En basitinden, Ghost içindeki tema motorunun mantıksal ifadeleri işleme ve bir gönderiye ait içeriği bastırma şekli Jekyll'dan biraz farklıydı.

Aynı zamanda Ghost'un birden fazla temayı aynı anda kullanılabilir halde sunan bir yapısı varken, Jekyll aynı anda tek bir temayı kullanmaya müsade ediyordu. (Bu noktada her ikisinde de temalara ait dizin yapılarının farklı olduğunu gözlemleyebiliriz.)

Belki de Jekyll için birden fazla temayı aynı anda kullanmayı sağlayacak bir yapı mevcuttur. Benim bahsettiğim durum `jekyll new proje-adi` sonrası sunulan yapı ile alakalı.


Her neyse, buraya kadar bahsettiğim kısım efor hakkında az da olsa bilgi vermiştir diye düşünüyorum. Şimdi gelelim probleme;

Siz şu an bu yazıyı görüntülerken, sol tarafta anasayfaya yönledirilmenizi sağlayacak bir "Geri" bağlantısı görmektesiniz. Sol taraftaki "sidebar" olarak nitelendirilen menü, üzerinde çalıştığım Jekyll projesi dizinindeki `_includes/header.html` içerisinde oluşturulmaktadır. Bu "Geri" bağlantısının yazı sayfalarında görünmesi iyi hoş da, peki anasayfada görüntülenmemesi için ne yapmak gerek? İşte kilit soru bu. Sizi şöyle alalım:

- İlk değişikliğimizi Jekyll projemizin ana dizini altındaki `_config.yml` da yapacağız.

{% highlight bash %}
defaults:
  -
    scope:
      path: ""
      type: "posts"
    values:
      is_post: true
{% endhighlight %}

Yukarıdaki girdiği dosyanın en altına yapmanızda fayda var. Şimdi burada aslında ne yaptık onu irdeleyelim.

Projemizde tipi "post" olan her şey için `is_post` adında bir değişkene `true` değeri verilmesini sağladık. Yani bütün yazılara, sen yazısın belirtmesini yaptık. Bu tarz atamaları diğer tipler için de yapmanız mümkün; keyfinize kalmış.

Şimdi "Geri" düğmesini oluşturacak kısımda nasıl bir kontrol yaptık, ona bakalım. Benim projemde değişiklik, yukarıda da bahsettiğim gibi `_includes/header.html` üzerinde olacaktır.

Girdi ise şöyle:
![Gerekli düzenlemeler](/img/posts/jekyll_is_post.png)


Evet, hepsi bu kadar!

Siz de belirli tiplere yönelik ayırt edici işlemler yapmak için bu şekilde bir yol izleyebilirsiniz.

Kolaylıklar dilerim.
