---
hafta: 7
konu: süreç yerleşiminde akış-maliyet hesabı
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, süreç-yerleşimi, taşıma-maliyeti]
kaynak: HF07 slayt 26-33
---

# HF07A - Süreç Yerleşimi Taşıma Maliyeti

> [!summary] Bir cümlede
> Bir süreç yerleşiminin maliyeti, her bölüm çifti için akış, birim taşıma maliyeti ve uzaklığın çarpılıp toplanmasıyla bulunur; daha küçük toplam daha iyi yerleşimdir.

## Öğrenme hedefleri

- [ ] From-to matrisini yönlü veya yönsüz modele doğru aktarabilirim.
- [ ] Komşuluk maliyeti ile gerçek uzaklık maliyetini ayırabilirim.
- [ ] Bir yerleşimden uzaklık/komşuluk katsayılarını çıkarabilirim.
- [ ] İki alternatifi toplam maliyet ve tasarrufla karşılaştırabilirim.

## 0 - Soğuk başlangıç

> [!question]
> A-B arasında 40, B-A arasında 10 yük taşınıyor. Uzaklık 3 birim, iki yönde birim maliyet 2 TL/yük-birim olsun. Toplam maliyet nedir? Yalnız `40` akışını kullanmak ne zaman doğru olur?

> [!answer]- Beklenen açıklama
> Yönlü matris verildiyse iki yön de sayılır: $(40+10)(2)(3)=300$ TL. Yalnız 40, veri zaten iki yönün toplamı olarak verilmişse veya B-A akışı gerçekten sıfırsa kullanılabilir.

## 1 - Öğreten not

### Soruyu nasıl tanırsın?

Soruda bölüm çiftleri arasında **akış/yük/gezi sayısı**, birim taşıma maliyeti ve yerleşimden gelen uzaklık veya komşuluk bilgisi vardır. Amaç genellikle toplam taşıma maliyetini en küçüklemektir.

### Temel model

Yönlü from-to matrisi için:

$$
Z=\sum_i\sum_{j\ne i} f_{ij}c_{ij}d_{ij}
$$

| Sembol | Anlam | Birim |
|---|---|---|
| $f_{ij}$ | $i$'den $j$'ye akış | yük/dönem |
| $c_{ij}$ | bir yükü bir uzaklık birimi taşıma maliyeti | TL/(yük·birim) |
| $d_{ij}$ | $i$ ile $j$ arasındaki uzaklık veya soru katsayısı | birim |
| $Z$ | toplam dönemsel taşıma maliyeti | TL/dönem |

Akışlar çiftler için birleştirilmişse ve uzaklık/maliyet simetrikse:

$$
Z=\sum_{i<j}F_{ij}c_{ij}d_{ij},\qquad F_{ij}=f_{ij}+f_{ji}
$$

> [!warning] Çifte sayma
> Tam yönlü matris kullanırken bütün $i\ne j$ hücrelerini bir kez topla. $F_{ij}=f_{ij}+f_{ji}$ yaptıysan ayrıca hem $(i,j)$ hem $(j,i)$ hücresini toplama.

### Uzaklık yerine komşuluk maliyeti verilirse

Bazı sorular gerçek metre yerine bir katsayı kullanır:

$$
d_{ij}=\begin{cases}
1,&i,j\text{ komşu}\\
2,&i,j\text{ komşu değil}
\end{cases}
$$

Bu, gerçek geometrik uzaklık modeli değildir. Sorunun tanımladığı komşuluk kuralı aynen uygulanır. Normalde yalnız ortak sınır paylaşmak komşuluktur; ancak HF07 kaynak örneği ortak köşeyi de komşu kabul etmektedir.

### Çözüm sırası

1. Akışın yönlü mü, çiftler halinde mi verildiğini belirle.
2. Yerleşimde her çift için $d_{ij}$ değerini çıkar.
3. Her katkıyı $f_{ij}c_{ij}d_{ij}$ olarak hesapla.
4. Katkıları topla; birim ve dönem yaz.
5. Alternatif varsa $\text{tasarruf}=Z_{eski}-Z_{yeni}$ hesapla.

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF07, slayt 28-33
> Altı bölüm 2×3 ızgaraya yerleştiriliyor. Sıfır olmayan haftalık çift akışları: $F_{12}=50$, $F_{13}=100$, $F_{16}=20$, $F_{23}=30$, $F_{24}=50$, $F_{25}=10$, $F_{34}=20$, $F_{36}=100$, $F_{45}=50$. Komşu çiftin katsayısı 1, komşu olmayanın 2'dir. Başlangıç ve iyileştirilmiş yerleşimin maliyetini bulun.

Başlangıç yerleşimi:

| 1 | 2 | 3 |
|---|---|---|
| 4 | 5 | 6 |

Kaynak örneğinin ortak köşeyi de komşu sayan kuralıyla katkılar:

| Çift | Akış | Katsayı | Katkı |
|---|---:|---:|---:|
| 1-2 | 50 | 1 | 50 |
| 1-3 | 100 | 2 | 200 |
| 1-6 | 20 | 2 | 40 |
| 2-3 | 30 | 1 | 30 |
| 2-4 | 50 | 1 | 50 |
| 2-5 | 10 | 1 | 10 |
| 3-4 | 20 | 2 | 40 |
| 3-6 | 100 | 1 | 100 |
| 4-5 | 50 | 1 | 50 |

$$Z_0=570\text{ maliyet birimi/hafta}$$

İyileştirilmiş yerleşim:

| 2 | 1 | 3 |
|---|---|---|
| 4 | 5 | 6 |

Yeni katsayılarla:

$$
Z_1=50+100+20+60+50+10+40+100+50=480
$$

$$
\text{tasarruf}=570-480=90
$$

> [!success] Sonuç
> İkinci yerleşim haftada 90 maliyet birimi, yani başlangıca göre $90/570=%15{,}79$ tasarruf sağlar.

### Öz-açıklama

1. Neden yüksek akışlı 1-3 çiftinin katsayısını 2'den 1'e düşürmek değerlidir?
2. Kaynak örneğinde 2-4 çifti neden komşu sayıldı?
3. Akışlar yönlü verilseydi tablo nasıl değişirdi?

## 3 - Kademeli örnek

> [!question]
> Dört bölümün çift akışları $F_{AB}=20$, $F_{AC}=10$, $F_{AD}=5$, $F_{BC}=30$, $F_{BD}=15$, $F_{CD}=25$ olsun. Yerleşim `[A B C D]` doğrusal, bölümler arası uzaklık konum farkıdır ve $c=2$ TL/(yük·birim)'dir.
>
> 1. $d_{AB}=$ __, $d_{AC}=$ __, $d_{AD}=$ __
> 2. $Z=2[20(\_)+10(\_)+5(\_)+30(\_)+15(\_)+25(\_)]$
> 3. Toplam maliyeti yaz.

> [!answer]- Tam çözüm
> Uzaklıklar sırasıyla $1,2,3,1,2,1$'dir.
> $$Z=2[20+20+15+30+30+25]=280\text{ TL/dönem}$$

## 4 - Bağımsız sorular

### L1 - Yönlü matris

> [!question]
> $f_{AB}=12$, $f_{BA}=8$, $f_{AC}=5$, $f_{CA}=15$, $f_{BC}=10$, $f_{CB}=0$; $d_{AB}=2$, $d_{AC}=4$, $d_{BC}=3$ ve tüm $c_{ij}=3$ olsun. $Z$'yi bulun.

> [!answer]- Çözüm
> $$Z=3[(12+8)2+(5+15)4+(10+0)3]=3(150)=450$$
> Sonuç 450 TL/dönemdir.

### L2 - Alternatif seçimi

> [!question]
> Akışlar $F_{AB}=50$, $F_{AC}=10$, $F_{BC}=30$ ve $c=1$ olsun. L1 yerleşiminde uzaklıklar $(d_{AB},d_{AC},d_{BC})=(3,1,2)$; L2'de $(1,3,2)$'dir. Hangisi daha iyi, tasarruf ne kadar?

> [!answer]- Çözüm
> $$Z_{L1}=50(3)+10(1)+30(2)=220$$
> $$Z_{L2}=50(1)+10(3)+30(2)=140$$
> L2, dönem başına 80 maliyet birimi daha iyidir. Büyük $AB$ akışının yakınlaştırılması belirleyicidir.

### L3 - Yöntemi ve sayımı seç

> [!question]
> Bir matriste hem üst hem alt üçgen dolu, taşıma maliyetleri yönlere göre farklıdır. Bir öğrenci $f_{ij}+f_{ji}$ yapıp yalnız $c_{ij}$ ile çarpıyor. Bu işlem hangi koşulda geçerlidir, hangi koşulda yanlıştır?

> [!answer]- Çözüm
> $c_{ij}=c_{ji}$ ve $d_{ij}=d_{ji}$ ise akışlar birleştirilebilir. Yönlere göre maliyet farklıysa $f_{ij}c_{ij}d_{ij}$ ve $f_{ji}c_{ji}d_{ji}$ ayrı hesaplanmalıdır.

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. Yönlü toplam maliyet formülünü yaz.
2. Yönlü akışları tek çift akışına ne zaman dönüştürebilirsin?
3. Kaynak örneğinin alışılmadık komşuluk varsayımı nedir?
4. İki alternatif arasındaki tasarruf nasıl hesaplanır?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Yeni yönlü matris |  |  |  |
| D3 |  | HF07B ile karma seçim |  |  |  |
| D7 |  | İki alternatif, süreli |  |  |  |
| D14 |  | HF08A ile karma soru |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| Alt üçgeni yok saymak | Akış yönlü olabilir | Matrisin veri tanımını yaz |
| Yönleri birleştirip maliyeti tek yön almak | $c_{ij}\ne c_{ji}$ olabilir | Önce simetriyi kontrol et |
| Uzaklık yerine göz kararı komşuluk yazmak | Soru farklı katsayı tanımlayabilir | Her çift için ayrı $d_{ij}$ tablosu çıkar |
| İyileşmeyi yalnız yeni maliyetle vermek | Karşılaştırma eksik kalır | Farkı ve yüzde tasarrufu yaz |

## Kaynaklar

- [[HF7-P7-Yerlesim Tasarımı I-2025.pptx|Ders sunumu]], slayt 26-33
- [[05 Kaynaklar/MarkItDown/HF07 - Ham|HF07 ham metni]], yaklaşık satır 397-582
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
