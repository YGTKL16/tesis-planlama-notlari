---
hafta: 2
konu: çok ürün başa baş ve yap-satın al kararı
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, çok-ürün, başa-baş, yap-satın-al]
kaynak: HF02 slayt 41-50
---

# HF02B - Çok Ürün Başa Baş ve Yap Satın Al

> [!summary] Bir cümlede
> Çok ürünlü başa başta katkı oranları satış karmasıyla ağırlıklandırılır; yap-satın al kararında ise yatırım ile birim maliyet avantajının hangi hacimde dengelendiği bulunur.

## Öğrenme hedefleri

- [ ] Satış miktarı karması ile satış tutarı karmasını ayırabilirim.
- [ ] Ağırlıklı katkı payı oranını kurabilirim.
- [ ] Çok ürünlü başa baş satış tutarını ürünlere dağıtabilirim.
- [ ] Yap-satın al eşik miktarını toplam maliyetlerden türetebilirim.
- [ ] Eşik sonucunu kalite, kapasite ve tedarik riskiyle birlikte yorumlayabilirim.

## 0 - Soğuk başlangıç

> [!question]
> İki ürünün satış fiyatları farklıysa, “satışların %60'ı A ürünüdür” ifadesinin adet yüzdesi mi satış geliri yüzdesi mi olduğu neden önemlidir?

> [!answer]- Beklenen açıklama
> Çok ürün başa baş formülündeki ağırlık, sunumdaki tanıma göre ürünün toplam **satış tutarı** içindeki payıdır. Adet payı doğrudan kullanılırsa pahalı ve ucuz ürünlerin katkısı yanlış ağırlıklandırılır.

## 1 - Öğreten not

### Çok ürünlü başa baş

Ürün $i$ için:

$$
CMR_i=1-\frac{V_i}{P_i}=\frac{P_i-V_i}{P_i}
$$

Ürünün tahmini satış tutarı:

$$
S_i=P_iQ_i
$$

Toplam satış tutarındaki ağırlığı:

$$
W_i=\frac{S_i}{\sum_jS_j}
$$

Ağırlıklı katkı payı oranı:

$$
\overline{CMR}=\sum_iW_iCMR_i
$$

Satış tutarı cinsinden başa baş:

$$
BEP_{TL}=\frac{F}{\overline{CMR}}
$$

Mevcut satış karmasının korunacağı varsayılırsa ürün $i$'nin başa baş satış tutarı:

$$
BEP_i=W_iBEP_{TL}
$$

ve yaklaşık adet:

$$
q_i=\frac{BEP_i}{P_i}
$$

> [!warning] Varsayım
> Satış karması değişirse ağırlıklı katkı oranı ve başa baş noktası da değişir. Çok ürünlü sonuç sabit bir fizik yasası değil, verilen karmaya bağlı senaryodur.

### Yap veya satın al

Dışarıdan satın alma:

$$
TC_{satın}=c_1x
$$

İçeride üretim:

$$
TC_{yap}=K+c_2x
$$

$K$ gerekli yatırım/sabit maliyet, $c_1$ satın alma birim maliyeti ve $c_2$ içeride üretim birim maliyetidir. $c_1>c_2$ ise eşik:

$$
x^*=\frac{K}{c_1-c_2}
$$

- $x<x^*$: satın alma daha ucuzdur.
- $x>x^*$: içeride üretim daha ucuzdur.
- $x=x^*$: toplam maliyetler eşittir.

Tam adetlerde kesirli eşikten sonraki ilk birim, içeride üretimin gerçekten daha ucuz olduğu ilk aday olabilir; iki toplam maliyetle kontrol edilir.

## 2 - Tam çözümlü kaynak örneği: çok ürün

> [!example] Kaynak: HF02, slayt 43-45
> Bir lokantanın aylık sabit maliyeti 3.000 $'dır. Yılda 312 gün çalışmaktadır.

| Ürün | Yıllık adet | Fiyat ($) | Değişken maliyet ($) |
|---|---:|---:|---:|
| Sandviç | 9.000 | 5,00 | 3,00 |
| İçecek | 9.000 | 1,50 | 0,50 |
| Fırın patates | 7.000 | 2,00 | 1,00 |

### Satış tutarları ve katkılar

| Ürün | Satış ($) | $W_i$ | $CMR_i$ | $W_iCMR_i$ |
|---|---:|---:|---:|---:|
| Sandviç | 45.000 | 0,620690 | 0,400000 | 0,248276 |
| İçecek | 13.500 | 0,186207 | 0,666667 | 0,124138 |
| Fırın patates | 14.000 | 0,193103 | 0,500000 | 0,096552 |
| **Toplam** | **72.500** | **1,000000** |  | **0,468966** |

Yıllık sabit maliyet:

$$
F=3.000(12)=36.000\text{ $}
$$

Tam hassasiyetle:

$$
BEP_{\$}=\frac{36.000}{0{,}4689655}=76.764{,}71\text{ $/yıl}
$$

$$
BEP_{günlük}=\frac{76.764{,}71}{312}=246{,}04\text{ $/gün}
$$

> [!note] Kaynak yuvarlaması
> Sunum, ara ağırlıklı katkı oranını 0,470 olarak yuvarlayıp $36.000/0{,}47=76.596$ $/yıl ve yaklaşık 245,50 $/gün raporlar. Verilen ham sayıları tam hassasiyetle kullanınca 76.764,71 $/yıl çıkar. Sınavda ara değerleri mümkün olduğunca yuvarlamadan taşı.

### Öz-açıklama

1. Neden sabit maliyet 3.000 değil 36.000 alındı?
2. İçeceğin adet payı yüksek olsa da satış tutarı ağırlığı neden yalnız 0,186'dır?
3. Sandviç satış payı artarsa başa baş satış tutarı hangi yönde değişir?

## 3 - Tam çözümlü kaynak örneği: yap veya satın al

> [!example] Kaynak: HF02, slayt 47-50
> Klavyeyi dışarıdan almak 50 TL/adet; içeride üretmek 35 TL/adet ve 8.000.000 TL yatırım gerektiriyor.

$$
TC_{satın}=50x
$$

$$
TC_{yap}=8.000.000+35x
$$

Eşitle:

$$
50x=8.000.000+35x
$$

$$
15x=8.000.000
$$

$$
x^*=533.333{,}33
$$

Tam adet kontrolü:

- 533.333 adette satın alma 26.666.650 TL, yapma 26.666.655 TL'dir; satın alma 5 TL daha ucuzdur.
- 533.334 adette satın alma 26.666.700 TL, yapma 26.666.690 TL'dir; yapma 10 TL daha ucuzdur.

> [!success] Karar
> Yalnız ilgili maliyetler açısından 533.334 adet ve üzerindeki hacimde içeride üretim; daha düşük hacimde satın alma tercih edilir.

## 4 - Kademeli örnek

> [!question]
> Yıllık sabit maliyet 96.000 TL'dir. A ürününün satış geliri karmadaki payı %60, katkı payı oranı %40; B ürününün satış payı %40, katkı payı oranı %60'tır. Toplam ve ürün bazında başa baş satış tutarlarını bulun.
>
> 1. $\overline{CMR}=0{,}60(\_\_)+0{,}40(\_\_)=\_\_$
> 2. $BEP_{TL}=\_\_/\_\_$
> 3. Sonucu %60-%40 karmaya dağıtın.

> [!answer]- Tam çözüm
> $$\overline{CMR}=0{,}60(0{,}40)+0{,}40(0{,}60)=0{,}48$$
> $$BEP_{TL}=96.000/0{,}48=200.000\text{ TL}$$
> A ürününün satış tutarı $0{,}60(200.000)=120.000$ TL; B ürününün satış tutarı 80.000 TL'dir.

## 5 - Bağımsız sorular

### L1 - Yap veya satın al

> [!question]
> Satın alma maliyeti 42 TL/adet; içeride üretim maliyeti 27 TL/adet; yatırım 300.000 TL'dir. Eşik miktarı bulun ve 18.000 ile 25.000 adet talepler için karar verin.

> [!answer]- Çözüm
> $$x^*=300.000/(42-27)=20.000\text{ adet}$$
> 18.000 adette satın alma; 25.000 adette içeride üretim daha ucuzdur.

### L2 - Karmadan adede

> [!question]
> Kademeli örnekte A'nın fiyatı 60 TL, B'nin fiyatı 50 TL olsun. Başabaş satış karmasını yaklaşık adetlere çevirin.

> [!answer]- Çözüm
> A: $120.000/60=2.000$ adet. B: $80.000/50=1.600$ adet. Bu dağılım verilen satış **tutarı** karmasını korur.

### L3 - Kararı eleştir

> [!question]
> “Talep eşiğin üzerindeyse her koşulda içeride üretmek gerekir.” ifadesini değerlendirin.

> [!answer]- Çözüm
> Yanlıştır. Eşik yalnız modele katılan maliyetleri karşılaştırır. Kalite, gizlilik, tedarik kesintisi, kapasite uygunluğu, teslim süresi, yatırım riski, bakım ve teknolojik eskime de kararı değiştirebilir.

## 6 - Çıkış bileti

Notu kapatıp cevapla:

1. $W_i$, $CMR_i$ ve ağırlıklı katkı formüllerini yaz.
2. Çok ürün başa başın temel varsayımını yaz.
3. Yap-satın al eşiğini toplam maliyetlerden türet.
4. Eşik hacmin üzerinde içeride üretimin neden avantajlı olduğunu açıkla.

## 7 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Çok ürün varyantı |  |  |  |
| D3 |  | Yap-satın al + yorum |  |  |  |
| D7 |  | HF02 karma test |  |  |  |
| D14 |  | Aktarım sorusu |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| $W_i$ olarak adet yüzdesi kullanmak | Formülde satış tutarı payı gerekir | Önce $P_iQ_i$ hesapla |
| Katkı oranlarını ağırlıksız ortalamak | Ürünlerin satış payları farklıdır | $\sum W_iCMR_i$ kullan |
| Aylık sabit maliyeti yıllık satışla kullanmak | Dönemler uyuşmaz | Bütün değerleri aynı döneme getir |
| Ara oranları erken yuvarlamak | Başabaş sonucu kayabilir | Son adıma kadar hassasiyet koru |
| Yap-satın al kararında yalnız birim maliyete bakmak | İç üretim yatırımı gözden kaçar | İki toplam maliyeti yaz |

## Kaynaklar

- [[HF2-P2-Tesis Kapasite Planlama-2025.pptx|Ders sunumu]], slayt 41-50
- [[05 Kaynaklar/MarkItDown/HF02 - Ham|HF02 ham metni]], yaklaşık satır 551-684
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]

