---
hafta: 7
konu: REL şemasından ilişki ve blok diyagramı kurma
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, rel, ilişki-diyagramı, slp]
kaynak: HF07 slayt 61-81
---

# HF07C - İlişki Diyagramı Kurma

> [!summary] Bir cümlede
> İlişki diyagramı, REL kodlarını öncelik sırasıyla mekânsal yakınlığa dönüştürür; alanlar daha sonra birim bloklarla eklenerek uygulanabilir yerleşim geliştirilir.

## Öğrenme hedefleri

- [ ] REL şemasını bölüm bazlı ilişki çalışma tablosuna çevirebilirim.
- [ ] Metot I ve Metot II'nin seçim mantığını ayırabilirim.
- [ ] Bir adayın yerleştirilmiş bölümlerle ilişki imzasını oluşturabilirim.
- [ ] Alanı seçilen birim kare alanına dönüştürebilirim.

## 0 - Soğuk başlangıç

> [!question]
> Yerleştirilmiş iki bölümle ilişkileri sırasıyla `(A,U)` ve `(E,E)` olan iki adaydan hangisi önce seçilir? Neden yalnız toplam sayısal puan kullanmak kaynak yöntemle aynı olmayabilir?

> [!answer]- Beklenen açıklama
> Kaynak Metot II öncelik dizisinde `A*`, `EE`'den önce gelir; bu nedenle `(A,U)` adayı seçilir. Yöntem ilişki harflerini leksikografik/öncelik tabanlı karşılaştırır, keyfî sayısal ağırlık toplamı kullanmaz.

## 1 - Öğreten not

### Girdi ve çıktı

- **Girdi:** REL şeması, bölüm alanları, bina/şekil kısıtları.
- **Ara çıktı:** Ölçeksiz ilişki diyagramı.
- **Sonraki çıktı:** Alan şablonları eklenmiş blok yerleşim alternatifleri.

REL sırası genellikle:

$$A>E>I>O>U$$

`X`, yakınlaştırılacak bir derece değil, kaçınılması gereken ilişki olarak ayrıca denetlenir.

### Metot I

1. A ilişkili çiftleri yerleştir.
2. E ilişkilerini ekleyip yeniden düzenle.
3. X ilişkilerini ayıracak şekilde düzenle.
4. I, O ve kalan U ilişkilerini sırayla işle.
5. Tüm bölümleri ve öncelikli ilişkileri kontrol et.

Metot I bütün ilişki sınıflarını katman katman işler; tek bir kesin yerleşim garanti etmez.

### Metot II

1. En çok A ilişkisi olan ilk bölümü seç. E, sonra I sayısıyla bağ çöz.
2. İlk bölümle A ilişkili ikinci bölümü seç.
3. Her aday için mevcut yerleşimdeki bölümlerle ilişki harflerini çıkar.
4. Harfleri önem sırasına göre sırala ve imzaları karşılaştır.
5. Adayı en önemli ilişkileri sağlayacak konuma ekle; bütün bölümler bitene kadar tekrarla.

İki yerleşik bölüm varken kaynak önceliği:

$$AA>AE>AI>A*>EE>EI>E*>II>I*$$

Buradaki `*`, O veya U'dur. Üç yerleşik bölümde aynı mantık `AAA, AAE, AAI, AA*, AEE, AEI, ...` diye genişler.

> [!warning] X kontrolü
> Kaynak sıralama listesi pozitif yakınlıkları öne çıkarır. X ilişkili bir adayın fiziksel konumu ayrıca kontrol edilmelidir; iyi bir imza X komşuluğunu meşrulaştırmaz.

### Alanı birim kareye dönüştürme

Birim şablon alanı $a_0$ ise:

$$
n_i=\left\lceil\frac{A_i}{a_0}\right\rceil
$$

Tam bölünebilen kaynak örneğinde tavana yuvarlama görünmez; gerçek soruda eksik alan yaratmamak için yukarı yuvarlanır.

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF07, slayt 71-81
> Yedi bölümün REL çalışma tablosu aşağıdadır. Metot II yerleştirme sırasını bulun ve alanları şablon sayısına çevirin.

| REL | D1 | D2 | D3 | D4 | D5 | D6 | D7 |
|---|---|---|---|---|---|---|---|
| A |  |  |  |  | 6 | 5 |  |
| E | 2 | 1-4 |  | 2 |  | 7 | 6 |
| I | 4 | 5-6 |  | 1-5 | 2-4-7 | 2 | 5 |
| O | 3-5 |  | 1-6 |  | 1 | 3 |  |
| U | 6-7 | 3-7 | 2-4-5-7 | 3-6-7 | 3 | 1-4 | 1-2-3-4 |
| X |  |  |  |  |  |  |  |

1. A ilişkisi yalnız D5-D6 çiftindedir. D5 ve D6'nın A sayısı eşittir; D6'nın E ilişkisi D7 ile olduğundan kaynak D6'yı ilk seçer.
2. D6 ile A ilişkili D5 ikinci seçilir.
3. D7'nin D6-D5 ilişkileri E-I olduğundan D7 seçilir.
4. Kaynak sıralama karşılaştırmasıyla D2 (`II*`) seçilir.
5. Sonraki adaylar D4 (`EI**`), D1 (`EI***`) ve D3 olur.

$$
\boxed{6-5-7-2-4-1-3}
$$

Alan ve şablon sayıları:

| Bölüm | Alan (ft²) | Birim kare sayısı |
|---|---:|---:|
| D1 | 12.000 | 6 |
| D2 | 8.000 | 4 |
| D3 | 6.000 | 3 |
| D4 | 12.000 | 6 |
| D5 | 8.000 | 4 |
| D6 | 12.000 | 6 |
| D7 | 12.000 | 6 |

Buradan kaynak örneğin birim şablon alanı $a_0=2.000$ ft²'dir. Toplam $35$ birim kare gerekir.

> [!important]
> Yerleştirme sırası tek başına geometrik plan değildir. Sıradaki her bölüm, güçlü ilişkilerine yakın ve varsa X ilişkilerinden uzak olacak biçimde konumlandırılır; sonra alan şablonlarıyla birkaç blok alternatif geliştirilir.

### Öz-açıklama

1. D6 neden D5'ten önce seçildi?
2. `EI` imzası ne anlatır?
3. 7.000 ft² alan, 2.000 ft² birim şablonla kaç kare ister?

## 3 - Kademeli örnek

> [!question]
> İlk bölüm P'dir. Q'nun P ile ilişkisi A, R'nin E, S'nin I olsun. Q yerleştirildikten sonra R'nin `(E,E)`, S'nin `(I,A)` ilişkisi vardır.
>
> 1. İkinci bölüm __ seçilir.
> 2. Üçüncü aday imzaları: R=`__`, S=`__`.
> 3. Kaynak önceliğiyle üçüncü bölüm __ olur.

> [!answer]- Tam çözüm
> Q, P ile A ilişkili olduğu için ikincidir. R=`EE`, S=`AI` olur. `AI>EE` olduğundan S üçüncü seçilir.

## 4 - Bağımsız sorular

### L1 - Çalışma tablosu

> [!question]
> İlişkiler: 1-2=A, 1-3=E, 1-4=U, 2-3=I, 2-4=X, 3-4=O. Her bölüm için A/E/I/O/U/X satırlarına diğer bölüm numaralarını yaz.

> [!answer]- Çözüm
> | REL | D1 | D2 | D3 | D4 |
> |---|---|---|---|---|
> | A | 2 | 1 |  |  |
> | E | 3 |  | 1 |  |
> | I |  | 3 | 2 |  |
> | O |  |  | 4 | 3 |
> | U | 4 |  |  | 1 |
> | X |  | 4 |  | 2 |

### L2 - Alan şablonu

> [!question]
> Bölüm alanları 5.000, 7.500 ve 10.100 m²; birim kare 2.500 m²'dir. Gerekli kare sayılarını ve ayrılan toplam alanı bulun.

> [!answer]- Çözüm
> Kare sayıları $2,3,5$; toplam 10 karedir. Ayrılan alan 25.000 m², gerçek ihtiyaç 22.600 m², şablon fazlası 2.400 m²'dir.

### L3 - Yöntemi ve kısıtı seç

> [!question]
> İki adayın pozitif ilişki imzaları aynı, fakat birinin yerleştirilmiş komşulardan biriyle X ilişkisi var. Seçim nasıl yapılmalıdır?

> [!answer]- Çözüm
> X ilişkisi ayrıca kontrol edilir. X komşuluğundan kaçınabilen aday/konum tercih edilir; mümkün değilse alternatif geometri veya bağ çözme kuralı gerekir. X'i U gibi yıldız kabul etmek yanlıştır.

## 5 - Çıkış bileti

1. Metot I ile Metot II'nin temel farkını yaz.
2. `AE` ve `EE` adaylarından hangisi önceliklidir?
3. X ilişkisi sıralamada nasıl ele alınır?
4. Alan neden yukarı yuvarlanır?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Kaynak sıra üretimi |  |  |  |
| D3 |  | Alan şablonu + X tuzağı |  |  |  |
| D7 |  | HF08B ile karma kurma |  |  |  |
| D14 |  | Yeni REL tablosu |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| Harfleri rastgele sayısallaştırmak | Kaynak yöntem öncelik dizisi kullanır | A-E-I-O-U imzası yaz |
| X'i normal düşük yakınlık saymak | X kaçınılması gereken ilişkidir | Ayrı X kontrol sütunu aç |
| Sırayı nihai plan sanmak | Geometri ve alan henüz yoktur | Alan şablonuyla alternatif çiz |
| Alanı aşağı yuvarlamak | Yetersiz alan üretir | Birim kare sayısında tavan kullan |

## Kaynaklar

- [[HF7-P7-Yerlesim Tasarımı I-2025.pptx|Ders sunumu]], slayt 61-81
- [[05 Kaynaklar/MarkItDown/HF07 - Ham|HF07 ham metni]], yaklaşık satır 913-1235
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]

