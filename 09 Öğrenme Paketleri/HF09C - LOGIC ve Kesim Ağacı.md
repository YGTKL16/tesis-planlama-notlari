---
hafta: 9
konu: LOGIC giyotin kesimleri ve kesim ağacı
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, algoritma/logic, kesim-agaci]
kaynak: HF09 slayt 35-47
---

# HF09C - LOGIC ve Kesim Ağacı

> [!summary] Bir cümlede
> LOGIC, dikdörtgen alanı yatay/dikey tam kesimlerle bölen bir kesim ağacı kurar ve yaprak bölümleri değiştirerek uzaklık esaslı maliyeti iyileştirir.

## Öğrenme hedefleri
- [ ] LOGIC'in uzaklık esaslı olduğunu açıklayabilirim.
- [ ] Bir giyotin yerleşimi kesim ağacıyla gösterebilirim.
- [ ] Alan oranından kesim konumu hesaplayabilirim.
- [ ] Yaprak değişiminden sonra hangi alt ağacın yeniden kesileceğini belirleyebilirim.

## 0 - Soğuk başlangıç
> [!question]
> $12\times10$ m dikdörtgende solda toplam 50, sağda 70 m² kalacak dikey tam kesim hangi $x$ konumundadır?
> [!answer]- Yanıt
> Yükseklik 10 m olduğundan soldaki genişlik $50/10=5$ m; kesim soldan 5 m'dedir.

## 1 - Öğreten not
LOGIC, **Layout Optimization with Guillotine Induced Cuts** ifadesinden gelir. Kaynak açıkça “uzaklık esaslı amaç”, “kurma ve geliştirme” ve “tekrarlı gösterim” der.

### Giyotin kesim
Bir kesim mevcut dikdörtgen alt bölgeyi bir kenardan karşı kenara tamamen böler. Her iç düğüm:
- `V`: dikey kesim,
- `H`: yatay kesimdir.

Yapraklar bölümlerdir. Örneğin
```text
V( H(A,B), H(C,D) )
```
önce bütünü sol/sağ böler; sonra her yarıyı üst/alt böler.

### Kesim konumu
Alt bölge alanı $A_S$ ve bir çocuğun toplam alanı $A_L$ ise dikey kesimde:
$$x_L=W_S\frac{A_L}{A_S}$$
Yatay kesimde:
$$y_L=H_S\frac{A_L}{A_S}$$

### Geliştirme
1. Ağaçta iki yaprağı değiştir.
2. Ağaç yapısını/budamayı koru.
3. Değişimden etkilenen en küçük ortak alt ağacı alan oranlarıyla yeniden kes.
4. $C=\sum f_{ij}c_{ij}d_{ij}$ maliyetini karşılaştır.

> [!danger] Düzeltme
> LOGIC'i yalnız nitel komşuluk yöntemi diye tanımlamak yanlıştır. HF09 slayt 36 onu uzaklık esaslı olarak tanımlar; giyotin kesim ve kesim ağacı belirleyici özelliktir.

## 2 - Kaynak örneği
> [!example] Kaynak: HF09, slayt 40-46
> Kaynak ilk örnekte D ve G, ikinci örnekte eş ölçülü olmayan D ve E yapraklarını değiştirir. Sol alt ağaçtaki A, B, C, E, H değişmiyorsa kesim yalnız sağ taraftaki D, F, G için yeniden uygulanır.

Bu örnek şu kuralı gösterir: eş alan koşulu aranmaz; fakat değişen alanlar nedeniyle etkilenen alt ağacın kesim koordinatları yeniden hesaplanır. Ham metin resimlerdeki alan/koordinatları vermediği için sayısal maliyet türetilmemiştir.

## 3 - Tam çözümlü öğretim örneği
> [!example] Tamamen denetlenebilir öğretim örneği
> $12\times10=120$ m² bina; A=20, B=30, C=28, D=42. Ağaç `V(H(A,B),H(C,D))`.

Sol çocuk alanı $20+30=50$; genişliği $50/10=5$ m. Sağ genişlik 7 m.

Sol çocukta A'nın yüksekliği $20/5=4$ m, B'nin yüksekliği $30/5=6$ m. Sağ çocukta C'nin yüksekliği $28/7=4$ m, D'nin yüksekliği $42/7=6$ m.

Dolayısıyla bloklar: A $5\times4$, B $5\times6$, C $7\times4$, D $7\times6$; alanlar tam korunur.

## 4 - Kademeli örnek
> [!question]
> Aynı binada A ile D değiştiriliyor; ağaç `V(H(D,B),H(C,A))` oluyor.
> 1. Sol toplam alan $=\_\_$, genişlik $=\_\_$.
> 2. Sağ toplam alan $=\_\_$, genişlik $=\_\_$.
> [!answer]- Çözüm
> Sol $42+30=72$, genişlik $72/10=7{,}2$ m. Sağ $28+20=48$, genişlik $4{,}8$ m. İki alt ağacın da koordinatları değişir.

## 5 - Bağımsız sorular
### L1
> [!question]
> `H(V(A,B),C)` ağacında kök kesim yönü nedir?
> [!answer]- Çözüm
> Yatay; üst/alt çocuklardan biri A-B dikey bölünmesini, diğeri C'yi içerir.

### L2
> [!question]
> $15\times8$ bölgede bir dikey kesimin sol çocuğu 48 m² ise genişlikleri bulun.
> [!answer]- Çözüm
> Sol $48/8=6$ m, sağ $15-6=9$ m.

### L3
> [!question]
> Sabit bölüm ve önceden belirli şekil neden LOGIC için sorun oluşturur?
> [!answer]- Çözüm
> Yaprak değişimi ve tam yatay/dikey kesimler sabit konumu veya önceden zorunlu şekli korumayabilir.

## 6 - Çıkış bileti
1. LOGIC'in amaç türü nedir?
2. İç düğüm ve yaprak neyi temsil eder?
3. Değişim sonrası neden kesimler yeniden hesaplanır?

## 7 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Öğretim + kademeli |  |  |  |
| D1 |  | Ağaç okuma |  |  |  |
| D3 |  | Yaprak değişimi |  |  |  |
| D7 |  | LOGIC/BLOCPLAN ayırma |  |  |  |
| D14 |  | Maliyetli aktarım |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| LOGIC'i komşuluk yöntemi sanmak | Kaynak uzaklık esaslı der | Adı: giyotin kesim optimizasyonu |
| Alan oranını genişliğe doğrudan eşitlemek | Diğer boyut hesaba girer | $A=W\times H$ kontrolü |
| Değişimde yalnız etiketleri taşımak | Alanlar farklıysa kesim yeri değişir | Alt ağaç alanlarını yeniden topla |

## Kaynaklar
- [[HF9-P9-Yerlesim Tasarımı III-2025.pptx|HF09 sunumu]], slayt 35-47
- [[05 Kaynaklar/MarkItDown/HF09 - Ham|HF09 ham metni]], satır 526-654
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
