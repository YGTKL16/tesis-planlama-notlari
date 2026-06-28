---
hafta: 2
konu: dinamik kapasite büyüme kuralı
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, dinamik-kapasite, iskonto, ölçek-ekonomisi]
kaynak: HF02 slayt 52-63
---

# HF02C - Dinamik Kapasite Büyümesi

> [!summary] Bir cümlede
> Sabit hızla büyüyen talepte kapasite ilavelerinin büyüklüğü ve zaman aralığı, ölçek ekonomisi ile paranın zaman değeri dengelenerek seçilir.

## Öğrenme hedefleri

- [ ] Kapasite ilavesi büyüklüğü ile yatırım aralığı arasındaki ilişkiyi kurabilirim.
- [ ] Sonsuz yatırım dizisinin bugünkü değerini geometrik seriyle yazabilirim.
- [ ] Ölçek ekonomisi maliyet fonksiyonunu modele yerleştirebilirim.
- [ ] Boyutsuz $u=rx$ dönüşümüyle optimum aralığı bulabilirim.
- [ ] Model varsayımlarını ve sınırlamalarını yorumlayabilirim.

## 0 - Soğuk başlangıç

> [!question]
> Talep yılda sabit miktarda artarken çok sık küçük kapasite eklemek ile seyrek büyük tesis kurmak arasında hangi iki ekonomik etki çatışır?

> [!answer]- Beklenen açıklama
> Büyük ve seyrek yatırımlar ölçek ekonomisinden yararlanabilir; ancak kapasite daha erken kurulup uzun süre atıl kalabilir. Küçük ve sık yatırımlar talebi yakından izler fakat ölçek avantajını azaltır ve yatırımları öne çeker.

## 1 - Öğreten not

### Model değişkenleri

| Sembol | Anlam |
|---|---|
| $D$ | Talebin yıllık doğrusal artışı, kapasite/yıl |
| $x$ | İki kapasite ilavesi arasındaki zaman, yıl |
| $y$ | Her ilavede kurulacak kapasite |
| $r$ | Sürekli bileşik yıllık iskonto oranı |
| $f(y)$ | $y$ büyüklüğündeki kapasite ilavesinin maliyeti |

Talep yılda $D$ arttığına göre $x$ yıllık ihtiyacı karşılayan kapasite:

$$
y=xD
$$

### Sonsuz yatırım dizisinin bugünkü değeri

Kapasite ilaveleri $0,x,2x,3x,\ldots$ zamanlarında aynı büyüklükte yapılırsa:

$$
C(x)=f(xD)+e^{-rx}f(xD)+e^{-2rx}f(xD)+\cdots
$$

Bu bir geometrik seridir:

$$
C(x)=\frac{f(xD)}{1-e^{-rx}}
$$

### Ölçek ekonomisi maliyeti

Sunumdaki maliyet ailesi:

$$
f(y)=ky^a,\qquad 0<a<1
$$

$a<1$ olduğundan kapasite iki katına çıkınca maliyet $2^a$ katına çıkar; iki katına çıkmaz.

Model:

$$
C(x)=\frac{k(xD)^a}{1-e^{-rx}}
$$

### Optimum koşulu

$C(x)$'in logaritmasının türevi sıfıra eşitlenince:

$$
\frac{a}{x}-\frac{r}{e^{rx}-1}=0
$$

Buradan:

$$
\frac{rx}{e^{rx}-1}=a
$$

Boyutsuz dönüşüm:

$$
u=rx
$$

$$
g(u)=\frac{u}{e^u-1}=a
$$

Sunumdaki $u-g(u)$ tablosundan veya sayısal çözümden $u$ bulunur. Sonra:

$$
x^*=\frac{u}{r}
$$

$$
y^*=x^*D
$$

$$
f(y^*)=k(y^*)^a
$$

> [!important] Yapısal sonuç
> Optimum zaman aralığını $a$ ve $r$ belirler. Talep artışı $D$ ve ölçek katsayısı $k$, optimum ilave büyüklüğü ve maliyeti değiştirir; $x^*$ eşitliğinde görünmez.

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF02, slayt 60-62
> Kapasite maliyeti $f(y)=0{,}0107y^{0{,}62}$ milyon TL, yıllık talep artışı $D=5.000$ ton/yıl ve sürekli iskonto oranı $r=0{,}16$ olsun. Optimal yatırım aralığını, ilave kapasiteyi ve ilave maliyetini bulun.

### Adım 1 - $u$ değerini bul

$$
a=0{,}62
$$

Sunumdaki tablodan:

$$
g(u)=\frac{u}{e^u-1}\approx0{,}62
$$

değerini veren:

$$
u\approx0{,}89
$$

Kontrol:

$$
g(0{,}89)=\frac{0{,}89}{e^{0{,}89}-1}=0{,}62015
$$

### Adım 2 - Optimal zaman aralığı

$$
x^*=\frac{u}{r}=\frac{0{,}89}{0{,}16}=5{,}5625\text{ yıl}
$$

### Adım 3 - İlave kapasite

$$
y^*=x^*D=5{,}5625(5.000)=27.812{,}5\text{ ton}
$$

### Adım 4 - Her ilavenin maliyeti

$$
f(y^*)=0{,}0107(27.812{,}5)^{0{,}62}
=6{,}09274\text{ milyon TL}
$$

> [!success] Sonuç
> Yaklaşık her 5,5625 yılda bir 27.812,5 ton kapasite eklenir. Her ilavenin bugünkü nominal kurulum maliyeti yaklaşık 6,093 milyon TL'dir.

### Sonsuz dizinin bugünkü değeri

İstenirse bütün sonsuz yatırım dizisinin sıfır anındaki değeri:

$$
C(x^*)=\frac{6{,}09274}{1-e^{-0{,}16(5{,}5625)}}
=10{,}3382\text{ milyon TL}
$$

### Öz-açıklama

1. Neden her ilavenin büyüklüğü $xD$'dir?
2. Neden gelecekteki yatırımlar $e^{-rnx}$ ile indirgenir?
3. $a$ küçülürse ölçek ekonomisi güçlenir; bunun daha büyük ve seyrek yatırımlara etkisini açıklayın.

## 3 - Kademeli örnek

> [!question]
> $f(y)=0{,}015y^{0{,}62}$ milyon TL, $D=2.000$ birim/yıl ve $r=0{,}10$ olsun. $a=0{,}62$ için tablodan $u\approx0{,}89$ kullanın.
>
> 1. $x^*=\_\_/\_\_$
> 2. $y^*=x^*\_\_$
> 3. $f(y^*)=\_\_(y^*)^{\_\_}$

> [!answer]- Tam çözüm
> $$x^*=0{,}89/0{,}10=8{,}9\text{ yıl}$$
> $$y^*=8{,}9(2.000)=17.800\text{ birim}$$
> $$f(y^*)=0{,}015(17.800)^{0{,}62}=6{,}477\text{ milyon TL}$$

## 4 - Bağımsız sorular

### L1 - Bugünkü değer

> [!question]
> Her 4 yılda bir 5 milyon TL yatırım yapılacak ve sürekli iskonto oranı $r=0{,}12$ olacaktır. Sonsuz yatırım dizisinin sıfır anındaki değerini bulun.

> [!answer]- Çözüm
> $$C=\frac{5}{1-e^{-0{,}12(4)}}=13{,}116\text{ milyon TL}$$

### L2 - Kaynak çalışma sorusu

> [!question]
> $f(y)=0{,}0205y^{0{,}58}$ milyon TL, $D=3.000$ ton/yıl ve $r=0{,}12$ olsun. $g(u)=0{,}58$ eşitliğinin sayısal çözümü $u\approx1{,}00584$ verilmiştir. Optimal zaman, kapasite, ilave maliyeti ve ilk dört ilavenin $(t=0,x,2x,3x)$ bugünkü değer toplamını bulun.

> [!answer]- Çözüm
> $$x^*=1{,}00584/0{,}12=8{,}3820\text{ yıl}$$
> $$y^*=8{,}3820(3.000)=25.146{,}1\text{ ton}$$
> $$f(y^*)=0{,}0205(25.146{,}1)^{0{,}58}=7{,}3118\text{ milyon TL}$$
> İlk dört ilave:
> $$PV_4=7{,}3118\sum_{n=0}^{3}e^{-0{,}12(8{,}3820)n}
> =11{,}3218\text{ milyon TL}$$

### L3 - Modeli eleştir

> [!question]
> Dinamik kapasite büyüme modelinin gerçek bir tesis kararını tek başına belirleyememesinin en az dört nedenini yazın.

> [!answer]- Çözüm
> Model sonsuz tesis ömrü, sabit doğrusal talep artışı ve sürekli sabit iskonto varsayar. Teknolojik eskime, talep belirsizliği, stok ve kapasite açığı maliyetleri, vergi, mevzuat, konum, hizmet altyapısı ve farklı yatırım büyüklüklerinde değişen işletme maliyetleri modeli değiştirebilir.

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. $y=xD$ ilişkisini açıkla.
2. $C(x)$ geometrik seri formülünü yaz.
3. $u$ dönüşümünü ve optimum koşulunu yaz.
4. $x^*$, $y^*$ ve $f(y^*)$ çözüm sırasını yaz.

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Kaynak örneği kapalı kitap |  |  |  |
| D3 |  | Yeni parametrelerle optimizasyon |  |  |  |
| D7 |  | HF02 karma test |  |  |  |
| D14 |  | Model eleştirisi + hesap |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| $y=D/x$ yazmak | $x$ yılda biriken talep $xD$'dir | Birim kontrolü yap: yıl × kapasite/yıl |
| Basit iskonto $(1+r)^{-t}$ ile sürekli iskontoyu karıştırmak | Model $e^{-rt}$ kullanır | Sorudaki iskonto türünü işaretle |
| Geometrik serinin paydasını $1+e^{-rx}$ yazmak | Ortak oran çıkarılırken işaret değişmez | $1+q+q^2=1/(1-q)$ hatırla |
| $u$ bulduktan sonra doğrudan kapasite sanmak | $u=rx$ boyutsuzdur | Önce $x=u/r$, sonra $y=xD$ |
| Tek yatırım maliyeti ile sonsuz dizinin PV'sini karıştırmak | $f(y^*)$ ve $C(x^*)$ farklı büyüklüklerdir | Soruda “her ilave” mi “tüm dizi” mi istendiğini ayır |

## Kaynaklar

- [[HF2-P2-Tesis Kapasite Planlama-2025.pptx|Ders sunumu]], slayt 52-63
- [[05 Kaynaklar/MarkItDown/HF02 - Ham|HF02 ham metni]], yaklaşık satır 697-812
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]

