---
layout: post
title: "Virtual DOM Üzerine"
date: '2015-11-23 21:23:00'
---

Gün içerisinde bir süredir popülerliğinin üstel olarak arttığını düşündüğüm React.js hakkında çeşitli çalışmalar yaptım. Web üzerinde yaptığım arkaplan geliştirmelerinin yanı sıra, ön taraftaki işleri yoluna koymak da şu sıralar ilgi alanlarım arasında. Bunu ilk defa okuldaki bitirme projesi sırasında Angular.js ile denemiştim. Tabii o sıralar front-end geliştiricilerin ya da bir şekilde bu işlere bulaşmış insanların Angular.js'e pek de sıcak bakmadıklarının bilincindeydim. Yine de denemek maksadıyla projemin web istemcisinin View Rendering ve Routing işlerini Angular.js'e teslim etmiş bulundum.
Bahsi geçen çalışmalar sırasında, ziyaret ettiğim bloglarda da yine aynı paralellikte tartışmalara rastladım. Her bir yorum içerisinde kişisel olarak haklılık payı barındırıyor. Neyse, olayın bu kısmını daha da fazla dallandırmaya gerek yok, kim nerede istiyorsa orada bind etsin eventini :)
<br/><br/>
Buraya kadar bahsetmeye çalıştığım şey klasik yoğurt yeme biçimi hikayesinin ta kendisi aslında. Angular.js ile ilgili olumlu / olumsuz birçok yönden bahsedilebilir lakin, ben bu yazıda React.js'in hoşuma giden bir yaklaşımından bahsetmek niyetindeyim: Virtual DOM!
<br/><br/>
