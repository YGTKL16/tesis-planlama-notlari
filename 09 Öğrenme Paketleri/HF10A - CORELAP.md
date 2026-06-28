---
hafta: 10
konu: CORELAP TCR, bölüm seçimi ve yerleştirme puanı
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, algoritma/corelap]
kaynak: HF10 slayt 4-43 ve 79-103
---

# HF10A - CORELAP

> [!summary] Bir cümlede
> CORELAP, ilişki kodlarını sayısallaştırıp TCR ile bölüm sırası kurar; her yeni bölümü ağırlıklı tam/yarım komşuluk puanı en yüksek konuma yerleştirir.

## Öğrenme hedefleri
- [ ] İlişki matrisinden TCR hesaplayabilirim.
- [ ] A-E-I-O-U ve X kurallarıyla seçim sırası oluşturabilirim.
- [ ] Tam ve yarım komşulukla yerleştirme puanı hesaplayabilirim.
- [ ] Bağ bozma kurallarını doğru sırada uygulayabilirim.

## 0 - Soğuk başlangıç
> [!question]
> A=125, E=25, I=5, O=1, U=0, X=-125 iken bir bölümün ilişkileri A,A,O,X,U ise TCR nedir?
> [!answer]- Yanıt
> $125+125+1-125+0=126$.

## 1 - Öğreten not
### TCR
$$TCR_i=\sum_{j\ne i}w_{ij}$$
Sayısallaştırma vektörü soruda verilen vektördür; farklı slaytlarda farklı değerler kullanılır. Kendi ağırlığını seçip kaynak ağırlığıyla karıştırma.

### Bölüm seçimi
1. En yüksek TCR ilk bölümdür. Bağda daha çok A, sonra E... ilişkisi; kaynak varyantına göre alan veya rastgele seçim kullanılır.
2. Yerleştirilmiş bölümlerle önce A ilişkili adayları ara; yoksa E, I, O sırasına in.
3. Aynı ilişki düzeyinde en yüksek TCR'yi seç.
4. X ilişkili bölümleri sona ayır; bağda en küçük TCR'yi sona bırak.

### Yerleştirme puanı
$$PR(k,p)=\sum_{j\in yerleşmiş}w_{kj}q_{jp}$$
$q=1$ tam kenar komşuluğu, $q=\alpha$ yarım/köşe komşuluğudur; kaynak örneklerinde $\alpha=0{,}5$.

En yüksek PR seçilir. Eşitlikte ortak sınır uzunluğu; hâlâ eşitse kaynakta belirtilen tarama/rasgele kural uygulanır.

> [!tip] PR hesap tricki
> Bir konuma bölüm yerleştirirken: yalnız **halihazırda yerleşmiş** bölümlere bak; henüz yerleşmemiş bölümleri say**ma**.
> - Kenar temas → $\times 1$
> - Köşe temas → $\times 0{,}5$
> - X ilişkisi → negatif ağırlık (puanı düşürür!)
>
> Kısaca: *"Yerleşmişlere bak, kenara 1, köşeye yarım, X'i eksi yaz."*

> [!warning]
> TCR “hangi bölüm sırada?”, PR “seçilen bölüm nereye?” sorusunu cevaplar. Birini diğerinin yerine kullanma.

## 2 - Tam çözümlü kaynak örneği: TCR
> [!example] Kaynak: HF10, slayt 91-92
> A=125, E=25, I=5, O=1, U=0, X=-125.

| Bölüm | İlişki özeti | TCR |
|---|---|---:|
| 1 | 2A+O+U+X | $250+1-125=126$ |
| 2 | 2A+E+I+U | $250+25+5=280$ |
| 3 | 2A+E+2X | $250+25-250=25$ |
| 4 | A+O+U+2X | $125+1-250=-124$ |
| 5 | 2A+I+O+U | $250+5+1=256$ |
| 6 | 3A+O+X | $375+1-125=251$ |

Altı değer bağımsız toplamayla doğrulandı. TCR sırası tek başına 2,5,6,1,3,4'tür; kaynak seçim algoritması da bu örnekte aynı yerleştirme sırasını verir.

## 3 - Tam çözümlü kaynak örneği: PR
> [!example] Kaynak: HF10, slayt 85-86
> Bölüm 8'in bölüm 10 ile A, bölüm 5 ile U ilişkisi var; A=10.000, U=0, $\alpha=0{,}5$.

- Yalnız 5'e tam komşu: $PR=0$.
- 5'e tam, 10'a yarım: $PR=0+10.000(0{,}5)=5.000$.
- 5'e yarım, 10'a tam: $PR=0(0{,}5)+10.000=10.000$.

En yüksek puan 10.000 olan son konum seçilir.

## 4 - Kademeli örnek
> [!question]
> K bölümü A ile tam, B ile yarım komşu olacaktır. $w_{KA}=64$, $w_{KB}=16$, $\alpha=0{,}5$.
> $$PR=\_\_(1)+\_\_(0{,}5)=\_\_$$
> [!answer]- Çözüm
> $PR=64+8=72$.

## 5 - Bağımsız sorular
### L1
> [!question]
> A=4,E=3,I=2,O=1,U=0,X=-1; ilişkileri A,E,I,U,X olan bölümün TCR'si?
> [!answer]- Çözüm
> $4+3+2+0-1=8$.

### L2
> [!question]
> Seçilmemiş P ve Q, yerleşmiş bölümle A ilişkilidir. TCR'leri 18 ve 21. Hangisi seçilir?
> [!answer]- Çözüm
> Q; ilişki düzeyi eşitken TCR büyük olan seçilir.

### L3
> [!question]
> Konum 1 için iki tam E komşuluğu, konum 2 için bir tam A ve bir yarım I var. A=64,E=16,I=4, $\alpha=0{,}5$. Karar?
> [!answer]- Çözüm
> $PR_1=32$; $PR_2=64+2=66$. Konum 2.

## 6 - Çıkış bileti
1. TCR formülünü yaz.
2. X ilişkisi seçim sırasını nasıl etkiler?
3. Tam ve yarım komşuluğun katsayıları nedir?

## 7 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kaynak + kademeli |  |  |  |
| D1 |  | TCR tablosu |  |  |  |
| D3 |  | Seçim + PR |  |  |  |
| D7 |  | CORELAP/ALDEP karma |  |  |  |
| D14 |  | Tam algoritma |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| X'i sıfır almak | İstenmeyen ilişki negatif ağırlıklıdır | Verilen ağırlık vektörünü başa yaz |
| En yüksek TCR'yi her adım seçmek | Önce mevcut yerleşimle ilişki düzeyi aranır | A→E→I→O, sonra TCR |
| Köşeyi tam komşu saymak | Kaynak yarım katsayı kullanır | $q=0{,}5$ uygula |

## Kaynaklar
- [[HF10-P10-Yerlesim Tasarımı IV-2025.pptx|HF10 sunumu]], slayt 4-43, 79-103
- [[05 Kaynaklar/MarkItDown/HF10 - Ham|HF10 ham metni]], satır 29-536 ve 1072-1529
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
