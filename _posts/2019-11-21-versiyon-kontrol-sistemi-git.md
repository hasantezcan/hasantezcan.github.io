---
layout: post
title: "Versiyon Kontrol Sistemi GIT"
author: "Hasan Tezcan"
categories: blog
tags: [Git]
image: "/git.png"
date:   2019-11-21
---


Herhangi bir projeyi geliştiriken **`böyle bir tablo` ile muhakkak karşılaşmışsınızdır**. Bu bir ödevi yapmak için olabilir ya da bir şiir yazarken. 

<p align="center">
	<img alt="version_kontrol_sistemi" src="../assets/posts/versiyon-kontrol-sitemi-git/versiyon-kontrol-sitemi-sebep.png" width="400">
</p>

Projeniz üzerinde yapılan değişiklerinizi bir şekilde saklamak için aslına bu aşamalardan **geçen herkes** bu görselde olduğu ***farkına varmadan*** **`kendi versiyon kontrol sistemini geliştirir!`** ve bunu kullanır. 

Bu ilkel yönetemin ne kadar verimli olduğu tartışılır ama iyi düşünülmiş bir versiyon kontrol sistemine ihtiyaç duyduğumuz ortadadır.

Bugün sizlerle birlikte var olan versiyon kontrol sitemlerinden ve günümüzde yaygın olarak kullanılan GIT version kontol sisteminin nasıl kullanıldığından bahsedeceğim.

## Versiyon Kontrol Sistemi Nedir?

Versiyon kontol sistemleri herhangi bir proje üzerine çalışırken size yaptığınız değişiklikler ve yenilikler arasında boğulmadan temiz bir şekilde çalışabilme imkanı sunar.

Version kontol sistemleri ile çalışamayı öğrendikten sonra bir proje üzerinde **zamanda geri gidebilir** projenizin falanca zamanki halini o günkü hali ile inceleyebilir ya da projenizin o anki halini bozmadan üzerine yeni denemeler yapabilir ve bu denemeniz istediğiniz gibi olursa ana projenize bu özelliği ekleyebilirsiniz.

Bu söylediklerimi en başta gördüğümüz insan beyninin direk oluşturduğu versiyon kontrol sistemi ile yapmaya kalkmak bi yerde mantıklı olsa da bu yöntemle devam etmek bir yerden sonra **sizi sinir krizlerine sokabilir** **`hata ve hata projeninizi geliştirecem derken çalışır halinden de olmanıza sebep olablir.`**

Gelin şimdi var olan versiyon sistemlerne bir göz atalım.

- **CVS** : 1986, Versiyon kontrol sistemlerinin dedesidir.

- [**SVN**](http://subversion.tigris.org/) : Bu proje şu an kitli durumdadır.

- **`Git`** : üzerine detaylıca konuşacağımız versiyon kontrol sistemi.

- **Mercurial**

- **Bazaar**

- **Monotone**

> [**[0]**](https://www.smashingmagazine.com/2008/09/the-top-7-open-source-version-control-systems/),
> [**[1]**](https://www.g2.com/categories/version-control-systems?trending=)

Bu versiyon kontol sistemlerinden kimileri hala aktif kimileride şu an kulladığımız versiyon kontrol sistemlerine zamanına ilham olmuş ve şu an ömürlerini doldurmuş durumdadır.

Bugün biz günümüzde en yaygın kullanılan versiyon kontrol sistemi GIT ile çalışacağız ve projelerimizi git ile yönetmeyi öğreceğiz.

## Git Nedir?

[**Git**](https://git-scm.com/) özgür ve dağıtık bir version kontrol sistemidir. GIT, linux'ü geliştiren ekibin o zamanlar kullandıkları [**BitKeeper**](https://www.bitkeeper.org/) adlı proje yönetim araçının ücretsiz lisans anlaşmasının bitmesi ile Linus Toravalds ve ekibinin BitKeeper'ı kullanırken yaşadıkları sıkıntıları da göz ederek tasarladıkları 2005 yılında ortaya çıkan bir versiyon kontrol sistemidir.

Git ismi, [Linus Torvalds tarfından](https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git#:~:text=and%20in%20particular%20Linus%20Torvalds,%20the%20creator%20of%20Linux) Git'in ilk versiyonunun yayımlanması ile verilmişitir. Aslında Git kelimesi İngiliz  ingilicesinde **"aptal"** anlamına gelen argo bir kelime. [**[2]**](https://dictionary.cambridge.org/dictionary/english/git)

**bakınız:** [A Short History of Git](https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git)

<p align="center">
	<img alt="git_dictionary" src="../assets/posts/versiyon-kontrol-sitemi-git/git_dictionary.png" width="500">
</p>

Ayrıca Linus Torvalds "**GIT**" isminin açılımını şu şekilde ifade ediyor;
- Düzgün çalışıp iş gördüğünde ve sizi mutlu ettiğinde **Global Information Tracker** (Küresel bilgi takip sistemi)
- İstediğiniz gibi çalışmazsa ve sizi çıldırtırsa da **"Goddamn Idiotic Truckload of shit"**

## Neden `Versiyon Kontrol Araçları` kullanırız?

Genel olarak bir şeyler üretirken **hızlı hızlı** ilerleme yolunu seçiyoruz. Yazılım geliştiriken de verilen bir ödevi **hızlıca bitirip teslim etmek** çok daha kolayımıza gelebiliyor.

<p align="center">
	<img alt="" src="../assets/posts/versiyon-kontrol-sitemi-git/fast-chess.gif" width="100%">
</p>

Ödevlerin kapsamı küçük olduğu zaman bu yaklaşım gerçekten pratik bir çözüm olabiliyor. Fakat işler büyüdüğünde yani **`profesyonelleştiğinde`** hızlı hızlı hareket etmek zorlaşıyor ve **hata payınız git gide büyüyor.**

Böyle büyük çaplı işlerde ya da finansal sorumluluğunuz olan projelerde hata yapma şansınız çok daha az oluyor.

İşte tam bu durumu idare etmek ve yönetmek için **versiyon kontrol** kulanmak kaçınılmaz oluyor. 

Başta angarya gibi gelen **bu süreçin;** bir hata ile karşı karşıya kaldığında ve versiyon kontorlü yaptığınız için bu hataya hızlıca çözüm getirebildiğinizi gördüğünüzde **hiç de angaryadan olmadığını anlıyorsunuz.**

<p align="center">
	<img alt="" src="../assets/posts/versiyon-kontrol-sitemi-git/kasparov.gif" width="100%">
</p>

**Satranç oyunu** bu durumu anlamak ve açıklamak için çok güzel bir benzetme.

Eğer bir satranç musabakası izlediyseniz oyuncuların her hamleden sonra tahtanın yanı başındaki bir kağada bir şeyler yazdıklarını görmüşsünüzdur. 

<p align="center">
	<img alt="" src="../assets/posts/versiyon-kontrol-sitemi-git/chess-game.jpeg" width="100%">
</p>

Satranç oyuncuları bu kağıtlara oyun esnasında yapılan hamleleri not etmektedirler. İki oyuncuda bu hamleleri kaydeder. Maç sonunda bu kaydedilen hamleler sayesinde o maç baştan sona incelenebilir hale gelir. Yani o maçı her versiyonu ile iki oyuncu kayıt altına almış olur.

<p align="center">
  <img alt="imgName" src="../assets/posts/versiyon-kontrol-sitemi-git/chess-score-sheet-example.jpeg" width="65%">
  <br>
	<em>Chess score sheet example <a href="https://blog.chesshouse.com/how-to-read-and-write-algebraic-chess-notation/">- source</a> </em>
</p>

Öteyandan arkadaşlar arasında keyfine yapılan hızlı maçlar esnasında. Bu işlemi yapmak sizlere büyük bir angarya olarak gelebilir. İşte burada önemli yaptığınız projenin **sizin için ne kadar önemli olduğudur.**


## Git Nasıl kullanılır?
> **Git'in Temelleri**

Öncelikle git versioyon kontrol sistemi yazılımının **bilgisayarınızda yüklü olması** gerekiyor.

Bunu öğrenmek için GNU/Linux bir işletim sistemi kullanıyorsanız paket yöneticiniz ile git programnı aratıp bilgisayarınıza yüklü olup olmadığını öğrenebilirsiniz.

<p align="center">
	<img alt="git_is_exist" src="../assets/posts/versiyon-kontrol-sitemi-git/git_is_exist.png" width="">
</p>

Eğer GNU/Linux dışında bir işletim sistemi kullanıyorsanız kurulum aşamalarınıa [**git'in resmi sitesinden**](https://git-scm.com/downloads) bakabilirsiniz.

---

### `git init`

Projemizi versiyonlamak için önce proje dizinimize girip ardından da `git init` komutunu yürütmemiz yeterli.

```bash
$ git init
Initialized empty Git repository in /projenin_adresi
```
Komutu yürüttükten sonra projemiz içinde hiç bir şey değişmemiş gibi görünüyor fakat öyle değil.

```bash
$ ls -a
.  ..  .git
```

Git yazılımını projemizden başlatıktan sonra projemiz içine gizli halde gelen **.git diznini** görmekteyiz. Bu dizin içinde versiyonlamaya dair tüm dosyalar tutuluyor.

Bu dosyanın silinmesi halinde tüm versiyonlama işlemlermiz yok olacakıtır.

**`!!!`** Hatalı bir `git init` çalıştırılması durumunda `.git` dizinini silmek **versiyon kontrolünü dizninizden kaldıracaktır.**

---

<p align="center">
	<img alt="git_areas" src="../assets/posts/versiyon-kontrol-sitemi-git/git_areas.png" width="500">
</p>

## **`Commit`** Nedir ve Nasıl Çalışır?


### `git status`


### `git add`

iki tür dosya durumu vardır bunlar **tracked** ve **untracked**

Dosyaları staging area'ya almak için - stage

```bash
$ git add <dosya_adı>
```


stagin areaden çıkarmak için - unstage
```bash
$ git rm --cached <dosya_adı>
```

bu olaylar direk .git dosyalarına yansır bunu göremek için

ayrı bir terminalde şu komutu çalıştırsanız değişiklerikeri takip edebilrsiniz.

```bash
$ watch -n .5 tree .git
```

3 adet git objesi vardır bunlar;
- **blob** - collect of date - row data - descreption about the data
- **tree** - ...
- **commit** - en of the snapshot versionesed one

[**[3]**](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects)





### `git commit`

> a new snapshot


Bir commit geri gider yani HEAD kafasını bir önceki commitin kine eş hale getirir. Son durumdan kalan değişikler untracked hale gelir.
```bash
git reset HEAD~
```

<p align="center">
	<img alt="git_areas" src="../assets/posts/versiyon-kontrol-sitemi-git/cat-dog.png" width="500">
</p>

### `git log`



---

## Branchlar ile çalışmak

## `git brach`

bütün brachları listeler

```bash
git branch
```

brach oluşturmak

```bash
git checkout -b <branch_adi>
```

local brach silmek

```bash
git branch -d <branch_adi>
```

brachdaki güncellemeleri uzak depoya yollar
```bash
git push origin <branchname>
```
## `git stash`

```bash
git stash

git stash pop
```

## .gitignore dosyası

https://careerkarma.com/blog/gitignore/



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

## Annotation

**Annotation** denen bir kavramdan bahsetmek istiyorum. Türkçe dipnot demek olan bu kavram yazılan kod satırlarının kim tarafından yazıldığını ifade eder. Demin girdiğimiz git config'leri (ayarları) bu annotation'larda gözükür. Bu kullandığınız ide ya da metin editorlerinde ya kendiliğinden gelecektir ya da eklenti şekilde kurulabilir.  

<p align="center">
	<img alt="git_annotation" src="../assets/posts/versiyon-kontrol-sitemi-git/git_annotation.png" width="100%">
</p>

Annotation'lar sayasinde bir projede çalışırken okduğunuz kodun **kim tarafından ne zaman yazıldığını görebilirsiniz.** Ve dilediğiniz zaman bu kod parçacıkları için kodun sahibi ile belirttiği e-posta adresi ile ileteşime geçebilirsiniz.

Yani annotation'lar bir nevi imza görevi görür.  

**bakınız:** [vsCode için git lens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) eklentisi

---

# `Özel sorunlar ve çözümleri`

## Repo transfer etmek

Bunun için iki yol mevcut;
biri tüm commitlerinizi de saklayıp trasnfer etmek, diğeri de hiç bir commitinizi saklamadan trasfer etmek.

İkinci yol en basit olan hadi onla başlayalım.

### Bir git reposunu commit geçmişSİZ yeni bir repoya taşıma

Repolarımızda git ile ilgli tüm dosyalar `.git` adlı bir dizinde tutulur. Config dosyalarımız, commit geçmişimiz vb. tümü bu dosya içindedir.

Bizim commitlerimizi saklama gibi bir derdimiz yoksa bu dosyayı silmemiz gerekir ki tüm commitlerden arınalım ve yeni bir başlangıç yapalım.

GNU/Linux sistemlerde gizli dosyaları görmek için `ctrl + h` kısa yolunu kullanabilirsiniz.

```bash
rm -rf .git
```

dedikten sonra repo içindeki tüm dosyaları yeni reponuza yapıştırıp ilk commitinizi atabilirsiniz.

```
git add .
git commit -m "Initial commit"
```


### Bir git reposunu commit geçmişi ile beraber yeni bir repoya taşıma

> Git reponuzu commit geçmişi brachları ve tag'ları ile beraber yeni bir repoya yüklemek.

Hadi bu durmu simule edelim elinizde bir repo var ve bu repoyu bambaşka yeni bir repoya taşımak istiyorsunuz. Tüm commitler ile beraber. Taşıyacağınız repo bir başka kişinin reposu olabilir ya da bir organizasyon reposu olabilir. Bu hiç bir şeyi değiştirmez. Peki nasıl yaparız?

`1-` **İlk olarak transfer edeceğiniz repoyu belirleyin. Belli bir reponuz yoksa yeni bir repo oluşturun.**


`2-` **Sonrasında eski reponun bir mirror reposunu yaratarak başlayacağız.**

```bash
git clone --mirror old-repo-url new-repo-name
```

> `old-repo-url` yazan kısma taşımak istediğiniz reponun url'ini yazın. ve `new-repo-name` yazan yere de trasfer edeceğiniz reponun adını yazın.


`3-` **Repoya girin ve eski(orjinal) reponun remote referans bilgisini temizleyin.**

```bash
cd new-repo-name
```

Remote referans bilgisini sildiğinizi bu çalıştırılabilir ile kontrol edebilirsiniz.
> (Q ya basarak çıkabilirsiniz.)

```bash
git config --list
```

```bash
git remote remove origin
```
Bu çalıştırılabiliri çalıştırdıkran sonra remote bilgisinin artık olmadığını göreceksiniz.


`4-` **Yeni reponunuzun remote bilgisini ekleme**

Github, gitlab ya da bitbucket uzak reponuz neredeyse uzak reponuzun remote linkini local reponuza bu şekilde ekleyin;

```bash
git remote add origin new-repo-url
```
> `new-repo-url` yerine uzak reponuzun(remote) URL'ini girin.	 

`5-` **Yapılan tüm düzenlemeleri uzak repoya yollayın**

```bash
git push --all
git push --tags
```

`6-` **Uzak deponuzu clone'layın ve üzerinde çalıştığınız repoyu silin**

Bir üst dizine çıkıp üzerinizde çalıştığınız repoyu silin. Bu adımı bu repo üzerinde bu hali ile çalışamadığımız için gerçekleştiriyoruz. Bu haliyle içinde git dosyaları açık şekilde çalışıyor. Ve bu istemediğimiz bir şey.

```bash
cd ..
rm -rf new-repo-name
```

Sonrasında uzak repomuzdan(remote) bilgisayarımıza(local) tekar indiriyoruz.

```bash
git clone new-repo-url
```
> `new-repo-url` yerine uzak reponuzun(remote) URL'ini girin.


Bu aşamadan sonra reponuzu commitleri ile birlikte yeni reponuza transfer taşımış bulunuyorsunuz.

---

## Fork edilmis bir repoyu ana repo ile senkron etmek!

Aidiyetligi sizde olmayan bir repoya pull request attınız ve pull requestiniz merge oldu. Üzerine başka değişiklikler yapıldı ya da yapılmadı. Zaten merge olduktan sonra sizin reponuz bir commit geri kalıyor. Ve onu senkron etmeniz gerekiyor.

Bunu nasıl yaparız?

<!-- Github kullanıyorsanız arayüzden "Compare" tuşununa basıp bu işlemi gerçekleştirmeniz mümkün.

<p align="center">
	<img alt="git_areas" src="../assets/posts/versiyon-kontrol-sitemi-git/github-compare.png" width="800">
</p> -->

Komut satırı üzerinden nasıl yapılacağına bakalım.


```bash
$ git remote add upstream <original-repo-url>
```

```bash
$ git fetch upstream   # update local with upstream
```

```bash
$ git diff HEAD..upstream/master     # see diffs between local and upstream/master (if there is no diff then both are in sync)
```
```bash
$ git pull upstream master           # pull upstream's master into local branch
```
```bash
$ git push origin HEAD               # push to your forked repo's remote branch
```
[**[0]**](https://stackoverflow.com/questions/41542640/how-to-synchronize-fork-with-original-github-project)




..   
..  
..  
..   
..  
..  
..   
..  
..  
..   
..  
..  
..   
..  
..  
..   
..  
..  

## `Kaynakça:`
- [7 rules of a great git commit message](https://chris.beams.io/posts/git-commit/#:~:text=The%20seven%20rules%20of%20a%20great%20Git%20commit%20message)
- [Basic git commands](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html)
- [Atlassian git resource](https://www.atlassian.com/git)
