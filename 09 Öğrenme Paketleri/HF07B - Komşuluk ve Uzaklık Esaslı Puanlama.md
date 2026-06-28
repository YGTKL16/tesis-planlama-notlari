---
hafta: 7
konu: yerleşim alternatiflerinin komşuluk ve uzaklıkla puanlanması
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, komşuluk-puanı, uzaklık-puanı, rel]
kaynak: HF07 slayt 53-60
---

# HF07B - Komşuluk ve Uzaklık Esaslı Puanlama

> [!summary] Bir cümlede
> Komşuluk puanı yalnız temas eden bölüm çiftlerinin ilişki değerini büyütür; uzaklık puanı ise bütün ilgili akışların mesafeli maliyetini küçültür.

## Öğrenme hedefleri

- [ ] Bir blok plandan komşu çiftleri eksiksiz çıkarabilirim.
- [ ] A-E-I-O-U-X kodlarını sayısal puana çevirebilirim.
- [ ] Komşuluk skorunda maksimum, uzaklık maliyetinde minimum arandığını ayırabilirim.
- [ ] Dik doğrusal uzaklık ve yönlü akışla toplam maliyet hesaplayabilirim.

## 0 - Soğuk başlangıç

> [!question]
> Bir alternatifin komşuluk puanı 30, diğerinin 24; uzaklık maliyetleri sırasıyla 1.200 ve 900'dür. Hangi yerleşim kesin olarak daha iyidir?

> [!answer]- Beklenen açıklama
> Kesin karar verilemez. Komşuluk puanında büyük, uzaklık maliyetinde küçük değer iyidir; amaçların ağırlığı veya önceliği verilmelidir.

## 1 - Öğreten not

### Komşuluk esaslı puan

$$
S_A=\sum_{i<j}w_{ij}x_{ij}
$$

$$
x_{ij}=\begin{cases}1,&i,j\text{ ortak sınır paylaşıyor}\\0,&\text{aksi halde}\end{cases}
$$

Bu dersteki tipik ağırlıklar:

| REL | A | E | I | O | U | X |
|---|---:|---:|---:|---:|---:|---:|
| $w$ | 8 | 4 | 2 | 1 | 0 | -8 |

Amaç $S_A$'yı **maksimize etmektir**. X ilişkili iki bölümü komşu yapmak puanı düşürür.

Normalize etkinlik puanı, kaynak slayt 58'de:

$$
\eta=\frac{\sum_{i<j}w_{ij}x_{ij}}{\sum_{i<j}w_{ij}}
$$

> [!warning]
> Bu oran, paydadaki ağırlıkların hangi ilişkileri kapsadığı ve negatif X değerlerinin nasıl ele alındığı açıkça tanımlanırsa anlamlıdır. Alternatif karşılaştırmada çoğu zaman ham skor ve X ihlallerini ayrıca vermek daha güvenlidir.

### Uzaklık esaslı maliyet

$$
Z_D=\sum_i\sum_{j\ne i}f_{ij}c_{ij}d_{ij}
$$

Dik doğrusal uzaklık:

$$
d_{ij}=|x_i-x_j|+|y_i-y_j|
$$

Amaç $Z_D$'yi **minimize etmektir**. Merkez koordinatları kullanılıyorsa bölüm boyutları ağırlık merkezini değiştirir.

### Hızlı yöntem seçimi

| Verilen | Yöntem | İyi yön |
|---|---|---|
| REL kodları + blok temasları | Komşuluk skoru | büyük |
| Akış + uzaklık + birim maliyet | Uzaklık maliyeti | küçük |
| Her ikisi | İki ölçütlü değerlendirme | öncelik/ağırlık gerekir |

## 2 - Tam çözümlü kaynak örnekleri

### 2A - Komşuluk puanı

> [!example] Kaynak: HF07, slayt 56-57
> Yedi bölümlü yerleşimde komşu çiftlerin REL değerleri aşağıdadır. $A=8,E=4,I=2,O=1,U=0,X=-8$ ile puanı bulun.

| Komşu çift | REL | Puan |
|---|:---:|---:|
| 1-2 | E | 4 |
| 1-3 | O | 1 |
| 3-7 | U | 0 |
| 1-6 | U | 0 |
| 2-4 | E | 4 |
| 2-6 | O | 1 |
| 6-7 | E | 4 |
| 5-6 | A | 8 |
| 4-5 | I | 2 |

$$S_A=4+1+0+0+4+1+4+8+2=24$$

> [!success] Sonuç
> Kaynak slayttaki yerleşim puanı 24'tür. Yalnız gerçek ortak sınırlar sayılmış, köşe teması sayılmamıştır.

### 2B - Uzaklık maliyeti

> [!example] Kaynak: HF07, slayt 59-60
> Dört bölümlü yerleşimin yönlü akış ve merkezler arası uzaklık matrisleri verilmiştir; $c_{ij}=1$ kabul edilir.

Akış matrisi:

| From/To | A | B | C | D |
|---|---:|---:|---:|---:|
| A | - | 2 | 4 | 4 |
| B | 1 | - | 1 | 3 |
| C | 2 | 1 | - | 2 |
| D | 4 | 1 | 0 | - |

Uzaklık matrisi:

| From/To | A | B | C | D |
|---|---:|---:|---:|---:|
| A | - | 40 | 25 | 55 |
| B | 40 | - | 65 | 25 |
| C | 25 | 65 | - | 40 |
| D | 55 | 25 | 40 | - |

Satır katkıları:

$$A:2(40)+4(25)+4(55)=400$$
$$B:1(40)+1(65)+3(25)=180$$
$$C:2(25)+1(65)+2(40)=195$$
$$D:4(55)+1(25)+0(40)=245$$

$$Z_D=400+180+195+245=1.020$$

> [!note] Bağımsız doğrulama
> On iki yönlü hücrenin ayrı çarpım toplamı da 1.020'dir; simetrik uzaklık matrisi, yönlü akışların birini silmek için gerekçe değildir.

### Öz-açıklama

1. Komşuluk örneğinde neden yalnız dokuz çift toplandı?
2. Uzaklık örneğinde neden A-B ve B-A ayrı katkıdır?
3. Komşuluk puanı 24'ten 30'a çıktığında uzaklık maliyeti mutlaka düşer mi?

## 3 - Kademeli örnek

> [!question]
> Dört bölümün komşu çiftleri AB, AC, BD ve CD'dir. REL değerleri AB=A, AC=X, BD=E, CD=I olsun. Aynı bölümlerin koordinatları A(0,0), B(2,0), C(0,3), D(2,3)'tür. Yönlü akışlar $f_{AB}=10$, $f_{BA}=5$, $f_{CD}=8$, $f_{DC}=2$ ve $c=1$'dir.
>
> 1. $S_A=8+(\_)+4+2$
> 2. $d_{AB}=$ __, $d_{CD}=$ __
> 3. $Z_D=(10+5)(\_)+(8+2)(\_)$

> [!answer]- Tam çözüm
> $$S_A=8-8+4+2=6$$
> $d_{AB}=d_{CD}=2$ olduğundan:
> $$Z_D=15(2)+10(2)=50$$

## 4 - Bağımsız sorular

### L1 - Komşuluk

> [!question]
> Komşu çiftler 1-2, 1-3, 2-4, 3-4 ve 4-5'tir. REL değerleri sırasıyla A, E, X, I, A'dır. Standart ağırlıklarla puanı bulun.

> [!answer]- Çözüm
> $$S_A=8+4-8+2+8=14$$

### L2 - Uzaklık ve yön

> [!question]
> Koordinatlar A(1,1), B(5,2), C(2,6); akışlar $f_{AB}=4$, $f_{BA}=6$, $f_{AC}=3$, $f_{CA}=1$, $f_{BC}=8$, $f_{CB}=2$ ve $c=2$ olsun. Dik doğrusal uzaklıkla toplam maliyeti bulun.

> [!answer]- Çözüm
> $d_{AB}=5$, $d_{AC}=6$, $d_{BC}=7$.
> $$Z=2[(4+6)5+(3+1)6+(8+2)7]=2(144)=288$$

### L3 - Yöntemi seç

> [!question]
> Hastane yerleşiminde laboratuvar-acil servis ilişkisinin A, morg-kafeterya ilişkisinin X olduğu; ayrıca günlük hasta hareketlerinin verildiği söyleniyor. Tek sayı ile karar vermek için ne eksiktir?

> [!answer]- Çözüm
> REL yakınlık hedefi ile akış-mesafe maliyetini ortak karara çevirecek öncelik, ağırlık veya kısıt tanımı eksiktir. Güvenlik kaynaklı X ilişkisi yalnız negatif puan değil, sert kısıt da olabilir.

## 5 - Çıkış bileti

1. Komşuluk skoru ve uzaklık maliyeti formüllerini yaz.
2. Hangisinde büyük, hangisinde küçük değer iyidir?
3. Köşe teması neden genellikle komşuluk sayılmaz?
4. Yönlü akışta hangi hücreler toplanır?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Kaynak uzaklık örneği |  |  |  |
| D3 |  | HF07A ile yöntem seçimi |  |  |  |
| D7 |  | İki ölçütlü mini test |  |  |  |
| D14 |  | HF08B ile karma soru |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| X'i +8 almak | X istenmeyen komşuluktur | Ağırlık satırını önce yaz |
| Köşe temasını komşuluk saymak | Ortak sınır yoktur | Pozitif sınır uzunluğu ara |
| Uzaklık maliyetini maksimize etmek | Bu bir maliyettir | Amaç yönünü formülün yanına yaz |
| Simetrik uzaklık nedeniyle yönlü akışı silmek | Akış simetrik olmak zorunda değildir | Üst ve alt üçgeni ayrı kontrol et |

## Kaynaklar

- [[HF7-P7-Yerlesim Tasarımı I-2025.pptx|Ders sunumu]], slayt 53-60
- [[05 Kaynaklar/MarkItDown/HF07 - Ham|HF07 ham metni]], yaklaşık satır 834-912
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]

