
# Deneme 01 - Hesap Odaklı

> [!danger] Kurallar
> 75 dakika. Notlar kapalı. Her soruda verilen, istenen, yöntem, işlem ve karar cümlesi bulunmalı. Çözümleri sınav bitmeden açma.

## S1 - Yöntem seçimi · 10 puan

Aşağıdaki ifadeleri uygun yöntem ailesiyle eşleştirin:

1. En uzaktaki müşteriye erişim süresini küçültmek.
2. 0-1 makine-parça matrisini blok köşegen yapmak.
3. Mevcut yerleşimde bölüm çiftlerini takas etmek.
4. Sabit açma maliyeti olan aday depolar arasından seçim yapmak.
5. Nitel yakınlık tablosundan başlangıç yerleşimi kurmak.

## S2 - Fire ve kaynak · 15 puan

İki seri operasyondan sonra 900 tam sağlam ürün gereklidir. Fire oranları süreç sırasıyla %4 ve %2'dir.

1. Sürekli ilk giriş miktarını bulun.
2. Her operasyonda tamsayı zorunluysa geriye doğru planı bulun.
3. İlk operasyonda süre 3 dk/parça, vardiya 480 dk, performans %90 ve güvenilirlik %85 ise gereken makine sayısını bulun.

## S3 - Rassal üretim kararı · 15 puan

Tam 4 sağlam ürün teslim edilirse 120.000 TL alınacaktır; eksik parti kabul edilmez. Bir üretimin maliyeti 15.000 TL, sağlam çıkma olasılığı %90'dır. $Q=4,5,6$ adaylarının beklenen kârlarını bulun ve karar verin.

## S4 - Hücre içi sıra · 15 puan

| From/To | 1 | 2 | 3 | 4 |
|---|---:|---:|---:|---:|
| 1 | 0 | 5 | 0 | 25 |
| 2 | 30 | 0 | 0 | 15 |
| 3 | 10 | 40 | 0 | 0 |
| 4 | 10 | 0 | 0 | 0 |

Gidiş/geliş oranlarıyla makine sırasını bulun. Seçilen sırada ileri sıralı, atlamalı ve geri akış yüzdelerini hesaplayın.

## S5 - Yerleşim seçimi · 15 puan

Konum uzaklıkları $d_{AB}=2$, $d_{AC}=3$, $d_{BC}=5$; birleşik bölüm akışları $F_{12}=2$, $F_{13}=3$, $F_{23}=10$'dur. Birim maliyet 1.

1. Başlangıç `1A,2B,3C` maliyetini bulun.
2. Altı olası atama arasındaki en iyi maliyeti ve atamayı bulun.

## S6 - Toplam dikdoğrusal maliyet · 15 puan

| Nokta | Koordinat | Ağırlık |
|---:|---:|---:|
| 1 | $(1,1)$ | 5 |
| 2 | $(5,2)$ | 6 |
| 3 | $(2,8)$ | 2 |
| 4 | $(4,4)$ | 4 |
| 5 | $(8,6)$ | 8 |

Optimum tek tesis konumunu ve minimum toplam ağırlıklı uzaklığı bulun.

## S7 - Açma-atama yorumu · 15 puan

B ve C depoları açıkken beş müşterinin hizmet maliyetleri sırasıyla 500, 200, 1.200, 700, 800 TL'dir. D deposunun sabit maliyeti 3.000 TL'dir ve yalnız müşteri 3'ün hizmet maliyetini 300 TL'ye düşürmektedir. D açılmalı mı? Modelde $x_{ij}\le y_i$ kısıtının anlamını da açıklayın.

---

## Çözümler

> [!answer]- S1
> 1 minimax; 2 DCA/ROC; 3 ikili değişim/CRAFT; 4 kesikli açma-atama; 5 CORELAP/ALDEP.

> [!answer]- S2
> Sürekli: $900/(0{,}96\cdot0{,}98)=956{,}63$. Geriye tamsayı: $\lceil900/0{,}98\rceil=919$, $\lceil919/0{,}96\rceil=958$. Makine: $F=3(958)/(0{,}90\cdot480\cdot0{,}85)=7{,}827$, yani 8 makine.

> [!answer]- S3
> Beklenen kârlar: Q4=18.732 TL; Q5=35.224,80 TL; Q6=28.098 TL. Karar Q=5.

> [!answer]- S4
> Oranlar 0,60; 1; $\infty$; 0,25. Sıra 3-2-1-4. Toplam 135; ileri 95=%70,37, atlamalı 25=%18,52, geri 15=%11,11.

> [!answer]- S5
> Başlangıç $2(2)+3(3)+10(5)=63$. En iyi atama `3A,2B,1C` ve maliyet $10(2)+3(3)+2(5)=39$; simetrik ayna atama da aynı değeri verebilir.

> [!answer]- S6
> Her eksende ağırlıklı medyan: $(5,4)$. Amaç değeri $105$.

> [!answer]- S7
> Brüt tasarruf $1.200-300=900$; net tasarruf $900-3.000=-2.100$, D açılmaz. $x_{ij}\le y_i$, kapalı tesise müşteri atanmasını engeller.

## Sonuç kaydı

| Tarih | Puan / 100 | Süre | YÖN | MOD | VER | İŞL | BİR | YUV | YOR |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
|  |  |  |  |  |  |  |  |  |  |

Yanlışları 00 Pano/Çalışma Takibi#Hata günlüğü|Hata Günlüğü sayfasına aktar.
