---
hafta: 8
konu: ikili yer değişimiyle yerleşim iyileştirme
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, ikili-değişim, yerel-arama]
kaynak: HF08 slayt 13-27
---

# HF08A - İkili Yer Değişim Yöntemi

> [!summary] Bir cümlede
> İkili yer değişim yöntemi, mevcut yerleşimde bütün bölüm çiftlerini sırayla takas edip maliyeti en çok düşüren değişimi uygular ve iyileşme kalmayınca durur.

## Öğrenme hedefleri

- [ ] Dik doğrusal uzaklığı bölüm merkezlerinden hesaplayabilirim.
- [ ] $n(n-1)/2$ ikili değişim adayını eksiksiz üretebilirim.
- [ ] Her adayın yeni maliyetini doğru bölüm-konum eşlemesiyle bulabilirim.
- [ ] Durma koşulunu ve yerel optimum sınırını açıklayabilirim.

## 0 - Soğuk başlangıç

> [!question]
> Dört bölüm için bir iterasyonda kaç ikili takas vardır? En iyi takas mevcut maliyetle aynı sonucu verirse uygulanır mı?

> [!answer]- Beklenen açıklama
> $\binom42=6$ takas vardır. Amaç maliyet azaltmaksa eşit maliyet iyileşme değildir; özel bir bağ çözme gerekçesi yoksa yöntem durur.

## 1 - Öğreten not

### Temel maliyet

$$
Z(L)=\sum_i\sum_{j\ne i} f_{ij}c_{ij}d_{ij}(L)
$$

Dik doğrusal merkez uzaklığı:

$$d_{ij}=|x_i-x_j|+|y_i-y_j|$$

Bir iterasyondaki ikili aday sayısı:

$$N=\binom n2=\frac{n(n-1)}2$$

### Algoritma

1. Başlangıç yerleşiminin $Z_0$ maliyetini bul.
2. Bütün uygun bölüm çiftlerini üret.
3. Her çiftin konumunu takas et; yeni uzaklıkları ve $Z'$yi hesapla.
4. En küçük $Z'$yi seç.
5. $Z'<Z$ ise değişimi uygula ve yeni iterasyona geç.
6. Hiçbir aday daha iyi değilse dur.

> [!warning] İsim-konum tuzağı
> `[3,2,1,4]`, konum 1'de bölüm 3, konum 2'de bölüm 2, konum 3'te bölüm 1, konum 4'te bölüm 4 demektir. Uzaklık matrisi konumlara, akış matrisi bölüm adlarına aittir.

### Ne garanti eder?

- Mevcut çözüme göre yerel iyileşme.
- Sonlu aday kümesinde durma.
- **Küresel optimum garantisi yoktur.** Sonuç başlangıç yerleşimine bağlıdır.

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF08, slayt 20-26
> Eşit büyüklükte dört bölüm doğrusal `[1,2,3,4]` yerleşimindedir. Konum uzaklığı sıra farkıdır, $c=1$ ve çift akışları aşağıdadır.

| Çift | 1-2 | 1-3 | 1-4 | 2-3 | 2-4 | 3-4 |
|---|---:|---:|---:|---:|---:|---:|
| Akış | 10 | 15 | 20 | 10 | 5 | 5 |

Başlangıç:

$$
Z_{1234}=10(1)+15(2)+20(3)+10(1)+5(2)+5(1)=125
$$

### 1. iterasyon

| Takas | Yeni sıra | Maliyet |
|---|---|---:|
| 1-2 | 2134 | 105 |
| 1-3 | 3214 | **95** |
| 1-4 | 4231 | 120 |
| 2-3 | 1324 | 120 |
| 2-4 | 1432 | 105 |
| 3-4 | 1243 | 125 |

En iyi değişim 1-3'tür; yeni sıra `3214`, maliyet 95 olur.

### 2. iterasyon

`3214` düzeninden bütün takaslar yeniden denenir. En iyi aday, bölüm 3 ile 2'nin takasıdır:

$$Z_{2314}=90$$

Örneğin:

$$
Z_{2314}=10(1)+15(1)+20(2)+10(1)+5(3)+5(2)=90
$$

### 3. iterasyon ve durma

`2314` düzeninden en düşük komşu değer 95'tir; 90'dan küçük aday yoktur. Algoritma durur.

> [!success] Sonuç
> Kaynak örneğinin nihai yerleşimi `2314`, maliyeti 90'dır. Başlangıca göre tasarruf $125-90=35$, oran $35/125=%28$'dir.

> [!note] Bağımsız doğrulama
> Her iterasyonda altı permütasyon ayrı hesaplandı. Kaynak slaytlardaki ara yerleşim etiketleri karışık görünse de doğrulanmış maliyet yolu `1234 → 3214 → 2314` şeklindedir.

### Öz-açıklama

1. İlk iterasyonda neden yalnız komşu konumlar değil altı çift denenir?
2. Bir değişimden sonra neden uzaklık matrisi yeniden kurulmalıdır?
3. 90 maliyetli sonuç neden küresel optimum olarak adlandırılamaz?

## 3 - Kademeli örnek

> [!question]
> Üç doğrusal konumda `[A,B,C]` yerleşimi var; uzaklık sıra farkıdır. Çift akışları $F_{AB}=5$, $F_{AC}=20$, $F_{BC}=10$, $c=1$.
>
> 1. $Z_{ABC}=5(\_)+20(\_)+10(\_)$
> 2. Üç takası üret.
> 3. En iyi yeni sırayı ve maliyeti seç.

> [!answer]- Tam çözüm
> $Z_{ABC}=5(1)+20(2)+10(1)=55$.
>
> - A-B → BAC: $5(1)+20(1)+10(2)=45$
> - A-C → CBA: $5(1)+20(2)+10(1)=55$
> - B-C → ACB: $5(2)+20(1)+10(1)=40$
>
> En iyi değişim B-C, yeni sıra ACB ve maliyet 40'tır.

## 4 - Bağımsız sorular

### L1 - Aday sayısı

> [!question]
> 7 bölüm için bir iterasyonda kaç ikili değişim vardır? İki bölüm sabitse ve hiçbir takasa katılamıyorsa kaç aday kalır?

> [!answer]- Çözüm
> Tüm bölümler için $7(6)/2=21$. Yalnız 5 değişebilir bölüm için $5(4)/2=10$ aday kalır.

### L2 - Tam iterasyon

> [!question]
> `[1,2,3]` doğrusal yerleşiminde $F_{12}=12$, $F_{13}=4$, $F_{23}=9$ ve $c=2$ olsun. Başlangıcı ve bütün takasları hesaplayıp kararı ver.

> [!answer]- Çözüm
> Başlangıç: $2[12(1)+4(2)+9(1)]=58$.
>
> - 1-2 → 213: $2[12(1)+4(1)+9(2)]=68$
> - 1-3 → 321: $2[12(1)+4(2)+9(1)]=58$
> - 2-3 → 132: $2[12(2)+4(1)+9(1)]=74$
>
> Daha düşük maliyet yoktur; başlangıç yerel optimumdur.

### L3 - Yöntemi seç

> [!question]
> Hiç başlangıç yerleşimi verilmeyen boş bir binada ikili değişim yöntemi doğrudan uygulanabilir mi?

> [!answer]- Çözüm
> Hayır. Bu iyileştirme esaslı yöntem bir başlangıç çözümü ister. Önce ilişki diyagramı/grafik tabanlı bir kurma yöntemi veya başka bir başlangıç üreticisi kullanılmalıdır.

## 5 - Çıkış bileti

1. Aday sayısı formülünü yaz.
2. Bir iterasyonun altı adımını hatırdan sırala.
3. Bölüm-konum ayrımı nedir?
4. Durma koşulu ve optimum sınırı nedir?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Kaynak ilk iterasyon |  |  |  |
| D3 |  | L2 + HF07A karma |  |  |  |
| D7 |  | İki iterasyon, süreli |  |  |  |
| D14 |  | HF08C ile yöntem seçimi |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| Yalnız yan yana konumları takas etmek | Yöntem bütün uygun bölüm çiftlerini dener | $\binom n2$ kontrolü yap |
| Eski uzaklık matrisini kullanmak | Bölüm-konum eşleşmesi değişti | Her aday için konum haritası yaz |
| Eşit maliyeti iyileşme saymak | Amaç azalma sağlamaktır | `yeni < mevcut` koşulunu yaz |
| Sonucu küresel optimum sanmak | Yerel arama başlangıca bağlıdır | “yerel optimum” diye yorumla |

## Kaynaklar

- [[HF8-P8-Yerlesim Tasarımı II-2025.pptx|Ders sunumu]], slayt 13-27
- [[05 Kaynaklar/MarkItDown/HF08 - Ham|HF08 ham metni]], yaklaşık satır 162-449
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]

