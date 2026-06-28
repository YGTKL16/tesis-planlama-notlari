---
hafta: 10
tags: [ders/tesis-planlama, sorular]
soru_sayısı: 5
---

# HF10 — Yerleşim Tasarımı IV Soruları
## CORELAP · ALDEP · MULTIPLE

> [!info] Nasıl kullan?
> Soruyu gör → her alt soruyu (a–d) kapalı kitap çöz → `[!answer]-` kutusunu aç → hataları not et.

---

### S01 — Kolay — CORELAP TCR ve İlk Yerleştirme

> [!question] Soru
> Baykar'ın İHA gövde üretim hattında beş bölümün (1–5) yakınlık ilişkileri bir CORELAP çalışması için tabloya dökülmüştür. Ölçek **A = 10 000, E = 1 000, I = 100, O = 10, U = 0**. Yerleşim mühendisi ilk olarak hangi bölümü tezgâh planının merkezine koyacağına karar verecektir.
>
> | | 1 | 2 | 3 | 4 | 5 |
> |---|---|---|---|---|---|
> | **1** | — | A | E | I | O |
> | **2** | A | — | A | E | I |
> | **3** | E | A | — | I | O |
> | **4** | I | E | I | — | U |
> | **5** | O | I | O | U | — |
>
> a) Her bölümün TCR değerini hesaplayın.
> b) En yüksek TCR'li (ilk yerleştirilecek) bölümü belirleyin.
> c) Eşit TCR'li bölümler varsa bağ bozma kuralını uygulayın.
> ç) Bölüm 5 neden en sona kalır; TCR değerini yorumlayın.
> d) Eğer ölçek logaritmik (10'un kuvvetleri) yerine doğrusal (A=5, E=4, I=3, O=2, U=1) seçilseydi ilk yerleşen bölüm değişir miydi? Kısaca gerekçelendirin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Her bölümün diğer tüm bölümlerle ilişki ağırlıklarının toplamı (TCR).
> **Formül:** $TCR_i = \sum_{j \neq i} v(r_{ij})$ — bölümün kendi satırını topla.
> **Dikkat:** Köşegen (kendi kendine) ilişki yoktur. Beraberlikte önce A sayısı bağ bozar.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Her bölümün satırındaki ilişki ağırlıklarını topluyoruz.
> Hesap:
>
> | Bölüm | İlişkiler | Hesap | TCR |
> |---|---|---|---:|
> | 1 | A+E+I+O | 10 000+1 000+100+10 | **11 110** |
> | 2 | A+A+E+I | 10 000+10 000+1 000+100 | **21 100** |
> | 3 | E+A+I+O | 1 000+10 000+100+10 | **11 110** |
> | 4 | I+E+I+U | 100+1 000+100+0 | **1 200** |
> | 5 | O+I+O+U | 10+100+10+0 | **120** |
>
> Sonuç: TCR değerleri yukarıdaki gibi.
> Neden: TCR bölümün toplam "çekiciliğini" ölçer.
>
> **b)**
> Ne yapıyoruz: En büyük TCR'yi seçiyoruz.
> Sonuç: **Bölüm 2** (TCR=21 100) ilk yerleştirilir.
> Neden: İki adet A ilişkisi (1 ve 3 ile) onu açık ara öne taşır; CORELAP en yüksek TCR'li bölümü merkeze koyar.
>
> **c)**
> Ne yapıyoruz: Eşit TCR'li 1 ve 3'ü (11 110) bağ bozma kuralıyla ayırıyoruz.
> Hesap: Bölüm 1 → 1 adet A (Bölüm 2 ile); Bölüm 3 → 1 adet A (Bölüm 2 ile). A sayısı eşit → E sayısına bak: ikisi de 1E. Hâlâ eşit → düşük numara (notasyon kuralı) → Bölüm 1.
> Sonuç: İkinci yerleşmeye Bölüm 1 önce aday.
> Neden: Bağ bozma sırası: en çok A → en çok E → düşük indeks.
>
> **ç)**
> Ne yapıyoruz: Bölüm 5'in TCR'sini yorumluyoruz.
> Sonuç: Bölüm 5 (TCR=120) en zayıf bağlı bölümdür; en sona kalır.
> Neden: Diğerleriyle yalnız O, I, O ve bir U ilişkisi var; hiçbir güçlü (A/E) bağı yok, bu yüzden yerleşimde merkez değil çeper bölgeye düşer.
>
> **d)**
> Ne yapıyoruz: Ölçek değişiminin sıralamayı etkileyip etkilemediğini düşünüyoruz.
> Sonuç: İlk yerleşen yine Bölüm 2 olur, çünkü iki A ilişkisi her ölçekte en büyük katkıyı verir; ancak alt sıralarda eşitlikler/küçük farklar değişebilir.
> Neden: Logaritmik ölçek A'yı çok baskın yapar; doğrusal ölçekte farklar daralır ama Bölüm 2 yine de en fazla yüksek-sınıf ilişkiye sahip olduğundan başı çeker. Ölçek seçimi mutlak sıralamayı değil, ara bölümlerin görece konumunu etkileyebilir.

---

### S02 — Orta — CORELAP Tam Uygulama (4 Bölüm)

> [!question] Soru
> FNSS'nin zırhlı araç montaj atölyesinde 4 bölüm bir CORELAP çalışmasıyla yerleştirilecektir. Ölçek: **A = 125, E = 25, I = 5, O = 1, U = 0**. Süreç planlama uzmanı yerleştirme sırasını çıkaracak, ardından PR puanlarıyla son grid'i kuracaktır.
>
> | | 1 | 2 | 3 | 4 |
> |---|---|---|---|---|
> | **1** | — | A | E | O |
> | **2** | A | — | A | I |
> | **3** | E | A | — | U |
> | **4** | O | I | U | — |
>
> a) TCR değerlerini hesaplayıp yerleştirme sırasını çıkarın.
> b) Bölüm 2'yi merkeze koyup Bölüm 1 için tam komşu ile köşe komşu PR'lerini karşılaştırın.
> c) Bölüm 3 için aday konumların PR'lerini hesaplayıp en iyisini seçin.
> ç) Bölüm 4 için PR hesabını yapıp final grid'ini çizin.
> d) PR'de "tam komşu × 1, köşe komşu × 0,5" katsayıları neden kullanılır? Fiziksel anlamını açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** CORELAP'ın tüm adımları — TCR, seçim sırası, PR hesabı, yerleştirme.
> **Dikkat:** PR'de yalnız yerleşmiş bölümler sayılır. Tam komşu (kenar) × 1, köşe komşu × 0,5.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: TCR'leri hesaplayıp büyükten küçüğe, A-bağına dikkat ederek sıralıyoruz.
> Hesap:
>
> | Bölüm | Hesap | TCR |
> |---|---|---:|
> | 1 | 125+25+1 | **151** |
> | 2 | 125+125+5 | **255** ← en büyük |
> | 3 | 25+125+0 | **150** |
> | 4 | 1+5+0 | **6** |
>
> Seçim sırası: 2 (255) → 1 (151, 2 ile A) → 3 (150, 2 ile A) → 4 (6).
> Sonuç: **2 → 1 → 3 → 4**.
> Neden: Önce en yüksek TCR; sonra yerleşmiş bölümle en güçlü ilişkili adaylar.
>
> **b)**
> Ne yapıyoruz: Bölüm 2 merkeze (konum 0); Bölüm 1'in komşuluk tipine göre PR'sini hesaplıyoruz.
> Hesap: $v(1\!-\!2)=A=125$.
> - Tam komşu (kenar): $PR = 1\times125 = \mathbf{125}$
> - Köşe komşu: $PR = 0{,}5\times125 = \mathbf{62{,}5}$
> Sonuç: Tam komşu konum seçilir; Bölüm 1 sola yerleşir → `[1][2]`.
> Neden: Kenar teması ilişkinin tam karşılığını verir, köşe yarısını.
>
> **c)**
> Ne yapıyoruz: Bölüm 3'ün (3–2=A=125, 3–1=E=25) aday konumlarını puanlıyoruz.
> Hesap:
>
> | Konum | Komşular | PR |
> |---|---|---:|
> | 2'nin üstü | 2 tam (125) + 1 köşe (12,5) | **137,5** |
> | 2'nin altı | 2 tam (125) + 1 köşe (12,5) | **137,5** |
> | 2'nin sağı | 2 tam (125) | 125 |
> | 1'in üstü | 1 tam (25) + 2 köşe (62,5) | 87,5 |
> | 1'in solu | 1 tam (25) | 25 |
>
> Sonuç: En yüksek 137,5 (iki konum eşit); indeks kuralıyla üst seçilir → `[3]` üstte.
> ```
>    [3]
> [1][2]
> ```
> Neden: Hem A komşusu (2) hem E köşe komşusu (1) aynı anda kazanılıyor.
>
> **ç)**
> Ne yapıyoruz: Bölüm 4'ün (4–1=O=1, 4–2=I=5, 4–3=U=0) en iyi konumunu buluyoruz.
> Hesap:
>
> | Konum | Komşular | PR |
> |---|---|---:|
> | 2'nin altı | 2 tam (5) + 1 köşe (0,5) | **5,5** |
> | 2'nin sağı | 2 tam (5) + 3 köşe (0) | 5 |
> | 1'in altı | 1 tam (1) + 2 köşe (2,5) | 3,5 |
>
> Sonuç: 2'nin altı (PR=5,5). Final grid:
> ```
>    [3]
> [1][2]
>    [4]
> ```
> Neden: En yüksek toplam komşuluk katkısı buradan gelir.
>
> **d)**
> Ne yapıyoruz: Katsayıların mantığını açıklıyoruz.
> Sonuç: Kenar komşuluk iki bölümün gerçek malzeme/insan akışı için tam bir geçiş yüzeyi sağlar (×1); köşe teması yalnız tek noktada değdiği için kısmi yakınlık sayılır (×0,5).
> Neden: Yakınlık avantajı paylaşılan sınır uzunluğuyla orantılıdır; köşe sıfır uzunlukta değse de CORELAP onu "yarı yakınlık" olarak ödüllendirip tamamen yok saymaz.

---

### S03 — Orta — PR Tuzağı: Temas Tipine Bak

> [!question] Soru
> Havelsan'ın bir elektronik montaj hücresinde kısmi yerleşim aşağıdaki gibidir (A=125, E=25, I=5). Genç mühendis Deniz, yeni bölüm D'yi yerleştirirken "en güçlü ilişkili komşuya yapışayım" diye düşünmektedir.
>
> ```
> [B1][B2]
> [B3]
> ```
> B1: (0,1), B2: (1,1), B3: (0,0). D-B1=E(25), D-B2=A(125), D-B3=I(5).
> İki aday: **P1:** (1,0) — B2'nin altı, B3'ün sağı; **P2:** (2,1) — B2'nin sağı.
>
> a) P1 konumunun her komşuyla temas tipini (kenar/köşe) belirleyin.
> b) P1'in PR değerini hesaplayın.
> c) P2'nin PR değerini hesaplayın.
> ç) İki konumu karşılaştırın; Deniz'in sezgisi neden yanıltıcı?
> d) "En güçlü tek ilişkiye yapış" stratejisi CORELAP'ta ne zaman doğru, ne zaman yanlış sonuç verir? Bir kural önerin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** PR hesabında birden fazla komşunun kümülatif katkısı.
> **Dikkat:** P1 hem B2'ye hem B3'e kenar, B1'e köşe değiyor. Temas tipini doğru say.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: P1=(1,0)'ın komşularına göre temas tipini çıkarıyoruz.
> Hesap:
> - B2 (1,1): dikey kenar paylaşır → **kenar (tam)**
> - B3 (0,0): yatay kenar paylaşır → **kenar (tam)**
> - B1 (0,1): yalnız köşe değer → **köşe (yarım)**
> Sonuç: B2 tam, B3 tam, B1 köşe.
> Neden: Koordinat farkına bakarak ortak sınır olup olmadığı belirlenir.
>
> **b)**
> Ne yapıyoruz: Her temasın ağırlık×katsayı katkısını topluyoruz.
> Hesap:
> $$PR_{P1} = 1\cdot125 + 1\cdot5 + 0{,}5\cdot25 = 125+5+12{,}5 = \mathbf{142{,}5}$$
> Sonuç: $PR_{P1}=142{,}5$.
> Neden: Üç komşu birden katkı verir (kümülatif).
>
> **c)**
> Ne yapıyoruz: P2=(2,1) için temasları sayıyoruz.
> Hesap: Yalnız B2 (1,1) ile kenar paylaşır; B1 ve B3 iki kare uzakta → temas yok.
> $$PR_{P2} = 1\cdot125 = \mathbf{125}$$
> Sonuç: $PR_{P2}=125$.
> Neden: Güçlü ama tek bir komşu.
>
> **ç)**
> Ne yapıyoruz: İki PR'yi kıyaslıyoruz.
> Sonuç: $PR_{P1}=142{,}5 > PR_{P2}=125$ → D, **P1**'e yerleşir.
> Neden: P2 yalnız A komşusunu yakalar; P1 ise A (125) + I (5) + E köşe (12,5) toplamıyla daha yüksek. Tek güçlü ilişkiye odaklanmak, birden fazla komşunun toplam katkısını gözden kaçırır.
>
> **d)**
> Ne yapıyoruz: Sezgisel kuralı genelliyoruz.
> Sonuç: "En güçlü tek ilişkiye yapış" yalnız aday konumların başka komşusu yokken doğrudur. Birden çok yerleşmiş bölüme aynı anda temas eden konum varsa, tüm temasları toplayıp karşılaştırmak gerekir.
> Neden: PR bir toplam fonksiyonudur; lokal "en güçlü çift" optimumu garanti etmez. Kural: Her aday için tüm komşu katkılarını (kenar×1, köşe×0,5) topla, sonra kıyasla.
>
> > [!warning] Tuzak
> > B2 ile A ilişkisi var diye P2 seçmek; oysa P1 üç komşuya temas edip 142,5 ile geçer.

---

### S04 — Orta — ALDEP: İki Farklı Rassal Çalışma

> [!question] Soru
> STM'nin bir üretim binasında ALDEP ile yerleşim üretilecektir. S02 ile aynı REL tablosu (4 bölüm); ALDEP ağırlıkları **A=64, E=16, I=4, O=1, U=0** ve eşik ilişki **E ve üstü**'dür. Planlamacı iki farklı rassal tohumla iki çalışma yapıp daha iyisini seçecektir.
>
> Tesis 2 sütun × 4 satır ızgara. Her bölüm 2 kare. Dikey süpürme: sütunlar aşağıdan yukarıya, sonra sütun değiştir.
> **Çalışma A** — rassal sıra: **2-1-3-4** · **Çalışma B** — rassal sıra: **3-2-4-1**
>
> a) Çalışma A'nın dikey süpürme yerleşimini grid olarak çizin.
> b) Çalışma A'nın komşu çiftlerini ve toplam komşuluk puanını hesaplayın.
> c) Çalışma B için aynı işlemi yapın.
> ç) İki çalışmayı karşılaştırın; hangisi daha yüksek puan alır ve neden?
> d) ALDEP neden "iyi" ama "global en iyi olmayan" yerleşim üretir? Pratikte planlamacı bunu nasıl telafi eder?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** İki farklı rassal sıra → farklı yerleşim → karşılaştırma.
> **Dikkat:** Komşuluk puanı yalnız kenar paylaşan çiftleri kapsar; köşegen sayılmaz.

> [!answer]- Adım adım çözüm
> Dikey süpürme konum sırası (2 sütun, 4 satır, her dept 2 kare):
> (S1,R4)→(S1,R3)→(S1,R2)→(S1,R1)→(S2,R1)→(S2,R2)→(S2,R3)→(S2,R4)
>
> **a)**
> Ne yapıyoruz: 2-1-3-4 sırasını süpürme konumlarına yerleştiriyoruz.
> Hesap: 2→(S1,R4-R3), 1→(S1,R2-R1), 3→(S2,R1-R2), 4→(S2,R3-R4).
> Grid (yukarıdan aşağı):
> ```
> [2][4]
> [2][4]
> [1][3]
> [1][3]
> ```
> Sonuç: Yukarıdaki yerleşim.
> Neden: Süpürme her bölümü 2 ardışık kareye sırayla doldurur.
>
> **b)**
> Ne yapıyoruz: Kenar paylaşan çiftleri bulup ağırlıklarını topluyoruz.
> Hesap:
> - 2↔1 (S1, R2-R3 sınırı): A=64
> - 1↔3 (R1-R2 satır, S1-S2): E=16
> - 3↔4 (S2, R2-R3 sınırı): U=0
> - 2↔4 (R3-R4 satır, S1-S2): I=4
> $$\text{Puan}_A = 64+16+0+4 = \mathbf{84}$$
> Sonuç: 84.
> Neden: En güçlü çift 2↔1 (A) komşu kalmış.
>
> **c)**
> Ne yapıyoruz: 3-2-4-1 sırasıyla grid kurup puanlıyoruz.
> Hesap: 3→(S1,R4-R3), 2→(S1,R2-R1), 4→(S2,R1-R2), 1→(S2,R3-R4).
> ```
> [3][1]
> [3][1]
> [2][4]
> [2][4]
> ```
> Komşular:
> - 3↔2 (S1, R2-R3): A=64
> - 2↔4 (R1-R2, S1-S2): I=4
> - 4↔1 (S2, R2-R3): O=1
> - 3↔1 (R3-R4, S1-S2): E=16
> $$\text{Puan}_B = 64+4+1+16 = \mathbf{85}$$
> Sonuç: 85.
> Neden: Hem 3↔2 (A) hem 3↔1 (E) güçlü çiftler komşu.
>
> **ç)**
> Ne yapıyoruz: İki puanı kıyaslıyoruz.
> Sonuç: Çalışma B (85) > Çalışma A (84) → kıl payı B üstün.
> Neden: B'de iki güçlü ilişki (A ve E) aynı anda komşu kalırken, A'da yalnız bir A bağı tam değerlenip E bağı zayıf konumda. Küçük sıra farkı puanı değiştirebiliyor.
>
> **d)**
> Ne yapıyoruz: ALDEP'in rassal doğasını ve telafi yöntemini açıklıyoruz.
> Sonuç: ALDEP ilk bölümü ve eşik altı ilişkili bölümleri rassal seçtiğinden her tohum farklı sonuç verir; tek bir çalışma global optimumu garanti etmez. Pratikte 10–20 çalışma yapılıp en yüksek puanlı (veya kısıtları en iyi karşılayan) seçilir.
> Neden: Yapıcı + rassal sezgisel olduğu için tüm çözüm uzayını taramaz; tekrarla iyi bir çözümün yakalanma olasılığı artırılır.

---

### S05 — Zor — CORELAP vs ALDEP Karşılaştırması

> [!question] Soru
> Aselsan'ın yeni radar üretim binasında 5 bölümlü yerleşim için CORELAP ve ALDEP karşılaştırılacaktır. REL tablosu (A=10000, E=1000, I=100, O=10, U=0, X=−10000) aşağıdadır. Yöneticiler özellikle E bölümünün A bölümüyle olan X (istenmeyen) ilişkisinin yerleştirme sırasını nasıl etkilediğini merak etmektedir.
>
> | | A | B | C | D | E |
> |---|---|---|---|---|---|
> | **A** | — | A | E | U | X |
> | **B** | A | — | I | E | O |
> | **C** | E | I | — | A | I |
> | **D** | U | E | A | — | E |
> | **E** | X | O | I | E | — |
>
> a) CORELAP TCR tablosunu kurup yerleştirme sırasını belirleyin.
> b) E bölümünün X ilişkisiyle sıraya nasıl girdiğini açıklayın.
> c) Bu 5 bölümlük problemde kaç ikili değişim (pairwise swap) adayı olduğunu hesaplayın.
> ç) ALDEP hangi durumlarda CORELAP'a üstündür?
> d) X ilişkisi olmasaydı (E–A için U varsayılsaydı) E'nin sırası değişir miydi? Yeni TCR ile gerekçelendirin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** İki algoritmanın güçlü/zayıf yönlerini sayısal örnekle karşılaştırmak.
> **Dikkat:** X ilişkisi negatif ağırlık → TCR'yi düşürür → X'li bölüm en sona itilir.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Her bölümün satırını (X=−10000 dahil) topluyoruz.
> Hesap:
>
> | Bölüm | İlişkiler | Hesap | TCR |
> |---|---|---|---:|
> | A | A+E+U+X | 10000+1000+0−10000 | **1 000** |
> | B | A+I+E+O | 10000+100+1000+10 | **11 110** |
> | C | E+I+A+I | 1000+100+10000+100 | **11 200** |
> | D | U+E+A+E | 0+1000+10000+1000 | **12 000** |
> | E | X+O+I+E | −10000+10+100+1000 | **−8 890** ← en düşük |
>
> Seçim sırası: D (12000) → C (11200) → B (11110) → A (1000) → **E** (sona).
> Sonuç: D → C → B → A → E.
> Neden: En yüksek TCR önce; negatif TCR'li E en sona.
>
> **b)**
> Ne yapıyoruz: E'nin neden son sıraya düştüğünü açıklıyoruz.
> Sonuç: E, A ile X ilişkili olduğundan hem TCR'si negatif (−8 890) hem de CORELAP kuralıyla X'li bölümler en sona ertelenir.
> Neden: X (istenmeyen yakınlık) ağır negatif ağırlık taşır; bu bölümü erken yerleştirmek X çiftini komşu yapma riskini artırır, bu yüzden en sona bırakılır.
>
> **c)**
> Ne yapıyoruz: 5 bölümün ikili kombinasyonunu sayıyoruz.
> Formül: $\binom{5}{2} = \frac{5!}{2!\,3!}$.
> Hesap: $\binom{5}{2}=10$.
> Sonuç: 10 ikili değişim adayı.
> Neden: Her bölüm çiftinin yer değiştirmesi bir aday takastır; sırasız çift sayısı $\binom{n}{2}$.
>
> **ç)**
> Ne yapıyoruz: ALDEP'in üstün olduğu koşulları listeliyoruz.
> Sonuç: (1) n büyük (>15) — CORELAP'ın tek deterministik çözümü yerel minimuma daha kolay takılır; (2) çok katlı tesis — ALDEP bunu modelleyebilir; (3) planlamacıya birden çok alternatif sunma gereği.
> Neden: ALDEP rassallıkla geniş bir çözüm yelpazesi üretir; büyük/karmaşık problemlerde bu çeşitlilik avantaja dönüşür.
>
> **d)**
> Ne yapıyoruz: X→U varsayımıyla E'nin yeni TCR'sini buluyoruz.
> Hesap: E satırı U+O+I+E = $0+10+100+1000 = 1 110$.
> Sonuç: Yeni TCR=1 110; E artık A (1000) ile yakın, en sona değil A'dan hemen önce/sonra sıraya girer (D→C→B→{A,E}).
> Neden: X cezası kalkınca E'nin negatifliği yok olur; X-erteleme kuralı da devreden çıkar, böylece E ortalama bir bölüm gibi normal sıraya yerleşir.
>
> > [!warning] X kuralı
> > Negatif ağırlıklı X ilişkisi hem TCR'yi düşürür hem de bölümü yerleştirmede en sona iter; iki etki birlikte çalışır.
