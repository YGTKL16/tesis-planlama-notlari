---
hafta: 11
konu: dikdoğrusal tek tesis minisum, ağırlıklı medyan ve alternatif konumlar
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, konum, minisum, ağırlıklı-medyan]
kaynak: HF11 slayt 7-27
---

# HF11A - Minisum ve Ağırlıklı Medyan

![[07 Ekler/Grafikler/minisum-konum.svg]]

> [!summary] Bir cümlede
> Dikdoğrusal minisum problemi, yeni tesisin **toplam ağırlıklı uzaklığını** en aza indiren koordinatları her eksende ayrı bir ağırlıklı medyan hesabıyla bulur.

## Öğrenme hedefleri

- [ ] Sorudan dikdoğrusal minisum modelini seçebilirim.
- [ ] $x$ ve $y$ koordinatlarını ağırlıklı medyanla ayrı ayrı bulabilirim.
- [ ] Kümülatif ağırlık tam yarıya eşitse tek nokta yerine optimum aralığı yazabilirim.
- [ ] Bir aday konumun toplam ağırlıklı uzaklığını hesaplayabilirim.
- [ ] Optimum nokta kullanılamıyorsa alternatifleri ve eş maliyet hareketlerini değerlendirebilirim.

## 0 - Soğuk başlangıç

> [!question]
> Aynı doğru üzerindeki üç talep noktasının koordinat ve ağırlıkları $(0,4)$, $(4,2)$ ve $(10,6)$ olsun. Toplam ağırlığın yarısı 6'dır ve kümülatif ağırlık $x=4$'te tam 6 olur. Optimum koordinat yalnız $x=4$ müdür? Çözümü görmeden gerekçenizi yazın.

> [!answer]- Beklenen açıklama
> Hayır. Kümülatif ağırlık tam yarıya eşit olduğundan $x=4$ ile bir sonraki koordinat $x=10$ arasındaki **her nokta** optimumdur. Bu aralıkta sola ve sağa olan toplam ağırlıklar eşit kaldığı için bir yöndeki maliyet artışı diğer yöndeki azalışla dengelenir.

## 1 - Öğreten not

### Ne zaman kullanılır?

Şu işaretler birlikte görülüyorsa bu yöntem kullanılır:

- düzlemde **bir** yeni tesis konumlandırılacaktır,
- yeni tesis herhangi bir koordinata yerleşebilir,
- uzaklık Manhattan/dikdoğrusal uzaklıktır,
- amaç maksimum uzaklık değil, **toplam ağırlıklı uzaklığı** küçültmektir.

Uygulama örnekleri depo, malzeme dağıtım noktası veya ızgara koridorlarda hareket eden bir iş istasyonudur.

### Verilenler ve semboller

| Sembol | Anlam | Birim |
|---|---|---|
| $X=(x,y)$ | Yeni tesisin konumu | koordinat |
| $P_i=(a_i,b_i)$ | Mevcut tesis $i$'nin konumu | koordinat |
| $w_i$ | Tesis $i$ ile ilişki/akış/maliyet ağırlığı | sefer/gün veya TL/(birim uzaklık) |
| $d_i$ | $X$ ile $P_i$ arasındaki dikdoğrusal uzaklık | uzaklık |
| $f(x,y)$ | Toplam ağırlıklı uzaklık | ağırlık × uzaklık |

### Amaç fonksiyonu

$$
d_i(X,P_i)=|x-a_i|+|y-b_i|
$$

$$
\min f(x,y)=\sum_i w_i\bigl(|x-a_i|+|y-b_i|\bigr)
$$

Mutlak değerli toplam iki bağımsız parçaya ayrılır:

$$
f(x,y)=\underbrace{\sum_i w_i|x-a_i|}_{f_x(x)}
+\underbrace{\sum_i w_i|y-b_i|}_{f_y(y)}
$$

Bu ayrılabilirlik nedeniyle $x^*$ yalnız $a_i$ değerlerinden, $y^*$ yalnız $b_i$ değerlerinden bulunabilir.

### Ağırlıklı medyan algoritması

Her eksen için ayrı ayrı:

1. Koordinatları küçükten büyüğe sırala.
2. Aynı koordinattaki ağırlıkları birleştir.
3. Toplam ağırlığı $W=\sum_i w_i$ ve yarısını $W/2$ hesapla.
4. Kümülatif ağırlığın $W/2$'ye ulaştığı yeri bul.
5. Kümülatif toplam ilk kez $W/2$'yi **aşıyorsa**, o koordinat tek optimumdur.
6. Kümülatif toplam bir koordinatta $W/2$'ye **tam eşitse**, o koordinat ile sonraki daha büyük koordinat arasındaki her değer optimumdur.

> [!warning] Eşit yarı durumu
> “İlk kez yarıya eşit veya büyük olan koordinatı seç” kısa kuralı tek bir optimum nokta üretebilir; fakat eşitlikte tam çözüm bir **aralıktır**. İki eksende de aralık oluşursa optimum çözüm kümesi bir dikdörtgendir.

### Sonuç kontrolü

Bulduğunuz konum için mutlaka:

$$
f(x,y)=\sum_i w_i\left(|x-a_i|+|y-b_i|\right)
$$

hesaplayın. Sonuç yalnız “$(x,y)$ bulundu” ile bitmez; amaç değeri ve karar cümlesi yazılır.

### Alternatif konumlar

Optimum koordinat fiziksel olarak kullanılamıyorsa her uygulanabilir aday $A_k=(x_k,y_k)$ için $f(A_k)$ hesaplanır. Adaylar içindeki en küçük değer seçilir. Bu, ağırlıklı medyanı aday koordinatlara yuvarlamak değildir.

### Eş maliyet eğrilerinin hesap mantığı

Mevcut tesislerin koordinat çizgileri arasında kalan bir hücrede $f$ doğrusaldır. Hücrenin içinde:

$$
G_x=\sum_{a_i<x}w_i-\sum_{a_i>x}w_i,
\qquad
G_y=\sum_{b_i<y}w_i-\sum_{b_i>y}w_i
$$

olur. Amaç değerini değiştirmeyen küçük bir hareket için:

$$
G_x\,\Delta x+G_y\,\Delta y=0
$$

ve $G_y\ne0$ ise eş maliyet doğrusunun eğimi:

$$
\frac{\Delta y}{\Delta x}=-\frac{G_x}{G_y}
$$

şeklindedir. Bir tesisin $x$ veya $y$ koordinat çizgisi geçildiğinde çekiş dengesi değiştiği için eğri kırılır.

### Benzer yöntemlerden farkı

| Minisum | Minimax |
|---|---|
| Toplam $\sum_i w_i d_i$ küçültülür. | En büyük uzaklık $\max_i d_i$ küçültülür. |
| Ağırlıklı medyan kullanılır. | $u$-$v$ dönüşümü ve kapsama yarıçapı kullanılır. |
| Depo/taşıma maliyeti odaklıdır. | Acil hizmette en kötü erişim odaklıdır. |

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF11, slayt 12-18
> Beş mevcut tesisin koordinatları ve yeni tesisle günlük ilişkileri şöyledir. Dikdoğrusal toplam ağırlıklı uzaklığı en aza indiren konumu ve amaç değerini bulun. Optimum konum kullanılamıyorsa $(5,6)$, $(4,2)$ ve $(8,4)$ adaylarını karşılaştırın.

| Tesis | $(a_i,b_i)$ | $w_i$ |
|---:|---:|---:|
| 1 | $(1,1)$ | 5 |
| 2 | $(5,2)$ | 6 |
| 3 | $(2,8)$ | 2 |
| 4 | $(4,4)$ | 4 |
| 5 | $(8,6)$ | 8 |

### Adım 1 - Toplam ağırlık

$$
W=5+6+2+4+8=25,\qquad W/2=12{,}5
$$

### Adım 2 - $x$ ağırlıklı medyanı

| Sıra | $a_i$ | $w_i$ | Kümülatif ağırlık |
|---:|---:|---:|---:|
| 1 | 1 | 5 | 5 |
| 2 | 2 | 2 | 7 |
| 3 | 4 | 4 | 11 |
| 4 | 5 | 6 | **17** |
| 5 | 8 | 8 | 25 |

Kümülatif ağırlık 12,5'i ilk kez $a=5$'te aşar:

$$x^*=5$$

### Adım 3 - $y$ ağırlıklı medyanı

| Sıra | $b_i$ | $w_i$ | Kümülatif ağırlık |
|---:|---:|---:|---:|
| 1 | 1 | 5 | 5 |
| 2 | 2 | 6 | 11 |
| 3 | 4 | 4 | **15** |
| 4 | 6 | 8 | 23 |
| 5 | 8 | 2 | 25 |

Kümülatif ağırlık 12,5'i ilk kez $b=4$'te aşar:

$$y^*=4$$

Dolayısıyla optimum konum:

$$X^*=(5,4)$$

### Adım 4 - Amaç değerini hesapla

| Tesis | Uzaklık $|5-a_i|+|4-b_i|$ | $w_i d_i$ |
|---:|---:|---:|
| 1 | $4+3=7$ | 35 |
| 2 | $0+2=2$ | 12 |
| 3 | $3+4=7$ | 14 |
| 4 | $1+0=1$ | 4 |
| 5 | $3+2=5$ | 40 |
| **Toplam** |  | **105** |

### Adım 5 - Uygulanabilir alternatifleri karşılaştır

Slayttaki adayların yeniden hesaplanan değerleri:

| Aday | Toplam ağırlıklı uzaklık |
|---:|---:|
| $(5,6)$ | 115 |
| $(4,2)$ | **114** |
| $(8,4)$ | 132 |

> [!success] Karar
> Serbest konumlandırmada $(5,4)$ ve $f=105$ optimumdur. Bu nokta kullanılamıyor ve yalnız üç aday uygulanabiliyorsa $(4,2)$, $f=114$ ile adaylar içindeki en iyi konumdur.

### Öz-açıklama

1. $x$ ve $y$ hesaplarını neden birbirinden bağımsız yaptık?
2. $(4,2)$ neden global optimum değil, yalnız “adaylar içindeki en iyi” konumdur?
3. Toplam ağırlık 25 yerine 24 olup bir kümülatif toplam 12'ye eşit olsaydı sonuç nasıl değişebilirdi?

## 3 - Kademeli örnek

> [!question]
> $P_1=(0,0),w_1=4$; $P_2=(4,2),w_2=2$; $P_3=(10,6),w_3=6$ verilsin. Dikdoğrusal minisum optimum çözüm kümesini ve minimum amaç değerini bulun.
>
> 1. $W=\_\_$ ve $W/2=\_\_$.
> 2. $x$ için kümülatif ağırlık $a=4$'te yarıya tam eşittir; $x^*\in\_\_$.
> 3. $y$ için kümülatif ağırlık $b=2$'de yarıya tam eşittir; $y^*\in\_\_$.
> 4. Uygun bir optimum köşe seçip $f$ değerini hesaplayın.

> [!answer]- Tam çözüm
> $$W=4+2+6=12,\qquad W/2=6$$
>
> $x$ sıralamasında kümülatif ağırlık $x=4$'te 6 olur ve sonraki koordinat 10'dur:
> $$x^*\in[4,10]$$
>
> $y$ sıralamasında kümülatif ağırlık $y=2$'de 6 olur ve sonraki koordinat 6'dır:
> $$y^*\in[2,6]$$
>
> Optimum çözüm kümesi $[4,10]\times[2,6]$ dikdörtgenidir. Örneğin $(4,2)$ için:
> $$f(4,2)=4(4+2)+2(0+0)+6(6+4)=24+0+60=84$$
>
> Bu dikdörtgendeki her nokta aynı minimum $f^*=84$ değerini verir.

## 4 - Bağımsız sorular

### L1 - Temel

> [!question]
> Bir doğru üzerindeki noktalar $x=(1,4,7)$ ve ağırlıklar $w=(2,5,3)$ olsun. Ağırlıklı medyanı ve minimum toplam ağırlıklı uzaklığı bulun.

> [!answer]- Çözüm
> $W=10$, $W/2=5$ ve kümülatif ağırlıklar $2,7,10$'dur. İlk aşım $x=4$'te olduğundan $x^*=4$.
> $$f(4)=2|4-1|+5|4-4|+3|4-7|=6+0+9=15$$

### L2 - Tuzaklı / aktarım

> [!question]
> $P_1=(0,0),w_1=3$; $P_2=(4,0),w_2=1$; $P_3=(6,5),w_3=4$ için uygulanabilir adaylar $A=(4,1)$, $B=(5,4)$ ve $C=(8,2)$'dir. Önce serbest optimum çözüm kümesini, sonra adaylar içindeki en iyi konumu bulun.

> [!answer]- Çözüm
> $W=8$, yarısı 4'tür. $x=4$'te kümülatif ağırlık tam 4 olduğundan $x^*\in[4,6]$; $y=0$'da kümülatif ağırlık 4 olduğundan $y^*\in[0,5]$.
>
> | Aday | $f$ |
> |---:|---:|
> | $A=(4,1)$ | **40** |
> | $B=(5,4)$ | **40** |
> | $C=(8,2)$ | 52 |
>
> $A$ ve $B$ optimum dikdörtgenin içindedir ve eş maliyetlidir. Adaylar arasında iki optimum vardır; keyfî biçimde yalnız birini yazmak eksik cevaptır.

### L3 - Yöntemi seç

> [!question]
> Her durum için uygun yaklaşımı seçin:
>
> 1. Bir depo için toplam günlük taşıma maliyeti küçültülecektir; konum serbest ve yollar ızgara biçimindedir.
> 2. Bir ambulans noktası için en uzaktaki mahallenin erişim mesafesi küçültülecektir.
> 3. Ağırlıklı medyanla bulunan nokta yapılaşma nedeniyle kullanılamaz; üç izinli parsel verilmiştir.

> [!answer]- Çözüm
> 1. Dikdoğrusal minisum ve ağırlıklı medyan.
> 2. Dikdoğrusal minimax; toplam değil en kötü uzaklık amaçlanır.
> 3. İzinli üç adayın her biri için minisum amaç değeri hesaplanır ve en küçüğü seçilir.

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. Minisum sorusunu hangi üç ifadeden tanırsın?
2. Ağırlıklı medyan çözüm sırasını yaz.
3. Kümülatif ağırlık tam $W/2$ olduğunda neden tek koordinat yazılmaz?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli örnek |  |  |  |
| D1 |  | L1 |  |  |  |
| D3 |  | L2 + minimax sorusu |  |  |  |
| D7 |  | Kaynak örneğini kapalı kitap çöz |  |  |  |
| D14 |  | Karma konum testi |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| Koordinatları sıralayıp ağırlıkları eski sırada bıraktım. | Koordinat-ağırlık çifti ayrıldı. | Her satırda tesis kimliğini de taşıyacağım. |
| Eşit yarıda tek koordinat yazdım. | Optimum aralığı kaybettim. | “Eşit mi, aşıyor mu?” kontrolünü ayrı yazacağım. |
| Ağırlıksız uzaklıkları topladım. | Akış/maliyet etkisini yok saydım. | Her satırda önce $d_i$, sonra $w_i d_i$ sütunu açacağım. |
| Yasak optimumu en yakın adaya yuvarladım. | En yakın koordinat en düşük ağırlıklı maliyeti garanti etmez. | Bütün uygulanabilir adaylarda $f$ hesaplayacağım. |

## Kaynaklar

- Ders sunumu: [[HF11-P11-Tesis Konumu I-2025.pptx|HF11]], slayt 7-27; sayısal örnek slayt 12-18.
- [[05 Kaynaklar/MarkItDown/HF11 - Ham|HF11 ham metni]]
- Ders kitabı: Bölüm 10.2.1.1, tek tesis dikdoğrusal minisum modeli.
