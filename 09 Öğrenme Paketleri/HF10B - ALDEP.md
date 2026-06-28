---
hafta: 10
konu: ALDEP rassal bölüm seçimi ve dikey süpürme
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, algoritma/aldep]
kaynak: HF10 slayt 44-54
---

# HF10B - ALDEP

> [!summary] Bir cümlede
> ALDEP, eşik üstü yakınlıkları izleyerek rassal bölüm sıraları üretir, alanı dikey süpürmeyle doldurur ve alternatifleri komşuluk puanıyla karşılaştırır.

## Öğrenme hedefleri
- [ ] Minimum ilişki eşiğine göre aday bölüm seçebilirim.
- [ ] Rassallığın hangi adımlarda devreye girdiğini açıklayabilirim.
- [ ] Alanları birim kare sayısına dönüştürebilirim.
- [ ] Komşu çiftlerden toplam puan hesaplayabilirim.

## 0 - Soğuk başlangıç
> [!question]
> Minimum kabul E ise I ilişkili aday kabul edilir mi? E veya A ilişkili hiçbir aday yoksa ne olur?
> [!answer]- Yanıt
> I kabul edilmez. Kalan bölümlerden rassal seçim yapılır.

## 1 - Öğreten not
### Bölüm seçimi
1. İlk bölümü rassal seç.
2. Son seçilen bölümle minimum eşik kadar güçlü ilişkisi olan yerleşmemiş adayları bul.
3. Aday varsa bunlardan seçim yap; yoksa kalanlardan rassal seç.
4. Tüm bölümler seçilene kadar sürdür.

Eşik E ise kabul kümesi A ve E'dir. Adayların kendi arasındaki seçim kuralı soruda/yazılımda verilmelidir; ALDEP'in amacı aynı veriden çok sayıda alternatif üretmektir.

### Yerleştirme
- Sol üstten başla.
- Kullanıcının verdiği süpürme genişliğiyle aşağı doğru ilerle.
- Vektördeki bölüm gereken birim kare sayısını doldurunca sıradakine geç.
- Çok katlı yerleşim üretebilir.

### Değerlendirme
$$Z=\sum_{i<j}w_{ij}a_{ij}$$
$a_{ij}=1$ ise bölümler komşudur. Ağırlık vektörünü sorudan al; kaynak örneği A=64,E=16,I=4,O=1,U=0,X=-1024 kullanır.

> [!warning]
> ALDEP deterministik “tek doğru sıra” üretmez. Aynı girdi farklı rassal başlangıçlarla farklı vektör ve puan verir.

## 2 - Tam çözümlü kaynak örneği
> [!example] Kaynak: HF10, slayt 48-54
> $10\times18$ tesis, süpürme genişliği 2, minimum E. İlk vektör `4-2-1-6-5-7-3`, kaynak komşuluk puanı 120. Alternatif vektör `2-1-4-5-6-7-3`.

Alternatif için slayt komşu çiftleri verir:

| Çift | İlişki | Puan |
|---|---|---:|
| 2-1 | E | 16 |
| 1-4 | I | 4 |
| 4-5 | I | 4 |
| 5-6 | A | 64 |
| 6-7 | E | 16 |
| 7-3 | U | 0 |

$$Z=16+4+4+64+16+0=104$$

104 bağımsız toplamayla doğrulandı; ilk alternatifin kaynakta raporlanan 120 puanı daha yüksektir. Yine de nihai seçim gerçek kısıtlar açısından planlamacıya aittir.

Alan kontrolü: birim kare sayıları 30+20+15+30+20+30+30=175'tir; tesis 180 karelikse 5 kare boş/ayrılmış alan kalır.

## 3 - Kademeli örnek
> [!question]
> A=64,E=16,I=4,O=1,U=0,X=-1024. Bir yerleşimin komşu çiftleri A-B:A, B-C:E, C-D:U, D-E:I.
> $$Z=\_\_+\_\_+\_\_+\_\_=\_\_$$
> [!answer]- Çözüm
> $Z=64+16+0+4=84$.

## 4 - Bağımsız sorular
### L1
> [!question]
> Minimum I iken A, E, I, O adaylarından hangileri kabul kümesindedir?
> [!answer]- Çözüm
> A, E ve I.

### L2
> [!question]
> $600\,m^2$ alan, her grid $20\,m^2$ ise kaç birim kare gerekir?
> [!answer]- Çözüm
> $600/20=30$ kare.

### L3
> [!question]
> Yerleşim X'in puanı 140, Y'nin 128; Y sabit makineleri koruyor, X korumuyor. Hangisi seçilir?
> [!answer]- Çözüm
> Sabit makine zorunluysa Y uygulanabilir tek adaydır. Sezgisel puan gerçek kısıtların yerine geçmez.

## 5 - Çıkış bileti
1. ALDEP'te rassallık hangi iki durumda görülür?
2. Süpürme genişliği neyi değiştirir?
3. Neden tek çalıştırma yeterli değildir?

## 6 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kaynak + kademeli |  |  |  |
| D1 |  | Eşikle sıra |  |  |  |
| D3 |  | Süpürme + puan |  |  |  |
| D7 |  | ALDEP/CORELAP |  |  |  |
| D14 |  | Kısıtlı seçim |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| Eşik E iken I'yi kabul etmek | I daha düşük önemlidir | Kabul kümesini başta yaz |
| Bir vektörü optimal sanmak | Algoritma rassal/sezgiseldir | Birden çok alternatif üret |
| X'i küçük ceza sanmak | Kaynak örneğinde -1024 | Ağırlık vektörünü aynen geçir |

## Kaynaklar
- [[HF10-P10-Yerlesim Tasarımı IV-2025.pptx|HF10 sunumu]], slayt 44-54
- [[05 Kaynaklar/MarkItDown/HF10 - Ham|HF10 ham metni]], satır 536-742
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
