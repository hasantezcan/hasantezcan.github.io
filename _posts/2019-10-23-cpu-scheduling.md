---
layout: post
title: "CPU Scheduling"
author: "Hasan Tezcan"
categories: blog
tags: [Operating Systems]
image: "cpu.jpeg"
date:   2019-10-23
---

İşlemci zamanlamak, çoklu işlem yapabilen işletim sistemlerinin temelini oluşturur. Bu işletim sistemleri, CPU kullanımını işlemler arasında değiştirerek bilgisayarlarımızı daha üretken hale getirirler.

Bu yazı boyunca temel CPU zamanlama kavramlarından ve bazı CPU zamanlama algoritmalarından bahsedeceğim.

Tek çekirdekli sistemlerde birim zamanda sadece bir işlem çalışabilir. Diğer işlemlerin çalışabilmesi için işlemci çekirdeklerinin boşalması ve tekrar zamanlanabilir hale gelmesi gerekir. Çoklu programlamanın amacı ise işlemci kullanımını en üst düzeye çıkartmaktır.

Basit bilgisayar sistemlerinde bir işlemin başlayabilmesi için diğeri işlemin bitmesi gerekir. Örnek olarak işlemciye gelen bir I/O işlemi aslında o dakikadan itibaren bir bir başka cihazın işlem biriminde çalışıyor olsa da henüz o cihazdan cevap gelmeyip işlem tamamlanmadığından cevap gelene kadar CPU boşa çalışmış olur. Fakat çoklu programlama ile birlikte zamanı daha verimli kullanmaya başlarız. Birkaç işlem aynı anda bellekte barınabilir ve bu sayede bir işlem beklerken işletim sistemi CPU'yu bu işlemden uzaklaştırıp  CPU'yuya yeni bir işlem verebilir. Böylece işlem gücü boşa harcanmamış olur.

Kaynakların zamanlanması verimlik bakımından çok önemlidir. Özellikle de en temel bilgisayar kaynağı olan işlemcinin zamanlanması bize büyük ölçüde verim sağlayacaktır.
> Tekrar Eden CPU ve I/O İşlem Döngüsü

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/cpu-io-burst-cycle.png" width="300">
</p>


## CPU– I/O Burst Cycle

CPU zamanlamasının başarısı, gözlenen süreç özelliklerine bağlıdır. İşlem yürütme CPU yürütme döngüsünden ve I/O beklemesinden oluşur. İşlemler bu iki durum arasında değişmektedir.

İşlemler yürümeye CPU burst ile başlarlar sonrasında bunu bir I/O burst takip eder ve bunu da bir başka CPU burst ve sonra tekrar I/O burst ve en son sistemin istemesiyle bir CPU burst ile çalışma durdurulur.
CPU - I/O burst döngüleri cihazdan cihaza değişseler de Figür 5.2 dekine benzer bir frekans eğrisine sahip olma eğilimindedirler.  

> CPU zamanının kullanılmasına CPU burst diyoruz.

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/histogram-of-cpu-burst-durations.png" width="450">
</p>

## CPU Scheduler
> *İşlemci zamanlayıcısı*

Bellekte(RAM) çalışmaya hazır halde bekleyen işlemlerden birini seçerek işlemciyi ona ayırır.

CPU Scheduler kararlarını işlem;

1. **Çalışma(running)** durumundan **bekleme(waiting)** durumuna geçerken,
2. **Çalışma(running)** durumundan **hazır(ready)** durumuna geçişte
3. **Bekleme(waiting)** durumundan **hazır(ready)** durumuna geçişte
4. **Sonlandığında(terminates)** verir.

- 1 ve 4 durumlarında yapılan zamanlama **nonpreemptive(kesmeyen)**
- Diğer durumlar is **preemptive(kesen)**
    - Tüm modern işletim sistemleri Windows, Mac OS, Linux, and UNIX preemptive zamanlama algoritmalarını kullanırlar.


## Dispatcher

İşlemleri **Ready Quiden(RAM'den)** CPU'ya yükleyen ardından da **CPU'daki** işlemleri RAM'e kaydeden kaydeden yapı. **Context switch**'i gerçekleştiren birim. Process'leri taşırken kaldığı yerleri kaydedip tekrar çalışma durumda kaldığı yerden devam etmesini sağlar.(Register'ları, program counter'ları kaldığı yerden devam ettirir.)

**Dispatch latency,** dispecher'ların bir programı sonlandırıp diğerini başlatması için gereken süre.(geçikme süresi)


## Scheduling Criteria
> Zamanlama Kriterleri

- **CPU utilization** *(İşlemci kullanımı)* **:** İşlemciyi olabildiğince meşgul tutmak.
    - 100 birimlik bir işlem vaktinde CPU'ya bindirebildiğimiz işlem yükü.
    - Örneğin 100 birimlik bir işlem vaktinde CPU'ya 80 birim iş yaptırmışsam %80'lik bir CPU kullanımımız mevcuttur.

- **Throughput** *(Üretilen iş)* **:** Birim zamanda bitirdiğimiz işlem sayısı.

- **Turnaraound time** *(Devir zamanı)* **:** Bir işlem sonlanana kadar geçen toplam zaman
    - Bir işlemin scheduler tarafından ready kuyruğundan seçilip işleminin bitmesine kadar geçen süre.
    - Başlangıcı ile bitişi arasındaki toplam zaman.

- **Waiting time** *(Bekleme zamanı)* **:** Bir işlemin ready kuyruğunda geçirdiği toplam süre. *Bekleme süresi.*

- **Response time** *(Yanıt süresi)* **:** Bir isteğin gönderilmesi ile bu isteğine verilen yanıt arasında geçen süre.

> Bu kriterlerden yalnızca "**CPU untilization ve Throughput**" değerinin **fazla** olmasını isteriz. Diğerlerinin değeri ne kadar **az** ise zamanlama optimizasyonları da o oranda iyi olur.

# Scheduling Algorithms

## 1. First-Come, First-Served Scheduling, "FCFS"

CPU'nun işlemleri gelme sırasına göre işleme aldığı zamanlama algoritmasıdır. FCFS'da ilk gelen iş ilk yapılır o bittikten sonra sıradaki iş alınır ve bu düzen böyle devam eder.

- *İşlem önceliği, işlemlerin sıraya girme sıralarına göre belirlenir.*

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_1.png" width="450">
</p>

- İşlem sırasının **"Process 2, Process 3, Process 1"** olması durumunda sonuç nasıl değişirdi?

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_2.png" width="450">
</p>

**Convoy effect:**

- Burst time'ı küçük olan işlemler ilk olarak işleme alınırsa daha iyi bir optimizasyon sağlanır.

## 2. Shortest-Job-First Scheduling, "SJF"

İşlerimi burst time'ı en küçük olan ilk sırada olcak şekilde sıralar ve işleme bu sırada koyar. SJF en optimal zamanlama algoritmasıdır. Verilen bir iş kümesi için minimum ortalama bekleme süresini(average waiting time) sağlar.

Bu algoritmada **zorluk** işlemci kullanım sürelerini(burst time) tahmin etmektir.

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_3.png" width="500">
</p>

**Not:** Bu algortimanın çok verimli çalışmasına karşın sorunu bir işlemin çalışmadan önce burst time'ını bilemeyecek olmamızdır. İşlemlerin ancak çalıştıktan sonra ne kadar süre çalıştığını görebiliriz. Ama bunu anlamak için bazı analiz yöntemleri mevcut. Örneğin önceki verilere göre değerlendirimeler yapılabiliyor. Böylece bir sonraki işlemin ne kadar süreceği tahmin edilmeye çalışılıyor.

## Determining Length of next CPU

- İşlemci kullanım süresinin belirlenmesi

Sadece tahmin edilebilir.

Daha önceki işlemci kulanım süreleri kullanılarak üssel ortalama(exponential averaging) yöntemiyle tahmin edilebilir.

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/determining-length_of_next_cpu.png" width="500">
</p>

- Genelde **α** 1/2 ye eşittir.
- Preemptive versiyonuna **"shortest-remaining-time-first"** denir.

### Shortest-remaining-time-first örneği

Demin çözdüğümüz soruya bir de ready kuyruğuna gelme zamanını(arrival time) eklersek bu sorunun çözümü nasıl değişir?

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_4.png" width="500">
</p>

## 3.Priority Scheduling

Her bir işleme öncelik sayısı (tamsayı) atanır.

CPU en öncelikli olan işleme tahsis edilir.

- **En yüksek öncelik = En küçük tam sayı**

Preemptive(Kesilebilen işlem) ise işlem devam etse dahi o an daha öncelikli bir işlem geldiğinde yarıda kesilip öncelikli işlem yapılır.

Nonpreemptive(Kesilemeyen işlem)'lerde iste işlem tamamlandıktan sonra en yüksek öncelik kimde ise CPU'yu o işlem kullanır.

Bu algoritmanın yanında getirdiği bir problem vardır. Bu da **Starvation problemidir(açlık).** Düşük öncelikli bir işlem üzerine ondan daha öncelikli işlemlerin çokça gelmesi durumunda az öncelikli işlemimiz asla CPU'yu kullanamaz. Bu sorunu gidermek için bir çözümde vardır.

**Aging yöntemi**(yaşlandırma) önüne aldığı her işlemde bu önceliği az olan işlemimizin önceliğini yavaş yavaş artırırız. Böylece bu önceliksiz işlem de sistem kaynaklarından yararlanabilir.

### Priority Scheduling Örneği

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_7.png" width="550">
</p>

## 4. Round Robin Scheduling, "RR"

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/bread.png" width="350">
</p>

İşlemlerin belirlenen bir süreye göre sıra sıra işleme sokulmasıdır. İşlemlerin CPU'da kalabileceği maksimum süreye **time quantum** denir. İşlemler time quantum'a göre sıra sıra işleme girer ve çıkarlar. Sırası gelen işlem ready queue'den alınıp CPU'da  işleme konur time quantum süresi bitmesi ardından ready queue'nın sonuna koyulur, ready queue'da hazır bekleyen işlem de CPU'ya verilir. Bir işlemin time quantum'dan önce tamamlanması halinde ise bir sonraki işleme geçilir.

**Time quantum'un** artması ve azalmasıyla ortaya çıkan bazı problemler var. Bunlar;

Çok yüksek time quantum belirlersek örneğin;

Time quantum'a 1 yıl dersek; bu bir yılda sadece bir işlem çalışacak demek oluyor yani başka bir proses çalışmayacak. Tabi bu durumda işlem bir yıldan önce biteceği için. İşlem bittikten sonra öbür işlem gelecek ... Bir noktadan sonra aslında iş FCFS'a dönmüş oluyor.

#### `Çok yüksek time quantum belirlersek iş FCFS'a döner.`

Time quantum'u çok düşük belirlememiz halinde de CPU'daki context switchlerin maliyeti artamaya başlıyor. Çünkü time quantum'u küçük belirlememiz çok sık process değişikli yapmamıza sebep oluyor.

#### `Çok küçük time quantum belirlemek context switch maliyetini artırır`
<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/quantum_context_switch_relation.png" width="500">
</p>

## Round Robin Scheduling örneği

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_5.png" width="500">
</p>

## Turnaround Time, Time Quantum ile değişir;


<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/time_quantum_average_turn_around_time_graphics.png" width="400">
</p>

***Hadi bunu kanıtlayalım;***


<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_6_0.png" width="450">
</p>

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_6_q3.png" width="500">
</p>

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_6_q4.png" width="500">
</p>

<p align="center">
	<img alt="responsive-gif" src="/assets/posts/cpu-scheduling/question_6_q5.png" width="500">
</p>

- Hesaplamalarımızı yaptıktan sonra sonuçlarımızın tablodakiler ile örtüştüğünü görmekteyiz.

---------
> **NOT:** Anlatım boyunca gördüğünüz soru çözümlerinin tümü, tarafımca Figma'da tasarlanmıştır. Herhangi bir hata görmeniz taktirinde bana ulaşabilirsiniz.  


- Anlatımımızın sonuna geldik umarım sizler için faydalı olmuştur. Bir daha görüşümek üzere. İyi çalışmalar. :)

---
**> Kaynakça**

- **[Operating System Concepts Tenth Edition](https://www.os-book.com/OS10/)**

<!--
```bash
## çoklu kuyruklu işlemci zamanlama algoritması

multi level queue

student poroc is **şaka şaka**

çok seviye geri beslme kuyruğu

linux kernelini gradu bir tez

37. sayfa 62 sayfa var

40.sayfa

## CFS

AĞIRLIKLI RAOUND ROBİNN

hem proslerin priorty var hemn de raoid robin kulnaılıyr

protylere göre quantum time dağıtılıyor.

44 .sayfa

kernel derlemek
``` -->
