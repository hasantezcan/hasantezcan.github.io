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
	<img alt="responsive-gif" src="/assets/posts/versiyon-kontrol-sitemi-git/versiyon-kontrol-sitemi-sebep.png" width="400">
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
