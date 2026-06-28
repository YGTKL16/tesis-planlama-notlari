---
hafta: 8
tags: [ders/tesis-planlama, sorular]
soru_sayısı: 5
---

# HF08 — Yerleşim Tasarımı II Soruları

> [!info] Nasıl kullan?
> Soruyu gör → her şıkkı (a–d) kapalı kitap çöz → `[!answer]-` kutusunu aç → hataları not et.
> Kapsam: CRAFT $\Delta C$, ağırlık merkezi, tam iterasyon, konum-bölüm ayrımı, çok bölümlü iterasyon.

> [!warning] Slayt düzeltmesi (CRAFT)
> Ders slaytındaki CRAFT örneğinde başlangıç yerleşim maliyeti **3.310** olarak yazılıdır; **doğru değer 3.510'dur**. Hesaplarda 3.510 kullanın.

---

### S01 — Kolay — CRAFT ΔC formülü

> [!question] Soru
> Aselsan'ın bir kart üretim hattında CRAFT uzmanı Kaan Bey, dört eşit alanlı bölümü doğrusal dizdi ve iki bölümü takas etmenin maliyet değişimini ($\Delta C$) hesaplamak istiyor. Takasın yapılıp yapılmamasına $\Delta C$ işaretine bakarak karar verecek.
> Doğrusal `[1][2][3][4]` yerleşimi. Konum uzaklığı = konum numarası farkı. $c=1$.
> Simetrik akış matrisi:
>
> | | 1 | 2 | 3 | 4 |
> |-|---|---|---|---|
> | 1 | - | 20 | 35 | 10 |
> | 2 | 20 | - | 15 | 40 |
> | 3 | 35 | 15 | - | 5 |
> | 4 | 10 | 40 | 5 | - |
>
> a) Başlangıç toplam maliyeti $Z_0$'ı hesaplayın.
> b) Bölüm 1 ve 3'ü takas edip yeni atamayı yazın.
> c) Yeni maliyet ve $\Delta C_{1\leftrightarrow 3}$'ü hesaplayın.
> ç) Bunun yerine bölüm 2 ile 4 takas edilseydi ($F_{24}=40$ en büyük) maliyet nasıl etkilenirdi?
> d) $\Delta C$ işaretine göre takas kuralını (kabul / ret / nötr) özetleyin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** $Z_0$ ve takas $\Delta C$.
> **Hangi formül:** $Z = \sum_{i<j} F_{ij}\cdot d_{ij}$; $\Delta C = Z_{yeni} - Z_{eski}$.
> **Dikkat:** Takasta bölümler taşınır; uzaklık matrisi KONUMA aittir, değişmez.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Doğrusal konumlarda $F\cdot d$ topluyoruz.
> Formül/Yöntem: $d_{ij}=|i-j|$ (konum farkı).
> Hesap:
>
> | Çift | $F$ | $d$ | $F\cdot d$ |
> |:---:|:---:|:---:|:---:|
> | 1–2 | 20 | 1 | 20 |
> | 1–3 | 35 | 2 | 70 |
> | 1–4 | 10 | 3 | 30 |
> | 2–3 | 15 | 1 | 15 |
> | 2–4 | 40 | 2 | 80 |
> | 3–4 | 5 | 1 | 5 |
>
> Sonuç: $Z_0 = 20+70+30+15+80+5 = $ **220**.
> Neden: En ağır katkı 2–4 (80); bu çift uzakta (d=2) ve akışı yüksek.
>
> **b)**
> Ne yapıyoruz: 1 ve 3'ü takas edip yeni diziyi yazıyoruz.
> Formül/Yöntem: Bölüm 1 → konum 3, bölüm 3 → konum 1; 2 ve 4 sabit.
> Hesap: Yeni yerleşim `[3][2][1][4]`.
> Sonuç: Bölüm 3 başa, bölüm 1 üçüncü konuma geçti.
> Neden: İkili değişim yalnız iki bölümün konumunu takas eder.
>
> **c)**
> Ne yapıyoruz: Yeni konumlarla maliyeti hesaplayıp farkı alıyoruz.
> Formül/Yöntem: $\Delta C = Z_{yeni} - Z_0$.
> Hesap: Değişen çiftler — 1–4: $d$ 3→1 (10·1=10), 3–4: $d$ 1→3 (5·3=15); diğerleri aynı. $Z_{yeni} = 20+70+10+15+80+15 = 210$.
> Sonuç: $Z_{yeni} = 210$, $\Delta C = 210-220 = $ **−10**.
> Neden: 1–4 kısaldı (−20), 3–4 uzadı (+10); net −10 maliyet düşer.
>
> **ç)**
> Ne yapıyoruz: 2↔4 takasını test ediyoruz.
> Formül/Yöntem: Bölüm 2 → konum 4, bölüm 4 → konum 2 → `[1][4][3][2]`.
> Hesap: 1–2: $d$ 1→3 (60), 2–4: $d$ 2→2 (80), 1–4: $d$ 3→1 (10), 2–3: $d$ 1→1 (15), 1–3 (70), 3–4: $d$ 1→1 (5) → $Z = 60+70+10+15+80+5 = 240$.
> Sonuç: $Z = 240$, $\Delta C = +20$ → **kötüleşir**, takas yapılmaz.
> Neden: $F_{24}$ büyük olsa da 2–4 mesafesi değişmez; takas 1–2'yi uzatıp maliyeti artırır.
>
> **d)**
> Ne yapıyoruz: Karar kuralını yazıyoruz.
> Formül/Yöntem: İşaret kontrolü.
> Hesap: $\Delta C<0$ → maliyet düşer; $\Delta C>0$ → artar; $\Delta C=0$ → değişmez.
> Sonuç: **$\Delta C<0$ → takas yap; $\Delta C>0$ → yapma; $\Delta C=0$ → nötr (mevcudu koru).**
> Neden: CRAFT her iterasyonda en negatif $\Delta C$'li takası seçer.

---

### S02 — Orta — CRAFT ağırlık merkezi hesabı

> [!question] Soru
> Bir mobilya fabrikasının yerleşim mühendisi Sinem Hanım, bina içine yerleştirilmiş üç dikdörtgen bölümün ağırlık merkezlerini ve aralarındaki mesafeleri CRAFT için hesaplamak zorunda. Özellikle A ve B bölümleri arasındaki dik doğrusal uzaklığı doğru bulması gerekiyor.
> - **Bölüm A:** sol-alt $(0,0)$, sağ-üst $(5,4)$
> - **Bölüm B:** sol-alt $(5,0)$, sağ-üst $(8,4)$
> - **Bölüm C:** sol-alt $(0,4)$, sağ-üst $(8,7)$
>
> a) Her bölümün geometrik ağırlık merkezini hesaplayın.
> b) A ile B arasındaki dik doğrusal (rektlineer) uzaklığı hesaplayın.
> c) A ile C arasındaki rektlineer uzaklığı hesaplayın.
> ç) Bölüm B genişliği 3 m'den 5 m'ye çıksaydı (sağ köşe $(10,4)$) merkez ve $d_{AB}$ nasıl değişirdi?
> d) Çok parçalı (L/T şekilli) bölümlerde merkez hesabının neden farklı olduğunu açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Dikdörtgen bölümün merkezi ve merkezler arası rektlineer uzaklık.
> **Hangi formül:** $\bar x = \frac{x_{min}+x_{max}}{2}$, $\bar y = \frac{y_{min}+y_{max}}{2}$; $d = |\Delta x| + |\Delta y|$.
> **Dikkat:** Tek parça dikdörtgende orta nokta yeterli; çok parçalı bölümde alan ağırlıklı ortalama gerekir.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Her dikdörtgenin köşe ortalamasını alıyoruz.
> Formül/Yöntem: Merkez = (sol+sağ)/2, (alt+üst)/2.
> Hesap: A: $(\tfrac{0+5}{2}, \tfrac{0+4}{2})=(2{,}5; 2{,}0)$; B: $(\tfrac{5+8}{2}, \tfrac{0+4}{2})=(6{,}5; 2{,}0)$; C: $(\tfrac{0+8}{2}, \tfrac{4+7}{2})=(4{,}0; 5{,}5)$.
> Sonuç: A=(2,5; 2,0), B=(6,5; 2,0), C=(4,0; 5,5).
> Neden: Eşit yoğunluklu dikdörtgenin merkezi köşelerin ortasıdır.
>
> **b)**
> Ne yapıyoruz: A ve B merkezleri arası Manhattan uzaklığı.
> Formül/Yöntem: $d_{AB}=|\bar x_B-\bar x_A|+|\bar y_B-\bar y_A|$.
> Hesap: $|6{,}5-2{,}5|+|2{,}0-2{,}0| = 4{,}0+0$.
> Sonuç: $d_{AB} = $ **4,0 m**.
> Neden: Aynı $y$ hizasında olduklarından yalnız $x$ farkı sayılır.
>
> **c)**
> Ne yapıyoruz: A ve C merkezleri arası uzaklık.
> Formül/Yöntem: $d_{AC}=|\bar x_C-\bar x_A|+|\bar y_C-\bar y_A|$.
> Hesap: $|4{,}0-2{,}5|+|5{,}5-2{,}0| = 1{,}5+3{,}5$.
> Sonuç: $d_{AC} = $ **5,0 m**.
> Neden: C hem yatay hem dikey kayık olduğundan iki bileşen de katkı verir.
>
> **ç)**
> Ne yapıyoruz: B'yi genişletip merkezini ve $d_{AB}$'yi güncelliyoruz.
> Formül/Yöntem: Yeni B: $(5,0)$–$(10,4)$ → $\bar x_B = \tfrac{5+10}{2}=7{,}5$.
> Hesap: Yeni merkez $(7{,}5; 2{,}0)$; $d_{AB}=|7{,}5-2{,}5|+0 = 5{,}0$.
> Sonuç: Merkez $(7{,}5; 2{,}0)$, $d_{AB} = $ **5,0 m** (4,0'dan arttı).
> Neden: Genişleyen bölümün merkezi sağa kayar, A'ya uzaklık büyür.
>
> **d)**
> Ne yapıyoruz: Çok parçalı bölümün merkez mantığını açıklıyoruz.
> Formül/Yöntem: $\bar x = \frac{\sum A_k \bar x_k}{\sum A_k}$ (alan ağırlıklı).
> Hesap: L/T şekli alt dikdörtgenlere bölünür; her parçanın alanı ağırlık olur.
> Sonuç: Çok parçalı bölümde merkez **alan ağırlıklı ortalama** ile bulunur, basit orta nokta yanlıştır.
> Neden: Düzensiz şekilde kütle dağılımı eşit değildir; merkez büyük parçaya kayar.

---

### S03 — Orta — CRAFT tam iterasyon

> [!question] Soru
> Korkmaz'ın çelik mutfak eşyası tesisinde planlama uzmanı Barış Bey, dört eşit alanlı bölümü 2×2 gride yerleştirdi ve bir tam CRAFT iterasyonu yürütmek istiyor. Tüm altı ikili değişimi $\Delta C$ ile değerlendirip en iyi takası uygulayacak.
> Yerleşim:
> ```
> [P][Q]
> [R][S]
> ```
> Konumlar: P=(0,0), Q=(0,1), R=(1,0), S=(1,1). Rektlineer mesafe.
> Simetrik akış matrisi:
>
> | | P | Q | R | S |
> |-|---|---|---|---|
> | P | - | 15 | 40 | 5 |
> | Q | 15 | - | 8 | 30 |
> | R | 40 | 8 | - | 20 |
> | S | 5 | 30 | 20 | - |
>
> $c=1$.
>
> a) Konum mesafe matrisini oluşturun.
> b) Başlangıç maliyeti $Z_0$'ı hesaplayın.
> c) Tüm $C(4,2)=6$ ikili takası $\Delta C$ ile değerlendirin.
> ç) En iyi takas hangisi; yerleşim yerel optimum mu?
> d) Tüm $\Delta C \geq 0$ olması ne anlama gelir; küresel optimum garanti edilir mi?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Bir tam CRAFT iterasyonu.
> **Hangi yöntem:** Her takasta bölüm-konum eşlemesini güncelle, $Z_{yeni}$'yi hesapla.
> **Dikkat:** Akış matrisi P,Q,R,S bölümlerine; mesafe matrisi konumlara aittir (sabit).

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Konum çiftlerinin Manhattan mesafelerini buluyoruz.
> Formül/Yöntem: $d = |\Delta\text{satır}|+|\Delta\text{sütun}|$.
> Hesap: P–Q=1, P–R=1, P–S=2, Q–R=2, Q–S=1, R–S=1.
> Sonuç: Komşular 1, çapraz çiftler (P–S, Q–R) 2.
> Neden: 2×2 gridde köşegen uzaklık 2'dir.
>
> **b)**
> Ne yapıyoruz: $F\cdot d$ topluyoruz.
> Formül/Yöntem: $Z_0 = \sum F_{ij}d_{ij}$.
> Hesap: P-Q:15, P-R:40, P-S:10, Q-R:16, Q-S:30, R-S:20.
> Sonuç: $Z_0 = 15+40+10+16+30+20 = $ **131**.
> Neden: En büyük katkı P–R (40, komşu); zaten yakın.
>
> **c)**
> Ne yapıyoruz: Altı takası tek tek hesaplıyoruz.
> Formül/Yöntem: İki bölümün konumunu değiştir, $Z$ ve $\Delta C$'yi bul.
> Hesap:
>
> | Takas | $Z$ | $\Delta C$ |
> |:---:|:---:|:---:|
> | P↔Q | 188 | +57 |
> | P↔R | 153 | +22 |
> | P↔S | 131 | 0 |
> | Q↔R | 176 | +45 |
> | Q↔S | 153 | +22 |
> | R↔S | 188 | +57 |
>
> Sonuç: Yalnız P↔S nötr (0); diğerleri kötüleştirir.
> Neden: Büyük akışlı P–R ve Q–S çiftleri zaten komşu; her takas onları uzaklaştırıyor.
>
> **ç)**
> Ne yapıyoruz: En düşük $\Delta C$'yi seçiyoruz.
> Formül/Yöntem: En negatif $\Delta C$ = en iyi takas.
> Hesap: En küçük $\Delta C = 0$ (P↔S); negatif yok.
> Sonuç: İyileştiren takas **yok**; başlangıç `[P][Q]/[R][S]` **yerel optimumdur** ($Z=131$).
> Neden: Hiçbir tekil takas maliyeti düşürmüyor.
>
> **d)**
> Ne yapıyoruz: Yerel optimum kavramını yorumluyoruz.
> Formül/Yöntem: Tüm $\Delta C\geq0$ → komşu çözüm yok demektir.
> Hesap: Sadece ikili değişim uzayında minimum; başka topoloji denenmedi.
> Sonuç: Tüm $\Delta C\geq0$ → **yerel optimum**; **küresel optimum garanti değildir**.
> Neden: CRAFT açgözlüdür; farklı başlangıçla daha düşük maliyet bulunabilir.

---

### S04 — Orta — CRAFT konum vs bölüm tuzağı

> [!question] Soru
> Bir danışmanlık projesinde CRAFT eğitmeni Murat Bey, öğrencilerin sık yaptığı "bölüm numarası = konum numarası" hatasını örnekle göstermek istiyor. Üç bölümlü bir düzende başlangıç maliyetini ve 1–3 takasının sonucunu doğru hesaplayıp hatalı yaklaşımın etkisini anlatacak.
> Başlangıç ataması: Bölüm 1 → Konum A, Bölüm 2 → Konum B, Bölüm 3 → Konum C.
> Uzaklık matrisi (konumlara ait, değişmez): $d_{AB}=4$, $d_{AC}=6$, $d_{BC}=3$.
> Simetrik akış: $F_{12}=10$, $F_{13}=2$, $F_{23}=15$. $c=1$.
>
> a) Başlangıç maliyeti $Z_0$'ı hesaplayın (1@A, 2@B, 3@C).
> b) Bölüm 1 ve 3'ü takas edip yeni atamayı ve yeni maliyeti hesaplayın.
> c) $\Delta C$'ye göre takas kararını verin.
> ç) "Bölüm numarası = konum numarası" hatası yapılsaydı hesap nasıl bozulurdu?
> d) Bölüm–konum ayrımını korumak için pratik bir yöntem önerin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** CRAFT'ta bölüm–konum ayrımı.
> **Temel kural:** Uzaklık matrisi KONUMLARA (A,B,C); akış matrisi BÖLÜMLERE (1,2,3) aittir.
> **Dikkat:** En sık hata: takas sonrası uzaklık matrisini de değiştiğini sanmak.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Bölümlerin konumlarına göre $F\cdot d$ topluyoruz.
> Formül/Yöntem: 1@A, 2@B, 3@C.
> Hesap: 1–2 (A–B): 10·4=40; 1–3 (A–C): 2·6=12; 2–3 (B–C): 15·3=45.
> Sonuç: $Z_0 = 40+12+45 = $ **97**.
> Neden: Akış bölümden, mesafe konumdan okunur.
>
> **b)**
> Ne yapıyoruz: 1 ve 3'ü takas edip yeni atamayı kuruyoruz.
> Formül/Yöntem: Yeni atama 3@A, 2@B, 1@C; uzaklık matrisi AYNI.
> Hesap: 1–2 (C–B): 10·3=30; 1–3 (C–A): 2·6=12; 2–3 (B–A): 15·4=60. $Z_{yeni} = 30+12+60 = 102$.
> Sonuç: $Z_{yeni} = $ **102**.
> Neden: Bölümler taşındı; $d_{AB}, d_{AC}, d_{BC}$ değerleri sabit kaldı.
>
> **c)**
> Ne yapıyoruz: Farkı alıyoruz.
> Formül/Yöntem: $\Delta C = 102 - 97$.
> Hesap: $+5$.
> Sonuç: $\Delta C = +5$ → maliyet artar → takas **yapılmaz**.
> Neden: 2–3 çiftinin yükü (15) en uzak mesafeye (B–A=4) düştüğünden maliyet yükseldi.
>
> **ç)**
> Ne yapıyoruz: Hatalı yaklaşımı simüle ediyoruz.
> Formül/Yöntem: Öğrenci "bölüm 1 konum 1'de, takasla konum 3'e gitti, o yüzden 1. satır değişti" diyerek akışı konuma göre yeniden indeksler.
> Hesap: Bu, uzaklık matrisini yanlış yeniden eşler ve $d_{AB}$'yi sanki değişmiş gibi kullanır.
> Sonuç: Hem $Z_0$ hem $Z_{yeni}$ **bozulur**; karar yanlış çıkar.
> Neden: $d_{AB}$ her zaman 4'tür — hangi bölümün A/B'de olduğundan bağımsız.
>
> **d)**
> Ne yapıyoruz: Hatayı önleyecek pratik öneri veriyoruz.
> Formül/Yöntem: Bölüm→konum eşlemesini ayrı bir satırda tut, uzaklık matrisini asla silme.
> Hesap: Her takasta yalnız "hangi bölüm hangi konumda" sözlüğünü güncelle.
> Sonuç: **Bölüm–konum sözlüğünü ayrı yaz; uzaklık matrisi sabit kalsın.**
> Neden: İki tabloyu ayrı tutmak, indeks karışmasını kökten engeller.

---

### S05 — Zor — CRAFT iki iterasyon, 5 bölüm

> [!question] Soru
> Kardemir'in bir işleme atölyesinde kıdemli planlama mühendisi Hakan Bey, beş bölümlü doğrusal bir yerleşimi iki CRAFT iterasyonuyla iyileştirmek istiyor. Her iterasyonda on ikili değişimi tarayıp en iyi takası uygulayacak ve toplam iyileşme yüzdesini raporlayacak.
> Doğrusal `[1][2][3][4][5]` başlangıç. Konum uzaklığı = konum farkı. $c=1$.
> Simetrik akış matrisi:
>
> | | 1 | 2 | 3 | 4 | 5 |
> |-|---|---|---|---|---|
> | 1 | - | 50 | 10 | 5 | 30 |
> | 2 | 50 | - | 20 | 8 | 15 |
> | 3 | 10 | 20 | - | 40 | 3 |
> | 4 | 5 | 8 | 40 | - | 25 |
> | 5 | 30 | 15 | 3 | 25 | - |
>
> a) Başlangıç maliyeti $Z_0$'ı hesaplayın.
> b) 1. iterasyonda en umutlu takasları (1↔5, 1↔2, 3↔5) tarayıp $\Delta C$'lerini bulun.
> c) En iyi takası uygulayıp $Z_1$'i ve yeni yerleşimi belirleyin.
> ç) 1. iterasyondaki iyileşme yüzdesini hesaplayın.
> d) 2. iterasyon sonrası yerel optimum testini ve küresel optimum garantisini yorumlayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** İki tam CRAFT iterasyonu ve iyileşme oranı.
> **Hangi yöntem:** Her iterasyonda 10 ikiliyi tara, en negatif $\Delta C$'yi uygula.
> **Dikkat:** Büyük akışlı uzak çiftleri önce test et — 1–5 (50, d=4 değil; 1–2 d=1) ve 1–5 (30, d=4) kritik.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Doğrusal konumlarda $F\cdot d$ topluyoruz.
> Formül/Yöntem: $d_{ij}=|i-j|$.
> Hesap:
>
> | Çift | $F$ | $d$ | $F\cdot d$ |
> |:---:|:---:|:---:|:---:|
> | 1–2 | 50 | 1 | 50 |
> | 1–3 | 10 | 2 | 20 |
> | 1–4 | 5 | 3 | 15 |
> | 1–5 | 30 | 4 | 120 |
> | 2–3 | 20 | 1 | 20 |
> | 2–4 | 8 | 2 | 16 |
> | 2–5 | 15 | 3 | 45 |
> | 3–4 | 40 | 1 | 40 |
> | 3–5 | 3 | 2 | 6 |
> | 4–5 | 25 | 1 | 25 |
>
> Sonuç: $Z_0 = 50+20+15+120+20+16+45+40+6+25 = $ **357**.
> Neden: En ağır katkı 1–5 (120); akış 30 ama mesafe 4 (uzak).
>
> **b)**
> Ne yapıyoruz: Üç adayın $\Delta C$'sini hesaplıyoruz.
> Formül/Yöntem: Sadece takas edilen bölümleri içeren çiftler değişir.
> Hesap: **1↔5:** 1–2 (+100), 1–4 (−10), 2–5 (−30), 4–5 (+50) → $\Delta C = +110$. **1↔2:** 1–3 (−10), 1–4 (−5), 1–5 (−30), 2–3 (+20), 2–4 (+8), 2–5 (+15) → $\Delta C = -2$. **3↔5:** 1–3 (+20), 2–3 (+40), 1–5 (−60), 2–5 (−30) → $\Delta C = -30$.
> Sonuç: 1↔5 → **+110** (kötü); 1↔2 → **−2** (hafif iyi); 3↔5 → **−30** (en iyi).
> Neden: 3↔5, büyük 1–5 mesafesini 4→2 düşürerek en çok tasarruf eder.
>
> **c)**
> Ne yapıyoruz: En negatif $\Delta C$'li takası uyguluyoruz.
> Formül/Yöntem: 3↔5 → bölüm 5 konum 3'e, bölüm 3 konum 5'e.
> Hesap: $Z_1 = 357 - 30 = 327$; yeni yerleşim `[1][2][5][4][3]`.
> Sonuç: $Z_1 = $ **327**.
> Neden: 1–5 ve 2–5 yükleri kısaldı; 1–3 ve 2–3 uzaması bunu aşamadı.
>
> **ç)**
> Ne yapıyoruz: İyileşme oranını hesaplıyoruz.
> Formül/Yöntem: $\frac{Z_0 - Z_1}{Z_0}$.
> Hesap: $\frac{357-327}{357} = \frac{30}{357}$.
> Sonuç: İyileşme ≈ **%8,4**.
> Neden: Tek takas 30 birim tasarruf sağladı.
>
> **d)**
> Ne yapıyoruz: 2. iterasyonu ve optimumluk durumunu yorumluyoruz.
> Formül/Yöntem: Yeni dizide en umutlu uzak-büyük çiftleri (2–3 d=3, 1–3 d=4) tekrar tara.
> Hesap: Bu çiftleri yakınlaştıran takaslar 1–2 (d=1, F=50) gibi komşulukları bozup pozitif $\Delta C$ veriyor; iyileşme küçük kalıyor veya bitiyor.
> Sonuç: 2. iterasyonda tüm $\Delta C\geq0$ olursa **yerel optimuma** ulaşılır; **küresel optimum garanti edilmez**.
> Neden: CRAFT açgözlü olduğundan farklı başlangıç yerleşimi daha iyi sonuç verebilir.
>
> > [!tip] Özet
> > $Z_0 = 357 \rightarrow Z_1 = 327$ (%8,4 iyileşme). CRAFT yerel optimuma yakınsar; küresel en iyi için çoklu başlangıç denenir.
