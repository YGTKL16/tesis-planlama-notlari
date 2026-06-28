---
hafta: 4
tags: [ders/tesis-planlama, sorular]
soru_sayısı: 5
---

# HF04 — Ürün, Süreç ve Çizelgeleme Tasarımı III Soruları

> [!info] Nasıl kullan?
> Soruyu gör → cevaplamayı dene (kapalı kitap) → `[!answer]-` kutusunu aç → hataları not et.

---

### S01 — Kolay — Tek aşamalı fire

> [!question] Soru
> Bir döküm atölyesinin üretim sorumlususunuz. Bir operasyonda fire oranı %12'dir ve müşteriye 200 sağlam parça teslim edilmesi gerekmektedir.
>
> a) Operasyonun verim oranını ($1-s$) bulun.
> b) Gerekli teorik girdi miktarını ($I = O/(1-s)$) hesaplayın.
> c) Tam sayıya yuvarlama kararını verin: 227 mi 228 mi, neden?
> ç) Fire oranı %12 yerine %20 olsaydı girdi miktarı nasıl değişirdi?
> d) "$200/0{,}12$" şeklindeki yaygın hatayı açıklayıp doğru formülü gerekçelendirin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Hedef çıktıdan geriye giderek gerekli girdi.
> **Hangi formül:** $I = O / (1 - s)$ — çıktıyı verim oranına böl.
> **Dikkat:** Fire oranını paydaya değil, 1'den çıkar; payda $(1-0{,}12)=0{,}88$.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Verim oranını buluyoruz.
> Formül/Yöntem: $y = 1 - s$
> Hesap: $y = 1 - 0{,}12 = 0{,}88$
> Sonuç: Verim oranı %88.
> Neden: Giren her parçanın %88'i sağlam çıkar.
>
> **b)**
> Ne yapıyoruz: Teorik girdiyi hesaplıyoruz.
> Formül/Yöntem: $I = O/(1-s)$
> Hesap: $I = \dfrac{200}{0{,}88} = 227{,}27$
> Sonuç: Teorik girdi 227,27 parça.
> Neden: 200 sağlam parça için, fire payı kadar fazladan girdi gerekir.
>
> **c)**
> Ne yapıyoruz: Yuvarlama kararı veriyoruz.
> Formül/Yöntem: $\lceil I \rceil$ — parçalar bölünemez.
> Hesap: $227 \times 0{,}88 = 199{,}76 < 200$ → yetersiz; $\lceil 227{,}27 \rceil = 228$.
> Sonuç: 228 parça girilmelidir.
> Neden: Aşağı yuvarlama hedefin altında kalır, bu yüzden daima tavana yuvarlanır.
>
> **ç)**
> Ne yapıyoruz: What-if — fire %20.
> Formül/Yöntem: $I = 200/(1-0{,}20)$
> Hesap: $I = \dfrac{200}{0{,}80} = 250$ parça.
> Sonuç: Girdi 228'den 250'ye çıkar.
> Neden: Fire arttıkça verim paydası küçülür, aynı çıktı için daha fazla girdi gerekir.
>
> **d)**
> Ne yapıyoruz: Yaygın hatayı açıklıyoruz.
> Formül/Yöntem: $O/(1-s)$ ≠ $O/s$.
> Hesap: Hatalı yol "$200/0{,}12 = 1.666$" fire miktarına bölmedir; doğru olan verim oranına bölmektir.
> Sonuç: Doğru formül $I=O/(1-s)=228$; hatalı sonuç 1.666 anlamsızdır.
> Neden: Payda, sağlam çıkma oranı (verim) olmalıdır; fire oranı tek başına girdiyi belirlemez.
>
> > [!warning] Tuzak
> > Fire miktarına ($s$) bölmek girdiyi ~7 kat şişirir. Her zaman $1-s$'e böl.

---

### S02 — Orta — Çok aşamalı seri fire

> [!question] Soru
> Bir mobilya fabrikasının hat mühendisisiniz. Üretim hattında 4 seri istasyon var ve fire oranları sırasıyla $s_1 = \%5$, $s_2 = \%8$, $s_3 = \%6$, $s_4 = \%10$'dur. Hat sonunda 500 iyi parça isteniyor.
>
> a) İstasyon 4 ve İstasyon 3'ün girdilerini geriye doğru hesaplayın.
> b) İstasyon 2 ve İstasyon 1'in girdilerini hesaplayın.
> c) Tüm zincir için özet tabloyu (girdi / fire / çıktı) oluşturun.
> ç) Verim oranlarını toplamanın ($0{,}95+0{,}92+\ldots$) neden hatalı olduğunu açıklayın.
> d) Hat sonunda 500 yerine 501 iyi parça çıkmasını yorumlayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Seri fire zincirinin başlangıç miktarı ve yuvarlama etkisi.
> **Hangi yöntem:** Son istasyondan geriye $I_k = \lceil O_k / (1-s_k) \rceil$.
> **Dikkat:** İleri değil geriye git; her aşamada tavana yuvarla.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: İstasyon 4 ve 3 girdilerini buluyoruz.
> Formül/Yöntem: $I_k = \lceil O_k/(1-s_k) \rceil$, başlangıç $O_4=500$.
> Hesap: $I_4 = \left\lceil \dfrac{500}{0{,}90} \right\rceil = \lceil 555{,}56 \rceil = 556$; $I_3 = \left\lceil \dfrac{556}{0{,}94} \right\rceil = \lceil 591{,}49 \rceil = 592$.
> Sonuç: İstasyon 4 girdisi 556, İstasyon 3 girdisi 592.
> Neden: Her istasyonun çıktısı bir sonrakinin girdisidir, geriye doğru çözülür.
>
> **b)**
> Ne yapıyoruz: İstasyon 2 ve 1 girdilerini buluyoruz.
> Formül/Yöntem: Aynı formülü zincirin başına kadar uygula.
> Hesap: $I_2 = \left\lceil \dfrac{592}{0{,}92} \right\rceil = \lceil 643{,}48 \rceil = 644$; $I_1 = \left\lceil \dfrac{644}{0{,}95} \right\rceil = \lceil 677{,}89 \rceil = 678$.
> Sonuç: İlk istasyona en az 678 parça girilmelidir.
> Neden: Tüm fireler telafi edildiğinde başlangıç girdisi 678 olur.
>
> **c)**
> Ne yapıyoruz: Özet tabloyu (ileri) oluşturuyoruz.
> Formül/Yöntem: $O_k = \lfloor I_k(1-s_k) \rfloor$.
> Hesap:
>
> | İstasyon | Fire | Girdi | Fire miktarı | Çıktı (iyi) |
> |:---:|:---:|:---:|:---:|:---:|
> | 1 | %5 | 678 | 34 | 644 |
> | 2 | %8 | 644 | 51 | 593 |
> | 3 | %6 | 593 | 36 | 557 |
> | 4 | %10 | 557 | 56 | 501 |
>
> Sonuç: Zincir 678 → 644 → 593 → 557 → 501 iyi parça.
> Neden: Yukarı yuvarlamalar biriktiği için çıktı hedefin biraz üstündedir.
>
> **ç)**
> Ne yapıyoruz: Verim toplamanın hatasını açıklıyoruz.
> Formül/Yöntem: Seri sistemde verimler çarpılır, toplanmaz.
> Hesap: Toplam verim $\approx 0{,}95 \times 0{,}92 \times 0{,}94 \times 0{,}90 = 0{,}739$, toplama ($0{,}95+0{,}92+\ldots$) ise 1'i aşar ki anlamsızdır.
> Sonuç: Verimler çarpılmalı veya her aşama ayrı hesaplanmalıdır.
> Neden: Fire her aşamada bir önceki çıktının üzerine uygulanır; oranlar kümülatif olarak çarpılır.
>
> **d)**
> Ne yapıyoruz: 501 sonucunu yorumluyoruz.
> Formül/Yöntem: Yuvarlama artığı.
> Hesap: Her istasyonda tavana yuvarlama küçük fazlalıklar ekledi; toplamda hedef 500 yerine 501 iyi parça oluştu.
> Sonuç: 1 parça fazla, kabul edilebilir bir güvenlik payıdır.
> Neden: Tam sayı kısıtı nedeniyle gerçek çıktı teorik hedefin hafifçe üstüne çıkar; bu eksik üretim riskini engeller.

---

### S03 — Orta — Makine sayısı hesabı

> [!question] Soru
> Bir havacılık parçası üreten tesisin üretim müdürü olarak yeni hat için makine ihtiyacını belirliyorsunuz. Ürünün haftalık talebi 1.200 birim, bir makinenin işlem süresi 4 dk/birim; çalışma haftada 5 gün, günde 8 saattir. Makine verimliliği (performans) %95, güvenilirliği (kullanılabilirlik) %85, fire oranı %7'dir.
>
> a) Fire dahil üretilmesi gereken miktarı ($Q$) hesaplayın.
> b) Bir makinenin haftalık etkin süresini ($E \cdot H \cdot R$) hesaplayın.
> c) Gereken makine sayısını ($F$) hesaplayıp yuvarlayın.
> ç) Makine verimliliği %95 yerine %80'e düşseydi makine sayısı nasıl değişirdi?
> d) $E$ ve $R$'nin neden payda(d)a yer aldığını açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Kapasite ihtiyacını karşılayan minimum makine sayısı.
> **Hangi formül:** $F = \dfrac{S \cdot Q}{E \cdot H \cdot R}$ — talebi fire için geriye düzelt.
> **Dikkat:** Fire müşteri talebini artırır: önce $Q = D/(1-s)$, sonra makine formülü.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Fire dahil üretim miktarını buluyoruz.
> Formül/Yöntem: $Q = D/(1-s)$
> Hesap: $Q = \dfrac{1.200}{0{,}93} = 1.290{,}32 \approx 1.291$ birim/hafta.
> Sonuç: 1.291 birim üretilmelidir.
> Neden: %7 fire nedeniyle teslim için talepten fazla üretmek gerekir.
>
> **b)**
> Ne yapıyoruz: Etkin makine süresini hesaplıyoruz.
> Formül/Yöntem: $H_{etkin} = E \times H \times R$, $H = 5 \times 8 \times 60 = 2.400$ dk.
> Hesap: $H_{etkin} = 0{,}95 \times 2.400 \times 0{,}85 = 1.938$ dk/makine-hafta.
> Sonuç: Bir makine haftada 1.938 dk gerçek üretim yapar.
> Neden: Performans ve kullanılabilirlik kayıpları nominal 2.400 dk'yı düşürür.
>
> **c)**
> Ne yapıyoruz: Makine sayısını buluyoruz.
> Formül/Yöntem: $F = \dfrac{S \cdot Q}{E \cdot H \cdot R}$
> Hesap: $F = \dfrac{4 \times 1.291}{1.938} = \dfrac{5.164}{1.938} = 2{,}664 \Rightarrow \lceil 2{,}664 \rceil = 3$.
> Sonuç: En az 3 makine gereklidir.
> Neden: Kesirli makine olmadığından tavana yuvarlanır; 2 makine talebi karşılamaz.
>
> **ç)**
> Ne yapıyoruz: What-if — performans %80.
> Formül/Yöntem: $H_{etkin}=0{,}80 \times 2.400 \times 0{,}85 = 1.632$ dk; $F = (4 \times 1.291)/1.632$.
> Hesap: $F = \dfrac{5.164}{1.632} = 3{,}164 \Rightarrow \lceil 3{,}164 \rceil = 4$.
> Sonuç: Makine sayısı 3'ten 4'e çıkar.
> Neden: Düşük performans etkin süreyi azaltır, aynı iş için daha fazla makine gerekir.
>
> **d)**
> Ne yapıyoruz: $E$ ve $R$'nin yerini açıklıyoruz.
> Formül/Yöntem: Kapasite mantığı.
> Hesap: $E$ ve $R$ makinenin gerçek kapasitesini azaltan kayıplardır; kapasite azalınca ihtiyaç artar, bu yüzden paydaya yazılır.
> Sonuç: Düşük $E$/$R$ → büyük $F$.
> Neden: $E$/$R$'yi paya yazmak, kayıpların makine sayısını azalttığı yanılgısına yol açar ki bu yanlıştır.
>
> > [!warning] Tuzak
> > $E$ ve $R$'yi paya koymak yaygın hatadır. Düşük performans kapasiteyi azaltır (ihtiyacı artırır), bu yüzden etkin süre paydadadır.

---

### S04 — Orta — Operatör–makine sistemi: çevrim ve aylak süreler

> [!question] Soru
> Bir CNC atölyesinde operatör-makine dengesini kuruyorsunuz. Yarı otomatik sistemde operatörün süreleri: $a = 1{,}5$ dk (yükleme/boşaltma — hem operatör hem makine meşgul), $t = 5$ dk (otomatik işleme — yalnız makine), $b = 0{,}8$ dk (taşıma/yürüme — yalnız operatör).
>
> a) İdeal (dengeli) makine sayısı $n'$ değerini hesaplayın.
> b) $m=2$ için çevrim süresi $T(2)$ ve aylak süreleri hesaplayın.
> c) $m=3$ için çevrim süresi $T(3)$ ve aylak süreleri hesaplayın.
> ç) İki seçeneğin üretim oranını ($r = m/T$) karşılaştırın.
> d) $T(m)$ hesabında neden toplam değil maksimum alındığını açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Dengeleme noktası, çevrim ve atıl süreler.
> **Hangi formüller:** $n' = (a+t)/(a+b)$; $T(m) = \max\{a+t,\ m(a+b)\}$; $I_O = T(m) - m(a+b)$; $I_M = T(m) - (a+t)$.
> **Dikkat:** $T(m)$'de toplam değil maksimum alınır — sistem yavaş olanı bekler.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: İdeal makine sayısını buluyoruz.
> Formül/Yöntem: $n' = (a+t)/(a+b)$
> Hesap: $n' = \dfrac{1{,}5+5}{1{,}5+0{,}8} = \dfrac{6{,}5}{2{,}3} = 2{,}826$
> Sonuç: $n' \approx 2{,}83$ (tamsayı adaylar: $m=2$ ve $m=3$).
> Neden: Bu nokta operatör ve makinelerin tam dengelendiği teorik makine sayısıdır.
>
> **b)**
> Ne yapıyoruz: $m=2$ çevrim ve aylak sürelerini buluyoruz.
> Formül/Yöntem: $T(m)=\max\{a+t,\ m(a+b)\}$
> Hesap: $T(2)=\max\{6{,}5,\ 2 \times 2{,}3\} = \max\{6{,}5,\ 4{,}6\} = 6{,}5$ dk. $m=2 < n'$ → operatör bekler: $I_O = 6{,}5 - 4{,}6 = 1{,}9$ dk; $I_M = 0$.
> Sonuç: $T(2)=6{,}5$ dk, operatör çevrim başına 1,9 dk aylak.
> Neden: Makine sayısı yetersizken çevrimi makine süresi ($a+t$) belirler; operatör boşta kalır.
>
> **c)**
> Ne yapıyoruz: $m=3$ çevrim ve aylak sürelerini buluyoruz.
> Formül/Yöntem: Aynı formül, $m=3$.
> Hesap: $T(3)=\max\{6{,}5,\ 3 \times 2{,}3\} = \max\{6{,}5,\ 6{,}9\} = 6{,}9$ dk. $m=3 > n'$ → makineler bekler: $I_M = 6{,}9 - 6{,}5 = 0{,}4$ dk/makine; $I_O = 0$.
> Sonuç: $T(3)=6{,}9$ dk, her makine çevrim başına 0,4 dk aylak.
> Neden: Makine sayısı fazlayken çevrimi operatör turu ($m(a+b)$) belirler; makineler boşta kalır.
>
> **ç)**
> Ne yapıyoruz: Üretim oranlarını karşılaştırıyoruz.
> Formül/Yöntem: $r(m) = m/T(m)$
> Hesap: $r(2) = 2/6{,}5 = 0{,}308$ parça/dk; $r(3) = 3/6{,}9 = 0{,}435$ parça/dk.
> Sonuç: $m=3$ daha yüksek üretim hızı sağlar.
> Neden: Ek makine, daha uzun çevrime rağmen birim zamanda daha çok parça üretir.
>
> **d)**
> Ne yapıyoruz: Maksimum alma mantığını açıklıyoruz.
> Formül/Yöntem: Eşzamanlı çalışma.
> Hesap: Operatör turu ve makine süresi paralel ilerler; çevrim, ikisinden uzun olanı bittiğinde tamamlanır.
> Sonuç: $T(m)=\max\{a+t,\ m(a+b)\}$, toplam değil.
> Neden: Süreler aynı anda akar; toplamak onları ardışık sayardı ve çevrimi olduğundan uzun gösterirdi.

---

### S05 — Zor — Birim maliyet kararı

> [!question] Soru
> S04'teki CNC atölyesinde şimdi maliyet kararı veriyorsunuz. Operatörün saatlik maliyeti $c_o = 18$ TL, her bir makinenin saatlik maliyeti $c_m = 8$ TL'dir. S04'ten $T(2)=6{,}5$ dk ve $T(3)=6{,}9$ dk.
>
> a) Saatlik maliyetleri dakika cinsine çevirin.
> b) $m=2$ için birim başına maliyeti $C_u(2)$ hesaplayın.
> c) $m=3$ için birim başına maliyeti $C_u(3)$ hesaplayın.
> ç) Üretim hızı ve birim maliyeti birlikte değerlendirerek hangi $m$ seçilmeli?
> d) Maliyet ve hız kriterleri farklı $m$ gösterseydi nasıl karar verilir?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Birim başına maliyet karşılaştırması ile en ekonomik makine ataması.
> **Hangi formül:** $C_u(m) = \dfrac{(c_o + m \cdot c_m) \cdot T(m)}{m}$ — birimleri tutarlı tut (dakika).
> **Dikkat:** Saat/dakika dönüşümünü unutma.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Maliyetleri dakikaya çeviriyoruz.
> Formül/Yöntem: TL/saat ÷ 60 = TL/dk.
> Hesap: $c_o = 18/60 = 0{,}30$ TL/dk; $c_m = 8/60 \approx 0{,}1333$ TL/dk.
> Sonuç: $c_o = 0{,}30$, $c_m \approx 0{,}1333$ TL/dk.
> Neden: $T(m)$ dakika cinsinden olduğu için maliyetler de dakikaya çevrilmelidir.
>
> **b)**
> Ne yapıyoruz: $m=2$ birim maliyetini buluyoruz.
> Formül/Yöntem: $C_u(m) = \dfrac{(c_o + m c_m) T(m)}{m}$
> Hesap: $C_u(2) = \dfrac{(0{,}30 + 2 \times 0{,}1333) \times 6{,}5}{2} = \dfrac{0{,}5667 \times 6{,}5}{2} = \dfrac{3{,}683}{2} = 1{,}84$ TL/parça.
> Sonuç: $C_u(2) \approx 1{,}84$ TL/parça.
> Neden: Çevrim maliyeti, o çevrimde üretilen parça sayısına ($m$) bölünür.
>
> **c)**
> Ne yapıyoruz: $m=3$ birim maliyetini buluyoruz.
> Formül/Yöntem: Aynı formül, $m=3$.
> Hesap: $C_u(3) = \dfrac{(0{,}30 + 3 \times 0{,}1333) \times 6{,}9}{3} = \dfrac{0{,}70 \times 6{,}9}{3} = \dfrac{4{,}83}{3} = 1{,}61$ TL/parça.
> Sonuç: $C_u(3) \approx 1{,}61$ TL/parça.
> Neden: Daha çok makine çevrim maliyetini artırsa da parça başına maliyeti düşürür.
>
> **ç)**
> Ne yapıyoruz: İki kriteri birlikte değerlendiriyoruz.
> Formül/Yöntem: Hız ($r$) + maliyet ($C_u$) karşılaştırması.
> Hesap:
>
> | $m$ | $T(m)$ | Üretim oranı | $C_u(m)$ |
> |:---:|:---:|:---:|:---:|
> | 2 | 6,5 dk | 0,308 parça/dk | 1,84 TL/parça |
> | 3 | 6,9 dk | 0,435 parça/dk | 1,61 TL/parça |
>
> Sonuç: $m=3$ seçilmelidir.
> Neden: $m=3$ hem daha yüksek üretim hızı hem daha düşük birim maliyet sağlar; iki kriter de aynı yönü gösterir.
>
> **d)**
> Ne yapıyoruz: Kriterler çelişirse karar yolunu açıklıyoruz.
> Formül/Yöntem: Bağlama göre öncelik.
> Hesap: Maliyeti düşük $m$ üretim hedefini de karşılıyorsa o seçilir. Çelişki varsa: (1) kapasite hedefi zorunluysa üretim hızı baskın, (2) hacim düşük ve talep kısıtlı değilse birim maliyet baskın.
> Sonuç: Tek bir kural değil, soru bağlamı önceliği belirler.
> Neden: Maliyet minimizasyonu ile talep karşılama farklı amaçlardır; hangisinin kısıt olduğu kararı yönlendirir.
