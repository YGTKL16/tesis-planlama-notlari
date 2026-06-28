---
hafta: 5
konu: küme tanılama, maliyet analizi ve Hollier sıralama
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, kume-tanilama, maliyet-analizi, hollier]
kaynak: HF05 slayt 35-66
---

# HF05B - Küme Maliyet Analizi ve Hollier

> [!summary] Bir cümlede
> Küme tanılama bağlantılı makine-parça bileşenlerini, maliyet analizi kapasite sınırında değerli parça gruplarını, Hollier ise hücre içindeki makine sırasını belirler.

## Öğrenme hedefleri
- [ ] Makine-parça grafiğinin bağlantılı bileşenlerinden hücre çıkarabilirim.
- [ ] Maliyet önceliği ve makine sınırıyla parça kabul/istisna kararı verebilirim.
- [ ] Hollier geliş/gidiş oranlarını hesaplayıp sıra kurabilirim.
- [ ] İleri sıralı, atlamalı ve geri akış yüzdelerini hesaplayabilirim.

## 0 - Soğuk başlangıç
> [!question]
> Bir makinenin gidiş toplamı 45, geliş toplamı 15 ise Hollier oranı nedir ve akışın hangi tarafına yakındır?
> [!answer]- Yanıt
> $45/15=3$; yüksek oran nedeniyle sıranın başına yakındır.

## 1 - Öğreten not
### Küme tanılama
Makine ve parçaları iki düğüm türü olan bir grafik gibi düşün. Bir satırdan başla; 1'ler üzerinden parçalara, o parçaların 1'leri üzerinden makinelere geç. Yeni düğüm kalmayana dek oluşan bağlantılı bileşen bir hücredir.

### Maliyet analizi
1. En yüksek maliyetli parçadan başla.
2. Gerektirdiği makineleri ve bağlantılı aday parçaları bul.
3. Adayları maliyet önceliğiyle eklerken farklı makine sayısını izle.
4. Makine üst sınırı aşılırsa aday istisnai parçadır; hücreye alınmaz/fason düşünülebilir.
5. Hücreyi ve istisnaları çıkar, kalan matrisle tekrarla.

> [!warning]
> Makine sınırı, matristeki 1 sayısı değil hücredeki **farklı makine** sayısıdır.

### Hollier
From-to matrisinde:
$$G_i=\sum_j f_{ij},\qquad A_i=\sum_j f_{ji},\qquad r_i=\frac{G_i}{A_i}$$

$r_i$ büyükten küçüğe sıralanır. $A_i=0,G_i>0$ ise oran $\infty$ ve makine başa gelir. Eşitlikte kaynak kuralı: gelen değeri yüksek olan öne alınır.

Bir sıra belirlendikten sonra hareketler:
- **İleri sıralı:** hemen sağdaki makineye,
- **Atlamalı:** sağa, fakat arada en az bir makine atlayarak,
- **Geri:** soldaki herhangi bir makineye.

Her yüzde $100\times kategori\ akışı/toplam\ hücre\ içi\ akış$tır.

## 2 - Kaynak örneği: maliyet analizi
> [!example] Kaynak: HF05, slayt 48-59
> En yüksek maliyetli P3=70 ile başlanır; hücre üst sınırı 4 makinedir. Kaynak prosedürü sonunda:

- Hücre 1: P2,P3,P6,P7; M1,M4,M7
- Hücre 2: P5,P8,P10,P11; M2,M3,M5,M6
- İstisnai parçalar: P1,P4,P9

Hücre 1'de 3, Hücre 2'de 4 farklı makine vardır; ikisi de sınırı aşmaz. Kaynak ara slaytlarındaki çizgi yayılımı düz metinde tamamen temsil edilmediğinden kabul zinciri görsel prosedür olarak izlenmelidir.

## 3 - Tam çözümlü kaynak örneği: Hollier
> [!example] Kaynak: HF05, slayt 63-66; matris PPTX görselinden okundu

| From/To | 1 | 2 | 3 | 4 | Gidiş | Geliş | Oran |
|---|---:|---:|---:|---:|---:|---:|---:|
| 1 | 0 | 5 | 0 | 25 | 30 | 50 | 0,60 |
| 2 | 30 | 0 | 0 | 15 | 45 | 45 | 1,00 |
| 3 | 10 | 40 | 0 | 0 | 50 | 0 | $\infty$ |
| 4 | 10 | 0 | 0 | 0 | 10 | 40 | 0,25 |

Azalan oranla sıra `3-2-1-4`.

Bu sırada:
- İleri sıralı: $3\to2=40$, $2\to1=30$, $1\to4=25$; toplam 95.
- Atlamalı: $3\to1=10$, $2\to4=15$; toplam 25.
- Geri: $1\to2=5$, $4\to1=10$; toplam 15.

$$T=95+25+15=135$$
$$p_s=95/135=70{,}37\%,\quad p_a=18{,}52\%,\quad p_g=11{,}11\%$$

Yuvarlanmış yüzdeler %70,4 + %18,5 + %11,1 = %100,0.

## 4 - Kademeli örnek
> [!question]
> Üç makine için gidiş/geliş toplamları A:30/10, B:20/20, C:10/30.
> 1. Oranlar $\_\_,\_\_,\_\_$.
> 2. Hollier sırası $\_\_-\_\_-\_\_$.
> [!answer]- Çözüm
> Oranlar 3, 1, 1/3; sıra A-B-C.

## 5 - Bağımsız sorular
### L1
> [!question]
> Bir hücre için aday parçaların maliyetleri 40,25,12; gereken makine kümeleri {1,2}, {2,3}, {4,5}; sınır 3. Maliyet sırasıyla hangi parçalar kabul edilir?
> [!answer]- Çözüm
> İlk parça {1,2}, ikinci eklenince {1,2,3}: kabul. Üçüncü {4,5} ekler ve toplam 5 olur: istisna.

### L2
> [!question]
> Oranlar M1=0,5; M2=$\infty$; M3=2; M4=1 ise sıra?
> [!answer]- Çözüm
> M2-M3-M4-M1.

### L3
> [!question]
> Toplam 200 hareketin 130'u ileri sıralı, 50'si atlamalı, 20'si geri. Yüzdeleri bulun.
> [!answer]- Çözüm
> %65, %25, %10.

## 6 - Çıkış bileti
1. Küme tanılamanın “bağlantılı bileşen” mantığını açıkla.
2. Hollier oranının pay ve paydasını yaz.
3. İleri sıralı ile atlamalı hareketi ayır.

## 7 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kaynak + kademeli |  |  |  |
| D1 |  | Maliyetli hücre |  |  |  |
| D3 |  | Hollier oranı |  |  |  |
| D7 |  | Yüzde sınıflama |  |  |  |
| D14 |  | Tam karma soru |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| 1'leri makine saymak | Aynı makine birçok parçada tekrar eder | Makine kümesinin birleşimini al |
| Geliş/gidişi ters bölmek | Sıra tersine döner | Satır=gidiş, sütun=geliş |
| Her sağ hareketi sıralı saymak | Makine atlanırsa atlamalıdır | Konum farkını kontrol et |

## Kaynaklar
- [[HF5-P5-Akış, Alan ve Etkinlik İlişkileri I 2025.pptx|HF05 sunumu]], slayt 35-66
- [[05 Kaynaklar/MarkItDown/HF05 - Ham|HF05 ham metni]], satır 426-1008
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
