---
layout: post
title: '"Failed to build gem native extension" İçin Çözüm Önerisi'
date: '2015-02-26 15:46:46'
---

**Dikkat:** Birazdan bu yazının devamında okuyacaklarınız, içerisinde Ubuntu 14.04.2 LTS yüklü bir makinede denenmiş olup, farklı dağıtımlar veya sistem konfigürasyonları için başarılı olabileceği iddia edilmeyen ifadeler içerebilir. Ruby veya Ruby on Rails ile geliştirme yapmıyorsanız bu yazı sizin için çok büyük bir önem ifade etmeyecektir.
<!--more-->

Çeşitli sebeplerden ötürü kararlılığını yitirdiğini düşündüğünüz işletim sisteminizi temiz kurulum yaparak eski güzel günlere döndürmek istediniz. Hemen ardından kolları sıvayıp bu işlemi gerçekleştirdiniz.

Haliyle sisteminize yeniden Ruby, ardından Ruby on Rails kurmak isteyebilirsiniz.

Herhangi bir paket yöneticisi kullanmadan Ruby kurmak için;

{% highlight bash %}
sudo apt-get install ruby-full
{% endhighlight %}

komutunu yürütmek işinizi görecektir.

Rails kurarken ise öncelikle bir Javascript Runtime'ına ihtiyacanız olacaktır. Node.js kurmak bu iş için en kısa çözüm yoludur. Şimdi gelelim yazının başında bahsedilen hatayı almanızı sağlayacak duruma.

Öncelikle
{% highlight bash %}
gem install rails
{% endhighlight %}

komutunu yürütmeyi denediniz. Sisteminiz `root` haklarına sahip değilseniz kurulumu tamamlayamayacaktır. Hemen bir `root` kullanıcısına geçip aynı komutu tekrar yürüttünüz ve bir süre bekledikten sonra aşağıdakine benzer bir ekran ile karşılaştınız:

![Failed to build gem native extension hatası](/img/posts/failed-to-build-gem-native-extension.png)

Tam olarak bu noktada aşağıdaki komutu koşmanızla bu hatayı çözmeniz mümkündür.

{% highlight bash %}
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties
{% endhighlight %}

Bu komutu yürütmeniz ile birlikte yapacağınız yüklemeler Rails'in sağlıklı yüklenmesi için gerekli bağımlılıkları yüklemek işini de görecektir.

Bu yüklemenin ardından yeniden `gem install rails` komutunu yürüttüğünüzde yüklemeniz sağlıklı bir biçimde tamamlanacaktır.

**Not:**
Burada yükleyeceğiniz paketlerin tamamının bu hatayı çözmek için gerekli olduğunu düşünmüyorum. İsterseniz paketleri tek tek yükleyip hangisinin yüklenmesinden sonra hatanın ortadan kalktığını gözlemleyebilirsiniz.

Kolaylıklar dilerim.
