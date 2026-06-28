---
hafta: 9
tags: [ders/tesis-planlama, sorular, algoritma/blocplan, algoritma/logic, algoritma/mcraft]
soru_sayısı: 5
---

# HF09 — Yerleşim Tasarımı III Soruları (MCRAFT · BLOCPLAN · LOGIC)

> [!info] Nasıl kullan?
> Soruyu gör → her alt soruyu (a–d) kapalı kitap çözmeyi dene → çözümü aç → hata kodla.
> Bağlantılı ders notu: [[01 Ders Notları/HF09 - Yerleşim Tasarımı III|HF09]] · Paketler: [[09 Öğrenme Paketleri/HF09B - BLOCPLAN|HF09B]] · [[09 Öğrenme Paketleri/HF09C - LOGIC ve Kesim Ağacı|HF09C]]

---

### S01 — Kolay — BLOCPLAN Akış → REL Dönüşümü

> [!question] Soru
> ASELSAN'ın Gölbaşı tesisinde dört üretim bölümü (A: Kart Dizgi, B: Test, C: Kalite, D: Sevkiyat) arasında günlük yönlü malzeme akışları izlenmiştir. Yerleşim mühendisi Ece Hanım, bu yönlü akışları BLOCPLAN'ın nitel REL şemasına çevirip hangi bölümlerin yan yana konması gerektiğini belirleyecektir.
>
> | Çift | $f_{ij}$ | $f_{ji}$ |
> |---|---:|---:|
> | A–B | 25 | 15 |
> | A–C | 8 | 2 |
> | A–D | 5 | 5 |
> | B–C | 30 | 20 |
> | B–D | 12 | 8 |
> | C–D | 4 | 6 |
>
> a) Simetrik toplam akış matrisini ($F_{ij}=f_{ij}+f_{ji}$) kurun.
> b) En büyük $F$ değerine göre 5 eşit aralıklı A–E–I–O–U sınıf sınırlarını belirleyin.
> c) Her çiftin REL ilişki kodunu atayın.
> ç) Hangi çift "A" (mutlak gerekli) kodunu alır; BLOCPLAN'da A ve E çiftlerini komşu yapmak puanı neden artırır?
> d) Mühendis yanlışlıkla yalnız $f_{ij}$ değerini sınıflasaydı (toplamı almasaydı) hangi çiftte hata yapardı? Bir örnekle açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Yönlü akış matrisini BLOCPLAN'ın nitel REL şemasına dönüştürmek.
> **Hangi algoritma:** BLOCPLAN Adım 1 (simetrikleştir) + Adım 2 (sınıfla).
> **Dikkat:** $f_{ij} \ne f_{ji}$ olabilir; toplamı almadan sınıflamayın. Aralıkları $\max F / 5$ genişliğinde ve dahil sınırlı kurun.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Her çift için iki yöndeki akışı toplayıp simetrik $F_{ij}$ buluyoruz.
> Formül: $F_{ij} = f_{ij} + f_{ji}$.
> Hesap:
>
> | Çift | $f_{ij}$ | $f_{ji}$ | $F_{ij}$ |
> |---|---:|---:|---:|
> | A–B | 25 | 15 | **40** |
> | A–C | 8 | 2 | **10** |
> | A–D | 5 | 5 | **10** |
> | B–C | 30 | 20 | **50** |
> | B–D | 12 | 8 | **20** |
> | C–D | 4 | 6 | **10** |
>
> Sonuç: En büyük simetrik akış $F_{BC}=50$.
> Neden: BLOCPLAN ilişki yönünü değil, iki bölüm arasındaki toplam etkileşimi önemser.
>
> **b)**
> Ne yapıyoruz: $\max F$'i 5 eşit dilime bölerek A–E–I–O–U sınırlarını kuruyoruz.
> Formül: Aralık genişliği $= \max F / 5 = 50/5 = 10$.
> Hesap:
>
> | Aralık | Kod |
> |---|---|
> | 41 – 50 | **A** |
> | 31 – 40 | **E** |
> | 21 – 30 | **I** |
> | 11 – 20 | **O** |
> | 0 – 10 | **U** |
>
> Sonuç: 10 birim genişlikte 5 eşit dilim.
> Neden: En yüksek akış en üst sınıfı tanımlar, geri kalanlar buna göre ölçeklenir.
>
> **c)**
> Ne yapıyoruz: Her $F_{ij}$'yi ait olduğu aralığa göre kodluyoruz.
> Hesap:
>
> | Çift | $F_{ij}$ | Kod |
> |---|---:|---|
> | A–B | 40 | **E** |
> | A–C | 10 | **U** |
> | A–D | 10 | **U** |
> | B–C | 50 | **A** |
> | B–D | 20 | **O** |
> | C–D | 10 | **U** |
>
> Sonuç: B–C → A; A–B → E; B–D → O; A–C, A–D, C–D → U.
> Neden: Sayısal akış bandı doğrudan nitel ilişki yoğunluğuna karşılık gelir.
>
> **ç)**
> Ne yapıyoruz: En güçlü ilişkiyi belirleyip komşuluğun etkisini açıklıyoruz.
> Sonuç: **B–C** çifti "A" kodunu alır (F=50, en üst aralık). A–B "E" kodludur.
> Neden: BLOCPLAN'da komşu yapılan çiftlerin ilişki ağırlığı $Z_A$ komşuluk puanına eklenir; A (en yüksek) ve E (ikinci) çiftlerini komşu yapmak $Z_A$'yı en çok artırır. B–C ve A–B yan yana gelmezse en büyük katkılar kaybolur.
>
> **d)**
> Ne yapıyoruz: Simetrikleştirmeyi atlamanın yarattığı yanlışı bir çiftte gösteriyoruz.
> Sonuç: C–D çifti. Yalnız $f_{CD}=4$ alınırsa zaten U çıkar; ama tam ters yönde A–B çiftinde $f_{AB}=25$ tek başına 21–30 bandına düşüp **I** kodu alır — oysa simetrik $F_{AB}=40$ ile gerçek kod **E**'dir.
> Neden: Tek yönlü akış, çiftin gerçek etkileşim şiddetini eksik gösterir; BLOCPLAN simetrik toplamı kullanır. Önce topla, sonra sınıfla.
>
> > [!warning] Yaygın hata
> > $f_{ij}$ veya $f_{ji}$'yi tek başına sınıflamak. BLOCPLAN simetrik toplam akışı kullanır.

---

### S02 — Orta — BLOCPLAN $Z_A$ Komşuluk Puanı

> [!question] Soru
> TEI'nin Eskişehir motor fabrikasında beş atölye (1–5) için sayısal REL ağırlıkları aşağıda verilmiştir (A=10, E=5, I=2, O=1, U=0). Tesis ekibi iki farklı 2-bantlı taslak çizmiş ve hangisinin komşuluk puanının daha yüksek olduğunu tartışmaktadır.
>
> | Çift | $w_{ij}$ | Çift | $w_{ij}$ |
> |---|---:|---|---:|
> | 1–2 | 10 | 2–5 | 0 |
> | 1–3 | 5 | 3–4 | 1 |
> | 1–4 | 0 | 3–5 | 5 |
> | 1–5 | 2 | 4–5 | 2 |
> | 2–3 | 2 | | |
> | 2–4 | 10 | | |
>
> **Yerleşim I:**
> ```
> | 1 | 2 | 3 |
> | 4 | 5 |   |
> ```
> **Yerleşim II:**
> ```
> | 1 | 3 | 5 |
> | 2 | 4 |   |
> ```
> Her bölüm 1 birim kare.
>
> a) Yerleşim I için kenar-komşu çiftlerini ($a_{ij}=1$) listeleyin.
> b) Yerleşim I'in komşuluk puanı $Z_{A,I} = \sum w_{ij}\,a_{ij}$'yi hesaplayın.
> c) Yerleşim II için kenar-komşuları ve $Z_{A,II}$'yi hesaplayın.
> ç) İki yerleşimi karşılaştırın: hangisi daha iyi ve sebebi nedir?
> d) Yerleşim I'de köşe teması olan 3–5 çifti neden puana katılmadı? BLOCPLAN'ın komşuluk kuralını açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** İki alternatif yerleşimin komşuluk puanını karşılaştırmak.
> **Hangi algoritma:** BLOCPLAN $Z_A$.
> **Dikkat:** $a_{ij}=1$ yalnız kenar paylaşan çiftler için; köşe teması yeterli değil.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: `|1|2|3|` / `|4|5| |` ızgarasında ortak kenarı olan çiftleri buluyoruz.
> Hesap:
> - Yatay: 1–2 ✓, 2–3 ✓, 4–5 ✓
> - Dikey: 1–4 ✓, 2–5 ✓
> - 3–5 → yalnız köşe teması → kenar değil, sayılmaz
> Sonuç: Komşu çiftler {1–2, 2–3, 4–5, 1–4, 2–5}.
> Neden: Yalnız ortak sınıra sahip kareler malzeme/etkileşim taşıyabilir.
>
> **b)**
> Ne yapıyoruz: Komşu çiftlerin ağırlıklarını topluyoruz.
> Formül: $Z_{A,I} = w_{12}+w_{23}+w_{45}+w_{14}+w_{25}$.
> Hesap: $10+2+2+0+0 = \mathbf{14}$.
> Sonuç: $Z_{A,I}=14$.
> Neden: 1–2 (10) tek güçlü çift; geri kalanlar zayıf veya sıfır.
>
> **c)**
> Ne yapıyoruz: `|1|3|5|` / `|2|4| |` ızgarasında aynı işlemi yapıyoruz.
> Hesap:
> - Yatay: 1–3 ✓, 3–5 ✓, 2–4 ✓
> - Dikey: 1–2 ✓, 3–4 ✓
> $$Z_{A,II} = w_{13}+w_{35}+w_{24}+w_{12}+w_{34} = 5+5+10+10+1 = \mathbf{31}$$
> Sonuç: $Z_{A,II}=31$.
> Neden: En güçlü iki çift (1–2=10, 2–4=10) bu yerleşimde komşu kalır.
>
> **ç)**
> Ne yapıyoruz: İki puanı kıyaslıyoruz.
> Sonuç: $Z_{A,II}=31 > Z_{A,I}=14$ → **Yerleşim II** üstün.
> Neden: Yerleşim II en güçlü çiftleri (1–2 ve 2–4, ikisi de 10) komşu yapıyor; Yerleşim I bu çiftleri ayırıyor. Yerleşim tasarlarken "güçlü kim, güçlü kimi istiyor?" diye bakmak gerekir.
>
> **d)**
> Ne yapıyoruz: Köşe temasının neden sayılmadığını açıklıyoruz.
> Sonuç: 3 ve 5 yalnız bir köşe noktasında değiyor, ortak kenarları yok; bu yüzden $a_{35}=0$.
> Neden: BLOCPLAN komşuluğu "paylaşılan kenar uzunluğu" üzerinden tanımlar. Köşe teması ortak sınır üretmediğinden malzeme akışına/komşuluk avantajına katkı saymaz.
>
> > [!tip] Sezgi
> > Güçlü ağırlıklı çiftleri komşu yapamayan bir yerleşim, kalan tüm çiftleri kusursuz dizse bile düşük $Z_A$ alır.

---

### S03 — Orta — BLOCPLAN $ER$ Etkinlik Oranı

> [!question] Soru
> TEI ekibi S02'deki aynı REL ağırlık matrisini ve iki yerleşimin $Z_A$ değerlerini ($Z_{A,I}=14$, $Z_{A,II}=31$) kullanarak yöneticiye yerleşimin "potansiyelin yüzde kaçını yakaladığını" raporlayacaktır. Bunun için etkinlik oranını (ER) hesaplaması gerekir:
>
> $$ER = Z_A \,/\, \sum_{i<j} \max(w_{ij},\,0)$$
>
> a) ER paydasını (pozitif $w_{ij}$'lerin toplamı) kurun.
> b) $ER_I$ ve $ER_{II}$ değerlerini hesaplayın.
> c) Sonuçları yorumlayın: ER ve $Z_A$ aynı yönü mü gösteriyor?
> ç) İki yerleşim kıyaslanırken payda neden değişmez? Açıklayın.
> d) ER'nin ham $Z_A$ puanına kıyasla yöneticiye sunumda avantajı nedir?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** $ER$ paydası nasıl kurulur, $Z_A$ ile farkı ne?
> **Hangi algoritma:** BLOCPLAN $ER$.
> **Dikkat:** Payda = tüm pozitif $w_{ij}$'lerin toplamı. $U=0$ ve $X$ paydaya girmez.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: $w_{ij}>0$ olan çiftleri seçip topluyoruz.
> Hesap:
>
> | Çift | $w_{ij}$ | Pozitif mi? |
> |---|---:|---|
> | 1–2 | 10 | ✓ |
> | 1–3 | 5 | ✓ |
> | 1–4 | 0 | ✗ |
> | 1–5 | 2 | ✓ |
> | 2–3 | 2 | ✓ |
> | 2–4 | 10 | ✓ |
> | 2–5 | 0 | ✗ |
> | 3–4 | 1 | ✓ |
> | 3–5 | 5 | ✓ |
> | 4–5 | 2 | ✓ |
>
> $$\text{Payda} = 10+5+2+2+10+1+5+2 = \mathbf{37}$$
> Sonuç: Payda = 37.
> Neden: U=0 ilişkiler "mümkün en iyi" puana katkı vermez, paydaya girmez.
>
> **b)**
> Ne yapıyoruz: Her $Z_A$'yı paydaya bölüyoruz.
> Hesap:
> $$ER_I = \frac{14}{37} \approx \mathbf{0{,}38}, \qquad ER_{II} = \frac{31}{37} \approx \mathbf{0{,}84}$$
> Sonuç: $ER_I \approx 0{,}38$, $ER_{II} \approx 0{,}84$.
> Neden: ER, $Z_A$'nın normalize hâli; "mümkün olan en iyinin yüzde kaçı?" sorusunu yanıtlar.
>
> **c)**
> Ne yapıyoruz: İki ölçütün yönünü karşılaştırıyoruz.
> Sonuç: Evet, $Z_A$ ve ER aynı yönde — Yerleşim II her ikisinde de üstün.
> Neden: Payda her iki yerleşimde aynı olduğundan ER yalnız $Z_A$'nın ölçekli kopyasıdır; sıralamayı değiştirmez.
>
> **ç)**
> Ne yapıyoruz: Paydanın yerleşimden bağımsızlığını gerekçelendiriyoruz.
> Sonuç: Payda yalnız REL matrisine bağlı (pozitif ağırlıkların toplamı), yerleşim geometrisine bağlı değil.
> Neden: "Mümkün olan en iyi" senaryo tüm pozitif ilişkilerin komşu olduğu varsayımıdır; bu üst sınır geometriyle değişmez, sadece gerçekleşen $Z_A$ değişir.
>
> **d)**
> Ne yapıyoruz: ER'nin sunum avantajını açıklıyoruz.
> Sonuç: ER yüzde olarak yorumlanabilir (0–1 arası): "Yerleşim II pozitif ilişkilerin %84'ünü komşuluğa yansıttı."
> Neden: Ham $Z_A=31$ tek başına büyük mü küçük mü belli değil; ER bir üst sınıra göre normalize ettiği için farklı problemler arasında bile kıyaslanabilir bir başarı yüzdesi verir.
>
> > [!warning] ER paydası sabit
> > İki yerleşimi kıyaslarken payda her zaman aynı; yalnız $Z_A$ değişir.

---

### S04 — Orta — BLOCPLAN $RD$ İlişki-Uzaklık Puanı

> [!question] Soru
> Roketsan'ın bir üretim binasında dört bölüm (P: Prekürsör Hazırlama, Q: Dolum, R: Montaj, S: Test) yerleştirilecektir. Süreç mühendisi Kerem Bey iki farklı $2\times2$ yerleşim çizmiş ve hangisinin akış-ağırlıklı toplam mesafesini daha küçük yaptığını ölçmek istemektedir. Sayısal REL ağırlıkları: $w_{PQ}=10$, $w_{PR}=5$, $w_{PS}=1$, $w_{QR}=2$, $w_{QS}=0$, $w_{RS}=10$.
>
> | Bölüm | Yerleşim A merkezi | Yerleşim B merkezi |
> |---|---|---|
> | P | (5, 15) | (5, 15) |
> | Q | (15, 15) | (15, 5) |
> | R | (5, 5) | (5, 5) |
> | S | (15, 5) | (15, 15) |
>
> Rektilineer mesafe: $d_{ij}=|x_i-x_j|+|y_i-y_j|$. İlişki-uzaklık puanı: $RD = \sum_{i<j} w_{ij}\,d_{ij}$ (küçük olması istenir).
>
> a) Yerleşim A için her çiftin $d_{ij}$ ve $w_{ij}\cdot d_{ij}$ değerini tablolaştırın.
> b) $RD_A$ ve $RD_B$ değerlerini hesaplayın.
> c) Hangi yerleşim daha iyidir ve neden?
> ç) $RD$ ölçütünün yönü $Z_A$ ve $ER$'den nasıl farklıdır? "İyi yerleşim" üç ölçütte hangi yönleri gösterir?
> d) Tek başına $RD$'ye bakmak yeterli mi? Tam BLOCPLAN değerlendirmesinin üç ölçütü nasıl birlikte kullandığını açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Mesafe×ağırlık çarpımını toplayarak yerleşim kalitesini nicel ölçmek.
> **Hangi algoritma:** BLOCPLAN $RD$ (REL-DIST).
> **Dikkat:** $RD$ küçük olsun istenir; $Z_A$ ve $ER$'nin aksine yönü ters.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Yerleşim A koordinatlarıyla (P=(5,15), Q=(15,15), R=(5,5), S=(15,5)) rektilineer mesafeleri buluyoruz.
> Hesap:
>
> | Çift | $w_{ij}$ | $|\Delta x|$ | $|\Delta y|$ | $d_{ij}$ | $w\cdot d$ |
> |---|---:|---:|---:|---:|---:|
> | P–Q | 10 | 10 | 0 | 10 | 100 |
> | P–R | 5 | 0 | 10 | 10 | 50 |
> | P–S | 1 | 10 | 10 | 20 | 20 |
> | Q–R | 2 | 10 | 10 | 20 | 40 |
> | Q–S | 0 | 0 | 10 | 10 | 0 |
> | R–S | 10 | 10 | 0 | 10 | 100 |
>
> Sonuç: $w\cdot d$ sütunu yukarıdaki gibi.
> Neden: En güçlü çiftler (P–Q, R–S) en kısa mesafede (10) → düşük katkı.
>
> **b)**
> Ne yapıyoruz: A için sütunu topluyor, sonra B koordinatlarıyla (Q=(15,5), S=(15,15)) aynısını yapıyoruz.
> Hesap:
> $$RD_A = 100+50+20+40+0+100 = \mathbf{310}$$
>
> | Çift | $w_{ij}$ | $d_{ij}$ (B) | $w\cdot d$ |
> |---|---:|---:|---:|
> | P–Q | 10 | 20 | 200 |
> | P–R | 5 | 10 | 50 |
> | P–S | 1 | 10 | 10 |
> | Q–R | 2 | 10 | 20 |
> | Q–S | 0 | 10 | 0 |
> | R–S | 10 | 20 | 200 |
>
> $$RD_B = 200+50+10+20+0+200 = \mathbf{480}$$
> Sonuç: $RD_A=310$, $RD_B=480$.
> Neden: B'de P–Q ve R–S köşegen konumda (d=20), katkıları iki katına çıkıyor.
>
> **c)**
> Ne yapıyoruz: İki RD'yi kıyaslıyoruz.
> Sonuç: $RD_A=310 < RD_B=480$ → **Yerleşim A** daha iyi.
> Neden: A'da en güçlü çiftler (her ikisi $w=10$) birbirine yakın; B'de uzak. RD'de ağırlık×mesafe çarpıldığından güçlü çiftin uzak kalması cezayı büyütür.
>
> **ç)**
> Ne yapıyoruz: Üç ölçütün yönlerini karşılaştırıyoruz.
> Sonuç: $Z_A$ ↑ (büyük iyi), $ER$ ↑ (büyük iyi), $RD$ ↓ (küçük iyi).
> Neden: $Z_A$ ve $ER$ "ne kadar çok güçlü ilişki komşu?" der; $RD$ "güçlü ilişkiler ne kadar uzakta?" der — bu yüzden RD'de minimizasyon hedeflenir.
>
> **d)**
> Ne yapıyoruz: Tek ölçütün yetersizliğini ve üçlü değerlendirmeyi açıklıyoruz.
> Sonuç: Tek başına RD yeterli değildir; tam analizde $Z_A$, $ER$ ve $RD$ birlikte raporlanır. İyi yerleşim: $Z_A$↑, $ER$↑, $RD$↓ aynı anda.
> Neden: $Z_A$ yalnız komşu/komşu değil ikilisine bakar (mesafe ölçeğini görmez); RD mesafeyi ölçer ama normalize değildir; ER bir başarı yüzdesi verir. Üçü farklı boyutu yakaladığından birlikte bakılır.
>
> > [!tip] ZER özeti
> > $Z_A$↑, $ER$↑, $RD$↓ → iyi yerleşim. Üç ölçüt çelişirse karar verici öncelik belirler.

---

### S05 — Zor — LOGIC Kesim Ağacı: Tam Uygulama

> [!question] Soru
> TUSAŞ'ın bir kompozit üretim binası $20\times10 = 200\,\text{m}^2$ boyutlarındadır. Yerleşim uzmanı Can Bey, dört bölümü (A, B, C, D) giyotin kesim ağacıyla yerleştirip toplam akış-uzaklık maliyetini hesaplayacaktır.
>
> | Bölüm | Alan (m²) |
> |---|---:|
> | A | 40 |
> | B | 60 |
> | C | 50 |
> | D | 50 |
>
> Simetrik akış ($f_{ij}=f_{ji}$), birim taşıma maliyeti $c=1$ TL/birim·m:
>
> | Çift | Akış $f_{ij}$ |
> |---|---:|
> | A–B | 20 |
> | A–C | 5 |
> | A–D | 3 |
> | B–C | 15 |
> | B–D | 8 |
> | C–D | 12 |
>
> Kesim ağacı **$V(H(A,B),\;H(C,D))$**: kök dikey kesim; sol yarı yatay A-üst/B-alt; sağ yarı yatay C-üst/D-alt.
>
> a) Dikey (kök) kesim konumunu alan oranıyla bulun.
> b) Sol ve sağ alt ağaçların blok boyutlarını hesaplayın.
> c) Bölümlerin ağırlık merkezi koordinatlarını bulun.
> ç) Rektilineer mesafelerle toplam akış-uzaklık maliyetini $C = \sum_{i<j} f_{ij}\,d_{ij}$ hesaplayın.
> d) LOGIC kesim ağacının BLOCPLAN'ın bantlı yapısına göre avantajını açıklayın; "BLOCPLAN çözüm kümesi ⊆ LOGIC çözüm kümesi" ne demektir?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** LOGIC kesim ağacından gerçek blok koordinatları ve maliyet.
> **Hangi algoritma:** LOGIC (giyotin kesim + alan oranı).
> **Dikkat:** Kesim konumu alan oranıyla: $x_L = W_S \cdot (A_L / A_S)$. Her adımda bölümün kendi alt bölgesine göre oranla.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Kökte sol dal {A,B}'nin toplam alan oranını binanın genişliğine uyguluyoruz.
> Formül: $x_L = W \cdot (A_{sol}/A_{toplam})$.
> Hesap: $A_{sol}=40+60=100$, $x_L = 20\cdot(100/200) = \mathbf{10}$ m.
> Sonuç: Sol yarı 10×10 m, sağ yarı 10×10 m.
> Neden: Giyotin kesim alanları orantılı böler; eşit alanlı dallar genişliği yarıya ayırır.
>
> **b)**
> Ne yapıyoruz: Her yarıyı yatay kesimle alt-üst bloklara ayırıyoruz.
> Hesap:
> Sol H(A,B), genişlik 10, yükseklik 10:
> - B (alt): $10\times(60/100)=6$ m → blok $10\times6$
> - A (üst): $10\times(40/100)=4$ m → blok $10\times4$
> Sağ H(C,D), genişlik 10, yükseklik 10:
> - D (alt): $10\times(50/100)=5$ m → blok $10\times5$
> - C (üst): $10\times(50/100)=5$ m → blok $10\times5$
> Sonuç: A:10×4, B:10×6, C:10×5, D:10×5.
> Neden: Alt ağaçta yükseklik o bölgenin (10 m) alan oranıyla bölünür.
>
> ASCII yerleşim (x: 0→20, y: 0→10):
> ```
> y=10 +----------+----------+
>      |    A     |    C     |
> y=6  |  10×4 m  +----------+
> y=5  |          |    D     |
>      |    B     |  10×5 m  |
>      |  10×6 m  |          |
> y=0  +----------+----------+
>      x=0       x=10       x=20
> ```
>
> **c)**
> Ne yapıyoruz: Her bloğun x ve y aralığının orta noktasını alıyoruz.
> Hesap:
>
> | Bölüm | x aralığı | y aralığı | Merkez |
> |---|---|---|---|
> | B | 0–10 | 0–6 | **(5, 3)** |
> | A | 0–10 | 6–10 | **(5, 8)** |
> | D | 10–20 | 0–5 | **(15, 2,5)** |
> | C | 10–20 | 5–10 | **(15, 7,5)** |
>
> Sonuç: Yukarıdaki merkezler.
> Neden: Dikdörtgen blok merkezi köşelerin ortasıdır.
>
> **ç)**
> Ne yapıyoruz: Merkezler arası rektilineer mesafeyi bulup akışla çarpıp topluyoruz.
> Hesap:
>
> | Çift | $f_{ij}$ | $|\Delta x|$ | $|\Delta y|$ | $d_{ij}$ | $f\cdot d$ |
> |---|---:|---:|---:|---:|---:|
> | A–B | 20 | 0 | 5 | 5 | 100 |
> | A–C | 5 | 10 | 0,5 | 10,5 | 52,5 |
> | A–D | 3 | 10 | 5,5 | 15,5 | 46,5 |
> | B–C | 15 | 10 | 4,5 | 14,5 | 217,5 |
> | B–D | 8 | 10 | 0,5 | 10,5 | 84 |
> | C–D | 12 | 0 | 5 | 5 | 60 |
>
> $$C = 100+52{,}5+46{,}5+217{,}5+84+60 = \mathbf{560{,}5\;\text{TL}}$$
> Sonuç: Toplam maliyet 560,5 TL.
> Neden: En büyük katkı B–C (217,5) — güçlü akışlı bu çift köşegen blokları işgal ediyor.
>
> **d)**
> Ne yapıyoruz: İki yöntemin çözüm uzaylarını karşılaştırıyoruz.
> Sonuç: LOGIC yatay ve dikey kesimleri iç içe geçirebildiğinden BLOCPLAN'ın üretemediği yerleşimleri de üretir; her BLOCPLAN bantlı yerleşimi bir LOGIC ağacıyla temsil edilebilir ama tersi geçerli değildir.
> Neden: BLOCPLAN yalnız 2–3 bantlı dikdörtgen yapılar kurar; LOGIC ağacı daha esnek bölmelere izin verir. Bu yüzden "BLOCPLAN çözüm kümesi ⊆ LOGIC çözüm kümesi": LOGIC daha geniş bir uzayda arar, daha iyi minimuma ulaşma şansı yüksektir.
>
> > [!warning] En yaygın hata
> > Blok yüksekliğini ana bina yüksekliğine değil, o alt bölgenin yüksekliğine göre oranlamak. Sol alt ağaçta B'nin payı $10\times(60/100)=6$ m; 20 m bina genişliğiyle karıştırmayın.
