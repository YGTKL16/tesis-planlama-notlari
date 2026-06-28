---
hafta: 9
konu: MCRAFT süpürme paterni ve ikili değişim
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, algoritma/mcraft]
kaynak: HF09 slayt 5-16
---

# HF09A - MCRAFT

> [!summary] Bir cümlede
> MCRAFT, bir bölüm sırasını eş genişlikli bantlarda yılan biçimli süpürmeyle yerleşime çevirir ve bölüm çiftlerini değiştirerek akış-uzaklık maliyetini düşürür.

## Öğrenme hedefleri
- [ ] Bir yerleşimden süpürme yönünde bölüm vektörü çıkarabilirim.
- [ ] Vektör, alan ve bant genişliğinden blok uzunluklarını bulabilirim.
- [ ] Bir ikili değişimin yeni vektörünü ve maliyet etkisini hesaplayabilirim.
- [ ] MCRAFT ile CRAFT'ın değişim kısıtlarını ayırabilirim.

## 0 - Soğuk başlangıç
> [!question]
> Bir vektör `A-C-D-B-E` ise A ile E değiştirildiğinde yeni vektör nedir? Bu vektör tek başına değişimin iyi olduğunu kanıtlar mı?
> [!answer]- Yanıt
> `E-C-D-B-A` olur. Hayır; yeni yerleşim üretilip $\sum f_{ij}c_{ij}d_{ij}$ yeniden hesaplanmalıdır.

## 1 - Öğreten not
### Sorudan tanı
- Başlangıç yerleşimi veya bölüm vektörü vardır.
- Tesis dikdörtgen, bant sayısı verilmiş ve bantlar eş genişliktedir.
- Bitişik/eş alanlı olmayan bölümler de değiştirilebilir.

### Kurma adımları
1. Tesis yüksekliği $H$ ve bant sayısı $b$ için bant genişliğini bul: $w=H/b$.
2. Başlangıç yerleşimini sol üstten başlayıp satırlarda ters yönlere giden yılan yolu boyunca oku.
3. Vektördeki sırayı, her bölüm gereken hücre/alanı doldurana dek bantlara yerleştir.
4. Aday iki bölümü vektörde değiştir; kalan bölümler yeniden süpürülür.
5. $C=\sum_{i<j}F_{ij}c_{ij}d_{ij}$ değerini karşılaştır; yalnız $\Delta C<0$ ise iyileşme vardır.

Bir bölüm tek bant içindeyse yaklaşık uzunluğu $\ell_i=A_i/w$ olur. Bant sınırını aşan bölüm sonraki banda devam edebilir; şekil yalnız bu oranla belirlenmez.

> [!warning] Temel tuzak
> MCRAFT'ta “A ile B yer değiştirsin” geometrik blokların aynen taşınması değildir. Vektör değişir, tüm yerleşim süpürme boyunca yeniden üretilir.

## 2 - Kaynak örneği ve doğrulama
> [!example] Kaynak: HF09, slayt 12-15
> Bina $20\times9=180\,m^2$, üç bant; alanlar A=30, B=45, C=51, D=39, E=15 ve kaynak vektörü `A-C-D-B-E`dir.

$$30+45+51+39+15=180\,m^2$$
$$w=9/3=3\,m$$

Alan toplamı bina alanına tam eşittir; eksik/fazla alan yoktur. Tek bantta olsalardı eşdeğer uzunluklar A=10, B=15, C=17, D=13, E=5 m olurdu. C'nin 17 m uzunluğu 20 m bandı neredeyse doldurduğu için gerçek sınırlar süpürme ve bant geçişiyle belirlenir.

> [!note] Kaynak sınırı
> Slayt 15 yerleşimi görsel olarak verir; hücre koordinatları ham metinde yoktur. Bu yüzden vektör ve alan kontrolü doğrulanmış, görsel koordinatlar yeniden uydurulmamıştır.

## 3 - Kademeli örnek
> [!question]
> $12\times6$ m binada 2 bant vardır. Alanlar P=18, Q=12, R=24, S=18 ve vektör `P-Q-R-S`tir.
> 1. $w=\_\_/\_\_=\_\_$ m.
> 2. Alan toplamını bina alanıyla karşılaştır.
> 3. Q ile S değişirse vektörü yaz.
> [!answer]- Çözüm
> $w=6/2=3$ m; alanlar $18+12+24+18=72=12(6)$ m². Yeni vektör `P-S-R-Q`dur. İyileşme kararı için iki vektörün akış-uzaklık maliyetleri gerekir.

## 4 - Bağımsız sorular
### L1
> [!question]
> $24\times12$ m tesis 4 banttır. Bant genişliği ve $36\,m^2$ bölümün tek banttaki eşdeğer uzunluğu nedir?
> [!answer]- Çözüm
> $w=12/4=3$ m; $\ell=36/3=12$ m.

### L2
> [!question]
> `1-2-3-4-5` vektöründe 2 ve 5 değiştiriliyor. Yeni vektörü yaz ve CRAFT'ta ayrıca aranabilen fakat MCRAFT'ta zorunlu olmayan iki koşulu belirt.
> [!answer]- Çözüm
> `1-5-3-4-2`. CRAFT'taki bitişiklik veya eş alan koşulları MCRAFT değişimi için zorunlu değildir.

### L3
> [!question]
> Başlangıç maliyeti 8.420, değişim sonrası 7.960 ise $\Delta C=C_{yeni}-C_{eski}$ ve karar nedir?
> [!answer]- Çözüm
> $\Delta C=7960-8420=-460$; maliyet 460 azaldığı için değişim kabul edilir.

## 5 - Çıkış bileti
1. Süpürme paterni neyi vektöre dönüştürür?
2. Bant genişliği nasıl bulunur?
3. Bölüm değişiminden sonra neden bütün yerleşim yeniden kurulur?

## 6 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Vektör çıkarma |  |  |  |
| D3 |  | Değişim + maliyet |  |  |  |
| D7 |  | MCRAFT/CRAFT seçimi |  |  |  |
| D14 |  | Karma yerleşim sorusu |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| Blokları aynen takas etmek | MCRAFT vektörü yeniden süpürür | Yeni vektörü baştan yerleştir |
| Alan toplamını kontrol etmemek | Yerleşim taşabilir/boş kalabilir | $\sum A_i=WH$ yaz |
| Negatif $\Delta C$'yi kötü sanmak | Amaç maliyeti küçültmektir | $C_{yeni}-C_{eski}$ işaretini yorumla |

## Kaynaklar
- [[HF9-P9-Yerlesim Tasarımı III-2025.pptx|HF09 sunumu]], slayt 5-16
- [[05 Kaynaklar/MarkItDown/HF09 - Ham|HF09 ham metni]], satır 38-208
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
