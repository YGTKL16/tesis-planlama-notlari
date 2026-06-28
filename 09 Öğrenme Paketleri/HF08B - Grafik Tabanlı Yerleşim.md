---
hafta: 8
konu: ağırlıklı düzlemsel grafikle yerleşim kurma
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, grafik-tabanlı, komşuluk, kurma-algoritması]
kaynak: HF08 slayt 28-42
---

# HF08B - Grafik Tabanlı Yerleşim

> [!summary] Bir cümlede
> Grafik tabanlı yöntem, yüksek ağırlıklı bölüm ilişkilerini kesişmeyen kenarlarla komşuluğa dönüştürür ve elde edilen düzlemsel grafiği blok yerleşime çevirir.

## Öğrenme hedefleri

- [ ] İlişki şemasını düğüm-kenar-ağırlık gösterimine çevirebilirim.
- [ ] Başlangıç çiftini ve sonraki düğümü ağırlık toplamıyla seçebilirim.
- [ ] Bir yüz için aday ekleme puanı hesaplayabilirim.
- [ ] Düzlemsellik, yüz ve blok komşuluğu kavramlarını ayırabilirim.

## 0 - Soğuk başlangıç

> [!question]
> En ağır kenar AB=20'dir. Üçüncü aday C'nin A ve B ile toplamı 16, D'nin toplamı 23'tür. Hangisi seçilir? D'yi ekleyen kenarlar kesişiyorsa karar değişir mi?

> [!answer]- Beklenen açıklama
> Önce D seçilir; ancak grafik kesişmeden çizilemiyorsa bu ekleme uygulanabilir değildir. Ağırlık kadar düzlemsellik de zorunludur.

## 1 - Öğreten not

### Temel dil

| Kavram | Anlam |
|---|---|
| Düğüm/köşe | bölüm veya faaliyet |
| Kenar/ayrıt | sağlanması istenen komşuluk |
| Ağırlık $w_{ij}$ | komşuluğun değeri/önemi |
| Yüz | kenarlarla çevrili bölge; dış bölge de harici yüzdür |
| Düzlemsel grafik | kenarlar düğüm dışında kesişmeden çizilebilir |

Komşuluk skoru:

$$
S(G)=\sum_{(i,j)\in E(G)}w_{ij}
$$

Amaç, uygulanabilir düzlemsel grafikte yüksek ağırlıklı kenarları koruyarak $S(G)$'yi büyütmektir.

### Kurma algoritması

1. En büyük ağırlıklı bölüm çiftini seç.
2. Bu iki düğüme toplam ağırlığı en büyük üçüncü düğümü ekle:

$$s_k=w_{ka}+w_{kb}$$

3. Oluşan yüzlerden birine eklenecek düğüm için yüz puanı hesapla:

$$s(k,F)=\sum_{i\in \partial F}w_{ki}
$$

4. En yüksek uygulanabilir puanı veren düğüm-yüz seçimini yap.
5. Kenarların kesişmediğini kontrol ederek bütün düğümleri ekle.
6. Bağlı düğümleri ortak sınır paylaşacak biçimde blok plana dönüştür.

> [!warning] Her çizgi duvar olamaz
> Nihai blok planda bir kenar bir komşuluk sınırını temsil eder. Noktasal/köşe teması kenarı sağlamaz; alan ve şekil eklenince bazı grafik komşuluklarını aynı anda gerçekleştirmek zor olabilir.

### Yöntemin sınırı

Yalnız komşulukları değerlendirir; gerçek mesafeyi, ortak sınır uzunluğunu, bölüm alanını ve koridor rotasını doğrudan puanlamaz. Bu nedenle grafik, nihai ayrıntılı plan değil bir kurma aracıdır.

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF08, slayt 36-41
> Beş bölüm arasındaki ağırlıklar aşağıdadır. Grafik tabanlı yöntemle ekleme sırasını ve nihai komşuluk skorunu bulun.

| Çift | 1-2 | 1-3 | 1-4 | 1-5 | 2-3 | 2-4 | 2-5 | 3-4 | 3-5 | 4-5 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| $w$ | 9 | 8 | 10 | 0 | 12 | 13 | 7 | 20 | 0 | 2 |

### Adım 1 - En ağır çift

$$w_{34}=20$$

Başlangıç düğümleri 3 ve 4'tür.

### Adım 2 - Üçüncü düğüm

$$s_1=w_{13}+w_{14}=8+10=18$$
$$s_2=w_{23}+w_{24}=12+13=25$$
$$s_5=w_{53}+w_{54}=0+2=2$$

Düğüm 2 seçilir; 2-3-4 üçgen yüzü oluşur.

### Adım 3 - Dördüncü düğüm

Yüz sınırı `{2,3,4}` için:

$$s(1,F)=9+8+10=27$$
$$s(5,F)=7+0+2=9$$

Düğüm 1 seçilir ve yüz içine eklenir.

### Adım 4 - Son düğüm

Düğüm 5, en iyi uygulanabilir yüz olan `{1,2,4}` içine eklenir:

$$s(5,F)=w_{15}+w_{25}+w_{45}=0+7+2=9$$

Nihai grafikte sıfır ağırlıklı 1-5 kenarı topoloji için kullanılır; sekiz pozitif kenarın toplamı şöyledir:

$$S=9+8+10+12+13+7+20+2=81$$

> [!success] Sonuç
> Kaynak blok diyagramının toplam pozitif komşuluk ağırlığı 81'dir. Ekleme sırası çekirdek `3-4`, sonra `2`, `1`, `5` şeklindedir.

### Öz-açıklama

1. Düğüm 2 neden 1'den önce eklendi?
2. Düğüm 1'in yüz puanı neden 27'dir?
3. 1-5 ağırlığı sıfır olduğu halde çizgide görünmesi skoru değiştirir mi?

## 3 - Kademeli örnek

> [!question]
> Dört düğüm için $w_{AB}=10$, $w_{AC}=4$, $w_{AD}=1$, $w_{BC}=8$, $w_{BD}=6$, $w_{CD}=3$.
>
> 1. Başlangıç çifti __.
> 2. $s_C=4+\_=$ __; $s_D=1+\_=$ __.
> 3. Üçüncü düğüm __.
> 4. Son düğümün yüz puanı __.

> [!answer]- Tam çözüm
> Başlangıç AB'dir. $s_C=4+8=12$, $s_D=1+6=7$; C seçilir. D'nin ABC yüz puanı $1+6+3=10$'dur. K4 düzlemsel çizilebildiğinden toplam skor $10+4+1+8+6+3=32$ olur.

## 4 - Bağımsız sorular

### L1 - Üçüncü düğüm seçimi

> [!question]
> En ağır çift 2-5'tir. Aday 1'in bu çifte ağırlıkları 6 ve 7; aday 3'ün 10 ve 1; aday 4'ün 4 ve 12'dir. Hangisi seçilir?

> [!answer]- Çözüm
> Toplamlar 13, 11 ve 16'dır. Düğüm 4 seçilir.

### L2 - Yüz seçimi

> [!question]
> Aday X için iki yüzün sınırları $F_1={A,B,C}$, $F_2={A,C,D}$'dir. Ağırlıklar $w_{XA}=5$, $w_{XB}=9$, $w_{XC}=4$, $w_{XD}=8$ olsun. Her iki ekleme düzlemselse hangi yüz seçilir ve katkı farkı nedir?

> [!answer]- Çözüm
> $s(X,F_1)=5+9+4=18$, $s(X,F_2)=5+4+8=17$. $F_1$ seçilir; skor katkısı 1 daha büyüktür.

### L3 - Yöntemi seç

> [!question]
> Bölüm alanları ve koridor mesafeleri kritik, fakat ilişki ağırlıkları yok. Grafik tabanlı yöntem tek başına yeterli midir?

> [!answer]- Çözüm
> Hayır. Grafik yöntemi komşuluk ağırlığı ister ve gerçek mesafe/alanı doğrudan değerlendirmez. Akış-mesafe maliyeti ve alan kısıtlı blok tasarımı gerekir.

## 5 - Çıkış bileti

1. Düğüm, kenar ve yüzü tanımla.
2. Üçüncü düğüm puanını yaz.
3. Yüz ekleme puanını yaz.
4. Düzlemsellik neden zorunludur?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Kaynak ekleme sırası |  |  |  |
| D3 |  | Yüz seçimi |  |  |  |
| D7 |  | HF07C ile karma kurma |  |  |  |
| D14 |  | HF08A-C yöntem seçimi |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| Tek bir kenar ağırlığına bakmak | Yeni düğüm bir yüzle ilişki kurar | Sınırdaki ağırlıkları topla |
| Kesişen kenarları kabul etmek | Blok komşuluğuna çevrilemez | Her eklemede düzlemsellik kontrolü yap |
| Köşe temasını kenar sanmak | Ortak duvar oluşmaz | Pozitif sınır uzunluğu ara |
| Grafiği ayrıntılı plan sanmak | Alan ve mesafe henüz işlenmedi | Sonra blok/alan doğrulaması yap |

## Kaynaklar

- [[HF8-P8-Yerlesim Tasarımı II-2025.pptx|Ders sunumu]], slayt 28-42
- [[05 Kaynaklar/MarkItDown/HF08 - Ham|HF08 ham metni]], yaklaşık satır 454-638
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
