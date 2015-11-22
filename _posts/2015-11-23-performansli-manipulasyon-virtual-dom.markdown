---
layout: post
title: "Performanslı Manipülasyon: Virtual DOM"
date: '2015-11-23 21:23:00'
---

Şu sıralar React.js ile ilgili "Nedir, nasıl yapılır?" sorularına kendimce yanıtlar arıyorum. Bir yandan işin uygulanabilir taraflarını irdelerken, diğer yandan bu kütüphaneyi güzelleştiren neler var fikir sahibi olmanın derdindeyim. Kütüphane demek ne kadar doğru bilinmez ama, en genel haliyle bu kategori altında yer alabilir diye düşünüyorum.<!--more-->
<br/><br/>
Bugüne kadar arkaplandaki işleri optimize etmek ve okunaklı hale getirmek için sürekli olarak yeniliklerin birbirini kovalamasına alışkındım. Ön tarafla ilgili gelişmeler de son yıllarda buna paralel bir yol izlemeye başladı. Bence hem alternatiflerin artması açısından, hem de rekabetin kaliteyi arttırmasından dolayı oldukça güzel bir olay bu. Neyse, bu durum yazımın konusu değil.
<br/><br/>
Yazıda, en başta bahsettiğim incelemeler sırasında hoşuma giden bir React.js mimarisinden bahsedeceğim: Virtual DOM! Haydi başlayalım...
<br/><br/>
Mesele ön taraf olunca; geçmişten günümüze statik arayüzlerin, nasıl etkileşimli hale geldikleri konusunda hepimiz az çok bilgi sahibiyizdir. Etkileşim konusunda neredeyse sıkıntılar minimuma inmiş gibi. Günümüz problemi ise, bu etkileşimleri yaparken ne kadar performans harcandığı. Front-End teknolojileri tıpkı Back-End teknolojilerinde olduğu gibi gereksiz iş yapmaktan, performans problemlerine yol açmaktan kaçınmak için kendilerini yenilemek durumundalar.
<br/><br/>
Bu noktada React.js'in sunduğu Virtual DOM mimarisi, bahsi geçen sorunları minimize etmek için oldukça ideal görünüyor. Şimdi React.js bu işi nasıl yapıyor, önce ona bakalım:<br/><br/>
`DOM'a doğrudan müdahale etmek yerine, bir kopyasını oluştur ve değişiklikleri bunun üzerinde yap.`<br/><br/>
Buraya kadar her şey iyi güzel de, sonrasında ne olacak? Aslında cevap basit; değişiklikleri DOM'a yansıt. Peki ne zaman? Hemen değil, en uygun zamanda.
<br/><br/>
En uygun zamanı biraz açmak gerekirse; doğrudan veri değişimi olduğunda demek oldukça yerinde olacaktır. (Birazcık sabırlı olun, henüz gelmedik) Peki veri değişimini algılamak nasıl mümkün olabilir? Bunun birinci yolu; **Long Polling** adı verilen, belli aralıklarla verinin değişip değişmediğini kontrol eden yöntemdir. Bu yöntem pek sevilen ve tercih edilen bir yöntem değil. İkinci bir yolu ise nesnelerin state değişimlerini takip etmek. (Observing - Bu yöntem React.js'in seçtiği yöntemdir.) Eğer ortada değişmiş bir şey yoksa, re-render edilmeyi gerektiren bir durum da yoktur. Bu işleri performanslı yapmak için aşağıdaki üç prensibi yerine getirmek olmazsa olmazdır:<br/>
- Verimli Diff (Fark) algoritmaları kullanmak
- DOM güncellemelerini topluca yapmak (Her veri değişiminde değil, birden çok veri değişimini bir arada)
- Sadece ilgili kısmı güncellemek
<br/><br/>
React.js bu prensiplerin hepsini bir arada uygulamaya çalışan bir kütüphane. Henüz çok geniş çalışmalar yapmamış olsam da, ilginç yaklaşımlarıyla denenmeye değer olduğunu bir kez daha kanıtlıyor. Fırsatım olduğunda bir de Babel'dan bahsetmek istiyorum.

Kolaylıklar dilerim.

>Bu yazıyı hazırlarken [şuradan](http://tonyfreed.com/blog/what_is_virtual_dom) bir miktar faydalandım, bilgilerinize...
