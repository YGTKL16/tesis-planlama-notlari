---
hafta: 12
konu: kesikli tesis konumu, açma-atama modeli ve net yıllık tasarruf
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, kesikli-konum, açma-atama, ikili-model]
kaynak: HF12 slayt 15-27
---

# HF12B - Kesikli Tesis Konumu ve Açma Atama

> [!summary] Bir cümlede
> Kesikli tesis konumunda hangi aday tesislerin açılacağı ve her müşterinin hangi açık tesise atanacağı, sabit açma maliyeti ile hizmet maliyetinin toplamını en aza indirecek biçimde birlikte seçilir.

## Öğrenme hedefleri

- [ ] Sürekli konum-atama ile aday bölgeli kesikli konumu ayırabilirim.
- [ ] Açma ve atama ikili değişkenlerini doğru tanımlayabilirim.
- [ ] Amaç fonksiyonu ile tam atama ve açık tesise bağlama kısıtlarını yazabilirim.
- [ ] Küçük bir problemi açık tesis kümelerini enümere ederek çözebilirim.
- [ ] Mevcut açık tesislere yeni bir aday eklemenin net tasarrufunu hesaplayabilirim.

## 0 - Soğuk başlangıç

> [!question]
> Bir müşteriyi A tesisinden karşılama maliyeti 100 TL, B tesisinden 500 TL'dir. A'yı açmak 3.000 TL gerektirir ve B zaten açıktır. A'yı yalnız bu müşteri için açmak ekonomik midir? “500-100” hesabı neden tek başına yetmez?

> [!answer]- Beklenen açıklama
> Taşıma/hizmet tasarrufu $500-100=400$ TL'dir; fakat 3.000 TL açma maliyeti doğar. Net tasarruf $400-3.000=-2.600$ TL olduğundan ekonomik değildir.

## 1 - Öğreten not

### Ne zaman kullanılır?

- Tesislerin kurulabileceği aday bölgeler önceden bellidir.
- Her adayın sabit açma/kira maliyeti vardır.
- Her müşteriye her aday tesisten hizmet vermenin maliyeti bilinir.
- Hangi adayların açılacağı ve müşterilerin nasıl atanacağı birlikte seçilir.
- Temel sürümde her müşteri tam bir tesisten hizmet alır.

### Kümeler, parametreler ve değişkenler

| Gösterim | Anlam |
|---|---|
| $I$ | Aday tesisler kümesi |
| $J$ | Müşteriler kümesi |
| $F_i$ | Aday $i$'yi açmanın sabit dönem maliyeti |
| $c_{ij}$ | Müşteri $j$'yi tesis $i$'den karşılamanın dönem maliyeti |
| $q_j$ | Müşteri $j$'nin talebi |
| $K_i$ | Tesis $i$'nin kapasitesi |

$$
y_i=
\begin{cases}
1,&i\text{ tesisi açılırsa}\\
0,&\text{aksi halde}
\end{cases}
$$

$$
x_{ij}=
\begin{cases}
1,&j\text{ müşterisi }i\text{ tesisine atanırsa}\\
0,&\text{aksi halde}
\end{cases}
$$

### Kapasitesiz açma-atama modeli

$$
\min \quad \sum_{i\in I}F_i y_i
+\sum_{i\in I}\sum_{j\in J}c_{ij}x_{ij}
$$

Her müşteri tam bir tesise atanır:

$$
\sum_{i\in I}x_{ij}=1 \qquad \forall j\in J
$$

Atama yalnız açık tesise yapılır:

$$
x_{ij}\le y_i \qquad \forall i\in I,\;j\in J
$$

$$
x_{ij},y_i\in\{0,1\}
$$

> [!warning] Eksik model tuzağı
> $x_{ij}\le y_i$ yazılmazsa model, sabit maliyet ödemeden kapalı bir tesisten müşteriye hizmet atayabilir. İkili değişken koşulları yazılmazsa da kesirli açma/atama çözümü çıkabilir.

### Kapasiteli uzantı

Talep ve kapasite varsa:

$$
\sum_{j\in J}q_jx_{ij}\le K_i y_i
\qquad \forall i\in I
$$

eklenir. Sağ taraftaki $y_i$, kapalı tesisin kapasitesini sıfırlar.

### Küçük problemlerde enümerasyon

Açık tesis kümesi $S\subseteq I$ sabit ve kapasite yoksa her müşteri en ucuz açık tesise atanır:

$$
TC(S)=\sum_{i\in S}F_i
+\sum_{j\in J}\min_{i\in S}c_{ij}
$$

Küçük bir soruda boş olmayan bütün $S$ kümeleri hesaplanıp en küçük toplam seçilebilir.

### Net tasarrufla aday ekleme

Mevcut açık küme $S$ iken müşterinin güncel maliyeti:

$$
c_j(S)=\min_{i\in S}c_{ij}
$$

Kapalı bir $k$ tesisini açmanın brüt hizmet tasarrufu:

$$
GS(k\mid S)=\sum_j\max\{0,c_j(S)-c_{kj}\}
$$

Net tasarruf:

$$
NS(k\mid S)=GS(k\mid S)-F_k
$$

- $NS>0$: toplam maliyet azalır.
- $NS=0$: maliyet açısından eşdeğer çözüm oluşur.
- $NS<0$: yalnız ekleme kararı altında tesisi açmak ekonomik değildir.

> [!note] Kararın sınırı
> Net tasarruf hesabı, mevcut tesisler açık kalacak ve yalnız yeni tesis **eklenecekse** doğrudan kullanılır. Bütün açık/kapalı kararları serbestse, tam enümerasyon veya matematiksel model gerekir.

### Sürekli konum-atamadan farkı

| Konum-atama | Kesikli tesis konumu |
|---|---|
| Tesis koordinatları serbesttir. | Aday koordinatlar/bölgeler sabittir. |
| Her kümede ağırlıklı medyan bulunur. | Medyanla yeni nokta üretilmez. |
| Tesis sayısı + kümeler + koordinatlar seçilir. | Aday açma + müşteri atama seçilir. |

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF12, slayt 19-23
> Beş müşteri ve A-E arasında beş aday depo vardır. Hücreler müşteriye hizmetin yıllık maliyetini, son satır sabit yıllık açma maliyetini gösterir.

| Müşteri | A | B | C | D | E |
|---:|---:|---:|---:|---:|---:|
| 1 | 100 | 500 | 1.800 | 1.300 | 1.700 |
| 2 | 1.500 | 200 | 2.600 | 1.400 | 1.800 |
| 3 | 2.500 | 1.200 | 1.700 | 300 | 1.900 |
| 4 | 2.800 | 1.800 | 700 | 800 | 800 |
| 5 | 10.000 | 12.000 | 800 | 8.000 | 900 |
| **Sabit maliyet** | **3.000** | **2.000** | **2.000** | **3.000** | **4.000** |

### Soru 1 - Yalnız bir depo açılacaksa

Her sütunun hizmet maliyetlerini ve sabit maliyetini topla:

| Tek açık depo | Hizmet toplamı | Sabit | Toplam |
|---:|---:|---:|---:|
| A | 16.900 | 3.000 | 19.900 |
| B | 15.700 | 2.000 | 17.700 |
| C | 7.600 | 2.000 | **9.600** |
| D | 11.800 | 3.000 | 14.800 |
| E | 7.100 | 4.000 | 11.100 |

Yalnız bir depo açılacaksa C seçilir ve bütün müşteriler C'ye atanır.

### Soru 2 - B ve C açıkken atama

Her müşteri için B ve C sütunlarının küçüğü seçilir:

| Müşteri | B | C | Seçim | Maliyet |
|---:|---:|---:|---:|---:|
| 1 | 500 | 1.800 | B | 500 |
| 2 | 200 | 2.600 | B | 200 |
| 3 | 1.200 | 1.700 | B | 1.200 |
| 4 | 1.800 | 700 | C | 700 |
| 5 | 12.000 | 800 | C | 800 |

$$
TC(\{B,C\})=3.400+(2.000+2.000)=7.400
$$

### Soru 3 - Üçüncü depo gerekli mi?

**A adayı:** Yalnız müşteri 1'de maliyet 500'den 100'e düşer:

$$NS(A\mid\{B,C\})=(500-100)-3.000=-2.600$$

**D adayı:** Yalnız müşteri 3'te maliyet 1.200'den 300'e düşer:

$$NS(D\mid\{B,C\})=(1.200-300)-3.000=-2.100$$

**E adayı:** Hiçbir müşteride B-C mevcut maliyetinden daha düşük hizmet sağlamaz:

$$NS(E\mid\{B,C\})=0-4.000=-4.000$$

> [!success] Karar
> B ve C açık kalacaksa ilave depo kurulmaz. Üç kapalı adayın da net tasarrufu negatiftir; toplam maliyet 7.400 olarak kalır.

### Soru 4 - Dördüncü depo nüansı

Slayt 23, D'nin daha sonra eklenmesini ayrıca değerlendirir ve aynı mantıkla:

$$1.200-300-3.000=-2.100$$

bulur. Yeni tesis eklenmediği sürece mevcut müşteri maliyetleri değişmediğinden sonuç da değişmez.

### Öz-açıklama

1. Tek depo sütun toplamında sabit maliyet neden yalnız bir kez eklenir?
2. B ve C açıkken müşteri 3 neden D'nin açılmasıyla yeniden atanır?
3. Net tasarruf negatifse toplam maliyet hangi miktarda değişir?

## 3 - Kademeli örnek

> [!question]
> Üç aday tesis ve dört müşteri için hizmet maliyetleri ile sabit maliyetler şöyledir. Kapasite yoktur. Bütün açık tesis kümelerini karşılaştırıp optimumu bulun.
>
> | Müşteri | A | B | C |
> |---:|---:|---:|---:|
> | 1 | 2 | 6 | 9 |
> | 2 | 8 | 3 | 7 |
> | 3 | 6 | 5 | 2 |
> | 4 | 9 | 8 | 1 |
> | **Sabit** | **5** | **4** | **6** |
>
> Her $S$ için $TC(S)=\sum_{i\in S}F_i+\sum_j\min_{i\in S}c_{ij}$ kullanın.

> [!answer]- Tam çözüm
> | Açık küme | En ucuz hizmet toplamı | Sabit toplam | $TC$ |
> |---:|---:|---:|---:|
> | $\{A\}$ | 25 | 5 | 30 |
> | $\{B\}$ | 22 | 4 | 26 |
> | $\{C\}$ | 19 | 6 | 25 |
> | $\{A,B\}$ | 18 | 9 | 27 |
> | $\{A,C\}$ | 12 | 11 | 23 |
> | $\{B,C\}$ | 12 | 10 | **22** |
> | $\{A,B,C\}$ | 8 | 15 | 23 |
>
> Optimum açık küme $\{B,C\}$'dir. Müşteriler 1 ve 2 B'ye; 3 ve 4 C'ye atanır. Minimum toplam maliyet 22'dir.

## 4 - Bağımsız sorular

### L1 - Temel

> [!question]
> Üç aday tesis ve dört müşteri için kapasitesiz açma-atama modelini sembolik olarak yazın. Karar değişkenlerinin tanım kümelerini unutmayın.

> [!answer]- Çözüm
> $$\min \sum_{i=1}^{3}F_i y_i+\sum_{i=1}^{3}\sum_{j=1}^{4}c_{ij}x_{ij}$$
> $$\sum_{i=1}^{3}x_{ij}=1\quad j=1,\ldots,4$$
> $$x_{ij}\le y_i\quad i=1,2,3;\;j=1,\ldots,4$$
> $$x_{ij},y_i\in\{0,1\}$$

### L2 - Tuzaklı / aktarım

> [!question]
> Kademeli örnekte yalnız B açıktır. A ve C adaylarının ayrı ayrı net tasarruflarını bulun; hangi aday önce eklenmelidir?

> [!answer]- Çözüm
> B'nin müşteri maliyetleri $(6,3,5,8)$'dir.
>
> A yalnız müşteri 1'de $6-2=4$ tasarruf sağlar:
> $$NS(A\mid\{B\})=4-5=-1$$
>
> C, müşteri 3'te $5-2=3$ ve müşteri 4'te $8-1=7$ tasarruf sağlar:
> $$NS(C\mid\{B\})=3+7-6=4$$
>
> C eklenir. Toplam maliyet 26'dan 22'ye düşer.

### L3 - Yöntemi seç

> [!question]
> 1. Aday yerler A-D olarak verilmiş, her birinin kirası ve müşteri hizmet tablosu var.
> 2. Yeni iki tesis düzlemde herhangi bir yere konabilir; müşteri kümeleri bulunacak.
> 3. Aday tesiste kapasite 100 birim, atanan müşterilerin talepleri biliniyor.

> [!answer]- Çözüm
> 1. Kesikli açma-atama modeli.
> 2. Sürekli konum-atama; her kümede minisum.
> 3. Kesikli açma-atama modeline $\sum_jq_jx_{ij}\le K_i y_i$ kapasite kısıtı eklenir.

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. $y_i$ ve $x_{ij}$ neyi temsil eder?
2. $x_{ij}\le y_i$ kısıtı hangi fiziksel hatayı engeller?
3. Net tasarruf hesabında sabit maliyet neden çıkarılır?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli örnek |  |  |  |
| D1 |  | L1 |  |  |  |
| D3 |  | L2 + konum-atama sorusu |  |  |  |
| D7 |  | Kaynak örneğini kapalı kitap çöz |  |  |  |
| D14 |  | Karma konum testi |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| Yalnız hizmet maliyetini karşılaştırdım. | Sabit açma maliyetini yok saydım. | Her açık küme için hizmet ve sabit sütunlarını ayrı tutacağım. |
| $\sum_i x_{ij}\le1$ yazdım. | Bazı müşteriler hizmetsiz kalabilir. | Soru “her müşteri” diyorsa eşitliği 1 yazacağım. |
| $x_{ij}\le y_i$ bağını yazmadım. | Kapalı tesise atama yapılabilir. | Her atama değişkenini açma değişkenine bağlayacağım. |
| İkili koşulları yazmadım. | Model kesirli karar verebilir. | Modeli $x_{ij},y_i\in\{0,1\}$ ile bitireceğim. |
| Net tasarrufta negatif müşteri farklarını da topladım. | Yeni tesis daha pahalıysa müşteri ona atanmak zorunda değildir. | Her müşteri için $\max(0,c_j(S)-c_{kj})$ kullanacağım. |

## Kaynaklar

- Ders sunumu: [[HF12-P12-Tesis Konumu II-2025.pptx|HF12]], slayt 15-27; model slayt 17-18, sayısal örnek slayt 19-23.
- [[05 Kaynaklar/MarkItDown/HF12 - Ham|HF12 ham metni]]
