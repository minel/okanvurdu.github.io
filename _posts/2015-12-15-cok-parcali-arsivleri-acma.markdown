---
layout: post
title: "Çok parçalı arşivleri açma"
date: '2015-12-15 22:38:00'
---

Merhaba,<br/>
Bu yazıda birden fazla parçaya bölünüp ".rar" biçeminde arşivlenmiş dosyaları nasıl dışarı çıkarabiliriz, bundan bahsetmeye çalışacağım. Öncelikle, bu sorunla karşılaştığımda [şuradaki](http://askubuntu.com/a/476680) adımları uyguladığımda çözüm üretebildim. Yine belirmekte fayda var ki; bu işlemi Ubuntu 15.10 bir makinede gerçekleştirdim.<!--more--><br/><br/>
RAR arşivlerini açmak için "unrar" isimli programcıktan faydalanacağız. Dolayısıyla sisteminizde halihazırda kurulu değilse;<br/><br/>
`sudo apt-get install rar unrar`
<br/><br/>
komutunu yürüterek sisteminize kurabilirsiniz. Farklı dağıtımlar için de bu paketi depolarda bulabileceğinizi düşünüyorum. Kendi dağıtımınızın paket yöneticisi ile kurmayı denemenizi tavsiye ederim.
<br/><br/>
Şimdi ise aşağıdaki komutu yürüterek arşivinizi tamamen dışarı çıkartabilirsiniz:<br/><br/>
`unrar x -e file.part1.rar`
<br/><br/>
Formatından da anlayabileceğiniz gibi programcığa parametre olarak ilk parçanın ismini vermelisiniz. Evet, hepsi bu kadar.<br/><br/>
Kolaylıklar dilerim.
