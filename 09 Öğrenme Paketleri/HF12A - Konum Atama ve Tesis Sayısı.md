---
hafta: 12
konu: sürekli konum-atama, müşteri kümeleri ve tesis sayısı
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, konum-atama, enümerasyon, ağırlıklı-medyan]
kaynak: HF12 slayt 3-14
---

# HF12A - Konum Atama ve Tesis Sayısı

> [!summary] Bir cümlede
> Konum-atama modelinde tesis sayısı, müşterilerin tesislere ayrılması ve her müşteri kümesinin minisum konumu birlikte seçilir; toplam maliyet, küme içi taşıma ile tesis sabit maliyetinin toplamıdır.

## Öğrenme hedefleri

- [ ] Konum-atama problemini tek tesis minisum ve kesikli aday bölge modelinden ayırabilirim.
- [ ] Sabit bir tesis sayısı için müşteri kümelerini yazabilirim.
- [ ] Her kümenin optimum tesis konumunu ağırlıklı medyanla bulabilirim.
- [ ] Taşıma ve tesis sabit maliyetini aynı birimde toplayabilirim.
- [ ] Farklı tesis sayılarının en iyi çözümlerini karşılaştırabilirim.

## 0 - Soğuk başlangıç

> [!question]
> Dört müşteriye hizmet için tesis sayısını 1'den 2'ye çıkarmak taşıma maliyetini her zaman azaltır. Buna rağmen toplam maliyet neden artabilir? Karar vermek için hangi iki maliyet bileşeni gerekir?

> [!answer]- Beklenen açıklama
> İkinci tesis müşteriye yaklaşarak taşıma maliyetini azaltabilir; fakat yeni bir sabit kurulum/işletme maliyeti doğurur. Her $n$ için en iyi atamanın taşıma maliyeti ile $g(n)$ tesis maliyeti birlikte karşılaştırılmalıdır.

## 1 - Öğreten not

### Ne zaman kullanılır?

Bu modelde:

- müşterilerin koordinatları ve ağırlıkları bilinir,
- yeni tesisler düzlemde serbestçe konumlandırılabilir,
- her müşteri tam bir yeni tesise atanır,
- kaç tesis kurulacağı da karardır,
- her müşteri kümesi için tesis konumu, çoğunlukla dikdoğrusal minisumla bulunur.

> [!warning] HF12'deki iki ayrı problem
> **Konum-atama** modelinde tesis koordinatları müşteri kümelerinden sonra hesaplanır. **Tesis/fabrika konum** modelinde ise aday tesis bölgeleri baştan bellidir ve açma-atama kararı verilir. Bu iki modeli birbirine karıştırmayın.

### Verilenler ve semboller

| Sembol | Anlam | Birim |
|---|---|---|
| $m$ | Müşteri sayısı | adet |
| $n$ | Açılacak yeni tesis sayısı | adet |
| $P_i=(a_i,b_i)$ | Müşteri $i$'nin koordinatı | koordinat |
| $w_i$ | Müşteri ağırlığı/akışı | sefer, talep veya kişi |
| $C_k$ | Tesis $k$'ya atanan müşteri kümesi | küme |
| $X_k=(x_k,y_k)$ | Tesis $k$'nın konumu | koordinat |
| $g(n)$ | $n$ tesisin toplam sabit maliyeti | TL/dönem |

### Toplam maliyet

Dikdoğrusal uzaklıkta bir atama ve tesis konumları için:

$$
TC(n)=g(n)+\sum_{k=1}^{n}\sum_{i\in C_k}
c\,w_i\left(|x_k-a_i|+|y_k-b_i|\right)
$$

$c$, bir ağırlık-uzaklık biriminin parasal katsayısıdır; soruda maliyet zaten $w_i$ içine alınmışsa $c=1$ kullanılabilir.

### Enümerasyon algoritması

Her $n=1,2,\ldots,m$ için:

1. Müşterilerin $n$ boş olmayan kümeye olası atamalarını oluştur.
2. Her kümenin $x_k^*$ ve $y_k^*$ koordinatlarını o kümedeki müşterilerin ağırlıklı medyanıyla bul.
3. Küme içi minimum taşıma maliyetlerini topla.
4. $g(n)$ sabit tesis maliyetini ekle.
5. O $n$ için en düşük maliyetli atamayı sakla.
6. Farklı $n$ değerlerinin en iyilerini karşılaştır.

Tesis etiketleri önemsiz ve bütün tesisler kullanılacaksa farklı kümelemelerin sayısı Stirling sayısı $S(m,n)$'dir. Etiketli tesis atamalarını doğrudan saymak $n^m$ olasılık üretir; bunun içinde boş tesisler ve yalnız etiket farkı olan tekrarlar bulunabilir.

### Her kümede minisum

Bir küme $C_k$ sabitlendiğinde problem tek tesis minisuma dönüşür:

$$
\min_{x_k,y_k}\sum_{i\in C_k}w_i
\left(|x_k-a_i|+|y_k-b_i|\right)
$$

$x_k^*$ ve $y_k^*$ yalnız o kümedeki müşterilerden hesaplanır. Bütün müşterilerin ortak medyanını her kümeye kopyalamak yanlıştır.

### Hızlı alt sınırla eleme

Taşıma maliyeti negatif olamaz. Bir aday tesis sayısı için yalnız sabit maliyet bile mevcut en iyi toplam maliyetten büyükse:

$$
g(n)\ge TC_{\text{mevcut en iyi}}
$$

o $n$ ve daha pahalı seçenekler elenebilir. HF12 kahve dükkânı örneğinde tek tesis maliyeti 6.820 dolar iken $n\ge2$ için yalnız sabit maliyet en az 10.000 dolardır; bu nedenle iki veya daha fazla tesisin ayrıntılı atamasına gerek yoktur.

### Benzer yöntemlerden farkı

| Problem | Koordinatlar | Temel karar |
|---|---|---|
| Tek tesis minisum | Yeni konum serbest | Bir ağırlıklı medyan |
| Konum-atama | Birden çok yeni konum serbest | Tesis sayısı + kümeler + her kümenin medyanı |
| Kesikli tesis konumu | Aday konumlar baştan belli | Hangi adaylar açılsın + atamalar |

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF12, slayt 8-11
> Dört müşteri $P_1=(0,0)$, $P_2=(3,0)$, $P_3=(6,0)$ ve $P_4=(12,0)$ noktalarındadır. Ağırlıklar $(1,1,1,2)$ ve $n$ tesisin sabit maliyeti $g(n)=5n$'dir. Kaç tesis kurulmalı, müşteriler nasıl atanmalı ve tesisler nereye konmalıdır?

Noktalar aynı yatay doğru üzerinde olduğundan yalnız $x$ hesabı gerekir; bütün tesislerde $y=0$'dır.

### Senaryo 1 - $n=1$

Toplam ağırlık 5, yarısı 2,5'tir. Kümülatif ağırlık $x=6$'da 3'e ulaştığı için:

$$X_1=(6,0)$$

$$
TC(1)=1(6)+1(3)+1(0)+2(6)+5=26
$$

### Senaryo 2 - $n=2$

Kaynak slayt, örnek olarak $\{P_1\}$ ve $\{P_2,P_3,P_4\}$ kümelemesini gösterir. İkinci kümenin toplam ağırlığı 4'tür; $x=6$'da kümülatif ağırlık tam 2 olduğundan ikinci tesis $[6,12]$ aralığındaki her noktaya yerleşebilir. $x=6$ veya $x=12$ seçildiğinde:

$$TC=15+10=25$$

Fakat $n=2$ için bütün kümeler değerlendirilmelidir. En iyi kümeleme:

$$C_1=\{P_1,P_2,P_3\},\qquad C_2=\{P_4\}$$

Birinci kümenin medyanı $x=3$, ikinci tesisin konumu $x=12$'dir:

$$
TC(2)=\underbrace{(3+0+3)}_{\text{taşıma }=6}
+\underbrace{0}_{P_4}+\underbrace{10}_{g(2)}=16
$$

> [!warning] Enümerasyon dersi
> Slayt 10'daki $TC=25$, $n=2$ için gösterilen **bir atama durumunun** maliyetidir; $n=2$'nin minimumu değildir. Diğer atamalar incelendiğinde 16 bulunur.

### Senaryo 3 - $n=3$

En iyi çözümde bir komşu müşteri çifti aynı tesisi paylaşır, diğer ikisi ayrı tesis alır. Örneğin:

$$C_1=\{P_1,P_2\},\quad C_2=\{P_3\},\quad C_3=\{P_4\}$$

$P_1$-$P_2$ kümesinde tesis $[0,3]$ aralığında olabilir ve taşıma maliyeti 3'tür:

$$TC(3)=3+15=18$$

### Senaryo 4 - $n=4$

Her müşteri kendi tesisine atanır; taşıma sıfırdır:

$$TC(4)=0+20=20$$

### Karşılaştırma

| Tesis sayısı | En iyi taşıma maliyeti | Sabit maliyet | En iyi toplam maliyet |
|---:|---:|---:|---:|
| 1 | 21 | 5 | 26 |
| 2 | 6 | 10 | **16** |
| 3 | 3 | 15 | 18 |
| 4 | 0 | 20 | 20 |

> [!success] Karar
> İki tesis kurulmalıdır. Bir optimum çözümde $P_1,P_2,P_3$ müşterileri $(3,0)$ tesisine; $P_4$ ise $(12,0)$ tesisine atanır. Minimum toplam maliyet 16'dır.

### İkinci kaynak kontrolü - Kahve dükkânı

HF12 slayt 12-14'te ziyaretlerin %70'i ağırlığa çevrilerek $(35,21,49,42)$ elde edilir. Tek tesisin medyan konumu $(50,70)$'tir:

$$
TC(1)=0{,}25[35(30)+21(50)+49(80)+42(30)]+5.000
=6.820
$$

$n\ge2$ için yalnız sabit maliyet $5.000n\ge10.000>6.820$ olduğundan tek dükkân optimumdur.

### Öz-açıklama

1. Neden $n=2$ için yalnız slayt 10'daki ilk atamayı hesaplamak yeterli değildir?
2. Her müşteri kendi tesisini aldığında taşıma sıfır olsa da neden $n=4$ seçilmedi?
3. Kahve örneğinde hangi alt sınır ayrıntılı enümerasyonu gereksiz kıldı?

## 3 - Kademeli örnek

> [!question]
> Bir doğru üzerindeki müşteriler $P_1=0,w_1=1$; $P_2=4,w_2=1$; $P_3=10,w_3=2$ olsun. $g(n)=5n$ için $n=1,2,3$ seçeneklerini karşılaştırın.
>
> 1. $n=1$ medyan aralığı $\_\_$, taşıma maliyeti $\_\_$, toplam $\_\_$.
> 2. $n=2$ için olası üç ikili kümelemenin en iyisini bulun.
> 3. $n=3$ toplam maliyeti $\_\_$.

> [!answer]- Tam çözüm
> $n=1$: Toplam ağırlık 4'tür. Kümülatif ağırlık $x=4$'te tam 2 olduğundan medyan aralığı $[4,10]$'dur. $x=4$ için taşıma:
> $$1(4)+1(0)+2(6)=16$$
> Dolayısıyla $TC(1)=16+5=21$.
>
> $n=2$ için:
>
> | Kümeler | En iyi taşıma | Sabit | Toplam |
> |---|---:|---:|---:|
> | $\{P_1\},\{P_2,P_3\}$ | 6 | 10 | 16 |
> | $\{P_2\},\{P_1,P_3\}$ | 10 | 10 | 20 |
> | $\{P_3\},\{P_1,P_2\}$ | 4 | 10 | **14** |
>
> $n=3$ için taşıma sıfır, sabit maliyet 15'tir: $TC(3)=15$.
>
> Optimum $n=2$ ve toplam maliyet 14'tür. $P_1,P_2$ aynı tesise, $P_3$ ayrı tesise atanır.

## 4 - Bağımsız sorular

### L1 - Temel

> [!question]
> Bir müşteri kümesinde noktalar $x=(2,5,9)$, ağırlıklar $w=(3,2,5)$'tir. Bu kümeye hizmet eden tesisin optimum $x$ konumlarını ve küme içi taşıma maliyetini bulun.

> [!answer]- Çözüm
> $W=10$ ve yarısı 5'tir. $x=5$'te kümülatif ağırlık tam 5 olduğundan $x^*\in[5,9]$.
> $x=5$ seçilirse taşıma $3(3)+2(0)+5(4)=29$'dur.

### L2 - Tuzaklı / aktarım

> [!question]
> Bir konum-atama probleminde eldeki en iyi toplam maliyet 7.500 TL'dir. Üç tesisin yalnız sabit maliyeti 8.000 TL, taşıma maliyetleri ise negatif olamaz. $n=3$ için müşteri atamalarını tek tek hesaplamak gerekir mi?

> [!answer]- Çözüm
> Hayır. $TC(3)\ge g(3)=8.000>7.500$ olduğundan hiçbir üç tesis çözümü mevcut en iyiyi geçemez. Bu bir alt sınırla elemedir.

### L3 - Yöntemi seç

> [!question]
> 1. Tesisler düzlemde herhangi bir yere kurulabilir; müşteri kümeleri ve tesis sayısı bilinmiyor.
> 2. Yalnız A, B ve C aday arsaları kullanılabilir; açma maliyetleri biliniyor.
> 3. Tek depo kurulacak ve toplam ağırlıklı Manhattan uzaklığı küçültülecek.

> [!answer]- Çözüm
> 1. Konum-atama: kümeleri enümere et, her kümede minisum çöz, tesis sayılarını karşılaştır.
> 2. Kesikli tesis konumu/açma-atama modeli.
> 3. Tek tesis minisum ve ağırlıklı medyan.

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. Konum-atama modelinin üç ortak kararı nedir?
2. Sabit bir müşteri kümesinin tesis konumu nasıl bulunur?
3. Yalnız bir atama durumunu hesaplamak neden optimumu kanıtlamaz?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli örnek |  |  |  |
| D1 |  | L1 |  |  |  |
| D3 |  | L2 + kesikli konum sorusu |  |  |  |
| D7 |  | Kaynak örneğini kapalı kitap çöz |  |  |  |
| D14 |  | Karma konum testi |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| Bir $n$ için yalnız ilk atamayı hesapladım. | O durumun maliyetini buldum, minimumu değil. | Her $n$ için tüm farklı kümeleri veya geçerli eleme sınırını göstereceğim. |
| Her kümede bütün müşterilerin ortak medyanını kullandım. | Tesis konumu kendi hizmet kümesine bağlıdır. | Medyan tablosunun başına küme üyelerini yazacağım. |
| Taşıma azaldığı için daha çok tesisi seçtim. | Sabit maliyeti yok saydım. | Her satırda “taşıma + $g(n)$” sütunları açacağım. |
| Aday arsalar verilmiş soruda medyan hesapladım. | Kesikli modelde yeni koordinat seçilmez. | Önce “konum serbest mi, adaylı mı?” sorusunu cevaplayacağım. |

## Kaynaklar

- Ders sunumu: [[HF12-P12-Tesis Konumu II-2025.pptx|HF12]], slayt 3-14; örnekler slayt 8-14.
- [[05 Kaynaklar/MarkItDown/HF12 - Ham|HF12 ham metni]]

