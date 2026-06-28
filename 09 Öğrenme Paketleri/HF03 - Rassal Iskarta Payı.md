---
hafta: 3
konu: düşük hacimde rassal ıskarta payı
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, olasılık, binom, beklenen-kar]
kaynak: HF03 slayt 35-48
---

# HF03 - Rassal Iskarta Payı

> [!summary] Bir cümlede
> Düşük hacimli üretimde sağlam ürün sayısı rassal olduğunda, aday üretim miktarları binom olasılıkları ve **beklenen kâr** ile karşılaştırılır.

## Öğrenme hedefleri

- [ ] Düşük hacimli rassal ıskarta ile yüksek hacimli ortalama fire hesabını ayırabilirim.
- [ ] Binom olasılığını doğru kurabilirim.
- [ ] Her $(Q,x)$ durumu için kâr fonksiyonunu sözleşmeye göre yazabilirim.
- [ ] Aday $Q$ değerlerinin beklenen kârlarını karşılaştırabilirim.
- [ ] Zarar olasılığını doğru durumları toplayarak bulabilirim.

## 0 - Soğuk başlangıç

> [!question]
> Bir sipariş için tam 4 sağlam özel döküm gerekiyor. Bir dökümün sağlam çıkma olasılığı %90'dır. Ortalama fire yaklaşımıyla $4/0{,}90=4{,}44$ bulup doğrudan 5 üretmek neden tek başına yeterli bir ekonomik karar değildir?

> [!answer]- Beklenen açıklama
> Beş üretmek hedefe ulaşma olasılığını artırır; fakat ek bir dökümün maliyeti de vardır. Doğru karar yalnız beklenen sağlam ürün sayısına değil, her olası sağlam ürün sayısının olasılığına ve o durumda oluşan gelir/maliyete bağlıdır.

## 1 - Öğreten not

### Ne zaman kullanılır?

Şu işaretler birlikte görülüyorsa bu yaklaşım düşünülür:

- üretim hacmi küçüktür,
- her birimin sağlam/kusurlu sonucu rassaldır,
- kaç sağlam ürün çıkacağının ekonomik sonucu doğrusal değildir,
- eksik üretim, fazla üretim, hurda veya geri kazanım için farklı gelir/maliyet kuralları vardır,
- amaç yalnız hedef miktarı tutturmak değil, beklenen kârı enbüyüklemektir.

Yüksek hacimdeki yaklaşık

$$
I=\frac{O}{1-s}
$$

hesabı bu problemin yerine geçmez. Bu formül ortalama miktarı tahmin eder; düşük hacimli bir partide olası sonuçların ekonomik dağılımını göstermez.

### Semboller

| Sembol | Anlam |
|---|---|
| $Q$ | Üretilmesine karar verilen toplam miktar |
| $X$ | Sağlam çıkan ürün sayısı; rassal değişken |
| $x$ | $X$'in belirli bir gerçekleşen değeri |
| $p$ | Bir ürünün sağlam çıkma olasılığı |
| $R(Q,x)$ | $Q$ üretilip $x$ sağlam çıktığında gelir |
| $K(Q,x)$ | $Q$ üretilip $x$ sağlam çıktığında maliyet |
| $\Pi(Q,x)$ | Durum kârı, $R(Q,x)-K(Q,x)$ |
| $E[\Pi(Q)]$ | $Q$ üretim kararının beklenen kârı |

### Binom olasılığı

Bağımsız ürünlerin sağlam çıkma olasılığı sabit $p$ ise:

$$
X\sim\operatorname{Bin}(Q,p)
$$

$$
P(X=x)=\binom{Q}{x}p^x(1-p)^{Q-x}
$$

### Beklenen kâr

Önce her mümkün $x=0,1,\ldots,Q$ için sözleşmeye uygun kâr yazılır. Sonra:

$$
E[\Pi(Q)]
=\sum_{x=0}^{Q}P(X=x)\,\Pi(Q,x)
$$

hesaplanır. En yüksek beklenen kârı veren aday $Q$ seçilir.

> [!warning] En önemli nokta
> Evrensel tek bir kâr formülü yoktur. Müşterinin kaç ürün satın aldığı, eksik partiyi kabul edip etmediği, fazla ürünün değeri ve kusurlu ürünün geri kazanımı soru metninden kurulmalıdır.

### Çözüm sırası

1. Karar değişkeni $Q$ ve rassal sağlam ürün sayısı $X$'i tanımla.
2. Olasılık modelini kur: çoğunlukla $X\sim\operatorname{Bin}(Q,p)$ veya soruda verilen geçmiş dağılım.
3. Her $x$ için gelir ve maliyet kurallarını parçalı biçimde yaz.
4. $\Pi(Q,x)=R(Q,x)-K(Q,x)$ tablosunu oluştur.
5. Her hücreyi ilgili olasılıkla çarpıp topla.
6. Aday $Q$ değerlerini karşılaştır.
7. İsteniyorsa zarar oluşturan $x$ durumlarının olasılıklarını topla.

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF03, slayt 39-48
> Tam 4 sağlam döküm parçası gereklidir. Her sağlam parça için 30.000 TL ödenmektedir; ancak sipariş 4 sağlam parçanın tamamı çıkarsa kabul edilmektedir. Her dökümün maliyeti 15.000 TL ve sağlam çıkma olasılığı $p=0{,}90$'dır. $Q=4,5,6,7,8$ adaylarını karşılaştırın ve seçilen kararın zarar olasılığını bulun.

### Adım 1 - Olasılık modeli

$$
X\sim\operatorname{Bin}(Q,0{,}90)
$$

### Adım 2 - Gelir, maliyet ve kâr

Dört sağlam parça çıkarsa toplam gelir:

$$
4\times30.000=120.000\text{ TL}
$$

Sipariş dört sağlam parçanın altında kabul edilmediğinden:

$$
R(Q,x)=
\begin{cases}
120.000, & x\ge4\\
0, & x<4
\end{cases}
$$

$$
K(Q,x)=15.000Q
$$

Dolayısıyla:

$$
E[\Pi(Q)]=120.000P(X\ge4)-15.000Q
$$

### Adım 3 - Adayları karşılaştır

Örneğin $Q=5$ için:

$$
P(X\ge4)=P(X=4)+P(X=5)
$$

$$
=\binom54(0{,}9)^4(0{,}1)+(0{,}9)^5
=0{,}91854
$$

$$
E[\Pi(5)]
=120.000(0{,}91854)-15.000(5)
=35.224{,}80\text{ TL}
$$

Tüm adaylar:

| $Q$ | $P(X\ge4)$ | Beklenen gelir (TL) | Maliyet (TL) | Beklenen kâr (TL) |
|---:|---:|---:|---:|---:|
| 4 | 0,656100 | 78.732,00 | 60.000 | 18.732,00 |
| 5 | 0,918540 | 110.224,80 | 75.000 | **35.224,80** |
| 6 | 0,984150 | 118.098,00 | 90.000 | 28.098,00 |
| 7 | 0,997272 | 119.672,64 | 105.000 | 14.672,64 |
| 8 | 0,999568 | 119.948,20 | 120.000 | -51,80 |

En yüksek beklenen kâr $Q=5$ için elde edilir.

### Adım 4 - Zarar olasılığı

$Q=5$ iken sipariş kabul edilirse kâr $120.000-75.000=45.000$ TL; $X<4$ iken gelir sıfır ve kâr negatiftir. Bu nedenle:

$$
P(\Pi<0)=P(X<4)
$$

$$
=\sum_{x=0}^{3}\binom5x(0{,}9)^x(0{,}1)^{5-x}
=0{,}08146
$$

Zarar olasılığı yaklaşık **%8,15**'tir.

> [!success] Karar
> Verilen adaylar ve sözleşme koşulları altında 5 döküm üretmek, yaklaşık 35.224,80 TL ile en yüksek beklenen kârı verir. Bu karar zarar riskini sıfırlamaz; zarar olasılığı yaklaşık %8,15'tir.

> [!note] Kaynak kontrolü
> Slayttaki $Q=4,5,6,7$ değerleri yeniden hesapla uyuşmaktadır. Slayt grafiğinde $Q=8$ için küçük bir sayısal fark vardır; slaytta verilen temel girdilerle doğrudan hesap $-51{,}80$ TL verir.

### Öz-açıklama

1. Neden $4/0{,}90$ hesabıyla yetinmedik?
2. $Q$ arttıkça başarı olasılığı artmasına rağmen beklenen kâr neden önce artıp sonra düşüyor?
3. Müşteri dört sağlam ürünün altındaki ürünleri de tek tek satın alsaydı gelir fonksiyonu nasıl değişirdi?

## 3 - Kademeli örnek

> [!question]
> Tam 3 sağlam parça teslim edilirse 60.000 TL ödenen bir sipariş vardır; eksik parti kabul edilmez. Bir üretimin maliyeti 10.000 TL ve sağlam çıkma olasılığı %80'dir. $Q=3,4,5,6$ adayları arasından beklenen kârı en yüksek olanı bulun ve o kararın zarar olasılığını hesaplayın.
>
> Eksikleri tamamlayın:
>
> 1. $X\sim\operatorname{Bin}(Q,\_\_)$
> 2. $E[\Pi(Q)]=\_\_\_\_P(X\ge\_\_)-\_\_\_\_Q$
> 3. Her $Q$ için $P(X\ge3)$ değerini hesaplayın.
> 4. Beklenen kârları karşılaştırın.

> [!answer]- Tam çözüm
> $X\sim\operatorname{Bin}(Q,0{,}80)$ ve
> $$E[\Pi(Q)]=60.000P(X\ge3)-10.000Q$$
>
> | $Q$ | $P(X\ge3)$ | Beklenen kâr (TL) |
> |---:|---:|---:|
> | 3 | 0,51200 | 720,00 |
> | 4 | 0,81920 | **9.152,00** |
> | 5 | 0,94208 | 6.524,80 |
> | 6 | 0,98304 | -1.017,60 |
>
> Optimum karar $Q=4$'tür. Başarılı teslimatta kâr pozitiftir; zarar yalnız $X<3$ iken oluşur:
> $$P(\Pi<0)=P(X<3)=1-0{,}8192=0{,}1808$$
> Zarar olasılığı %18,08'dir.

## 4 - Bağımsız sorular

### L1 - Temel

> [!question]
> $Q=6$ ve $p=0{,}85$ iken tam 5 sağlam ürün çıkma olasılığını hesaplayın.

> [!answer]- Çözüm
> $$P(X=5)=\binom65(0{,}85)^5(0{,}15)=0{,}399334\approx\%39{,}93$$

### L2 - Tuzaklı / aktarım

> [!question]
> Tam 5 sağlam ürün teslim edilirse toplam 125.000 TL alınan, eksik partinin kabul edilmediği bir siparişte birim üretim maliyeti 14.000 TL ve sağlamlık olasılığı %85'tir. $Q=5,6,7,8$ arasından beklenen kârı en yüksek olanı ve seçilen kararın zarar olasılığını bulun.

> [!answer]- Çözüm
> $$E[\Pi(Q)]=125.000P(X\ge5)-14.000Q$$
>
> | $Q$ | $P(X\ge5)$ | Beklenen kâr (TL) |
> |---:|---:|---:|
> | 5 | 0,443705 | -14.536,84 |
> | 6 | 0,776484 | 13.060,54 |
> | 7 | 0,926235 | **17.779,35** |
> | 8 | 0,978648 | 10.330,94 |
>
> Optimum $Q=7$'dir. Başarılı teslimatta kâr $125.000-98.000=27.000$ TL olduğundan zarar yalnız $X<5$ iken oluşur:
> $$P(\Pi<0)=1-0{,}92623484=0{,}07376516\approx\%7{,}38$$

### L3 - Yöntemi seç

> [!question]
> Aşağıdaki iki durum için uygun yaklaşımı seçin ve nedenini yazın:
>
> 1. Yalnız 4 özel döküm gereklidir; her biri ya sağlam ya kusurludur ve eksik parti reddedilir.
> 2. Bir yıl içinde 100.000 standart parça üretilecek, ortalama fire oranı %3'tür.

> [!answer]- Çözüm
> 1. Düşük hacim ve eşik tipi gelir nedeniyle binom olasılıklarıyla beklenen kâr enümerasyonu kullanılır.
> 2. Yüksek hacimde ortalama verim yaklaşımı uygundur: gerekli giriş yaklaşık $100.000/(1-0{,}03)$ ile bulunur. Tam parça ve aşama bazlı yuvarlama ayrıca kontrol edilir.

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. $P(X=x)$ formülünü yaz.
2. Beklenen kârın çözüm sırasını altı adımda yaz.
3. Ortalama fire yaklaşımının bu problemde neden yetersiz olduğunu açıkla.
4. Zarar olasılığını bulurken hangi $x$ değerlerinin toplanacağı nasıl belirlenir?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Yeni temel varyant |  |  |  |
| D3 |  | Yeni L2 + HF04 karşılaştırma |  |  |  |
| D7 |  | Süreli karma mini test |  |  |  |
| D14 |  | Aktarım sorusu |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| $Q=O/(1-s)$ ile doğrudan karar vermek | Olası sonuçların ekonomik dağılımını görmez | Düşük hacim + rassallık + eşik gelir işaretlerini kontrol et |
| Geliri her sağlam ürün için doğrusal yazmak | Eksik parti kabul edilmiyorsa gelir sıfır olabilir | Sözleşmenin kabul ve fazla ürün kurallarını parçalı yaz |
| Yalnız en olası $x$'i kullanmak | Beklenen kâr bütün mümkün sonuçları içerir | $x=0,\ldots,Q$ durumlarının olasılık toplamını kontrol et |
| Zarar olasılığını $P(X<hedef)$ sanmak | Bazı sorularda eksik satış veya geri kazanım zararı önleyebilir | Önce $\Pi(Q,x)<0$ yapan durumları belirle |

## Kaynaklar

- [[HF3-P3-Ürün, Süreç ve Çizelgeleme Tasarımı II-2025.pptx|Ders sunumu]], slayt 35-48
- [[05 Kaynaklar/MarkItDown/HF03 - Ham|HF03 ham metni]], yaklaşık satır 390-566
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
