---
aliases: [Deneme 02, Çözümlü Sınav]
tags: [ders/tesis-planlama, deneme, bütünleme, çözümlü]
süre: 90 dakika
puan: 100
durum: aktif
---

# Deneme 02 — Adım Adım Çözümlü Tam Sınav

> [!danger] Çalışma Kuralı
> Önce her soruyu **çözümleri kapalı** olarak çöz. Bitirince cevabını aç ve her adımı karşılaştır. Bir adım bile farklıysa hata kodunu tabloya yaz.

| Soru | Konu | Yöntem | Puan |
|:---:|---|---|---:|
| S1 | Çok ürünlü başa baş | Ağırlıklı CMR | 10 |
| S2 | Rassal ıskarta ve beklenen kâr | Binom + karar | 10 |
| S3 | Aşamalı fire ve makine | Geriye yürütme + $\lceil F\rceil$ | 10 |
| S4 | Operatör-makine atama | $n'$ ve $C_u$ | 10 |
| S5 | ROC hücre oluşturma | İkili ağırlık | 10 |
| S6 | From-to ve Hollier | Sıralama oranı | 10 |
| S7 | CRAFT ikili değişim | $\Delta C$ hesabı | 10 |
| S8 | CORELAP | TCR + yerleştirme puanı | 10 |
| S9 | Minisum + Minimax | Ağırlıklı medyan + UV dönüşüm | 15 |
| S10 | Kesikli tesis konumu | Enümerasyon + net tasarruf | 15 |
| **Toplam** | | | **100** |

---

## S1 — Çok Ürünlü Başa Baş · 10 puan

Bir fabrikada üç ürün üretilmektedir. Sabit maliyet 720 000 TL/yıldır.

| Ürün | Birim fiyat (TL) | Değişken maliyet (TL) | Satış hacmi (adet/yıl) |
|:---:|---:|---:|---:|
| A | 200 | 120 | 3 000 |
| B | 150 | 90 | 5 000 |
| C | 300 | 180 | 2 000 |

**(a)** Her ürün için katkı marjı oranını (CMR) bulun.  
**(b)** Ağırlıklı CMR'yi hesaplayın.  
**(c)** Başa baş satış hacmini (TL cinsinden) bulun.

> [!answer]- Adım Adım Çözüm
>
> ### Adım 1 — Katkı Marjı Oranları
>
> $$CMR_i = \frac{P_i - V_i}{P_i}$$
>
> | Ürün | $P-V$ | CMR |
> |:---:|---:|---:|
> | A | $200-120=80$ | $80/200=0{,}40$ |
> | B | $150-90=60$ | $60/150=0{,}40$ |
> | C | $300-180=120$ | $120/300=0{,}40$ |
>
> ### Adım 2 — Toplam Satış Gelirleri ve Paylar
>
> | Ürün | Gelir (TL) | Pay $w_i$ |
> |:---:|---:|---:|
> | A | $200\times3000=600\,000$ | $600/1\,750=0{,}343$ |
> | B | $150\times5000=750\,000$ | $750/1\,750=0{,}429$ |
> | C | $300\times2000=600\,000$ | $600/1\,750=0{,}343$ |
> | **Toplam** | **1 750 000** | **1,000** |
>
> ### Adım 3 — Ağırlıklı CMR
>
> $$\overline{CMR} = \sum_i w_i \cdot CMR_i = 0{,}343(0{,}40)+0{,}429(0{,}40)+0{,}343(0{,}40)$$
>
> > [!note] Dikkat
> > Bu sorudaki tüm CMR değerleri eşittir (0,40). Bu durum nadir olmakla birlikte gerçek sorularda farklı CMR'ler beklenir.
>
> $$\overline{CMR} = 0{,}40\;(0{,}343+0{,}429+0{,}343) = 0{,}40 \times 1 = 0{,}40$$
>
> ### Adım 4 — Başa Baş Satış Hacmi
>
> $$S_{BB} = \frac{F}{\overline{CMR}} = \frac{720\,000}{0{,}40} = 1\,800\,000 \text{ TL}$$
>
> > [!success] Karar
> > Karışım sabit kalırsa toplam satış 1 800 000 TL'yi geçtiğinde fabrika kâra geçer.

---

## S2 — Rassal Iskarta ve Beklenen Kâr · 10 puan

Kalite kontrolden sağlam çıkma olasılığı **%80** olan bir süreçte tam **3 sağlam ürün** teslim edilirse **90 000 TL** gelir elde edilecektir; eksik teslimat kabul edilmez. Bir ürün üretim maliyeti **20 000 TL**'dir.

$Q=3, 4, 5$ değerleri için beklenen kârı hesaplayın ve en iyi kararı verin.

> [!answer]- Adım Adım Çözüm
>
> ### Adım 1 — Formül Kurulumu
>
> $X \sim \text{Bin}(Q, 0{,}80)$ olmak üzere:
>
> $$E[\Pi(Q)] = 90\,000 \times P(X \ge 3) - 20\,000 \times Q$$
>
> ### Adım 2 — $Q=3$ için Hesap
>
> $$P(X=3)=\binom33(0{,}8)^3(0{,}2)^0=0{,}512$$
>
> $$P(X\ge3)=0{,}512$$
>
> $$E[\Pi(3)]=90\,000(0{,}512)-20\,000(3)=46\,080-60\,000=-13\,920 \text{ TL}$$
>
> ### Adım 3 — $Q=4$ için Hesap
>
> $$P(X=3)=\binom43(0{,}8)^3(0{,}2)^1=4(0{,}512)(0{,}2)=0{,}4096$$
>
> $$P(X=4)=\binom44(0{,}8)^4(0{,}2)^0=0{,}4096$$
>
> $$P(X\ge3)=0{,}4096+0{,}4096=0{,}8192$$
>
> $$E[\Pi(4)]=90\,000(0{,}8192)-20\,000(4)=73\,728-80\,000=-6\,272 \text{ TL}$$
>
> ### Adım 4 — $Q=5$ için Hesap
>
> $$P(X=3)=\binom53(0{,}8)^3(0{,}2)^2=10(0{,}512)(0{,}04)=0{,}2048$$
>
> $$P(X=4)=\binom54(0{,}8)^4(0{,}2)^1=5(0{,}4096)(0{,}2)=0{,}4096$$
>
> $$P(X=5)=(0{,}8)^5=0{,}3277$$
>
> $$P(X\ge3)=0{,}2048+0{,}4096+0{,}3277=0{,}9421$$
>
> $$E[\Pi(5)]=90\,000(0{,}9421)-20\,000(5)=84\,789-100\,000=-15\,211 \text{ TL}$$
>
> ### Özet Tablo
>
> | $Q$ | $P(X\ge3)$ | Gelir beklentisi | Maliyet | Beklenen kâr |
> |:---:|---:|---:|---:|---:|
> | 3 | 0,5120 | 46 080 | 60 000 | **−13 920** |
> | 4 | 0,8192 | 73 728 | 80 000 | **−6 272** |
> | 5 | 0,9421 | 84 789 | 100 000 | **−15 211** |
>
> > [!success] Karar
> > Üç aday içinde en az kayıp **Q = 4** ile gerçekleşir (−6 272 TL). Beklenen kâr tüm adaylarda negatif olduğundan bu sözleşme finansal olarak dezavantajlıdır; ancak zorunluysa Q = 4 seçilir.

---

## S3 — Aşamalı Fire ve Makine Gereksinimi · 10 puan

Üç sıralı operasyondan sonra **500 sağlam ürün** gerekmektedir. Fire oranları sırasıyla $s_1=0{,}05$, $s_2=0{,}03$, $s_3=0{,}02$'dir.

**(a)** Kesirli ilk giriş miktarını bulun.  
**(b)** Her aşamada tam sayı zorunluysa geriye doğru planı çıkarın.  
**(c)** Operasyon 1'de standart süre 6 dk/parça, tek vardiya 480 dk, performans %88, güvenilirlik %90 ise gerekli makine sayısını bulun.

> [!answer]- Adım Adım Çözüm
>
> ### Adım 1 — Kesirli Giriş
>
> $$I_1=\frac{O_3}{\prod_{k=1}^{3}(1-s_k)}=\frac{500}{0{,}95\times0{,}97\times0{,}98}=\frac{500}{0{,}9031}\approx 553{,}7$$
>
> ### Adım 2 — Geriye Tam Sayı Planlama
>
> Geri yürütme sırasıyla:
>
> $$I_3=\left\lceil\frac{500}{1-0{,}02}\right\rceil=\left\lceil\frac{500}{0{,}98}\right\rceil=\lceil510{,}20\rceil=511$$
>
> $$I_2=\left\lceil\frac{511}{1-0{,}03}\right\rceil=\left\lceil\frac{511}{0{,}97}\right\rceil=\lceil526{,}8\rceil=527$$
>
> $$I_1=\left\lceil\frac{527}{1-0{,}05}\right\rceil=\left\lceil\frac{527}{0{,}95}\right\rceil=\lceil554{,}7\rceil=555$$
>
> | Aşama | Girdi | Fire | Çıktı |
> |:---:|---:|---:|---:|
> | Op 1 | 555 | $555\times0{,}05=27{,}75\to28$ | 527 |
> | Op 2 | 527 | $527\times0{,}03=15{,}81\to16$ | 511 |
> | Op 3 | 511 | $511\times0{,}02=10{,}22\to11$ | 500 ✓ |
>
> ### Adım 3 — Makine Gereksinimi
>
> $$F=\frac{S\cdot I_1}{E\cdot H\cdot R}=\frac{6\times555}{0{,}88\times480\times0{,}90}$$
>
> $$F=\frac{3\,330}{380{,}16}=8{,}76$$
>
> $$\lceil8{,}76\rceil=\mathbf{9}\text{ makine}$$
>
> > [!warning] Yuvarlama Yönü
> > Üretim hedefi karşılanmalı → daima $\lceil F\rceil$ alınır. 8 makine kapasite yetersizliği yaratır.

---

## S4 — Operatör-Makine Atama · 10 puan

Otomatik makinede: yükleme süresi $a=1{,}5$ dk, makine çalışma süresi $t=5$ dk, boşaltma süresi $b=0{,}5$ dk. Operatör saatlik maliyeti $c_o=60$ TL, makine saatlik maliyeti $c_m=90$ TL.

**(a)** Teorik atama sayısını bulun.  
**(b)** $m=2$ ve $m=3$ için çevrim süresini, üretim hızını ve birim maliyeti hesaplayın.  
**(c)** Hangi atama ekonomiktir?

> [!answer]- Adım Adım Çözüm
>
> ### Adım 1 — Teorik Atama Sayısı
>
> $$n'=\frac{a+t}{a+b}=\frac{1{,}5+5}{1{,}5+0{,}5}=\frac{6{,}5}{2{,}0}=3{,}25$$
>
> Adaylar: $\lfloor3{,}25\rfloor=3$ ve $\lceil3{,}25\rceil=4$. Bu örnekte $m=2$ ve $m=3$ karşılaştırılacak.
>
> ### Adım 2 — $m=2$ için
>
> $$T(2)=\max\{a+t,\;m(a+b)\}=\max\{6{,}5,\;2(2{,}0)\}=\max\{6{,}5,\;4{,}0\}=6{,}5\text{ dk}$$
>
> Operatör bekliyor (boş kalıyor), çünkü $m(a+b)<a+t$.
>
> $$r(2)=\frac{2}{6{,}5}=0{,}308\text{ parça/dk}$$
>
> $$C_u(2)=\frac{(c_o+mc_m)\cdot T(m)}{m}=\frac{(60+2\times90)\times(6{,}5/60)}{2}=\frac{240\times0{,}1083}{2}=\frac{26}{2}=13\text{ TL/parça}$$
>
> ### Adım 3 — $m=3$ için
>
> $$T(3)=\max\{6{,}5,\;3(2{,}0)\}=\max\{6{,}5,\;6{,}0\}=6{,}5\text{ dk}$$
>
> $$r(3)=\frac{3}{6{,}5}=0{,}462\text{ parça/dk}$$
>
> $$C_u(3)=\frac{(60+3\times90)\times(6{,}5/60)}{3}=\frac{330\times0{,}1083}{3}=\frac{35{,}75}{3}=11{,}92\text{ TL/parça}$$
>
> ### Özet
>
> | $m$ | $T(m)$ dk | Üretim hızı | $C_u$ TL/parça |
> |:---:|---:|---:|---:|
> | 2 | 6,5 | 0,308 | 13,00 |
> | 3 | 6,5 | 0,462 | **11,92** |
>
> > [!success] Karar
> > $m=3$ hem daha yüksek üretim hızı hem de daha düşük birim maliyet sağlar. Operatör kullanımı artarken makine kullanımı değişmez (çevrim süresi aynı kaldı).

---

## S5 — ROC Hücre Oluşturma · 10 puan

Aşağıdaki $5\times5$ makine-parça matrisi verilmiştir ($M$: Makine, $P$: Parça).

| | P1 | P2 | P3 | P4 | P5 |
|:---:|:---:|:---:|:---:|:---:|:---:|
| **M1** | 1 | 0 | 1 | 0 | 1 |
| **M2** | 0 | 1 | 0 | 1 | 0 |
| **M3** | 1 | 0 | 1 | 0 | 0 |
| **M4** | 0 | 1 | 0 | 1 | 1 |
| **M5** | 1 | 0 | 0 | 0 | 1 |

ROC algoritmasını uygulayarak blok köşegen yapıya ulaşın. Sütun ve satır sırasını verin.

> [!answer]- Adım Adım Çözüm
>
> ### Adım 1 — Satır Puanları ($C=5$ sütun)
>
> Ağırlıklar soldan sağa: $2^4=16$, $2^3=8$, $2^2=4$, $2^1=2$, $2^0=1$
>
> | Makine | P1 | P2 | P3 | P4 | P5 | Skor |
> |:---:|:---:|:---:|:---:|:---:|:---:|---:|
> | M1 | 1 | 0 | 1 | 0 | 1 | $16+4+1=21$ |
> | M2 | 0 | 1 | 0 | 1 | 0 | $8+2=10$ |
> | M3 | 1 | 0 | 1 | 0 | 0 | $16+4=20$ |
> | M4 | 0 | 1 | 0 | 1 | 1 | $8+2+1=11$ |
> | M5 | 1 | 0 | 0 | 0 | 1 | $16+1=17$ |
>
> Azalan skor → Yeni satır sırası: **M1(21), M3(20), M5(17), M4(11), M2(10)**
>
> ### Adım 2 — Yeniden Sıralanmış Matris
>
> | | P1 | P2 | P3 | P4 | P5 |
> |:---:|:---:|:---:|:---:|:---:|:---:|
> | M1 | 1 | 0 | 1 | 0 | 1 |
> | M3 | 1 | 0 | 1 | 0 | 0 |
> | M5 | 1 | 0 | 0 | 0 | 1 |
> | M4 | 0 | 1 | 0 | 1 | 1 |
> | M2 | 0 | 1 | 0 | 1 | 0 |
>
> ### Adım 3 — Sütun Puanları ($R=5$ satır)
>
> Ağırlıklar yukarıdan aşağıya: $2^4=16$, $2^3=8$, $2^2=4$, $2^1=2$, $2^0=1$
>
> | Parça | M1 | M3 | M5 | M4 | M2 | Skor |
> |:---:|:---:|:---:|:---:|:---:|:---:|---:|
> | P1 | 1 | 1 | 1 | 0 | 0 | $16+8+4=28$ |
> | P3 | 1 | 1 | 0 | 0 | 0 | $16+8=24$ |
> | P5 | 1 | 0 | 1 | 1 | 0 | $16+4+2=22$ |
> | P2 | 0 | 0 | 0 | 1 | 1 | $2+1=3$ |
> | P4 | 0 | 0 | 0 | 1 | 1 | $2+1=3$ |
>
> Azalan skor → Yeni sütun sırası: **P1(28), P3(24), P5(22), P2(3), P4(3)**
>
> P2 ve P4 bağ durumunda — sıra muhafaza edilir: P2 önce.
>
> ### Adım 4 — Son Blok Köşegen Matris
>
> | | **P1** | **P3** | **P5** | **P2** | **P4** |
> |:---:|:---:|:---:|:---:|:---:|:---:|
> | **M1** | 1 | 1 | 1 | 0 | 0 |
> | **M3** | 1 | 1 | 0 | 0 | 0 |
> | **M5** | 1 | 0 | 1 | 0 | 0 |
> | **M4** | 0 | 0 | 1 | 1 | 1 |
> | **M2** | 0 | 0 | 0 | 1 | 1 |
>
> > [!success] Sonuç
> > **Hücre 1:** M1, M3, M5 — P1, P3, P5 (artık eleman: P5, M4 birden fazla hücreyi kapsamaktadır).
> > **Hücre 2:** M4, M2 — P2, P4.
> > P5 iki hücreyle ortak; bu bir "kemik" (bottleneck) parçadır ve pratik çözümde çoğaltma veya özel yönlendirme gerektirir.

---

## S6 — From-To Matrisi ve Hollier Sıralaması · 10 puan

Dört bölüm (1-2-3-4) arasındaki yönlü akış matrisi aşağıdadır:

| From\To | 1 | 2 | 3 | 4 |
|:---:|:---:|:---:|:---:|:---:|
| 1 | — | 40 | 0 | 20 |
| 2 | 10 | — | 30 | 0 |
| 3 | 0 | 0 | — | 50 |
| 4 | 30 | 0 | 10 | — |

**(a)** Her bölüm için gönderilen (G) ve alınan (A) toplam akışları bulun.  
**(b)** Hollier sıralama oranlarını hesaplayın.  
**(c)** Hollier sıralamasını oluşturun ve akış yüzdelerini bulun (ileri, atlamalı, geri).

> [!answer]- Adım Adım Çözüm
>
> ### Adım 1 — G ve A Hesabı
>
> | Bölüm | G (Gönderilen) | A (Alınan) | Oran $G/A$ |
> |:---:|---:|---:|---:|
> | 1 | $40+0+20=60$ | $10+0+30=40$ | $60/40=1{,}50$ |
> | 2 | $10+30+0=40$ | $40+0+0=40$ | $40/40=1{,}00$ |
> | 3 | $0+0+50=50$ | $0+30+10=40$ | $50/40=1{,}25$ |
> | 4 | $30+0+10=40$ | $20+0+50=70$ | $40/70=0{,}57$ |
>
> ### Adım 2 — Hollier Sıralaması
>
> Sıralama oranı büyükten küçüğe: $1(1{,}50) > 3(1{,}25) > 2(1{,}00) > 4(0{,}57)$
>
> **Hollier sırası:** **1 → 3 → 2 → 4**
>
> ### Adım 3 — Akış Analizi
>
> Sıra: 1(konum 1) → 3(konum 2) → 2(konum 3) → 4(konum 4)
>
> Her akış çifti için yönü belirle:
>
> | Akış | Miktar | 1→3 | 1→2 | 1→4 | 3→2 | 3→4 | 2→4 | Geri mi? |
> |---|---:|---|---|---|---|---|---|---|
> | $f_{13}=0$ | 0 | ileri | | | | | | |
> | $f_{14}=20$ | 20 | | atlama | | | | | |
> | $f_{12}=40$ | 40 | | atlama(2→3 arası üzerinden geçer) | | | | | |
>
> > [!note] Not
> > "Atlama" = bir konum atlayarak ileri; sıra 1→3→2→4 olduğundan 1→2 hareketi bölüm 3'ü atlıyor.
>
> Tüm akışlar (sıfırlar hariç):
>
> | Çift | Miktar | Yön |
> |---|---:|---|
> | 1→2 (1.kn → 3.kn) | 40 | İleri (atlamalı) |
> | 1→4 (1.kn → 4.kn) | 20 | İleri (atlamalı) |
> | 2→1 (3.kn → 1.kn) | 10 | **Geri** |
> | 2→3 (3.kn → 2.kn) | 30 | **Geri** |
> | 3→4 (2.kn → 4.kn) | 50 | İleri |
> | 4→1 (4.kn → 1.kn) | 30 | **Geri** |
> | 4→3 (4.kn → 2.kn) | 10 | **Geri** |
>
> Toplam akış: $40+20+10+30+50+30+10=190$
>
> | Yön | Miktar | Yüzde |
> |---|---:|---:|
> | İleri (ardışık) | 50 | $50/190=26{,}3\%$ |
> | İleri (atlamalı) | 60 | $60/190=31{,}6\%$ |
> | Geri | 80 | $80/190=42{,}1\%$ |
>
> > [!warning]
> > Geri akış %42 → bu yerleşim sırası zayıf; bölüm arasındaki çift yönlü bağımlılıklar ($2\leftrightarrow4$ gibi) Hollier'ın sınırlılığını gösterir.

---

## S7 — CRAFT İkili Değişim · 10 puan

Dört bölüm (A, B, C, D) 2×2 ızgaraya yerleştirilmiştir:

```
┌──────┬──────┐
│  A   │  B   │   Satır 1
├──────┼──────┤
│  C   │  D   │   Satır 2
└──────┴──────┘
```

Ağırlık merkezleri (konum merkezi): A=(0,5;1,5), B=(1,5;1,5), C=(0,5;0,5), D=(1,5;0,5). Dikdörtgen uzaklık kullanılır.

Yönlü akış ve birim maliyet (tüm çiftler için $c_{ij}=1$):

| | A | B | C | D |
|:---:|---:|---:|---:|---:|
| **A** | — | 10 | 30 | 5 |
| **B** | 5 | — | 0 | 20 |
| **C** | 10 | 0 | — | 40 |
| **D** | 0 | 15 | 25 | — |

**(a)** Mevcut yerleşim maliyetini bulun.  
**(b)** B-C değişiminin maliyetini ve $\Delta C$'yi hesaplayın. Değişim yapılmalı mı?

> [!answer]- Adım Adım Çözüm
>
> ### Adım 1 — Uzaklık Matrisi (Dikdörtgen)
>
> $d_{ij}=|x_i-x_j|+|y_i-y_j|$
>
> | | A(0.5,1.5) | B(1.5,1.5) | C(0.5,0.5) | D(1.5,0.5) |
> |:---:|---:|---:|---:|---:|
> | **A** | 0 | 1 | 1 | 2 |
> | **B** | 1 | 0 | 2 | 1 |
> | **C** | 1 | 2 | 0 | 1 |
> | **D** | 2 | 1 | 1 | 0 |
>
> ### Adım 2 — Mevcut Maliyet
>
> $$C=\sum_{i\ne j}f_{ij}\cdot c_{ij}\cdot d_{ij}$$
>
> Her yönlü akış ayrı satır:
>
> | Akış | $f$ | $d$ | $f\cdot d$ |
> |---|---:|---:|---:|
> | A→B | 10 | 1 | 10 |
> | A→C | 30 | 1 | 30 |
> | A→D | 5 | 2 | 10 |
> | B→A | 5 | 1 | 5 |
> | B→D | 20 | 1 | 20 |
> | C→A | 10 | 1 | 10 |
> | C→D | 40 | 1 | 40 |
> | D→B | 15 | 1 | 15 |
> | D→C | 25 | 1 | 25 |
> | **Toplam** | | | **165** |
>
> $C_0 = 165$ ($c_{ij}=1$ olduğundan çarpıma gerek yok)
>
> ### Adım 3 — B-C Değişimi Sonrası Yeni Konumlar
>
> Değişim sonrası: A=(0.5,1.5), **C=(1.5,1.5)**, **B=(0.5,0.5)**, D=(1.5,0.5)
>
> Yeni uzaklıklar:
>
> | | A | B(eski C yeri) | C(eski B yeri) | D |
> |:---:|---:|---:|---:|---:|
> | **A** | 0 | 1 | 1 | 2 |
> | **B→yeni** | 1 | 0 | 2 | 1 |
> | **C→yeni** | 1 | 2 | 0 | 1 |
> | **D** | 2 | 1 | 1 | 0 |
>
> > [!note] Dikkat
> > Uzaklık matrisi yapısal olarak aynı kaldı (ızgara simetrik). Ancak hangi bölümün hangi konumda olduğu değişti.
>
> Değişimden etkilenen akışlar yeniden hesaplanır (B ve C içeren tüm satırlar):
>
> | Akış | $f$ | Eski $d$ | Yeni $d$ | Fark |
> |---|---:|---:|---:|---:|
> | A→B | 10 | 1 | 1 | 0 |
> | A→C | 30 | 1 | 1 | 0 |
> | B→A | 5 | 1 | 1 | 0 |
> | B→D | 20 | 1 | 1 | 0 |
> | C→A | 10 | 1 | 1 | 0 |
> | C→D | 40 | 1 | 1 | 0 |
> | B→C | 0 | 2 | 2 | 0 |
> | C→B | 0 | 2 | 2 | 0 |
>
> > [!warning]
> > Bu özel durumda simetrik ızgara ve eşit boyutlu bölümler nedeniyle B-C değişimi maliyet farkı oluşturmuyor: $\Delta C = 0$.
>
> > [!tip] Gerçek Sınavda
> > CRAFT soruları genellikle asimetrik akışlarla $\Delta C < 0$ olan bir değişim sorar. Değişimi "her seferinde yalnız iki bölümü taşı, diğerlerini sabit tut" kuralıyla uygula.

---

## S8 — CORELAP Yerleşim Oluşturma · 10 puan

Dört bölüm için REL chart verilmiştir. Ağırlıklar: A=4, E=3, I=2, O=1, U=0, X=−4.

| | **W** | **X** | **Y** | **Z** |
|:---:|:---:|:---:|:---:|:---:|
| **W** | — | A | I | O |
| **X** | A | — | E | U |
| **Y** | I | E | — | A |
| **Z** | O | U | A | — |

**(a)** TCR değerlerini hesaplayın.  
**(b)** CORELAP bölüm seçim sırasını oluşturun.  
**(c)** Aşağıdaki 2×2 ızgaraya yerleştirme puanlarını hesaplayıp W'yi yerleştirildikten sonra X'i nereye koyarsınız?

```
┌────┬────┐
│ P1 │ P2 │
├────┼────┤
│ P3 │ P4 │
└────┴────┘
```

> [!answer]- Adım Adım Çözüm
>
> ### Adım 1 — TCR Hesabı
>
> | Bölüm | İlişkiler | Sayısal değerler | TCR |
> |:---:|---|---:|---:|
> | W | X:A, Y:I, Z:O | 4+2+1 | **7** |
> | X | W:A, Y:E, Z:U | 4+3+0 | **7** |
> | Y | W:I, X:E, Z:A | 2+3+4 | **9** |
> | Z | W:O, X:U, Y:A | 1+0+4 | **5** |
>
> ### Adım 2 — Seçim Sırası
>
> 1. **Y** (TCR=9, en yüksek) → çekirdek, P1'e yerleştirilir.
> 2. Yerleşmiş: {Y}. Bölümlere Y ile ilişkiler: W(I=2), X(E=3), Z(A=4).
>    - En güçlü ilişki: **Z ile A (4)** → Z seçilir.
>    - Z, Y'ye komşu yerleştirilecek.
> 3. Yerleşmiş: {Y, Z}. Kalan: W, X.
>    - W ile Y: I=2; W ile Z: O=1 → W toplam ilişki = 3
>    - X ile Y: E=3; X ile Z: U=0 → X toplam ilişki = 3
>    - Bağ → TCR büyüğü seç: W(7) = X(7); kaynak bağ kuralı: alfabetik → W.
>    - **W** seçilir.
> 4. Son: **X**.
>
> **CORELAP sırası:** Y → Z → W → X
>
> ### Adım 3 — Yerleştirme Puanı (X için)
>
> Y P1'e, Z P2'ye yerleştirilmiş olsun. W P3'e yerleştirildi (tam komşu: Y ve Z ile).
>
> X için her pozisyona $PR(X, p) = \sum_{j\in\{Y,Z,W\}} w_{Xj}\cdot q_{jp}$ hesaplanır ($q=1$ tam komşu, $q=0{,}5$ çapraz/köşe).
>
> | Pozisyon | Y | Z | W | PR |
> |:---:|:---:|:---:|:---:|---:|
> | P4 | $3\times0{,}5$ (çapraz) | $3\times1$ (tam) | $0\times1$ (tam) | **4,5** |
>
> > [!success] Karar
> > X, P4'e yerleştirilir. Son yerleşim: Y(P1), Z(P2), W(P3), X(P4).

---

## S9 — Minisum + Minimax Tesis Konumu · 15 puan

Beş mevcut tesis aşağıdaki koordinat ve ağırlıklara sahiptir:

| Tesis | $(a_i, b_i)$ | $w_i$ |
|:---:|:---:|:---:|
| 1 | (2, 1) | 4 |
| 2 | (6, 3) | 6 |
| 3 | (1, 7) | 3 |
| 4 | (5, 5) | 5 |
| 5 | (9, 4) | 7 |

**(a) Minisum:** Dikdoğrusal ağırlıklı medyanla optimum konumu ve minimum toplam ağırlıklı uzaklığı bulun.  
**(b) Minimax:** $uv$ dönüşümüyle optimum konum kümesini bulun.

> [!answer]- Adım Adım Çözüm
>
> ## Bölüm A — Minisum
>
> ### Adım 1 — Toplam Ağırlık
>
> $$W=4+6+3+5+7=25,\qquad W/2=12{,}5$$
>
> ### Adım 2 — $x^*$ (Ağırlıklı Medyan)
>
> | Sıra | $a_i$ | $w_i$ | Kümülatif |
> |:---:|:---:|:---:|:---:|
> | 1 | 1 | 3 | 3 |
> | 2 | 2 | 4 | 7 |
> | 3 | 5 | 5 | 12 |
> | 4 | **6** | **6** | **18** |
> | 5 | 9 | 7 | 25 |
>
> Kümülatif ağırlık 12,5'i **ilk kez** $a=6$'da aşar → $x^*=6$
>
> ### Adım 3 — $y^*$ (Ağırlıklı Medyan)
>
> | Sıra | $b_i$ | $w_i$ | Kümülatif |
> |:---:|:---:|:---:|:---:|
> | 1 | 1 | 4 | 4 |
> | 2 | 3 | 6 | 10 |
> | 3 | **4** | **7** | **17** |
> | 4 | 5 | 5 | 22 |
> | 5 | 7 | 3 | 25 |
>
> Kümülatif ağırlık 12,5'i **ilk kez** $b=4$'te aşar → $y^*=4$
>
> Optimum konum: $X^*=(6,4)$
>
> ### Adım 4 — Minimum Toplam Uzaklık
>
> | Tesis | $|6-a_i|+|4-b_i|$ | $w_i d_i$ |
> |:---:|:---:|:---:|
> | 1 | $|6-2|+|4-1|=4+3=7$ | $4\times7=28$ |
> | 2 | $|6-6|+|4-3|=0+1=1$ | $6\times1=6$ |
> | 3 | $|6-1|+|4-7|=5+3=8$ | $3\times8=24$ |
> | 4 | $|6-5|+|4-5|=1+1=2$ | $5\times2=10$ |
> | 5 | $|6-9|+|4-4|=3+0=3$ | $7\times3=21$ |
> | **Toplam** | | **89** |
>
> > [!success] Minisum Sonuç
> > $X^*=(6,4)$, $f^*=89$ birim-ağırlık.
>
> ---
>
> ## Bölüm B — Minimax
>
> ### Adım 5 — UV Dönüşümü
>
> $$u_i=a_i+b_i,\qquad v_i=a_i-b_i$$
>
> | Tesis | $u_i$ | $v_i$ |
> |:---:|:---:|:---:|
> | 1 | $2+1=3$ | $2-1=1$ |
> | 2 | $6+3=9$ | $6-3=3$ |
> | 3 | $1+7=8$ | $1-7=-6$ |
> | 4 | $5+5=10$ | $5-5=0$ |
> | 5 | $9+4=13$ | $9-4=5$ |
>
> $$u_{min}=3,\quad u_{max}=13,\quad \Delta u=10$$
> $$v_{min}=-6,\quad v_{max}=5,\quad \Delta v=11$$
>
> ### Adım 6 — Optimum Yarıçap
>
> $$R^*=\frac12\max\{\Delta u,\Delta v\}=\frac12\max\{10,11\}=\frac{11}{2}=5{,}5$$
>
> ### Adım 7 — Optimum UV Aralıkları
>
> $$U^*=[u_{max}-R^*,\;u_{min}+R^*]=[13-5{,}5,\;3+5{,}5]=[7{,}5,\;8{,}5]$$
>
> $$V^*=[v_{max}-R^*,\;v_{min}+R^*]=[5-5{,}5,\;-6+5{,}5]=[-0{,}5,\;-0{,}5]$$
>
> $V^*$ tek nokta: $v^*=-0{,}5$
>
> ### Adım 8 — Geri Dönüşüm
>
> $u\in[7{,}5;\;8{,}5]$, $v=-0{,}5$ için:
>
> $$x=\frac{u+v}{2},\qquad y=\frac{u-v}{2}$$
>
> | $u$ | $x=(u-0{,}5)/2$ | $y=(u+0{,}5)/2$ |
> |:---:|:---:|:---:|
> | 7,5 | $7/2=3{,}5$ | $8/2=4{,}0$ |
> | 8,5 | $8/2=4{,}0$ | $9/2=4{,}5$ |
>
> > [!success] Minimax Sonuç
> > Optimum konum kümesi $(3{,}5;\;4{,}0)$ ile $(4{,}0;\;4{,}5)$ arasındaki doğru parçasıdır. Minimum maksimum uzaklık $R^*=5{,}5$ birimdir.

---

## S10 — Kesikli Tesis Konumu ve Net Tasarruf · 15 puan

Dört müşteri (1-4) ve üç aday depo (A, B, C) için hizmet ve sabit maliyetler:

| Müşteri | A | B | C |
|:---:|:---:|:---:|:---:|
| 1 | 300 | 800 | 500 |
| 2 | 900 | 200 | 600 |
| 3 | 400 | 500 | 300 |
| 4 | 700 | 300 | 800 |
| **Sabit maliyet** | **2 000** | **1 500** | **1 800** |

**(a)** Yalnız tek depo açılacaksa hangi depo seçilir? Toplam maliyeti bulun.  
**(b)** Yalnız B ve A açıkken toplam maliyeti bulun ve her müşteriyi atayın.  
**(c)** B ve A açıkken C'nin açılması net tasarruf sağlar mı?  
**(d)** Kapasitesiz model kısıtlarını sembolik olarak yazın.

> [!answer]- Adım Adım Çözüm
>
> ### Adım 1 — Tek Depo Seçimi
>
> Her sütun için en düşük hizmet maliyetinin toplamı + sabit maliyet:
>
> | Depo | M1 | M2 | M3 | M4 | Hizmet Toplamı | Sabit | **Toplam** |
> |:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
> | A | 300 | 900 | 400 | 700 | 2 300 | 2 000 | **4 300** |
> | B | 800 | 200 | 500 | 300 | 1 800 | 1 500 | **3 300** |
> | C | 500 | 600 | 300 | 800 | 2 200 | 1 800 | **4 000** |
>
> > [!success]
> > Tek depo: **B** seçilir. Toplam maliyet = **3 300** TL.
>
> ### Adım 2 — B ve A Açıkken Atama
>
> Her müşteri için $\min(c_{Aj}, c_{Bj})$:
>
> | Müşteri | A | B | Seçim | Maliyet |
> |:---:|:---:|:---:|:---:|:---:|
> | 1 | 300 | 800 | **A** | 300 |
> | 2 | 900 | 200 | **B** | 200 |
> | 3 | 400 | 500 | **A** | 400 |
> | 4 | 700 | 300 | **B** | 300 |
>
> $$TC(\{A,B\})=(300+200+400+300)+(2000+1500)=1200+3500=\mathbf{4700\text{ TL}}$$
>
> > [!warning]
> > A ve B açılması ($F_A+F_B=3500$) mevcut hizmet giderini azaltsa da tek B'nin maliyeti (3 300 TL) daha düşüktür. Bu $\{A,B\}$ değil, tek B'nin daha iyi olduğunu gösterir.
>
> ### Adım 3 — C'nin Net Tasarrufu ($\{A,B\}$ bazında)
>
> Mevcut müşteri maliyetleri ({A,B} açıkken): M1=300, M2=200, M3=400, M4=300.
>
> $$GS(C\mid\{A,B\})=\sum_j\max\{0,\;c_j(\{A,B\})-c_{Cj}\}$$
>
> | Müşteri | $c_j(\{A,B\})$ | $c_{Cj}$ | Tasarruf |
> |:---:|:---:|:---:|:---:|
> | 1 | 300 | 500 | $\max(0,300-500)=0$ |
> | 2 | 200 | 600 | $\max(0,200-600)=0$ |
> | 3 | 400 | 300 | $\max(0,400-300)=100$ |
> | 4 | 300 | 800 | $\max(0,300-800)=0$ |
>
> $$GS(C\mid\{A,B\})=100$$
>
> $$NS(C\mid\{A,B\})=100-1800=-1700<0$$
>
> > [!success] Karar
> > C açılmamalıdır. Brüt tasarruf yalnız 100 TL iken sabit maliyet 1 800 TL'dir. Net kayıp 1 700 TL.
>
> ### Adım 4 — Sembolik Model
>
> **Karar değişkenleri:**
>
> $$y_i=\begin{cases}1,&i\in\{A,B,C\}\text{ tesisi açılırsa}\\0,&\text{aksi halde}\end{cases}$$
>
> $$x_{ij}=\begin{cases}1,&j\text{ müşterisi }i\text{ tesisine atanırsa}\\0,&\text{aksi halde}\end{cases}$$
>
> **Model:**
>
> $$\min\;\sum_{i\in\{A,B,C\}}F_i y_i+\sum_{i\in\{A,B,C\}}\sum_{j=1}^{4}c_{ij}x_{ij}$$
>
> $$\sum_{i\in\{A,B,C\}}x_{ij}=1\qquad\forall j=1,2,3,4\quad\text{(her müşteri tam bir depoya atanır)}$$
>
> $$x_{ij}\le y_i\qquad\forall i,j\quad\text{(yalnız açık depoya atama yapılır)}$$
>
> $$x_{ij},y_i\in\{0,1\}$$

---

## Sonuç Kaydı

| Tarih | S1 | S2 | S3 | S4 | S5 | S6 | S7 | S8 | S9 | S10 | Toplam |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| | /10 | /10 | /10 | /10 | /10 | /10 | /10 | /10 | /15 | /15 | /100 |

### Hata Kodu Dökümü

| Soru | Hata Kodu | Ne yapacağım |
|---|:---:|---|
| | YÖN / MOD / VER / İŞL / BİR / YUV / YOR | |

> [!tip] Bağlantılar
> - [[03 Formüller/Formül Föyü|Formül Föyü]] — tüm formüller tek sayfada
> - [[00 Pano/Yöntem Seçici|Yöntem Seçici]] — hangi algoritmayı ne zaman
> - [[08 Hesaplamalar/Sınav Doğrulama Raporu|NumPy Doğrulama]] — Python ile çözüm doğrulama
