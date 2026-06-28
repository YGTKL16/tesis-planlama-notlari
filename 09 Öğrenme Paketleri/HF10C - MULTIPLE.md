---
hafta: 10
konu: MULTIPLE alan doldurma eğrisi ve bölüm değişimi
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, algoritma/multiple, cok-katli]
kaynak: HF10 slayt 55-76
---

# HF10C - MULTIPLE

> [!summary] Bir cümlede
> MULTIPLE, bölüm vektörünü bir alan doldurma eğrisi üzerinde hücrelere haritalar; bitişik olmayan bölümleri değiştirip yerleşimi yeniden kurarak uzaklık maliyetini iyileştirir.

## Öğrenme hedefleri
- [ ] Geçerli alan doldurma eğrisinin kurallarını denetleyebilirim.
- [ ] Bölüm alanlarını hücre sayılarına çevirebilirim.
- [ ] Vektörü eğri üzerinde yerleşime dönüştürebilirim.
- [ ] İkili değişim sonrası yeni vektör ve maliyet kararını bulabilirim.

## 0 - Soğuk başlangıç
> [!question]
> Her hücre $4\,m^2$ ve bölüm alanı $12\,m^2$ ise eğri boyunca kaç ardışık hücre ayrılır?
> [!answer]- Yanıt
> $12/4=3$ hücre.

## 1 - Öğreten not
### Geçerli SFC
Alan/oylum doldurma eğrisi:
1. Her kullanılabilir hücreyi tam bir kez ziyaret eder.
2. Ardışık hücreler yatay veya dikey komşudur; köşegen atlama yoktur.
3. Bir bölümün gereken hücreleri tamamlanmadan sonraki bölüme geçmez.

### Yerleşim
Hücre alanı $a_g$ ise:
$$n_i=\frac{A_i}{a_g}$$
$n_i$ tam sayı değilse grid çözünürlüğü/veri hatası açıklanmalıdır.

Vektör sırasıyla ilk bölüm $n_1$, ikinci bölüm $n_2$ ... hücreyi alır. İki bölüm değişince vektör değişir ve tüm haritalama yeniden yapılır.

### Amaç
MULTIPLE uzaklık esaslı, kurma ve geliştirme algoritmasıdır. Genel maliyet:
$$C=\sum_{i<j}F_{ij}c_{ij}d_{ij}$$
Çok katlı uygulamada $d_{ij}$ seçilen taşıma sistemi ve kat geçişlerini içermelidir; tek bir evrensel $\alpha$ formülü slaytta verilmemiştir.

> [!warning]
> MULTIPLE yalnız “çok kat formülü” değildir. Ayırt edici hesap, vektörün SFC üzerinde hücre bloklarına dönüştürülmesi ve her değişimde yeniden kurulmasıdır.

## 2 - Tam çözümlü kaynak örneği
> [!example] Kaynak: HF10, slayt 58-69
> Alanlar 1=16, 2=8, 3=4, 4=16, 5=8, 6=12 m²; vektör `1-2-3-4-5-6`. Kaynak 1 ve 5'i değiştirir: `5-2-3-4-1-6`.

Alan toplamı:
$$16+8+4+16+8+12=64\,m^2$$

Kaynak görselindeki SFC, $8\times8=64$ birim kareden oluşur. Toplam alan da 64 m² olduğundan her hücre 1 m²'dir. Hücre gereksinimleri:
$$n=(16,8,4,16,8,12),\qquad \sum n_i=64$$

Başlangıç eğri aralıkları 1:1-16, 2:17-24, 3:25-28, 4:29-44, 5:45-52, 6:53-64 olur. Değişimden sonra 5:1-8, 2:9-16, 3:17-20, 4:21-36, 1:37-52, 6:53-64 olur. Alanlar korunur, fakat merkezler ve maliyet değişebilir.

> [!note]
> Eğrinin geometrik koordinatları slayt görselindedir; ham metinde yoktur. $8\times8$ grid, hücre sayıları ve vektör aralıkları doğrudan görselle doğrulanmış, koordinatlar uydurulmamıştır.

## 3 - Kademeli örnek
> [!question]
> 12 hücreli SFC'de alan/hücre sayıları A=3, B=2, C=4, D=3 ve vektör `A-B-C-D`.
> 1. Eğri sıra aralıklarını yaz.
> 2. B ile D değişirse yeni vektör ve aralıklar nedir?
> [!answer]- Çözüm
> Başlangıç A:1-3, B:4-5, C:6-9, D:10-12. Yeni vektör `A-D-C-B`; A:1-3, D:4-6, C:7-10, B:11-12.

## 4 - Bağımsız sorular
### L1
> [!question]
> Bir SFC 20 hücreden 19'unu bir kez, birini iki kez ziyaret ediyor. Geçerli mi?
> [!answer]- Çözüm
> Hayır; her hücre tam bir kez ziyaret edilmelidir.

### L2
> [!question]
> Alanlar 18, 27, 9 m²; grid 3 m² ise hücre sayıları ve toplam nedir?
> [!answer]- Çözüm
> 6, 9, 3; toplam 18 hücre.

### L3
> [!question]
> Üç alternatif maliyet 54.200, 54.540 ve 54.900. Yalnız maliyet ve aynı uygulanabilirlik varsayımıyla karar?
> [!answer]- Çözüm
> 54.200; kaynak slayt 75'teki en düşük maliyetli alternatiftir.

## 5 - Çıkış bileti
1. Geçerli SFC'nin üç koşulunu yaz.
2. İkili değişim neden yalnız iki blok koordinatını etkilemeyebilir?
3. Uygun eğri ne zaman elle tasarlanır?

## 6 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kaynak + kademeli |  |  |  |
| D1 |  | Hücre dönüşümü |  |  |  |
| D3 |  | Vektör değişimi |  |  |  |
| D7 |  | MULTIPLE/MCRAFT |  |  |  |
| D14 |  | Çok katlı maliyet |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| Köşegen hücreye geçmek | SFC yalnız kenar komşuluğu kullanır | Her ardışık çifti kontrol et |
| Değişimde hücre sayılarını da takas etmek | Alan bölüm kimliğiyle kalır | $n_i=A_i/a_g$ tablosunu koru |
| En büyük maliyeti seçmek | Uzaklık maliyeti minimize edilir | En küçük uygulanabilir $C$ |

## Kaynaklar
- [[HF10-P10-Yerlesim Tasarımı IV-2025.pptx|HF10 sunumu]], slayt 55-76
- [[05 Kaynaklar/MarkItDown/HF10 - Ham|HF10 ham metni]], satır 742-1058
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
