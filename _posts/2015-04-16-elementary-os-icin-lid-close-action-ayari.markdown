---
layout: post
title: Elementary OS için "lid-close-action" ayarı
date: '2015-04-16 10:19:02'
permalink: :title.html
---

Bildiğiniz gibi son zamanların popüler Linux dağıtımlarından birisi "Elementary OS". Ben de geçtiğimiz günlerde yayınlanan kararlı versiyonu "Freya" (0.3) yı kurduktan sonra, karşılaştığım bir soruna nasıl çözüm ürettiğimi paylaşmak istedim.

**Öncelikle sorun şu:**
Dizüstü bilgisayarımın kapağını kapattığımda bilgisayarım uyku moduna geçiyor.
<!--more-->

Bunu önleyebilir miyim sorusuyla yola çıktığımda Elementary OS'in kendi sunduğu Güç Seçenekleri (Power Settings) arabirimi "Ben böyle bir opsiyon sunmuyorum" yanıtını verdi. Belki biraz daha kurcalasaydım bir seçenek bulabilirdim. Fakat hızlıca halledebilmek adına Google'a başvurdum.

Kullanmayı tercih ettiğim çözüm yolu, **Dconf Editor** adlı bir programcığın bu işi çözebileceğinden bahsediyordu.

Dconf Editor, sistem konfigürasyonuna doğrudan yerel veritabanı üzerinde müdahale etmenizi sağlıyor. Yani Dconf Editor, sisteminizin konfigürasyonları okuduğu veritabanı üzerinde değişiklik yapmaya yarıyor.

Dconf Editor'u ister kabuktan, isterseniz Software Center'dan kurabilirsiniz.

Kurulumun ardından Dconf Editor'u çalıştırıp sol panelde aşağıdaki yolu açtım:

**org -> gnome -> settings daemon -> plugins -> power**

Daha sonra sağ kısımdaki seçenekler içerisinde 2 alanı aşağıdaki gibi güncelledim:

![](/img/posts/dconf-editor.png)

İlk alan bilgisayarınız fişe takılıyken, ikincisi ise bataryayı kullanırken geçerli olacaktır.

Ayarları bu şekilde değiştirmenizin ardından başka bir işlem yapmanıza gerek kalmıyor. Ayarlar doğrudan aktif hale geliyor.

Başka bir çözüm önerisinde görüşünceye dek hoşçakalın.
