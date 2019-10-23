---
layout: post
title: "Rails ve görüntü işleme"
author: "Hasan Tezcan"
categories: blog
tags: [Ruby on Rails]
image: "ruby-on-rails.png"
date:   2019-08-26
---

Geçtiğimiz haftalarda çalışmış olduğum bir rails projesinde birtakım resimleri saat yönünün tersine 90 derece döndürecek bir button yapmam, ve bu işlem gerçekleşirken de sayfanın yenilenmemesi gerekiyordu.

Göreve başlamadan önce **"Bir rails projesinde nasıl resim işlemesi yapılır?"** ile ilgili herhangi bir bilgim yoktu ve ne yapacağımı bilmiyordum. Görevi bitirdikten sonra hem ilerde bakıp hatırlayabilceğim bir kaynak olsun diye hem de aynı sorunu yaşayan bir başkasına faydası dokunur diye bu yazıyı yazmak istedim.

Birazdan sizlere bir rails projesinde Nasıl görüntü işleme yapılır, bunu yaparken hangi araçlar kullanılmalıdır. Ve en son da bu işlem nasıl sayfa yenilenmeden gerçekleşiri konuşacağız. Hazırsanız başlayalım..

>Bu yazı iki hafta önceki ben ve benim gibiler için gelsin...  

### `Rails ve görüntü işleme`

Görüntü işleme nasıl yapılır diye baktığımda ilk bulduğum araç [**Image Magick**](https://imagemagick.org/) oldu. Image magick aslında bir terminal uygulaması. Bir çok resim işleme işi bu uygulama sayesinde yapılabiliyor.

>	imagemagick'i **paket yöneticinizle** tarayıp kolayca indirebilirsiniz.(manjaro kullandığımdan benim paket yöneticim **pacman**)

<p align="center">
	<img alt="imagemagick.png" src="/assets/posts/image-procesing/imagemagick.png" width="650">
</p>

Imagemagick'i kullanımı çok basit. Bir fotoğrafı siyah beyaz yapmak için bu satırı terminalde çalıştırmamız yeterli.

```bash
$ convert -type Grayscale colorful-image.jpg monocroma-image.png
```
<p align="center">
	<img alt="imagemagick.png" src="/assets/posts/image-procesing/grayscale.png" width="800">
</p>

Şimdi de bize gerekli olan döndürme işlemini deneyelim. Döndürme işlemini -rotate deyip ardından kaç derece dönmesini istiyorsak onu yazıyoruz.

```bash
$ convert -rotate 90 old-guy.png rotated-old-guy.png
```
<p align="center">
	<img alt="imagemagick.png" src="/assets/posts/image-procesing/old-guy.png" width="800">
</p>

> - [**mogrify**](https://imagemagick.org/script/mogrify.php): "convert" ile aynı işi yapar. Ondan tek farkı verileri üzerine yazmasıdır.
```bash
	mogrify -rotate 90 old-guy.png
```

> Bu ve bunun gibi bir çok manipulasyonu yapmak mümkün. Imagemagick ile daha başka neler yapılır görmek isterseniz aşağıdaki kaynaklara göz atabilirsiniz.
 - [**Tüm imagemagick komutları**](https://www.imagemagick.org/script/command-line-options.php)
 - [Image Geometry](https://imagemagick.org/script/command-line-processing.php#geometry)
	- [transpose](https://imagemagick.org/script/command-line-options.php#transpose)   `-flip -rotate 90`


#### - Peki rails projemiz içinde `imagemagick'i` nasıl çalıştırıcaz?
Bunu sağlamak için üretilen gemler var bunlardan birini kullanmamız gerekli. Resim işleme(image processing) için en çok kullanılan gemler "[`minimagick`](https://github.com/minimagick/minimagick) ve [`rmagick`](https://rmagick.github.io)". Minimagick rmagick'e göre daha performanslı çalıştığından ve [rails guide](https://guides.rubyonrails.org/active_storage_overview.html#transforming-images)'ın da önerdiği görüntü işleme gem'i oluduğundan **minimagick** gem'ini kullanacağız.

Minimagick kulanmadan önce bilgisayarınıza Imagemagick'i kurmuş olmanız gerekiyor. (Imagemgick'in nasıl kurulduğuna yukarda değinmiştim)  

Imagemagick'i kurduktan sonra `gemfile` içine aşağıdaki satırı ekliyoruz.

```ruby
gem "mini_magick"
```














































-   
-
-   
-
-   
-
-   
-
-   
-
-   
-
-   
-
-   
-








---
**> Resource**

- [***Deepak Singh***](https://dev.to/spidergears/rails-action-pack-variants-1lc3)

- [ ***richonrails.com***](https://richonrails.com/articles/action-pack-variants-in-rails-4-1)
