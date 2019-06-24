---
layout: post
title: "Rails Action Pack Variants"
author: "Hasan Tezcan"
categories: blog
tags: [Ruby on Rails]
image: "/assets/posts/rails-action-pack-variant//ruby-on-rails.png"
date:   2019-06-24
---
***Yazan: [hasantezcan](https://github.com/hasantezcan)***
---

**Responsive** yapılar, akıllıca tasarlanmış, sayfaların boyutlarına(platformlara) göre şekillenen yetenekli ve esnek tasarım yapılarıdır ve günümüzde de çokca tercih edilmektedir.

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/rails-action-pack-variant/responsive.gif" width="650">
</p>

Responsive tasarımların bu çok yetenkli halleri, içinde yüklü miktarda JS, CSS ve HTML kodu bulundurmasına sebep oluyor. Bu durum da özellikle mobil cihazlar için arayüz kullanımlarında hız kayıplarına neden oluyor.

Neyseki **[Ruby on Rails 4.1 ile birlikte](https://github.com/rails/rails/blob/v5.0.0.beta2/actionpack/lib/abstract_controller/callbacks.rb#L190-L193)** `"Action Pack Variants"` adında yeni bir özellik duyurdu. Action Pack Variants **siteye hangi platformdan girdiğinizi tespit eder ve
tarayıcınıza hangi sayfayı yükleyeceğine karar verir.** Bu sayede sayfalarınızın yüklenme **hızları artmış** olur.

Bugün de sizlerle Rail Action Pack Variants'ı **Rails 4.1 ve sonrası** projelerde nasıl kullacağını göstermek adına bir uygulama yapacağız.  

## Rails Action Pack Variants Uygulaması

### `Demo için kurulum:`

Öncelikle **Action Pack Variantlarını** denemek için bir controller oluşturalım.

```ruby
  rails g controller Homes show
```

Action Pack Variantlarını denerken rahat edebilmemiz açsından projemizin açılış sayfasını `Homes#show` olarak güncelleyelim.

```ruby
Rails.application.routes.draw do
  resource :home, only: [:show]
  root to: "homes#show"
end
```

Gerekli hazırlıkları tamamladık. Peki **Action Pack Variantlarını nasıl kullancağız?**

Action Pack Variantları **application controller** içinde **before_action** methodu ile kullanılır. Şimdi siz de `application controller` içine gidip mevcut yapınızı buna uygun şekilde düzenleyin.

```ruby
class ApplicationController < ActionController::Base
  # Prevent CSRF attacks by raising an exception.
  # For APIs, you may want to use :null_session instead.
  protect_from_forgery with: :exception

  before_action :detect_browser

private
  def detect_browser
    case request.user_agent
      when /iPad/i
        request.variant = :tablet
      when /iPhone/i
        request.variant = :phone
      when /Android/i && /mobile/i
        request.variant = :phone
      when /Android/i
        request.variant = :tablet
      when /Windows Phone/i
        request.variant = :phone
      else
        request.variant = :desktop
    end
  end
end
```
### Peki, Nasıl Çalışır?

`detect_browser` çağırıldığında `request.variant` olması gerektiği gibi ayarlanır. Biz örneğimizde sayfamıza tablet, telefon ya da masaüstünden mi girdiğini tespit ediyoruz.

> Ayrıca bu yapıyı Internet Explorer versiyonlarını tespit etmek gibi işerlde de kullanabilirsiniz.

> NOT: `before_filter`, `before_action` ile aynı işi yapmaktadır. Rails 5.1 den itibaren de `before_filter` [kullanımdan kaldırılmıştır.](https://github.com/rails/rails/blob/v5.0.0.beta2/actionpack/lib/abstract_controller/callbacks.rb#L190-L193)


Bu yapı piyasada bulunan bazı cihazların hangi platforma ait olduğunu tespit edemeyebilir. Bu sorun bazı cihaz üreticilerinin, cihazın hangi platforma dahil olduğunu uygun şekilde belirtmemesinden kaynaklanır. Fakat günün sonunda çoğu cihazın hangi platforma dahil olduğunu bu yapı ile tayin edebiliriz.

---
### `view katmanı:`

Şimdi ise farklı ekranlarda görmek istediğimiz view katmanlarını oluşturalım. View dosyalarını oluştururken isimlendirmeyi aşağıdaki yapıda oluşturuyoruz.

- **show.html+`platform_adı`.erb**

Öncelikle varsayılan olan masaüstü view'imiz oluşturalım. Bu kısımda herhangi bir platform adı belitmemize gerek yok.

#### `show.html.erb`

```html
<div class="jumbotron jumbotron-fluid bg-warning">
  <div class="container text-dark">
    <h1 class="display-2">Desktop</h1>
    <h1 class="display-4">All other users get redirected here.</h1>
  </div>
</div>
```
---
Telefon için olan görünümü ayarlamak için `phone` etiketini kullanıyoruz.

#### `show.html+phone.erb`

```html
<div class="jumbotron jumbotron-fluid bg-success">
  <div class="container text-white">
    <h1 class="display-2">Phone</h1>
    <h1 class="display-4">You are running on a smart phone</h1>
  </div>
</div>
```

---
Tablet ekranları için de `tablet` etiketini kullanarak view dosyamızı oluşturuyoruz.

#### `show.html+tablet.erb`

```html
<div class="jumbotron jumbotron-fluid bg-danger">
  <div class="container text-white">
    <h1 class="display-2">Tablet</h1>
    <h1 class="display-4">You are running on a tablet.</h1>
  </div>
</div>
```
---
Evet şuan yapıyı kurmuş bulunmaktayız.

### `Peki nasıl test edicez?`

Google developer tools'u kullanarak sistemi kolayca test edebilirz.

- İlk olarak varsayılan olarak ayarladığımız. Masaüstü görünümü ile karşılaşıcaz.

<p align="center">
	<img alt="os-nedir" src="/assets/posts/rails-action-pack-variant/desktopp-view.png" width="650">
</p>

- Diğer platformlardan nasıl göründüğünü görmek için;
#### `CTRL` + `SHIFT` + `I`
ile google developers tool'u açıyoruz ve ardından. Görüntülemek istediğimiz platformu resimdeki gibi belirliyoruz.

**NOT:** Platform değiştirdikden sonra **sayfayı yenilemeyi** unutmayın! Şuan yaptığımız işlem bir responsive tasarımı simüle etmekten ziyade platform özeline oluşturulmuş **biricik** bir sayfanın görüntüleme işlemidir.

<p align="center">
	<img alt="google-developers-tool-img" src="/assets/posts/rails-action-pack-variant/google-developers-tool.png" width="650">
</p>

<p align="center">
	<img alt="ipad-view-img" src="/assets/posts/rails-action-pack-variant/ipad-view.png" width="350">
</p>

<p align="center">
	<img alt="iphone-view-img" src="/assets/posts/rails-action-pack-variant/iphone-view.png" width="250">
</p>
---

- Evet anasayfamızı her platform için farklı şekilde tasarlayıp görüntüledik`(view katmanı)`. **Peki bunu controller katmanı için de yapmak mümkün mü?**

### `controller katmanı:`

`format.html` yapıları içinde platformlara özel sorgular yapabiliyoruz. Mesela internet Explorer 6/7 kulanan kullanıcıları tespit edip onlara tarayıcılırını güncellemeleri gerektiğini gösterebiliriz.

```ruby
class HomesController < ApplicationController
  def show
    @device = "others"
    respond_to do |format|

        format.html.phone do # phone variant
          # add code here for phones
        end

        format.html.tablet do # tablet variant
          # add code here for tablets
        end

        format.html.desktop do
          # add code here for desktops and other devices
        end
    end # end respond_to
  end # end show
end # end class
```

### `View katmanında hangi variantın kullanıldığını tespit etmek istersek?`

Bunu yapmanın kolay bir yolu var. Bu örneğe bakarak bunu anlayabilir ve sizde kodunuza buna benzeterek sorununuzu çözebilirsiniz.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>ActionPackVariantsExample</title>
    <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track' => true %>
    <%= javascript_include_tag 'application', 'data-turbolinks-track' => true %>
    <%= csrf_meta_tags %>
  </head>
  <body>
    <%= yield %>

    <% if request.variant.include? :tablet %>
      <small>Welcome Tablet User</small>
    <% elsif request.variant.include? :phone %>
      <small>Welcome Phone User</small>
    <% end %>
  </body>
</html>
```
---------

Anlatımımızın sonuna geldik umarım sizler için faydalı olmuş, çözümü bulup burdan öyle ayrılıyorsunuzdur. Bir daha görüşümek üzre. İyi çalışmalar. :smile:






Kaynaklar
----------

[Deepak Singh](https://dev.to/spidergears/rails-action-pack-variants-1lc3)

[richonrails.com](https://richonrails.com/articles/action-pack-variants-in-rails-4-1)

[coderwall.com](https://coderwall.com/p/etlnvg/how-to-use-rails-4-1-actionpack-variants)
