---
layout: post
title: Ruby için Redcarpet
date: '2015-02-03 17:43:04'
permalink: :title.html
---

Redcarpet, Ruby betiklerimizde markdown işlemek için kullanabileceğimiz bir kütüphanedir.

######Markdown?
Formal bir tanım değil de öznel olarak yorum yapmak gerekirse; "Markdown, HTML kodu yaz(a)mayacak kadar üşengeç (zamanı kıymetli) insanlar için düz yazıya en yakın işaretleme dilidir."
<!--more-->

Çünkü markdown ile bir metni kalın yapmak için `<b>buraya metin gelecek</b>` şeklinde etiket açıp kapatmanıza gerek yoktur. `*metin buraya gelecek*` gibi bir ifade kullanmanız yeterlidir. Ya da `<h1..6>` kullanımı ile başlık oluşturmak yerine ifadenizin başına başlık seviyesi kadar `# (diyez)` koymanız yeterlidir.

İlk başta tanım yaparken dikkatinizi çekmek için **üşengeç** ifadesini kullandım fakat markdown, yazmaya çalıştığınız metni etiketlere boğulmaktan kurtaran, aynı zamanda toplam saklama boyutunu da oldukça düşüren bir yapıdır. (Yine de üşengeçler için ideal bir ifade etme biçimidir.)

###### Nerede ve neden?
"Her şey iyi hoş da, bunu nerede ve nasıl kullanacağım?" diye sorabilirsiniz.
"Şu an okumakta olduğunuz yazı markdown kullanılarak yazıldı." desem sanırım güzel bir başlangıç yapmış oluruz.

![İnandırıcılığı olsun diye](/img/posts/Screenshot-from-2015-02-03-20-42-41.png)

Bunun yanısıra kişisel projelerinizde de kullanmanız mümkün. Örnek olarak, geliştirdiğiniz bir web uygulaması içerisinde "Yardım Merkezi" tarzında bir bölüm mevcut ve çeşitli içerik sayfalarından meydana geliyor.

İçine sadece açıklama ve birkaç resim koyacağınız her sayfa için uzun uzun HTML kodu yazmak ne kadar sıkıcı değil mi?

"Hazır editörler var, neden yazayım ki?" dediğinizi duyar gibiyim. Redcarpet'ı web uygulamanıza entegre etmek, muhtemelen Javascript kullanılarak yazılmış ve içerisinde zilyon tane gereksiz dosya barındıran bir editörü entegre etmekten çok daha kolaydır.

###### Peki nasıl?
Rails tarafında kurulum oldukça basit. (Tıpkı diğer tüm Ruby kütüphaneleri için olduğu gibi)

Halihazırda bir Rails projeniz varsa kurulum, Gemfile'ınıza
```
gem 'redcarpet'
```
eklemesini yaptıktan sonra komut istemcinizde proje dizininize ulaşarak

```
bundle install
```
komutunu yürütmenizle tamamlanacaktır.

Bunun yerine komut istemcinizi açarak
```
gem install redcarpet
```
komutunu yürütmek de eşdeğer bir durumdur.

> **Unutmadan:**
2. yolu kullanarak kurulum yapsanız bile Gemfile'ınıza bu kütüphaneyi tanımlamalısınız.


###### Sonra?
Kurulum biter bitmez içinizde büyüyen merakı hızlıca gidermek için aşağıdaki adımları takip ediniz:

* Komut istemcinizi açınız.
* `irb` komutunu yürüterek Etkileşimli Ruby Kabuğu'nu aktif hale getiriniz.
* Redcarpet kütüphanesini kullanabilemek için öncelikle bunu kabuğa bildirmeliyiz. `require  'redcarpet'` komutunu yürüterek bu işlemi tamamlayınız.
* Redcarpet'ın bir Instance'ını oluşturmak için her şey hazır. Şimdi ise;

```
markdown = Redcarpet::Markdown.new(Redcarpet::Render::HTML, {})
markdown.render('*Bu bir örnektir*')
```
komutlarını yürüttükten sonra aşağıdaki gibi bir çıktı ile karşılaşacaksınız:

![](/img/posts/Screenshot-from-2015-02-03-20-36-16.png)

Gördüğünüz gibi en son koştuğumuz komutun ardından oluşan çıktıda HTML etiketleri mevcut.

Basit bir örnekle kullanımını da ifade ettikten sonra https://github.com/vmg/redcarpet adresinden daha detaylı uygulama bilgilerine ulaşabileceğinizi belirtip, iyi çalışmalar diliyorum.
