---
hafta: 6
konu: faaliyet ilişki diyagramı ve bölüm alan gereksinimi
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, rel-chart, iliski-diyagrami, alan-hesabi]
kaynak: HF06 slayt 63-107
---

# HF06B - Faaliyet İlişki Diyagramı ve Alan Hesabı

![[07 Ekler/Diyagramlar/faaliyet-iliski-diyagrami.svg]]

> [!summary] Bir cümlede
> Akış ve akış dışı gerekçeler A-E-I-O-U-X ilişkilerine çevrilir; faaliyet diyagramına alan gereksinimleri eklenerek ölçekli mekân ilişkisi oluşturulur.

## Öğrenme hedefleri
- [ ] Akış miktarlarını ilişki sınıflarına çevirebilirim.
- [ ] A-E-I-O-U-X ve gerekçe kodlarıyla REL chart kurabilirim.
- [ ] Alan katsayısıyla işletme donanım alanı hesaplayabilirim.
- [ ] Ara depo, kalite, serbest ve ulaşım alanlarını ekleyebilirim.

## 0 - Soğuk başlangıç
> [!question]
> İlişki ağırlıkları A=4,E=3,I=2,O=1,U=0,X=-1 ise A ile X'i aynı çizim hedefi gibi ele almak neden yanlıştır?
> [!answer]- Yanıt
> A yakınlığı zorlar; X ayrılığı gerektirir. İşaretleri ve geometrik hedefleri ters yönlüdür.

## 1 - Öğreten not
### REL chart
Her bölüm çifti için:
- ilişki kodu: A, E, I, O, U, X/XX,
- gerekçe kodu: ör. 01 ortak ekipman, 02 malzeme, 03 personel, 04 denetim, 06 gürültü/kirlilik.

Kaynak sayısal gösterimi: A=4,E=3,I=2,O=1,U=0,X=-1; XX daha büyük negatif ceza alabilir.

Akıştan ilişkiye geçişte sınıf sınırları probleme göre kurulur. HF06 kaynak örneği: 0-11 U, 12-22 O, 23-34 I, 35-46 E, 47-57 A. Slayttaki “11-22” yazımı 11'i iki sınıfa soktuğu için ayrık sınır olarak 12-22 yorumlanmalıdır.

### Diyagram sırası
1. Önce A bağlarını çiz.
2. E, sonra I ve O bağlarını ekleyip her turda düzenle.
3. X/XX çiftlerini uzak tut.
4. Çizgi kesişmelerini azalt; önemli bağları kısa tut.
5. Bütün bölümlerin ve önemli ilişkilerin temsil edildiğini denetle.

### Alan hesabı
Makine türü $j$ için taban alanı $A_{tb,j}$, alan katsayısı $K_{A,j}$, adet $M_j$:
$$A_{id}=\sum_j M_jK_{A,j}A_{tb,j}$$

Kaynak görselindeki destek alanı yaklaşık katsayıları:
$$A_{ad}=0{,}20A_{id},\quad A_{kk}=0{,}13A_{id},\quad A_{sa}=0{,}18A_{id},\quad A_{uy}=0{,}25A_{id}$$

Bu dört kalem kullanılıyorsa:
$$A_{top}=A_{id}(1+0{,}20+0{,}13+0{,}18+0{,}25)=1{,}76A_{id}$$

Personel, bakım, tesis hizmetleri ve özel depolar ayrıca eklenebilir; aynı alanı iki kez sayma.

## 2 - Tam çözümlü kaynak örneği: akış ilişkileri
> [!example] Kaynak: HF06, slayt 83-85
> Toplam akışlar: B-D=56, A-C=44, D-E=42, B-C=30, C-D=14, A-B=12.

Kaynak sınıflarıyla:
- B-D: A
- A-C ve D-E: E
- B-C: I
- C-D ve A-B: O
- Akışsız çiftler yalnız akış ölçütü kullanılıyorsa U'dur; X ancak ayrı bir istenmeme gerekçesi varsa verilmelidir.

> [!warning] Kaynak tutarsızlığı
> Slayt 85 akışsız çiftleri X göstermiştir. X “arzu edilmez” demektir; sıfır akış tek başına X kanıtı değildir. Sınavda hocanın verilen sınıf tablosunu uygularken bu varsayımı açık yaz.

## 3 - Tam çözümlü kaynak örneği: alan katsayısı
> [!example] Kaynak: HF06, slayt 95-97; katsayı tablosu PPTX görselinden okundu
> 20 adet 10 m², 15 adet 13 m², 5 adet 7 m² tezgâh. Tablo katsayıları sırasıyla 3,11; 3,00; 3,42.

$$A_{id}=20(10)(3{,}11)+15(13)(3{,}00)+5(7)(3{,}42)$$
$$A_{id}=622+585+119{,}7=1.326{,}7\,m^2$$

Eğer dört genel destek oranı da uygulanırsa:
$$A_{top}=1{,}76(1326{,}7)=2.334{,}992\approx2.335{,}0\,m^2$$

İkinci sonuç öğretim genişletmesidir; kaynak slayt 97 yalnız ana fonksiyon alanını sorar.

## 4 - Kademeli örnek
> [!question]
> $A_{id}=500\,m^2$. Ara depo, kalite kontrol, serbest ve ulaşım oranları kaynak değerleridir.
> 1. Dört destek alanını bul.
> 2. Toplamı bul.
> [!answer]- Çözüm
> 100, 65, 90, 125 m²; destek toplamı 380, genel toplam $500+380=880\,m^2$.

## 5 - Bağımsız sorular
### L1
> [!question]
> Akış 33 ise kaynak örneği sınıflarında ilişki kodu ve puanı nedir?
> [!answer]- Çözüm
> I ve 2.

### L2
> [!question]
> 8 adet makinenin taban alanı 6 m², alan katsayısı 3,65. $A_{id}$?
> [!answer]- Çözüm
> $8(6)(3{,}65)=175{,}2\,m^2$.

### L3
> [!question]
> A-B ilişkisi A, A-C ilişkisi X, B-C ilişkisi E. Diyagramdaki üç geometrik hedefi yaz.
> [!answer]- Çözüm
> A-B en yakın; B-C mümkün olduğunca yakın; A-C ayrı. Çakışma varsa A ve X zorunluluklarına öncelik verilip kısıt açıklanır.

## 6 - Çıkış bileti
1. REL chart ilişki kodu ile gerekçe kodunu ayır.
2. Akışsız çift neden otomatik X değildir?
3. $A_{id}$ ve $A_{top}$ arasındaki farkı yaz.

## 7 - Tekrar kaydı
| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kaynak + kademeli |  |  |  |
| D1 |  | Akış sınıflama |  |  |  |
| D3 |  | Alan katsayısı |  |  |  |
| D7 |  | REL + alan karma |  |  |  |
| D14 |  | Mekân diyagramı |  |  |  |

## Hata kartı
| Yanlış adım | Neden yanlış? | Kontrol |
|---|---|---|
| Sıfır akışı X yapmak | X için olumsuz gerekçe gerekir | Akış dışı gerekçeyi ara |
| Yüzdeleri art arda uygulamak | Kaynak oranları $A_{id}$ tabanlıdır | Her kalemi doğrudan $A_{id}$ ile çarp |
| Katsayıyı yalnız makine sayısıyla çarpmak | Taban alanı eksik kalır | $MKA_{tb}$ birimini kontrol et |

## Kaynaklar
- [[HF6-P6-Akış, Alan ve Etkinlik İlişkileri II 2025.pptx|HF06 sunumu]], slayt 63-107
- [[05 Kaynaklar/MarkItDown/HF06 - Ham|HF06 ham metni]], satır 785-1369
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
