---
hafta: 6
konu: MAG taşınabilirlik ölçüsü ve geliş-gidiş matrisi
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, mag, from-to, akis-siddeti]
kaynak: HF06 slayt 48-62 ve 83-85
---

# HF06A - MAG Akış Şiddeti ve From-To Matrisi

![[07 Ekler/Grafikler/from-to-matrisi.svg]]

> [!summary] Bir cümlede
> MAG farklı malzemeleri taşınabilirlik bakımından ortak ölçüye çevirir; rota üzerindeki ardışık geçişler bu eşdeğer miktarlarla yönlü from-to matrisine yazılır.

## Öğrenme hedefleri
- [ ] Hacimden A değerini interpolasyonla bulabilirim.
- [ ] B-C-D-E düzeltmeleriyle parça başına MAG hesaplayabilirim.
- [ ] Üretim ve taşıma sayısıyla dönemsel akış şiddeti bulabilirim.
- [ ] Rotalardan yönlü ve toplam akış matrisi kurabilirim.

## 0 - Soğuk başlangıç
> [!question]
> Günde 20 adet üretilen ürünün eşdeğer taşıma katsayısı 2 ve rotası A-B-C ise A→B ve B→C hücrelerine ne yazılır?
> [!answer]- Yanıt
> Her geçişe $20(2)=40$ yazılır.

## 1 - Öğreten not
### MAG
Parça başına MAG:
$$M=A\left[1+\frac14(B+C+D+E)\right]$$

- A: hacimden gelen temel MAG.
- B: yoğunluk, C: biçim, D: zarar riski, E: durum/taşıma güçlüğü düzeltmesi.
- A tablosunda tam değer yoksa doğrusal interpolasyon yapılır:
$$A=A_1+\frac{V-V_1}{V_2-V_1}(A_2-A_1)$$

Dönemsel hareket şiddeti:
$$F=M\times Q\times h$$
$Q$ üretim miktarı, $h$ aynı geçişin parça başına tekrar sayısıdır.

### From-to
Her ürün için rotadaki **ardışık yönlü çiftleri** çıkar. Ürün eşdeğer miktarını her geçişe ekle:
$$f_{ij}=\sum_p Q_p e_p n_{ijp}$$

Yönlü matris simetrik değildir. Yön önemsiz toplam akış gerekiyorsa:
$$F_{ij}=f_{ij}+f_{ji}\quad(i<j)$$

> [!warning]
> A-C-B rotası A→C ve C→B üretir; A→B üretmez. Rota içindeki ardışık olmayan çiftleri ekleme.

## 2 - Tam çözümlü kaynak örneği: MAG
> [!example] Kaynak: HF06, slayt 55-56
> Çap 6 cm, yükseklik 17 cm silindir; $\pi=3$. B=2,C=1,D=-1,E=1; yılda 50.000 adet.

Yarıçap 3 cm:
$$V=\pi r^2h=3(3^2)(17)=459\,cm^3$$

Tabloda 150 cm³→1 MAG, 1.500 cm³→3,5 MAG:
$$A=1+\frac{459-150}{1500-150}(3{,}5-1)=1{,}5722$$

$$M=1{,}5722\left[1+\frac{2+1-1+1}{4}\right]=2{,}7514\ MAG$$

$$F=2{,}7514(50.000)=137.569\ MAG/yıl$$

> [!important] Kaynaktaki yuvarlama farkı
> Slayt A'yı 1,57 alıp sonucu 2,74 ve yıllık 137.000 verir. Oysa $1{,}57(1{,}75)=2{,}7475$, iki ondalıkta 2,75'tir. Tam interpolasyonla 2,7514 bulunur. Sınavda hocanın tablo/yuvarlama yaklaşımı belirtilerek işlem gösterilmelidir.

## 3 - Tam çözümlü kaynak örneği: from-to
> [!example] Kaynak: HF06, slayt 59 ve 83-85
> P1: 30, A-C-B-D-E; P2: 12, A-B-D-E; P3: 7 fakat iki kat eşdeğer, A-C-D-B-E.

P3 eşdeğer miktarı $7(2)=14$.

| Yön | Hesap | Akış |
|---|---|---:|
| A→B | P2 | 12 |
| A→C | P1+P3 | 44 |
| B→D | P1+P2 | 42 |
| B→E | P3 | 14 |
| C→B | P1 | 30 |
| C→D | P3 | 14 |
| D→B | P3 | 14 |
| D→E | P1+P2 | 42 |

Toplam akışta B-D çifti $42+14=56$ ve B-C çifti $0+30=30$ olur. Kaynak toplamlarıyla eşleşir.

## 4 - Kademeli örnek
> [!question]
> X: 10 adet, A-B-C; Y: 6 adet ve eşdeğer katsayısı 3, C-B-A.
> 1. Y'nin eşdeğer miktarı $=\_\_$.
> 2. $f_{AB}=\_\_$, $f_{BA}=\_\_$, $f_{BC}=\_\_$, $f_{CB}=\_\_$.
> [!answer]- Çözüm
> Y=18. $f_{AB}=10$, $f_{BA}=18$, $f_{BC}=10$, $f_{CB}=18$.

## 5 - Bağımsız sorular
### L1
> [!question]
> $A=4$, B=1,C=0,D=-1,E=2 ise parça MAG değeri?
> [!answer]- Çözüm
> $4[1+(1+0-1+2)/4]=6$ MAG.

### L2
> [!question]
> 250 cm³ için 150→1 ve 1500→3,5 tablosundan A'yı doğrusal interpolasyonla bul.
> [!answer]- Çözüm
> $A=1+(100/1350)(2{,}5)=1{,}1852$.

### L3
> [!question]
> $f_{PQ}=70$, $f_{QP}=25$. Yönlü matris neden iki değeri de saklar; toplam akış nedir?
> [!answer]- Çözüm
> Taşıma yönleri farklı operasyonel anlam taşır; toplam $F_{PQ}=95$.

## 6 - Çıkış bileti
1. MAG formülünü ve beş bileşeni yaz.
2. From-to matrisinin neden asimetrik olduğunu açıkla.
3. Rota tablosundan hücre doldurma sırasını yaz.

## 7 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kaynak + kademeli |  |  |  |
| D1 |  | MAG interpolasyon |  |  |  |
| D3 |  | From-to matrisi |  |  |  |
| D7 |  | MAG + rota karma |  |  |  |
| D14 |  | İlişki sınıflama |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| Çapı yarıçap almak | Hacim dört kat büyür | $r=d/2$ yaz |
| B+C+D+E'yi doğrudan A'ya eklemek | Düzeltme A ile çarpılır | Köşeli parantezi önce bul |
| Rota içindeki her çifti eklemek | Yalnız ardışık geçiş vardır | Rotayı oklarla yeniden yaz |

## Kaynaklar
- [[HF6-P6-Akış, Alan ve Etkinlik İlişkileri II 2025.pptx|HF06 sunumu]], slayt 48-62, 83-85
- [[05 Kaynaklar/MarkItDown/HF06 - Ham|HF06 ham metni]], satır 563-785 ve 1060-1153
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
