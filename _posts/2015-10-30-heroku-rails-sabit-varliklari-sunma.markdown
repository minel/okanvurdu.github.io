---
layout: post
title: "Heroku + Rails: Sabit varlıkları sunma"
date: '2015-10-30 23:40:00'
---
Merhaba,<br/>
Bu yazıda; bir Rails uygulamasını Heroku'ya deploy ederken karşılaştığım küçük bir problemden bahsedip,  çözüm yollarından birini örnekleyeceğim.

Öncelikle yazı başlığını Türkçe + İngilizce karmaşası olmasın diye bu şekilde seçtim. Burada "sabit varlıklar" ile ifade etmeye çalıştığım; "assets" olarak bilinen, içerisinde uygulamanıza ait stil dosyaları, javascript betikleri vb. kaynakları barındıran yapının genel adıdır.<!--more-->

Development ortamında bahsi geçen CSS ve Javascript dosyalarına erişimde herhangi bir problem yaşamıyordum. Uygulamayı Heroku'ya deploy edip Procuduction ortamına taşıdığımda ise, asset pipeline'ın ürettiği çıktılara tarayıcı tarafından erişilememekteydi. Bildiğiniz; `404 - Resource Not Found` hatası ile karşılaşmaktaydım.

Küçük bir araştırmanın ardından şununla karşılaştım:<br/>
[https://devcenter.heroku.com/articles/ruby-support#static-assets](https://devcenter.heroku.com/articles/ruby-support#static-assets)

####Tam olarak nedeni ise şöyle:
Heroku dışındaki Rails deploymentları; Load Balancing, sabit varlıkları doğrudan sunmak vb. işlemler için Nginx gibi bir HTTP Proxy sunucusuna ihtiyaç duyar. Örneğin, bir CSS dosyasına erişim sağlamak istediğinizde Nginx bunu diskteki `/public/assets/blahblah.css` yolu üzerinden sunmaya çalışır.

Heroku bu noktada üçüncü parti bir proxy sunucusuna ihtiyaç duymadığı için, yapılandırmanın kontrolü uygulamanıza verecek biçimde güncelleştirilmesi gerekir.

Aşağıdaki satırları Gemfile'ınıza ekleyerek bunu sağlamanız mümkün:<br/>
`gem 'rails_serve_static_assets'`<br/>
`gem 'rails_stdout_logging'`

Kolaylıklar dilerim.
