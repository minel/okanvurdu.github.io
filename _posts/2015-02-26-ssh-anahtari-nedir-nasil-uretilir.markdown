---
layout: post
title: 'SSH: Nedir, Nerede, Nasıl?'
date: '2015-02-26 10:58:33'
---

Küçük bir Google araması ("What is SSH") yaptığımda SSH hakkında şöyle bir tanıma eriştim:

"SSH, uzaktaki bir bilgisayara güvenli bir biçimde erişmek için kullanılan UNIX tabanlı komut arayüzü/protokolüdür."

SSH'ı mantıksal olarak bir kimlik belgesi ile bağdaştırabiliriz. Hizmet aldığınız servisler sizden kimliğinizi (başka bir deyişle imzanızı) alarak altyapılarına erişme hakkınız olup olmadığını kontrol ederler. Bu sayede yetkisiz erişimler ortadan kaldırılırken veri alışverişi de güvenli bir hal alır.
<!--more-->

####Gerçek Hayattan Örnek: Github

SSH kullanarak verilerinize güvenli erişim sağlayabileceğiniz birçok servis mevcut. Ben kısaca Github'dan bahsederek konu hakkında fikir sahibi olmanızı sağlamaya çalışacağım.

Bir depoyu kendi makinenize kopyalamak (clonelamak) istediğinizde karşınıza çeşitli yollar çıkmaktadır:

![Github'da depo clonelama opsiyonları](/img/posts/github-clone-repo-options.png)

Eğer daha öncesinde sadece **HTTPS** üzerinden clone yaptıysanız SSH'ı tıkladığınızda bağlantı formatının değiştiğini görebilirsiniz.

Buraya kadar her şey iyi hoş da sorulması gereken bir soru var:

Bir SSH anahtarını nasıl üretirim ve Github'a bunu nasıl tanımlarım?

Güzel soru.

İşe öncelikle SSH anahtarı oluşturmakla başlayalım. UNIX tabanlı bir işletim sisteminde (Ben Ubuntu üzerinde yapacağım) komut istemcinizi açınız. (Ubuntu için Terminal)

```
ssh-keygen -t rsa -C "eposta@adresiniz.com"
```

komutunu yürütünüz.

İlk olarak:

```
> Enter file in which to save the key (/home/okan/.ssh/id_rsa):
```

şeklinde bir çıktı alacaksınız.

SSH anahtarları kullanıcı dizininiz altında `.ssh` isimli bir dizinde dosya olarak saklanmaktadır. Dilerseniz bu dizine gidip (`cd ~/.ssh` komutu yardımıyla) `ls -al` komutunu vererek SSH anahtarlarınızın bir listesine ulaşabilirsiniz.

Burada istemcinizin sizden beklediği "anahtarı hangi dosya ismi ile kaydedeyim?" sorusunun yanıtıdır. Hiçbir şey belirtmeden Enter ile devam ettiğinizde, anahtarınızı `/home/okan/.ssh/id_rsa` dosyasında saklayacağını parantez içinde bildirmektedir.

Bu kısımda dosya adı vererek ya da varsayılan dosya adını kabul ederek devam ettikten sonra ise

```
> Enter passphrase (empty for no passphrase):
```

çıktısı ile karşılaşacaksınız. Burada beklenen ise bu anahtarı özel bir şifre ile koruyup korumayacağınızdır. Bu anahtarı kullanarak verilerinize erişmeye çalıştığınızda ekstra bir güvenlik önlemi olarak belirttiğiniz parolanın sorulmasını sağlayabilirsiniz. Bu kısmı da boş geçme (Enter ile) şansınız mevcut. Bir parola verseniz de vermeseniz de sizden bunu doğrulamanız bir sonraki adımda beklenecektir. Bu adımı da geçmenizin ardından şöyle bir mesaj ile karşılaşırsınız:

```
The key fingerprint is:
**:**:**:**:**:**:**:**:**:**:**:**:**:**:**:** eposta@adresiniz.com
```

Artık SSH anahtarınız hazır hale geldi. Şimdi bunu Github tarafından kimlik doğrulama için kullanılabilir hale getirelim.

* Komut istemcinizi açınız.
* SSH anahtarlarınızın depolandığı dizine gidiniz:

```
cd ~/.ssh
```

* Aşağıdaki komutu vererek SSH anatarınızın içeriğinin ekrana bastırılmasını sağlayınız:

```
cat anahtar_dosyaniz.pub (mesela: cat id_rsa.pub)
```

* Ekrana bastırılan metni kopyalayınız ve daha önceden oturum açmış olduğunuz https://github.com/settings/ssh adresine gidiniz.

Burada Github'da tanımlamış olduğunuz SSH anahtarlarının bir listesini görebilirsiniz.

* "Add SSH Key" düğmesine tıklayarak SSH anahtarı eklemek için gerekli alanlara erişim sağlayınız.

![Github'da SSH anahtarı ekleme ekranı](/img/posts/github-add-ssh-key.png)

* Alanları resimde açıklanan biçimde doldurduktan sonra "Add key" düğmesine tıklayarak ekleme işlemini tamamlayınız.

Böylelikle bir SSH anahtarı oluşturup kullanılabilir hale geldik. Burada oluşturduğunuz anahtarı sizden SSH anahtarı isteyen sınırsız sayıda serviste kullanmanız mümkün, herhangi bir kısıtlama bulunmamakta. Buradan sonrası ise size kalmış...

Kolaylıklar dilerim.
