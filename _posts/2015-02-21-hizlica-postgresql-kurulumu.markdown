---
layout: post
title: Hızlıca PostgreSQL Kurulumu
date: '2015-02-21 16:13:03'
---

Merhaba, bu blog gönderisinde "Ubuntu 14.04 x64 üzerinde temiz bir biçimde PostgreSQL nasıl kurulur?" sorusuna kendimce yanıt vermeye çalışacağım.

Başlamadan önce belirtmekte fayda var; kurulum yaptığım Ubuntu sürümü çok da büyük bir önem arz etmemekte. Üst sürümlerde aynı adımları uygulamanız mümkün olmakla birlikte  alt sürümlerde de (birkaç versiyon) problem yaşamayacağınız kanısındayım.
<!--more-->

- İlk olarak bir Terminal (ya da kendi kabuk programınız) penceresi açalım.
- Debian tabanlı sistemlerde öntanımlı paket yöneticisi APT (Aptitude)'dir. Kuruluma başlamadan önce paket yöneticimizin kaynaklarını (repositories) güncellemesi için aşağıdaki komutu yürütelim:

{% highlight bash %}
sudo apt-get update
{% endhighlight %}

- Şimdi ise kurulumu yapmak için aşağıdaki komutu yürütelim:

{% highlight bash %}
sudo apt-get install postgresql postgresql-contrib
{% endhighlight %}

Kuruluma başlamadan önce sizden onay vermeniz istenebilir. Uygun biçimde onaylayarak devam ediniz.

- Bu adımların sonunda PostgreSQL'i sisteminize başarıyla kurmuş olduğunuz. Şimdi gelin PostgreSQL'in çalışır durumda olup olmadığını kontrol edelim:

{% highlight bash %}
service postgresql status
> 9.3/main (port 5432): online
{% endhighlight %}

İlk satırdaki komutu yürütmenizin ardından ikinci satırdaki gibi bir yanıt alıyorsanız her şey yolunda gitmiş demektir. Kurulum sonrası PostgreSQL servisi otomatik olarak çalışır hale gelmektedir.

Peki PostgreSQL online yani aktif olmamışsa ne yapılmalı?

{% highlight bash %}
sudo service postgresql start
{% endhighlight %}

Üstteki komutu yürüttükten sonra bir önceki komutu (`service postgresql status`) yürüterek durumunu kontrol ediniz. Eğer hala çalışır hale gelmemişse bu gönderi altına aldığınız hatayı belirtmeniz durumunda çeşitli çözüm önerilerini tartışabiliriz.

Böylelikle sistemimizi PostgreSQL ile birlikte çalışmaya elverişli bir hale getirdik.

Kolaylıklar dilerim.
