---
layout: post
title: Ubuntu'da Disk Mount Problemi ve Çözümü
date: '2015-09-13 13:50:00'
---
Merhaba, birazdan aşağıda paylaşacağım bilgileri [şuradan](http://askubuntu.com/a/532753) faydalanarak hazırladığımı önceden belirtmekte fayda var.

Kişisel bilgisayarımda şu anda Ubuntu 15.04 (Vivid Vervet) kurulu. Bu kurulumdan önce yine aynı bilgisayarda Windows 10 ve Ubuntu 14.04.3 LTS (Trusty Tahr) bir arada yer almaktaydı.<!--more-->

Halihazırda Ubuntu ve Windows'u birlikte kullanırken, bir süre sonra Ubuntu üzerinde NTFS diskleri mount edememeye başladım. Aslında bu sıklıkla karşılaşılan bir durumdur. Windows'ta yapılan bir Hibernate (Hazırda Bekletme) işlemi, Ubuntu üzerinde disklere erişememekle sonuçlanır.

Artık tamamı ile Ubuntu 15.04'e geçtiğimde yine NTFS bir diski mount etmeye kalkışınca işlem başarısızlıkla sonuçlandı. Tabii bu duruma bir "Dur!" demek gerekirdi.

Siz de benzer bir problemle karşılaşırsanız aşağıdaki adımlar derdinize derman olabilir:

- Öncelikle diskin hangi partitionda olduğunu bilmeniz gerekiyor. Bunun için kabukta /dev yoluna gidip diskinizi bulun. Hızlı bir çözüm için, Ubuntu ile birlikte gelen "Disks" i de kullanmanız mümkün.

- Şimdi bu işlemi bitirmek için `ntfsfix` programcığını çalıştırma vakti. Kabuk penceresi açıp `sudo ntfsfix /dev/diskiniz` komutunu yürütün.

Programcığın çalışmasını tamamlamasının ardından bir dosya yöneticisi penceresi açıp problemli diski mount etmeye çalışın. Çok büyük bir aksilik olmamışsa sorununuz çözülmüş olacaktır.

Kolaylıklar dilerim.
