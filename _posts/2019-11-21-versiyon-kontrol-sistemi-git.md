---
layout: post
title: "Versiyon Kontrol Sistemi GIT"
author: "Hasan Tezcan"
categories: blog
tags: [Git]
image: "git.jpeg"
date:   2019-11-21
---

<p align="center">
	<img alt="version_kontrol__sistemi" src="/assets/posts/versiyon-kontrol-sitemi-git/versiyon-kontrol-sitemi-sebep.png" width="400">
</p>

Herhangi bir projeyi geliştiriken böyle bir tablo ile muhakkak karşılaşmışsınızdır. Bu bir ödevi yapmak için olabilir ya da bir şiir yazarken. Projeniz üzerinde yapılan değişiklerinizi bir şekilde saklamak için aslına bu aşamalardan geçen herkes bu görselde olduğu kendi versiyon sistemini geliştirir ve bunu kullanır. Ne kadar verimli olduğu tartışılır ama bir versiyon kontrol sistemine ihtiyaç duyduğumuz ortadadır.

Bugün sizlerle birlikte var olan versiyon kontrol sitemlerinden ve günümüzde yaygın olarak kullanılan GIT version kontol sisteminin nasıl kullanıldığından bahsedeceğim.

## Versiyon Kontrol Sistemi Nedir?

Versiyon kontol sistemleri herhangi bir proje üzerine çalışırken size yaptığınız değişiklikler ve yenilikler arasında boğulmadan temiz bir şekilde çalışabilme imkanı sunar.

Version kontol sistemleri ile çalışamayı öğrendikten sonra bir proje üzerinde zamanda geri gidebilir projenizin falanca zamanki halini o günkü hali ile inceleyebilir ya da projenizin o anki halini bozmadan üzerine yeni denemeler yapabilir ve bu denemeniz istediğiniz gibi olursa ana projenize bu özelliği ekleyebilirsiniz.

Bu söylediklerimi en başta gördüğümüz insan beyninin direk oluşturduğu versiyon kontrol sistemi ile yapmaya kalkmak bi yerde mantıklı olsa da bu yöntemle devam etmek bir yerden sonra sizi sinir krizlerine sokabilir hata ve hata projeninizi geliştirecem derken çalışır halinden de olmanıza sebep olablir.

Gelin şimdi var olan versiyon sistemlerne bir göz atalım.

- **CVS** : 1986, Versiyon kontrol sistemlerinin dedesidir.

- [**SVN**](http://subversion.tigris.org/) : Bu proje şu an kitli durumdadır.

- **Git** : üzerine detaylıca konuşacağımız versiyon kontrol sistemi.

- **Mercurial**

- **Bazaar**

- **Monotone**

> [**[0]**](https://www.smashingmagazine.com/2008/09/the-top-7-open-source-version-control-systems/),
> [**[1]**](https://www.g2.com/categories/version-control-systems?trending=)

Bu versiyon kontol sistemlerinden kimileri hala aktif kimileride şu an kulladığımız versiyon kontrol sistemlerine zamanına ilham olmuş ve şu an ömürlerini doldurmuş durumdadır.

Bugün biz günümüzde en yaygın kullanılan versiyon kontrol sistemi GIT ile çalışacağız ve projelerimizi git ile yönetmeyi öğreceğiz.

## Git Nedir?

[**Git**](https://git-scm.com/) özgür ve dağıtık bir version kontrol sistemidir. GIT, linux'ü geliştiren ekibin o zamanlar kullandıkları [**BitKeeper**](https://www.bitkeeper.org/) adlı proje yönetim araçının ücretsiz lisans anlaşmasının bitmesi ile Linus Toravalds ve ekibinin BitKeeper'ı kullanırken yaşadıkları sıkıntıları da göz ederek tasarladıkları 2005 yılında ortaya çıkan bir versiyon kontrol sistemidir.

Git ismi, Linus Torvalds tarfından Git'in ilk versiyonunun yayımlanması ile verilmişitir. Aslında Git kelimesi İngiliz  ingilicesinde **"aptal"** anlamına gelen argo bir kelime. [**[2]**](https://dictionary.cambridge.org/dictionary/english/git)

<p align="center">
	<img alt="git_dictionary" src="/assets/posts/versiyon-kontrol-sitemi-git/git_dictionary.png" width="500">
</p>

Ayrıca Linus Torvalds "**GIT**" isminin açılımını şu şekilde ifade ediyor;
- Düzgün çalışıp iş gördüğünde ve sizi mutlu ettiğinde **Global Information Tracker**(Küresel bilgi takip sistemi)
- İstediğiniz gibi çalışmazsa ve sizi çıldırtırsa da **"Goddamn Idiotic Truckload of shit"**

## Git Nasıl kullanılır?

Öncelikle git versioyon kontrol sistemi yazılımının bilgisayarınızda yüklü olması gerekiyor.

Bunu öğrenmek için GNU/Linux bir işletim sistemi kullanıyorsanız paket yöneticiniz ile git programnı aratıp bilgisayarınıza yüklü olup olmadığını öğrenebilirsiniz.

<p align="center">
	<img alt="git_is_exist" src="/assets/posts/versiyon-kontrol-sitemi-git/git_is_exist.png" width="">
</p>

Eğer GNU/Linux dışında bir işletim sistemi kullanıyorsanız kurulum aşamalarınıa [**git'in resmi sitesinden**](https://git-scm.com/downloads) bakabilirsiniz.

---

### `git config`

Versiyonlamaya başlamadan önce yazacağımız kodların kimin tarafından yazılıdığının bilinmesi açısından GIT ayarlarımızı yapmamız gerekiyor.

hali hazırdaki git ayarlarını  görmek için

```bash
$ git config --list
```
Henüz bir ayar girmemişseniz boş bir çıktı alacaksınız. Ayarlamak için;

```bash
$ git config --global user.name "kullanıcı_adınız"
$ git config --global user.email "mail_adresiniz"
```

Şimdi projemizi versiyonlamak için hazırız.

### `git init`

Projemizi versiyonlamak için önce proje dizinimize girip ardından da git init komutunu yürütmemiz yeterli.

```bash
$ git init
Initialized empty Git repository in /projenin_adresi
```
Komutu yürüttükten sonra hiç bir şey değişmemiş gibi görüyor fakat öyle değil.

```bash
$ ls -a
.  ..  .git
```

git yazılımını projemizden başlatıktan sonra projemiz içine gizli halde gelen **git diznini** görmekteyiz. Bu dizin içinde versiyonlamaya dair tüm dosyalar tutuluyor. Bu dosyanın silinmesi halinde tüm versiyonlama işlemlermiz yok olacakıtır.  
