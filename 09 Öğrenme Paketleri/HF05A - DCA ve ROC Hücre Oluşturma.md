---
hafta: 5
konu: DCA ve ROC ile makine-parça hücreleri
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, hucre-olusturma, dca, roc]
kaynak: HF05 slayt 18-34
---

# HF05A - DCA ve ROC Hücre Oluşturma

> [!summary] Bir cümlede
> DCA satır/sütun toplamları ve 1'leri bloklaştıran ötelemelerle, ROC ise ikili ondalık ağırlıklarla makine-parça matrisini hücresel bloklara dönüştürür.

## Öğrenme hedefleri
- [ ] Makine-parça matrisini kurup satır/sütun toplamlarını bulabilirim.
- [ ] DCA sıralama ve bloklaştırma adımlarını uygulayabilirim.
- [ ] ROC satır ve sütun ondalık değerlerini hesaplayabilirim.
- [ ] İstisnai parça ve darboğaz makineyi tanıyabilirim.

## 0 - Soğuk başlangıç
> [!question]
> `1 0 1 1` ikili satırının soldan sağa ağırlıkları 8,4,2,1 ise ondalık değeri kaçtır?
> [!answer]- Yanıt
> $1(8)+0(4)+1(2)+1(1)=11$.

## 1 - Öğreten not
### Makine-parça matrisi
$b_{ij}=1$ ise parça $i$, makine $j$ üzerinde işlem görür; aksi halde 0'dır. Matris işlem tekrarını veya sırasını değil, yalnız gereksinimin varlığını gösterir.

### DCA
1. Her satır ve sütundaki 1'leri topla.
2. Kaynak prosedürüne göre satırları azalan, sütunları artan toplamla ön sırala.
3. İlk satırdaki 1'li sütunları sola; sonra ikinci satırın 1'li sütunlarını kalan düzen içinde sola taşı.
4. İlk sütundaki 1'li satırları yukarı; sonra diğer sütunlarla sürdür.
5. Köşegen boyunca yoğun 1 bloklarını hücre olarak ayır.

### ROC / ikili sıralama
$m$ sütunlu matris için satır değeri:
$$R_i=\sum_{p=1}^{m}b_{ip}2^{m-p}$$
$n$ satırlı matris için sütun değeri:
$$C_j=\sum_{p=1}^{n}b_{pj}2^{n-p}$$

Satırları ve sütunları ikili değerlerine göre yeniden sırala; matris değişmeyene kadar tekrarla. Yaygın ROC gösteriminde sol/üst en büyük ikili ağırlıktır ve değerler azalan sıralanır. Slaytta ağırlık yönü “sağdan sola/alttan üste” tarif edildiğinden, sınavda **verilen ağırlık yönü ile sıralama yönünü birlikte** izle.

> [!warning]
> ROC hücre sınırını otomatik çizmez; sıralama sonunda 1'lerin yoğunlaştığı bloklar yorumlanır.

## 2 - Tam çözümlü kaynak örneği: DCA
> [!example] Kaynak: HF05, slayt 20-22; matris PPTX görselinden doğrulandı

Başlangıç ilişkileri:
- P1: M1,M3; P2: M1; P3: M2,M4,M5
- P4: M1,M3; P5: M2; P6: M4,M5

Satır toplamları: $(2,1,3,2,1,2)$; makine toplamları M1=3, diğerlerinin her biri 2'dir.

Kaynak nihai sırası:
- Sütunlar: M5-M4-M2-M3-M1
- Satırlar: P3-P6-P5-P4-P1-P2

Hücre 1: makineler M2,M4,M5; parçalar P3,P5,P6. Hücre 2: makineler M1,M3; parçalar P1,P2,P4. Her 1 kendi bloğunda kaldığı için bu örnekte blok dışı istisna yoktur.

## 3 - Tam çözümlü öğretim örneği: ROC
> [!example] Kaynak tablosu bozuk OLE önizlemesi olduğu için denetlenebilir öğretim örneği

$$B=\begin{bmatrix}1&0&1\\0&1&1\\1&0&0\end{bmatrix}$$

Satır ağırlıkları 4,2,1:
$$R=(5,3,4)$$
Azalan sıra: satır 1,3,2.

Yeni matriste sütun değerleri, üstten alta 4,2,1 ağırlıklarıyla:
- sütun 1: $1(4)+1(2)+0(1)=6$
- sütun 2: $0+0+1=1$
- sütun 3: $1(4)+0+1=5$

Azalan sütun sırası 1,3,2 olur. Sonraki turda sıra değişmezse durulur.

## 4 - Kademeli örnek
> [!question]
> Satırlar A=`1100`, B=`0011`, C=`1000`; ağırlıklar 8,4,2,1.
> 1. $R_A=\_\_$, $R_B=\_\_$, $R_C=\_\_$.
> 2. Azalan satır sırası nedir?
> [!answer]- Çözüm
> $R_A=12$, $R_B=3$, $R_C=8$; sıra A-C-B.

## 5 - Bağımsız sorular
### L1
> [!question]
> P parçası M1,M3,M4 kullanıyorsa satır toplamı nedir?
> [!answer]- Çözüm
> 3.

### L2
> [!question]
> `0101` satırının 8,4,2,1 ağırlıklarıyla ROC değeri nedir?
> [!answer]- Çözüm
> $0+4+0+1=5$.

### L3
> [!question]
> Bir makine iki hücrenin birçok parçasınca zorunlu kullanılıyorsa sorun ve üç çözüm yaz.
> [!answer]- Çözüm
> Darboğaz/ortak makinedir. Hücre sınırına koyma, makineyi çoğaltma, parçayı yeniden tasarlama veya fason üretim seçeneklerinden üçü yazılır.

## 6 - Çıkış bileti
1. DCA'nın satır ve sütun öteleme mantığını yaz.
2. ROC satır değeri formülünü yaz.
3. İkili matrisin saklayamadığı iki bilgi nedir?

## 7 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kaynak + kademeli |  |  |  |
| D1 |  | DCA matrisi |  |  |  |
| D3 |  | ROC turu |  |  |  |
| D7 |  | DCA/ROC karma |  |  |  |
| D14 |  | Darboğaz yorumu |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| 1'i işlem sayısı sanmak | Matris yalnız var/yok bilgisidir | Hücre anlamını başta yaz |
| ROC'ta ağırlık yönünü ters almak | Ondalık değer ve sıra değişir | 2'nin kuvvetlerini tablo üstüne yaz |
| Tek satır sıralayıp durmak | Sütunlar da satırları değiştirir | Matris değişmeyene dek iki adımı tekrarla |

## Kaynaklar
- [[HF5-P5-Akış, Alan ve Etkinlik İlişkileri I 2025.pptx|HF05 sunumu]], slayt 18-34
- [[05 Kaynaklar/MarkItDown/HF05 - Ham|HF05 ham metni]], satır 222-426
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
