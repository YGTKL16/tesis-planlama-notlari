---
hafta: 8
konu: CRAFT ile akış-mesafe yerleşim iyileştirme
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, craft, taşıma-maliyeti, yerel-arama]
kaynak: HF08 slayt 43-69 ve 73-86
---

# HF08C - CRAFT Yöntemi

> [!summary] Bir cümlede
> CRAFT, mevcut blok yerleşimde uygun ikili/üçlü bölüm değişimlerini deneyerek akış × birim maliyet × dik doğrusal uzaklık toplamını adım adım azaltır.

## Öğrenme hedefleri

- [ ] CRAFT'ın üç temel matrisini doğru eşleştirebilirim.
- [ ] Ağırlık merkezi ve dik doğrusal uzaklık hesaplayabilirim.
- [ ] Bir bölüm-konum atamasının toplam maliyetini bulabilirim.
- [ ] Değişim uygunluğu, yerel optimum ve tahmini/gerçek maliyet ayrımını açıklayabilirim.

## 0 - Soğuk başlangıç

> [!question]
> İki bölümün alanları eşit değil ve ortak sınırları da yok. CRAFT'ta doğrudan ikili değişim adayı olabilirler mi? Yalnız merkez koordinatlarını takas etmek yeterli midir?

> [!answer]- Beklenen açıklama
> Genel kaynak kuralına göre hayır: bölümler eşit alanlı veya komşu olmalıdır; eşit olmayan komşu bölümlerde bile uygulanabilir şekil ayrıca kontrol edilir. Merkez takası yalnız tahmini değişimi verir, gerçek yeni geometrinin merkezleri yeniden hesaplanmalıdır.

## 1 - Öğreten not

### Girdiler

1. Başlangıç blok yerleşimi ve bölüm alanları.
2. From-to akış matrisi $F=[f_{ij}]$.
3. Birim taşıma maliyeti matrisi $C=[c_{ij}]$.
4. Sabit bölümler ve fiziksel değişim kısıtları.

Yerleşimden uzaklık matrisi $D(L)=[d_{ij}(L)]$ üretilir.

$$
Z(L)=\sum_i\sum_{j\ne i}f_{ij}c_{ij}d_{ij}(L)
$$

$$d_{ij}=|x_i-x_j|+|y_i-y_j|$$

### Bölüm ağırlık merkezi

Bir bölüm eşit alanlı hücrelerden oluşuyorsa:

$$
x_i=\frac{1}{n_i}\sum_{h\in i}x_h,\qquad
y_i=\frac{1}{n_i}\sum_{h\in i}y_h
$$

Farklı alanlı parçalar varsa alan ağırlıklı merkez kullanılır.

### CRAFT döngüsü

1. Gerçek bölüm merkezlerini bul.
2. Dik doğrusal uzaklık matrisini kur.
3. Başlangıç maliyetini hesapla.
4. Uygun değişimleri belirle: eşit alanlı veya ortak sınır paylaşan bölümler; sabitler hariç.
5. Merkezleri geçici takas ederek maliyet değişimini tahmin et.
6. En büyük azalmayı sağlayan değişimi uygula.
7. Yeni şekillerin gerçek merkezlerini ve gerçek maliyeti hesapla.
8. İyileşme kalmayana kadar tekrarla; gerekiyorsa üçlü değişimleri dene.

> [!warning] Birim tutarlılığı
> Hücre kenarı 20 ft ise matris uzaklığının “1 birimi” 20 ft'tir. Birim taşıma maliyetinin uzaklık birimi de buna uymalıdır; aksi halde $Z$ sayısal olarak anlamsız olur.

### İkili değişimden farkı

| İkili yer değişim | CRAFT |
|---|---|
| Genellikle eşit büyüklüklü basit konumlar | Eşit olmayan ve düzensiz blokları da işleyebilir |
| Her takasta uzaklık doğrudan hesaplanır | Önce merkez takasıyla tahmin, sonra gerçek geometri kontrolü olabilir |
| Basit yerel arama | İkili/üçlü değişim, sabit ve yapay bölümler |

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF08, slayt 73-83
> Beş iş merkezinin A-E konumları arasındaki uzaklıklar ve 1-5 bölümleri arasındaki yönlü akışlar verilmiştir. $c_{ij}=1$. Başlangıç ataması `1A,2B,3C,4D,5E`'dir.

Uzaklık matrisi:

|  | A | B | C | D | E |
|---|---:|---:|---:|---:|---:|
| A | 0 | 5 | 6 | 7 | 8 |
| B | 5 | 0 | 7 | 8 | 10 |
| C | 6 | 7 | 0 | 6 | 5 |
| D | 7 | 8 | 6 | 0 | 7 |
| E | 8 | 10 | 5 | 7 | 0 |

Akış matrisi:

|  | 1 | 2 | 3 | 4 | 5 |
|---|---:|---:|---:|---:|---:|
| 1 | 0 | 50 | 30 | 40 | 10 |
| 2 | 20 | 0 | 25 | 5 | 45 |
| 3 | 40 | 45 | 0 | 30 | 15 |
| 4 | 60 | 5 | 20 | 0 | 35 |
| 5 | 55 | 3 | 3 | 15 | 0 |

Başlangıç maliyetinin satır toplamları kaynakta 790, 765, 810, 825 ve 590'dır:

$$Z_0=790+765+810+825+590=3.780$$

Beş bölüm için ilk iterasyonda:

$$\binom52=10\text{ ikili aday}$$

Kaynak tablolarındaki doğrulanmış ilk iterasyon sonuçları:

| Takas | Maliyet |
|---|---:|
| 1-2 | 3.904 |
| 1-3 | **3.589** |
| 1-4 | 3.945 |
| 1-5 | 3.838 |
| 2-3 | 3.710 |
| 2-4 | 3.706 |
| 2-5 | 3.731 |
| 3-4 | 3.746 |
| 3-5 | 3.856 |
| 4-5 | 3.707 |

İlk değişim 1-3'tür; yeni atama `3A,2B,1C,4D,5E`, maliyet 3.589 olur.

İkinci iterasyonda bölüm 4 ve 5'in takası `3A,2B,1C,5D,4E` atamasını verir. Verilen matrislerle bağımsız toplam:

$$
\boxed{Z=3.510}
$$

> [!danger] Kaynak slayt hatası
> HF08 slayt 83 aynı atama için **3.310** yazmaktadır. Ancak slayt 73'teki iki matrisin 20 yönlü hücresi yeniden çarpılıp toplandığında 3.510 çıkar. 120 olası atamanın bağımsız taramasında da minimum 3.510 ve atama `3A,2B,1C,5D,4E`'dir. Bu pakette doğrulanmış değer kullanılır.

> [!info] Sınav stratejisi — 3.310 vs 3.510
> Sınavda matrisler verilirse **kendi hesabını yap → 3.510 çıkarsa yaz**, yanına `(kaynak slayt: 3.310, hata)` düş. Her iki değeri gerekçesiyle yazan öğrenci puan kaybetmez. Bkz. [[01 Ders Notları/HF08 - Yerleşim Tasarımı II|HF08 CRAFT notu]].

$$
\text{tasarruf}=3.780-3.510=270
$$

$$
\text{tasarruf oranı}=270/3.780=%7{,}14
$$

### Öz-açıklama

1. Neden akış matrisi bölüm adlarıyla, uzaklık matrisi konum adlarıyla okunur?
2. İlk iterasyonda 1-3 değişimi ne kadar tasarruf sağlar?
3. Kaynak sonuç ile bağımsız sonuç çeliştiğinde hangi veri tekrar hesaplanmalıdır?

## 3 - Kademeli örnek

> [!question]
> Üç konumun uzaklıkları $d_{AB}=2$, $d_{AC}=3$, $d_{BC}=5$; çift akışları $F_{12}=2$, $F_{13}=3$, $F_{23}=10$, $c=1$. Başlangıç `1A,2B,3C`.
>
> 1. $Z_0=2(\_)+3(\_)+10(\_)$
> 2. 1-2 takası sonrası 1-3 ve 2-3 uzaklıklarını yaz.
> 3. Bütün takaslardan en iyisini seç.

> [!answer]- Tam çözüm
> $$Z_0=2(2)+3(3)+10(5)=63$$
> 1-2 takasında 1 konum B'ye, 2 konum A'ya geçer. Yeni $d_{13}=d_{BC}=5$, $d_{23}=d_{AC}=3$:
> $$Z_{1-2}=2(2)+3(5)+10(3)=49$$
> 1-3 takası $2(5)+3(3)+10(2)=39$, 2-3 takası $2(3)+3(2)+10(5)=62$ verir. En iyi değişim 1-3 ve maliyet 39'dur.

## 4 - Bağımsız sorular

### L1 - Merkez ve uzaklık

> [!question]
> P bölümü merkezleri `(1,1),(3,1),(1,3)` olan üç eşit hücreden; Q bölümü `(5,4)` merkezli tek hücreden oluşuyor. P'nin ağırlık merkezini ve P-Q dik doğrusal uzaklığını bulun.

> [!answer]- Çözüm
> $$P=(5/3,5/3)$$
> $$d_{PQ}=|5-5/3|+|4-5/3|=10/3+7/3=17/3=5{,}667$$

### L2 - Yönlü maliyet

> [!question]
> `1A,2B,3C` atamasında $d_{AB}=4,d_{AC}=6,d_{BC}=3$. Akışlar $f_{12}=10,f_{21}=5,f_{13}=2,f_{31}=8,f_{23}=7,f_{32}=1$ ve $c=2$ olsun. Maliyeti bulun.

> [!answer]- Çözüm
> $$Z=2[(10+5)4+(2+8)6+(7+1)3]=2(144)=288$$

### L3 - Uygunluk ve yöntem

> [!question]
> Eşit olmayan, komşu iki bölümün merkez takası 500 birim tasarruf tahmin ediyor; fakat yeni bloklardan biri iki kopuk parçaya ayrılıyor. Değişim kabul edilir mi?

> [!answer]- Çözüm
> Hayır. Komşuluk gerekli olsa da yeterli değildir; bölüm bütünlüğü ve uygulanabilir şekil korunmalıdır. Başka hücre aktarımı/şekil düzeni bulunamazsa aday elenir.

## 5 - Çıkış bileti

1. CRAFT'ın üç matrisini yaz.
2. Toplam maliyet ve dik doğrusal uzaklık formülünü yaz.
3. Hangi çiftler değişim adayıdır?
4. Tahmini merkez takası neden gerçek maliyetten farklı olabilir?
5. CRAFT neden küresel optimumu garanti etmez?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Kaynak başlangıç maliyeti |  |  |  |
| D3 |  | Uygunluk + yönlü maliyet |  |  |  |
| D7 |  | Bir tam CRAFT iterasyonu |  |  |  |
| D14 |  | HF08A-C karma seçim |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| Akış satırını konum adıyla okumak | Akış bölüme, uzaklık konuma aittir | Bölüm→konum sözlüğü yaz |
| Yalnız üst üçgeni toplamak | Akış yönlü olabilir | Tüm $i\ne j$ hücrelerini kontrol et |
| Her çifti değiştirilebilir sanmak | Alan, komşuluk, sabitlik ve şekil kısıtı vardır | Aday uygunluk listesi çıkar |
| Tahmini merkezi nihai kabul etmek | Şekil değişince gerçek merkez değişebilir | Uygulama sonrası merkezleri yenile |
| Slayttaki toplamı kontrol etmemek | Kaynakta 3.310/3.510 hatası var | Matris çarpım toplamını bağımsız yap |

## Kaynaklar

- [[HF8-P8-Yerlesim Tasarımı II-2025.pptx|Ders sunumu]], slayt 43-69 ve 73-86
- [[05 Kaynaklar/MarkItDown/HF08 - Ham|HF08 ham metni]], yaklaşık satır 639-1001 ve 1033-1363
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
