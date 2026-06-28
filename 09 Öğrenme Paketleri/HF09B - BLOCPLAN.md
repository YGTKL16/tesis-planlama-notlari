---
hafta: 9
konu: BLOCPLAN akış, komşuluk ve REL-DIST hesabı
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, algoritma/blocplan]
kaynak: HF09 slayt 17-34
---

# HF09B - BLOCPLAN

> [!summary] Bir cümlede
> BLOCPLAN, yönlü akışı simetrik toplam akışa çevirip nitel ilişki sınıfları üretir; yerleşimi komşuluk ve ilişki-uzaklık puanlarıyla değerlendirir.

## Öğrenme hedefleri
- [ ] From-to matrisini toplam akış matrisine dönüştürebilirim.
- [ ] Akışları A-E-I-O-U aralıklarına sınıflandırabilirim.
- [ ] Komşuluk etkinlik oranı ile REL-DIST'i ayırabilirim.
- [ ] Ağırlık merkezi uzaklıklarıyla puan hesaplayabilirim.

## 0 - Soğuk başlangıç
> [!question]
> $f_{12}=30$, $f_{21}=18$ ise toplam akış $F_{12}$ kaçtır? Yön bilgisi korunur mu?
> [!answer]- Yanıt
> $F_{12}=48$; simetrikleştirme yön bilgisini kaldırır.

## 1 - Öğreten not
### 1. Toplam akış
$$F_{ij}=f_{ij}+f_{ji}\qquad(i<j)$$

### 2. Beş ilişki sınıfı
Slayt prosedüründe en büyük toplam akış beşe bölünür ve A, E, I, O, U aralıkları kurulur. Sınır değerleri çakışmayacak biçimde açık yazılmalıdır. X genellikle akıştan değil, istenmeyen ilişki bilgisinden gelir.

### 3. İlişkileri sayısallaştır
Kaynak örnek ağırlıkları: A=10, E=5, I=2, O=1, U=0, X=-10.

### 4. İki farklı puan
Komşuluk puanı yalnız ortak sınırı olan çiftleri ödüllendirir:
$$Z_A=\sum_{i<j}w_{ij}a_{ij},\quad a_{ij}\in\{0,1\}$$

Etkinlik oranı:
$$ER=\frac{Z_A}{\sum_{i<j}\max(w_{ij},0)}$$

> [!important] ER paydası
> Payda = tüm pozitif ilişki çiftlerinin ağırlık toplamı ($\sum_{i<j}\max(w_{ij},0)$). X ilişkilerini dışarıda bırak, kalanları topla. **"Negatifi at, kalanı topla."**

İlişki-uzaklık puanı:
$$RD=\sum_{i<j}w_{ij}d_{ij}$$

$d_{ij}$ genellikle bölüm ağırlık merkezleri arasındaki doğrusal uzaklıktır. Kaynağın işaret kuralında pozitif yakınlık ağırlıkları kullanıldığı için küçük $RD$ tercih edilir; X negatifse yorum ayrıca belirtilmelidir.

> [!warning]
> $ER$ büyük olsun, $RD$ küçük olsun. Aynı iki yerleşim komşulukta eşit, uzaklıkta farklı olabilir.

## 2 - Tam çözümlü kaynak örneği
> [!example] Kaynak: HF09, slayt 31-34
> Ağırlıklar A=10, E=5, I=2, O=1, U=0, X=-10. Slayttaki ağırlık×uzaklık üst üçgeni: 30, 25, 16, 12, 6, 40 ve kalanlar 0'dır.

$$RD=30+25+16+12+6+40=129$$

Örneğin D1-D2 ilişkisi A ve uzaklık 3 olduğundan $10(3)=30$; D4-D5 ilişkisi A ve uzaklık 4 olduğundan $10(4)=40$ olur. Toplam 129 bağımsız toplamayla doğrulandı.

Kaynağın slayt 27-29 örneğinde başlangıç ve nihai komşuluk puanı $15/24=0{,}625\approx0{,}63$ ile eşit; uzaklık maliyetleri ise 61.062,70 ve 58.133,34'tür. Yani nihai çözüm uzaklık açısından 2.929,36 daha iyidir.

## 3 - Kademeli örnek
> [!question]
> $f_{AB}=14,f_{BA}=6$; $f_{AC}=3,f_{CA}=5$; $f_{BC}=9,f_{CB}=11$.
> 1. $F_{AB}=\_\_$, $F_{AC}=\_\_$, $F_{BC}=\_\_$.
> 2. A-B=A(10), A-C=U(0), B-C=E(5); uzaklıklar 2, 6, 3 ise $RD$ nedir?
> [!answer]- Çözüm
> Toplam akışlar 20, 8, 20. $RD=10(2)+0(6)+5(3)=35$.

## 4 - Bağımsız sorular
### L1
> [!question]
> En büyük toplam akış 90 ise slayttaki beş eş aralık genişliği kaçtır?
> [!answer]- Çözüm
> $90/5=18$; kaynakta 73-90 A, 55-72 E, 37-54 I, 19-36 O, 0-18 U kullanılır.

### L2
> [!question]
> Komşu olumlu ilişkilerin toplamı 18, bütün olumlu ilişkilerin toplamı 30 ise etkinlik oranı nedir?
> [!answer]- Çözüm
> $ER=18/30=0{,}60$.

### L3
> [!question]
> İki çözümde $ER=0{,}70$ eşit; $RD_1=420$, $RD_2=365$. Kaynak işaret kuralıyla hangisi seçilir?
> [!answer]- Çözüm
> İkinci; ilişki-uzaklık puanı 55 daha küçüktür.

## 5 - Çıkış bileti
1. Yönlü akış nasıl simetrikleştirilir?
2. $ER$ ile $RD$ hangi bilgiyi kaybeder/korur?
3. Neden “puan yüksek iyidir” cümlesi her iki ölçüt için kullanılamaz?

## 6 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | From-to dönüşümü |  |  |  |
| D3 |  | ER + RD |  |  |  |
| D7 |  | BLOCPLAN/MCRAFT karma |  |  |  |
| D14 |  | Yöntem seçimi |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| $f_{ij}$'yi tek başına almak | Toplam akış çift yönü birleştirir | $f_{ij}+f_{ji}$ yaz |
| ER ve RD'yi aynı yönde yorumlamak | ER maksimize, pozitif RD minimize edilir | Ölçüt adını sonuç yanına yaz |
| Uzaklık yerine komşuluk kullanmak | REL-DIST gerçek mesafeyi ister | Ağırlık merkezlerini bul |

## Kaynaklar
- [[HF9-P9-Yerlesim Tasarımı III-2025.pptx|HF09 sunumu]], slayt 17-34
- [[05 Kaynaklar/MarkItDown/HF09 - Ham|HF09 ham metni]], satır 209-526
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
