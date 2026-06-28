---
aliases: [Karma Havuz, Yöntem Seçme Soruları]
tags: [ders/tesis-planlama, soru-bankası, karma, aktif-geri-getirme]
---

# Karma Soru Havuzu

> [!danger] Uygulama
> Başlıklarda yöntem adı yoktur — önce hangi yöntemin gerektiğine **sen** karar ver. Her soruda `verilen → istenen → yöntem → birim` dört satırını yaz, sonra her alt soruyu (a–d) kapalı kitap çöz, en son `[!answer]-` kutusunu açıp hata kodla.

---

### K01 — Orta — Başa Baş + Kapasite

> [!question] Soru
> Doğtaş'ın yeni bir yemek masası modeli için açılacak hattının yıllık sabit maliyeti **360.000 TL**, satış fiyatı **150 TL/birim**, değişken maliyeti **90 TL/birim**'dir. Hattın yıllık en iyi işletim kapasitesi **9.000 birim**'dir.
>
> a) Birim katkı payını ($p-v$) hesaplayın.
> b) Zarar etmemek (kâr ≥ 0) için satılması gereken en küçük tam adedi (başa baş) bulun.
> c) Hat tam kapasitede (9.000 birim) çalışırsa yıllık kârı hesaplayın.
> ç) Değişken maliyet tedarik zoruyla 90 → 100 TL'ye çıksaydı başa baş adedi nasıl değişirdi?
> d) Başa baş noktası kapasiteye (9.000) tehlikeli derecede yakın olsaydı yönetime ne önerirdiniz?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Tek ürün başa baş analizi + kapasiteyle ilişkilendirme.
> **Hangi yöntem:** $x_{BB} = F / (p - v)$; kâr $= x(p-v) - F$.
> **Dikkat:** Katkı payı = fiyat − **değişken** maliyet; sabit maliyeti birime dağıtma.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Bir birimin sabit maliyete bıraktığı katkıyı buluyoruz.
> Formül: Katkı payı $= p - v$.
> Hesap: $150 - 90 = 60$ TL/birim.
> Sonuç: **60 TL/birim**.
> Neden: Her satılan masa, 60 TL'lik kısmı sabit maliyeti kapatmaya ayırır.
>
> **b)**
> Ne yapıyoruz: Sabit maliyeti katkı payına bölüyoruz.
> Formül: $x_{BB} = F / (p-v)$.
> Hesap: $360.000 / 60 = 6.000$ birim.
> Sonuç: **6.000 birim**.
> Neden: 6.000 birimde toplam katkı (360.000) tam sabit maliyete eşit, kâr sıfır.
>
> **c)**
> Ne yapıyoruz: Tam kapasitede toplam katkıdan sabiti düşüyoruz.
> Formül: Kâr $= x(p-v) - F$.
> Hesap: $9.000 \times 60 - 360.000 = 540.000 - 360.000 = 180.000$ TL.
> Sonuç: **180.000 TL** kâr.
> Neden: Başa baş üstündeki her birim doğrudan kâra döner (3.000 birim × 60).
>
> **ç)**
> Ne yapıyoruz: Yeni katkı payıyla başa başı yeniden hesaplıyoruz.
> Hesap: Katkı $= 150 - 100 = 50$; $x_{BB} = 360.000 / 50 = 7.200$ birim.
> Sonuç: Başa baş **6.000 → 7.200** birime yükselir.
> Neden: Her birim daha az katkı verince sabiti kapatmak için daha çok satmak gerekir; güvenlik payı (kapasiteye uzaklık) daralır.
>
> **d)**
> Ne yapıyoruz: Başa başın kapasiteye yakınlığını risk olarak yorumluyoruz.
> Sonuç: 7.200 başa baş, 9.000 kapasiteye %80 yüklenme demektir; küçük bir talep düşüşü zarara sokar. Öneri: fiyat/maliyet pazarlığıyla katkı payını yükseltmek, sabit maliyeti kısmak veya bu kadar düşük güvenlik payı olan yatırımı yeniden değerlendirmek.
> Neden: Başa baş kapasiteye yaklaştıkça "güvenlik payı" (margin of safety) azalır; dalgalı talepte risk artar.
>
> Paket: [[09 Öğrenme Paketleri/HF02A - Kapasite ve Tek Ürün Başa Baş|HF02A]].

---

### K02 — Zor — Binom ile Optimum Üretim Miktarı

> [!question] Soru
> Nurol Makina, bir savunma ihalesinde **tam 3 sağlam** ürün teslim ederse **60.000 TL** alacaktır; eksik parti kabul edilmez (en az 3 sağlam gerekir, fazlası teslim edilmez). Bir ürünün üretim maliyeti **10.000 TL**, sağlam çıkma olasılığı **%80**'dir. Üretim planlamacı $Q = 3, 4, 5, 6$ adaylarını beklenen kâr açısından karşılaştıracaktır.
>
> a) Beklenen kâr fonksiyonunu $Q$ cinsinden yazın ($X \sim \text{Binom}(Q;\,0{,}8)$).
> b) $Q=3$ ve $Q=4$ için "en az 3 sağlam" olasılığını ve beklenen kârı hesaplayın.
> c) $Q=5$ ve $Q=6$ için aynı hesabı yapın.
> ç) Dört adayı bir tabloda toplayıp en yüksek beklenen kârlı $Q$'yu seçin.
> d) Maliyet 10.000 → 8.000 TL'ye inseydi optimum $Q$ büyür mü küçülür mü? Sezgisel gerekçelendirin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Rassal ıskarta altında beklenen kârı maksimize eden üretim miktarı.
> **Hangi yöntem:** $E[\text{kâr}] = 60.000 \cdot P(X \ge 3) - 10.000\,Q$.
> **Dikkat:** Fazla üretim güvenceyi (P(X≥3)) artırır ama her ek birim 10.000 TL maliyet ekler — denge noktası aranır.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Gelir × başarı olasılığından maliyeti çıkarıyoruz.
> Formül: $E[\text{kâr}](Q) = 60.000 \cdot P(X \ge 3) - 10.000\,Q$, $X \sim \text{Binom}(Q; 0{,}8)$.
> Sonuç: Yukarıdaki fonksiyon.
> Neden: Ödeme yalnız "en az 3 sağlam" olunca alınır; maliyet her üretilen birim için kesin.
>
> **b)**
> Ne yapıyoruz: $Q=3$ ve $Q=4$ olasılıklarını binomla buluyoruz.
> Hesap:
> $Q=3$: $P(X\ge3)=0{,}8^3=0{,}512$ → $E=60.000(0{,}512)-30.000=30.720-30.000=\mathbf{720}$ TL.
> $Q=4$: $P(X\ge3)=\binom{4}{3}0{,}8^3 0{,}2 + 0{,}8^4 = 0{,}4096+0{,}4096=0{,}8192$ → $E=60.000(0{,}8192)-40.000=49.152-40.000=\mathbf{9.152}$ TL.
> Sonuç: 720 ve 9.152 TL.
> Neden: 4. birim güvenceyi 0,512 → 0,819'a sıçratır; ek 10.000 maliyete rağmen büyük kazanç.
>
> **c)**
> Ne yapıyoruz: $Q=5$ ve $Q=6$ için $1-P(X\le2)$ hesaplıyoruz.
> Hesap:
> $Q=5$: $P(X\le2)=0{,}2^5+5(0{,}8)(0{,}2^4)+10(0{,}8^2)(0{,}2^3)=0{,}00032+0{,}0064+0{,}0512=0{,}05792$; $P(X\ge3)=0{,}94208$ → $E=56.524{,}8-50.000=\mathbf{6.524{,}80}$ TL.
> $Q=6$: $P(X\le2)=0{,}2^6+6(0{,}8)(0{,}2^5)+15(0{,}8^2)(0{,}2^4)=0{,}000064+0{,}001536+0{,}01536=0{,}01696$; $P(X\ge3)=0{,}98304$ → $E=58.982{,}4-60.000=\mathbf{-1.017{,}60}$ TL.
> Sonuç: 6.524,80 ve −1.017,60 TL.
> Neden: 5. ve 6. birim güvenceyi az artırır (0,82→0,94→0,98) ama her biri 10.000 ekler; marjinal fayda maliyetin altına düşer.
>
> **ç)**
> Ne yapıyoruz: Dört adayı sıralıyoruz.
> Hesap:
>
> | $Q$ | $P(X\ge3)$ | Beklenen kâr (TL) |
> |---:|---:|---:|
> | 3 | 0,512 | 720 |
> | **4** | 0,8192 | **9.152** ← en yüksek |
> | 5 | 0,94208 | 6.524,80 |
> | 6 | 0,98304 | −1.017,60 |
>
> Sonuç: Optimum **$Q=4$** (9.152 TL).
> Neden: Marjinal güvence kazancı 4. birime kadar maliyeti aşar, sonra düşer — tek tepe noktası $Q=4$.
>
> **d)**
> Ne yapıyoruz: Birim maliyet düşünce optimumun yönünü düşünüyoruz.
> Sonuç: Maliyet ucuzlarsa optimum $Q$ **büyür** (5'e kayabilir); fazladan güvence almanın bedeli azaldığı için daha çok yedek üretmek kârlı hale gelir.
> Neden: Marjinal birim faydası (ek güvence × 60.000) sabit kalırken marjinal maliyet düştüğünden, kâr-pozitif kalan birim sayısı artar.
>
> Paket: [[09 Öğrenme Paketleri/HF03 - Rassal Iskarta Payı|HF03]].

---

### K03 — Orta — Fire: Aşamalı vs Tek Yuvarlama

> [!question] Soru
> Norm Cıvata'nın bir hattında iki seri operasyondan sonra **240 tam sağlam** parça gerekmektedir. Fire oranları süreç sırasıyla **%4** (1. operasyon) ve **%6** (2. operasyon)'dır. Üretim mühendisi hatta kaç parça sokulacağını hesaplayacaktır.
>
> a) İki operasyonun bileşik geçiş (sağlam kalma) oranını hesaplayın.
> b) Tek-yuvarlama (bileşik oranla tek seferde) yöntemiyle giriş miktarını bulun.
> c) Geriye doğru aşamalı (operasyon bazlı, her adımda yukarı yuvarlayarak) giriş miktarını bulun.
> ç) İki sonucu karşılaştırın; neden aşamalı yöntem daha güvenlidir?
> d) Operasyon sırası (%6 önce, %4 sonra) değişseydi aşamalı sonuç değişir miydi? Kontrol edin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Çok aşamalı fire altında giriş miktarı; iki yuvarlama stratejisinin farkı.
> **Hangi yöntem:** Tek: $I = N / \prod(1-s_k)$. Aşamalı: her operasyonda $\lceil \cdot \rceil$ ile geriye doğru.
> **Dikkat:** Geriye doğru çalış (son operasyondan başla); her adımda **yukarı** yuvarla.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Sağlam kalma oranlarını çarpıyoruz.
> Hesap: $(1-0{,}04)(1-0{,}06) = 0{,}96 \times 0{,}94 = 0{,}9024$.
> Sonuç: Bileşik geçiş oranı **0,9024**.
> Neden: Her operasyon bağımsız olarak parçanın bir kısmını eler; geçiş oranları çarpılır.
>
> **b)**
> Ne yapıyoruz: Hedefi bileşik orana bölüp tek seferde yuvarlıyoruz.
> Hesap: $I = 240 / 0{,}9024 = 265{,}96 \Rightarrow \lceil 265{,}96 \rceil = 266$.
> Sonuç: Tek-yuvarlama **266** parça.
> Neden: Tüm fireyi tek bir oran gibi ele alır, ara yuvarlamayı atlar.
>
> **c)**
> Ne yapıyoruz: Son operasyondan geriye, her adımda yukarı yuvarlıyoruz.
> Hesap:
> 2. op çıkışı 240 olmalı → giriş $= \lceil 240/0{,}94 \rceil = \lceil 255{,}32 \rceil = 256$.
> 1. op çıkışı 256 olmalı → giriş $= \lceil 256/0{,}96 \rceil = \lceil 266{,}67 \rceil = 267$.
> Sonuç: Aşamalı **267** parça.
> Neden: Her operasyon kesikli (tam) parça işlediğinden, her aşamada ayrı ayrı tamsayıya yuvarlanır.
>
> **ç)**
> Ne yapıyoruz: İki yöntemi kıyaslıyoruz.
> Sonuç: Tek-yuvarlama 266, aşamalı 267 → aşamalı **1 parça fazla** ister.
> Neden: Aşamalı yöntem her ara aşamada da tam sağlam parça garanti eder; tek-yuvarlama ara kayıpları görmezden geldiği için hedefi az da olsa ıskalama riski taşır. Üretimde aşamalı daha güvenlidir.
>
> **d)**
> Ne yapıyoruz: Sırayı ters çevirip (%6 önce, %4 sonra) tekrar hesaplıyoruz.
> Hesap: $\lceil 240/0{,}96 \rceil = \lceil 250 \rceil = 250$; sonra $\lceil 250/0{,}94 \rceil = \lceil 265{,}96 \rceil = 266$.
> Sonuç: Sıra değişince aşamalı sonuç **267 → 266** olur.
> Neden: Ara yuvarlamalar sıraya duyarlıdır; büyük fireyi sona koymak (önce küçük fire) burada bir parça fazla isterken, büyük fireyi öne almak daha az ister. Tek-yuvarlama ise sıradan bağımsız 266 verir.
>
> Paket: [[09 Öğrenme Paketleri/HF04A - Fire ve Donanım Gereksinimi|HF04A]].

---

### K04 — Zor — ROC ile Hücre Oluşturma

> [!question] Soru
> Ermetal'in pres atölyesinde bir makine-parça matrisi (satır = makine, sütun = parça) aşağıdaki gibidir. Endüstri mühendisi, satır ve sütunları ikili (binary) ağırlıklarla kararlı sıraya getirip hücreleri görünür kılacaktır.
> $$B=\begin{bmatrix}1&0&1\\0&1&1\\1&0&0\end{bmatrix}$$
>
> a) İlk iterasyonda satır ağırlıklarını (sütun konumu $2^{n-j}$) hesaplayıp satırları sıralayın.
> b) Yeni satır sırasıyla sütun ağırlıklarını ($2^{m-i}$) hesaplayıp sütunları sıralayın.
> c) Yeni sütun sırasıyla satır ağırlıklarını tekrar hesaplayıp kararlılığı (stability) kontrol edin.
> ç) Nihai satır ve sütun sırasını yazın; matrisi yeniden dizip oluşan hücreleri belirtin.
> d) ROC'un köşegen blok yapısı her zaman "kusursuz" hücre verir mi? Artık (residual) eleman riskini açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Rank Order Clustering ile satır/sütun yeniden sıralama.
> **Hangi yöntem:** Satır ağırlığı $=\sum_j b_{ij}2^{n-j}$; sütun ağırlığı $=\sum_i b_{ij}2^{m-i}$; sıralama tekrarlanır, değişmeyince durur.
> **Dikkat:** Her iterasyonda büyükten küçüğe sırala; iki ardışık iterasyon aynıysa kararlıdır.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Sütun ağırlıkları (sol→sağ) 4-2-1 ile satır ağırlıklarını buluyoruz.
> Hesap:
> $r_1=[1,0,1] \to 4+0+1 = 5$
> $r_2=[0,1,1] \to 0+2+1 = 3$
> $r_3=[1,0,0] \to 4+0+0 = 4$
> Sıralama (büyük→küçük): $r_1(5), r_3(4), r_2(3)$ → satır sırası **1-3-2**.
> Sonuç: Satır sırası 1-3-2.
> Neden: Sola yığılan 1'ler büyük ağırlık verir; en "dolu sol" satır üste çıkar.
>
> **b)**
> Ne yapıyoruz: Satırları $r_1, r_3, r_2$ dizip satır konumu 4-2-1 ile sütun ağırlıklarını buluyoruz.
> Hesap (sıra: $r_1, r_3, r_2$):
> $c_1: (1,1,0) \to 4+2+0 = 6$
> $c_2: (0,0,1) \to 0+0+1 = 1$
> $c_3: (1,0,1) \to 4+0+1 = 5$
> Sıralama: $c_1(6), c_3(5), c_2(1)$ → sütun sırası **1-3-2**.
> Sonuç: Sütun sırası 1-3-2.
> Neden: Üstte yığılan 1'ler büyük ağırlık verir; en "dolu üst" sütun sola gelir.
>
> **c)**
> Ne yapıyoruz: Sütunları $c_1, c_3, c_2$ dizip satır ağırlıklarını tekrar buluyoruz.
> Hesap (sütun sırası $c_1, c_3, c_2$, ağırlık 4-2-1):
> $r_1: (1,1,0) \to 6$; $r_3: (1,0,0) \to 4$; $r_2: (0,1,1) \to 3$.
> Sıralama: $r_1(6), r_3(4), r_2(3)$ → satır sırası 1-3-2 (değişmedi).
> Sonuç: Kararlı (stable) — satır sırası önceki iterasyonla aynı.
> Neden: İki ardışık iterasyonda sıralama değişmediğinde ROC durur.
>
> **ç)**
> Ne yapıyoruz: Nihai sırayla matrisi yeniden diziyoruz.
> Sonuç: Satır **1-3-2**, sütun **1-3-2**. Yeniden dizilmiş matris:
> $$\begin{array}{c|ccc} & c_1 & c_3 & c_2 \\ \hline r_1 & 1 & 1 & 0 \\ r_3 & 1 & 0 & 0 \\ r_2 & 0 & 1 & 1 \end{array}$$
> Hücre 1: {makine 1,3 — parça 1}; Hücre 2: {makine 2 — parça 3,2} ile makine 1'in parça 3 ile çakışması bir köşegen-dışı (residual) 1 oluşturur.
> Neden: ROC 1'leri köşegene yığarak doğal hücreleri görünür kılar.
>
> **d)**
> Ne yapıyoruz: ROC'un sınırını açıklıyoruz.
> Sonuç: Hayır — ROC köşegen blokları görünür kılar ama her zaman temiz ayrışma garanti etmez. Burada makine 1'in hem parça 1 hem parça 3 işlemesi köşegen-dışı bir "artık" eleman bırakır; bu, hücreler arası ortak makine/parça (bottleneck) demektir.
> Neden: Gerçek matrisler nadiren tam blok-köşegendir; artık elemanlar makine çoğaltma, parça yeniden rotalama veya istisna-hücre kararı gerektirir.
>
> Paket: [[09 Öğrenme Paketleri/HF05A - DCA ve ROC Hücre Oluşturma|HF05A]].

---

### K05 — Orta — Yönlü From-To Matrisi (Eşdeğer Akış)

> [!question] Soru
> Tırsan'ın bir treyler atölyesinde X ürünü **10 adet** üretilir, rotası **A → B → C**'dir. Y ürünü **6 adet** üretilir, ağırlık (eşdeğer) katsayısı **3**'tür ve rotası **C → B → A**'dır. Süreç mühendisi yönlü from-to akış matrisini kuracaktır.
>
> a) Y'nin eşdeğer (ağırlıklı) akış miktarını hesaplayın.
> b) X'in katkıladığı yönlü hücreleri yazın.
> c) Y'nin katkıladığı yönlü hücreleri yazın.
> ç) Sıfır olmayan tüm from-to hücrelerini birleşik tabloda gösterin.
> d) Simetrik (yönsüz) akış matrisi $F_{ij}=f_{ij}+f_{ji}$'ye geçilseydi A–B ve B–C çiftlerinin değeri ne olurdu?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Eşdeğer katsayıyla ağırlıklandırılmış yönlü akış matrisi.
> **Hangi yöntem:** Her ürün rotasındaki ardışık çiftlere (adet × katsayı) ekle; yön korunur.
> **Dikkat:** A→B ile B→A farklı hücrelerdir (yönlü); eşdeğer katsayıyı unutma.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Y'nin gerçek adedini katsayıyla ölçekliyoruz.
> Hesap: $6 \times 3 = 18$ eşdeğer yük.
> Sonuç: Y'nin akış şiddeti **18**.
> Neden: Eşdeğer katsayı, Y'nin bir biriminin taşıma yükü açısından 3 X birimine denk olduğunu söyler.
>
> **b)**
> Ne yapıyoruz: X'in A→B→C rotasını ardışık çiftlere açıyoruz.
> Hesap: A→B: 10; B→C: 10.
> Sonuç: $f_{AB}=10$, $f_{BC}=10$.
> Neden: 10 adet X, her ardışık operasyon çiftinde 10 yük taşır.
>
> **c)**
> Ne yapıyoruz: Y'nin C→B→A rotasını ardışık çiftlere açıyoruz.
> Hesap: C→B: 18; B→A: 18.
> Sonuç: $f_{CB}=18$, $f_{BA}=18$.
> Neden: Eşdeğer 18 yük, Y'nin ters yöndeki (C→B→A) güzergâhında akar.
>
> **ç)**
> Ne yapıyoruz: Tüm sıfır olmayan hücreleri topluyoruz.
> Sonuç:
>
> | From\To | A | B | C |
> |---|---:|---:|---:|
> | **A** | — | 10 | 0 |
> | **B** | 18 | — | 10 |
> | **C** | 0 | 18 | — |
>
> Neden: X ileri yönü, Y geri yönü doldurur; çakışan yön yoktur.
>
> **d)**
> Ne yapıyoruz: Çiftleri yönsüz toplama indirgiyoruz.
> Hesap: $F_{AB}=f_{AB}+f_{BA}=10+18=28$; $F_{BC}=f_{BC}+f_{CB}=10+18=28$.
> Sonuç: A–B = **28**, B–C = **28**.
> Neden: Simetrik matris yönü silip toplam etkileşimi verir; BLOCPLAN/REL-DIST gibi yöntemler bu yönsüz değeri kullanır.
>
> Paket: [[09 Öğrenme Paketleri/HF06A - MAG Akış Şiddeti ve From-To Matrisi|HF06A]].

---

### K06 — Kolay — CRAFT Takas Kararı

> [!question] Soru
> Arçelik'in Çayırova süreç yerleşiminde toplam yönlü akış-mesafe maliyeti **570** birimdir. CRAFT bir aday takas (iki bölümün yer değiştirmesi) deniyor; yalnız etkilenen çiftlerin net değişimi **−90** bulunuyor.
>
> a) Takas sonrası yeni maliyeti hesaplayın.
> b) Bu bir minimizasyon problemi olduğuna göre takasın kabul edilip edilmeyeceğine karar verin.
> c) CRAFT neden "yalnız etkilenen çiftlerin" değişimine bakar, tüm maliyeti baştan hesaplamaz?
> ç) Net değişim **+40** çıksaydı karar ne olurdu?
> d) Birden çok aday takas (örn. −90, −30, +40) varsa CRAFT hangisini seçer ve sonra ne yapar?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** İyileştirici algoritmada takas kabul kuralı.
> **Hangi yöntem:** $Z' = Z + \Delta$; minimizasyonda $\Delta < 0$ ise kabul.
> **Dikkat:** Negatif net değişim = maliyet düşüşü = iyi.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Mevcut maliyete net değişimi ekliyoruz.
> Hesap: $Z' = 570 + (-90) = 480$.
> Sonuç: Yeni maliyet **480**.
> Neden: Net değişim, takasın toplam maliyete etkisidir.
>
> **b)**
> Ne yapıyoruz: Yeni maliyeti eskiyle kıyaslıyoruz.
> Sonuç: $480 < 570$ → takas **kabul edilir**.
> Neden: Minimizasyonda maliyeti düşüren her takas iyileştirmedir.
>
> **c)**
> Ne yapıyoruz: Hesaplama verimini açıklıyoruz.
> Sonuç: Takas yalnız iki bölümün konumunu değiştirir; sadece bu bölümleri içeren çiftlerin mesafesi değişir, diğer tüm çiftler aynı kalır. Bu yüzden değişmeyenleri yeniden toplamak gereksizdir.
> Neden: Marjinal (delta) hesabı, her takas için tüm matrisi yeniden çarpmaktan çok daha hızlıdır — büyük problemlerde kritik.
>
> **ç)**
> Ne yapıyoruz: Pozitif değişim senaryosunu değerlendiriyoruz.
> Sonuç: $\Delta = +40$ olsaydı $Z'=610 > 570$ → takas **reddedilir**.
> Neden: Maliyeti artıran takas minimizasyon hedefine aykırıdır.
>
> **d)**
> Ne yapıyoruz: Çoklu aday arasında seçim kuralını yazıyoruz.
> Sonuç: CRAFT en negatif (en çok düşüren) takası seçer → −90'ı uygular; ardından yeni yerleşimde tüm aday takasları yeniden değerlendirir. İyileştiren takas kalmayınca durur (yerel optimum).
> Neden: Açgözlü (greedy) en dik iniş; her turda en büyük kazancı alıp tekrarlar, iyileşme bitince sonlanır.
>
> Paket: [[09 Öğrenme Paketleri/HF07A - Süreç Yerleşimi Taşıma Maliyeti|HF07A]].

---

### K07 — Kolay — Algoritma Tanıma (TCR + PR)

> [!question] Soru
> BMC'nin yerleşim ekibinde bir yöntem şöyle çalışıyor: önce her bölümün diğerleriyle toplam yakınlık derecesi hesaplanıyor, en yüksek olan merkeze konuyor; sonra her yeni bölüm, yerleşmiş komşulara göre olası konumlarda puanlanıp en iyi yere yerleştiriliyor.
>
> a) Bu yapıcı (construction) algoritmanın adını söyleyin.
> b) Bölüm seçiminde kullanılan puanın adını ve ne ölçtüğünü yazın.
> c) Konum seçiminde kullanılan puanın adını ve nasıl hesaplandığını yazın.
> ç) Bu algoritma deterministik mi rassal mı; aynı girdiyle hep aynı sonucu verir mi?
> d) Aynı problemi rassal başlangıç + süpürmeyle çözen alternatif yapıcı algoritma hangisidir; temel farkı nedir?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Yöntem tanıma — TCR (seçim) + PR (yerleştirme) imzası.
> **Hangi yöntem:** Bu imza **CORELAP**'a aittir.
> **Dikkat:** TCR/PR → CORELAP; rassal+süpürme → ALDEP; mevcut yerleşim iyileştirme → CRAFT.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: İmzayı yöntemle eşliyoruz.
> Sonuç: **CORELAP** (Computerized Relationship Layout Planning).
> Neden: "Toplam yakınlık derecesiyle seç, komşuluk puanıyla yerleştir" tam CORELAP akışıdır.
>
> **b)**
> Ne yapıyoruz: Seçim puanını tanımlıyoruz.
> Sonuç: **TCR** (Total Closeness Rating) — bölümün diğer tüm bölümlerle ilişki ağırlıklarının toplamı.
> Neden: En yüksek TCR'li bölüm "en çok istenen" olduğundan merkeze konur.
>
> **c)**
> Ne yapıyoruz: Yerleştirme puanını tanımlıyoruz.
> Sonuç: **PR** (Placement Rating) — aday konumdaki yerleşmiş komşularla ilişki ağırlıklarının (kenar ×1, köşe ×0,5) toplamı.
> Neden: En yüksek PR'li konum, güçlü ilişkili komşulara en yakın olandır.
>
> **ç)**
> Ne yapıyoruz: Belirlenimi değerlendiriyoruz.
> Sonuç: **Deterministik** — aynı REL girdisiyle hep aynı yerleşimi üretir.
> Neden: TCR ve PR hesapları rassallık içermez; bağ bozma kuralları da sabittir.
>
> **d)**
> Ne yapıyoruz: Rassal alternatifi belirtiyoruz.
> Sonuç: **ALDEP** — ilk bölümü (ve eşik altı ilişkilileri) rassal seçer, dikey süpürmeyle yerleştirir; farklı tohumlarla çok sayıda alternatif üretir.
> Neden: CORELAP tek deterministik çözüm verirken ALDEP çeşitlilik üretir; büyük problemlerde çoklu-alternatif avantaja döner.
>
> Paket: [[09 Öğrenme Paketleri/HF10A - CORELAP|HF10A]].

---

### K08 — Orta — Ağırlıklı Medyan: Optimum Aralık

> [!question] Soru
> Yurtiçi Kargo, tek eksen (otoyol koridoru) üzerindeki müşterilerine hizmet edecek bir aktarma noktası konumlandıracaktır. Koordinat-ağırlık çiftleri: $(0,4)$, $(4,2)$, $(10,6)$.
>
> a) Toplam ağırlığı ve eşiği ($W/2$) hesaplayın.
> b) Koordinatları sıralayıp kümülatif ağırlık tablosunu kurun.
> c) Optimumun tek nokta mı aralık mı olduğunu belirleyip $x^*$'ı yazın.
> ç) $x=4$ ve $x=10$ noktalarında $f(x)=\sum w_i|x-a_i|$ hesaplayıp eşitliği doğrulayın.
> d) Ağırlık çifti $(4,2) \to (4,3)$ olsaydı çözüm tek noktaya döner miydi? Gerekçelendirin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Minisum tek eksen; kümülatif ağırlık $W/2$'ye **eşit** olunca optimum aralık.
> **Hangi yöntem:** Sırala, kümülatifle; $W/2$'yi aşan ilk nokta = tek nokta, **eşit** olan = aralık.
> **Dikkat:** "Eşit" durumunu "aştı" sanıp tek nokta yazma — bu en sık tuzak.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Ağırlık toplamı ve yarısı.
> Hesap: $W = 4+2+6 = 12$; $W/2 = 6$.
> Sonuç: $W=12$, eşik **6**.
> Neden: Medyan, ağırlığın yarısının iki yana düştüğü noktadır.
>
> **b)**
> Ne yapıyoruz: Koordinat sırasıyla kümülatif kuruyoruz.
> Hesap:
>
> | $a_i$ | $w_i$ | Kümülatif |
> |---:|---:|---:|
> | 0 | 4 | 4 |
> | 4 | 2 | **6** (= W/2) |
> | 10 | 6 | 12 |
>
> Sonuç: $x=4$'te kümülatif tam **6**'ya eşit.
> Neden: Solda 6, sağda 6 birim ağırlık kalır — denge tek nokta değil.
>
> **c)**
> Ne yapıyoruz: Eşitlik durumunun sonucunu yazıyoruz.
> Sonuç: Kümülatif tam $W/2$'ye eşit → optimum **$x^* \in [4,\,10]$** aralığı.
> Neden: $a=4$ ile sonraki koordinat $a=10$ arasındaki her noktada sol/sağ ağırlık eşit kalır, $f$ sabittir.
>
> **ç)**
> Ne yapıyoruz: İki uçta $f$ hesaplıyoruz.
> Hesap:
> $x=4$: $4|4-0|+2|4-4|+6|4-10| = 16+0+36 = 52$.
> $x=10$: $4|10-0|+2|10-4|+6|10-10| = 40+12+0 = 52$.
> Sonuç: İki uçta da $f=\mathbf{52}$ → aralık doğrulandı.
> Neden: Aralık içinde sağa gitmek soldan kaybedip sağdan kazandırır; net değişim sıfır.
>
> **d)**
> Ne yapıyoruz: Ağırlık değişiminin etkisini kontrol ediyoruz.
> Hesap: $(4,3)$ ile $W=4+3+6=13$, $W/2=6{,}5$; kümülatif $x=4$'te $4+3=7 > 6{,}5$ → eşik **aşılır**.
> Sonuç: Çözüm **tek noktaya** ($x^*=4$) döner.
> Neden: Kümülatif tam $W/2$'ye eşit kalmayıp aştığında düz bölge tek denge noktasına çöker.
>
> Paket: [[09 Öğrenme Paketleri/HF11A - Minisum ve Ağırlıklı Medyan|HF11A]].

---

### K09 — Zor — Minimax (u-v Dönüşümü)

> [!question] Soru
> İzmir Büyükşehir Belediyesi bir acil servis istasyonu konumlandıracaktır. Üç talep noktası: $(0,0)$, $(8,0)$, $(2,6)$. Amaç, en uzaktaki noktaya dikdoğrusal uzaklığı en küçük yapmaktır (minimax).
>
> a) Her nokta için $u_i = a_i+b_i$ ve $v_i = a_i-b_i$ değerlerini bulun.
> b) $\Delta u$, $\Delta v$ yayılımlarını ve minimax yarıçapı $R^*$'ı hesaplayın.
> c) $U^*$ ve $V^*$ optimum aralıklarını kurun; hangi eksenin çöktüğünü belirtin.
> ç) Geriye dönüşümle optimum çözüm kümesini (nokta/doğru parçası) yazın.
> d) Bir iç noktada en uzak talep uzaklığının $R^*$'a eşit olduğunu doğrulayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** En büyük uzaklığı minimize eden konum; u-v dönüşümü.
> **Hangi yöntem:** $R^* = \tfrac12 \max(\Delta u, \Delta v)$; aralıkları kur, $x=\tfrac{u+v}{2}, y=\tfrac{u-v}{2}$ ile geri dön.
> **Dikkat:** $R^*$ için **maksimum** yayılım alınır; büyük yayılım o ekseni tek noktaya çökertir.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: 45° dönüşümü uyguluyoruz.
> Hesap:
>
> | Nokta | $(a,b)$ | $u=a+b$ | $v=a-b$ |
> |---|---:|---:|---:|
> | P1 | (0,0) | 0 | 0 |
> | P2 | (8,0) | 8 | 8 |
> | P3 | (2,6) | 8 | −4 |
>
> Sonuç: $u\in\{0,8,8\}$, $v\in\{0,8,-4\}$.
> Neden: Dönüşüm Manhattan'ı Chebyshev'e çevirir, eksenleri ayırır.
>
> **b)**
> Ne yapıyoruz: Yayılımları ve yarıçapı buluyoruz.
> Hesap: $\Delta u = 8-0 = 8$; $\Delta v = 8-(-4) = 12$; $R^* = \tfrac12\max(8,12) = \mathbf{6}$.
> Sonuç: $R^*=6$.
> Neden: Minimax yarıçapı, baskın (büyük) yayılımın yarısıdır.
>
> **c)**
> Ne yapıyoruz: Optimum aralıkları kuruyoruz.
> Hesap:
> $V^* = [v_{\max}-R^*,\; v_{\min}+R^*] = [8-6,\; -4+6] = [2,\,2] \Rightarrow v^*=2$ (tek nokta).
> $U^* = [u_{\max}-R^*,\; u_{\min}+R^*] = [8-6,\; 0+6] = [2,\,6]$ (aralık).
> Sonuç: $v$ ekseni çöker ($v^*=2$), $u$ aralık kalır.
> Neden: $\Delta v > \Delta u$ olduğundan v ekseni tek noktaya iner.
>
> **ç)**
> Ne yapıyoruz: $x=\tfrac{u+v}{2}, y=\tfrac{u-v}{2}$ ile geri dönüyoruz.
> Hesap: $(u,v)=(2,2)\to(2,0)$; $(u,v)=(6,2)\to(4,2)$.
> Sonuç: Optimum, **$(2,0)$ – $(4,2)$ doğru parçası**.
> Neden: Tek nokta ($v$) + aralık ($u$) → ters dönüşümde doğru parçası.
>
> **d)**
> Ne yapıyoruz: İç nokta $(3,1)$'de en uzak talebi buluyoruz.
> Hesap: P1: $3+1=4$; P2: $5+1=6$; P3: $1+5=6$ → maks **6**.
> Sonuç: Maks $= 6 = R^*$ ✓.
> Neden: Optimum küme boyunca en uzak uzaklık sabit $R^*$ kalır; doğrulama tutar.
>
> Paket: [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|HF11B]].

---

### K10 — Orta — Net Tasarrufla Aday Tesis Kararı

> [!question] Soru
> Migros yeni bir aday dağıtım merkezini değerlendiriyor. Adayın sabit açma maliyeti **900 TL**'dir. Dört mağazanın mevcut açık tesislerle hizmet maliyetleri **500, 300, 800, 200**; aday açılırsa **200, 350, 400, 250** olacaktır.
>
> a) Hangi mağazaların aday tesise geçeceğini (aday daha ucuz) belirleyin.
> b) Brüt tasarrufu $GS = \sum_j \max\{0,\, c_{\text{eski},j} - c_{\text{aday},j}\}$ hesaplayın.
> c) Net tasarrufu $NS = GS - F_{\text{aday}}$ hesaplayıp kararı verin.
> ç) Sabit maliyet kaç TL'nin altına inseydi aday açmak kârlı olurdu (eşik)?
> d) "Aday birçok satırda daha ucuz, o yüzden açılmalı" sezgisi neden yanıltıcı? Bu veriyle gösterin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Yeni tesis ekleme kârlılığı — brüt tasarruf vs sabit maliyet.
> **Hangi yöntem:** Yalnız pozitif farkları topla; $NS = GS - F$.
> **Dikkat:** Pahalılaşan mağazalar geçmez; negatif farkı toplama.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Her mağazada eski vs aday maliyeti kıyaslıyoruz.
> Hesap: M1: 500>200 ✓; M2: 300<350 ✗; M3: 800>400 ✓; M4: 200<250 ✗.
> Sonuç: **M1 ve M3** aday tesise geçer; M2, M4 kalır.
> Neden: Mağaza yalnız ucuzladığı tesise kayar.
>
> **b)**
> Ne yapıyoruz: Pozitif farkları topluyoruz.
> Hesap: $GS = (500-200) + 0 + (800-400) + 0 = 300 + 400 = 700$.
> Sonuç: $GS = \mathbf{700}$ TL.
> Neden: Yalnız geçen mağazalar (M1: 300, M3: 400) tasarruf üretir.
>
> **c)**
> Ne yapıyoruz: Sabit maliyeti düşüyoruz.
> Hesap: $NS = 700 - 900 = -200$.
> Sonuç: $NS = -200 < 0$ → aday **açılmaz**.
> Neden: Açma maliyeti, geçen mağazaların tasarrufunu aşıyor.
>
> **ç)**
> Ne yapıyoruz: Kâr eşiğini buluyoruz.
> Hesap: $NS \ge 0 \Rightarrow F \le GS = 700$.
> Sonuç: $F < 700$ TL olsaydı açmak kârlı olurdu (tam 700'de kayıtsız).
> Neden: Brüt tasarruf 700 sabit; sabit maliyet bunun altına inince net tasarruf pozitife döner.
>
> **d)**
> Ne yapıyoruz: Sezgisel yanılgıyı gösteriyoruz.
> Sonuç: Aday 4 satırın 3'ünde (M1, M3 ucuz; M2, M4 pahalı aslında 2'sinde) cazip görünse de, asıl ölçüt tek tek hücreler değil **net tasarruf vs sabit maliyet**tir. Burada 700 < 900 olduğundan açmak toplam maliyeti 200 TL **artırır**.
> Neden: Tasarruf yalnız geçen mağazalardan gelir ve sabit maliyetle kıyaslanmalıdır; "ucuz görünüyor" sabit yatırımı görmezden gelir.
>
> Paket: [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|HF12B]].

---

### K11 — Kolay — Yöntem Seçimi: Yapıcı vs İyileştirici

> [!question] Soru
> TUSAŞ'ın bir danışmanının elinde yalnız **A-E-I-O-U-X ilişki tablosu** ve **bölüm alanları** vardır; mevcut (başlangıç) bir yerleşim yoktur. Yeni binanın ilk yerleşimi üretilecektir.
>
> a) Bu girdilerle CRAFT mı CORELAP mı doğrudan uygulanabilir? Seçin.
> b) Seçiminizin gerekçesini (girdi ihtiyacı açısından) açıklayın.
> c) Diğer algoritmanın çalışması için eksik olan girdi nedir?
> ç) İkisi bir arada nasıl kullanılır (hibrit akış)?
> d) BLOCPLAN bu durumda kullanılabilir mi; CORELAP'tan farkı nedir?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Construction (yapıcı) vs improvement (iyileştirici) ayrımı.
> **Hangi yöntem:** Başlangıç yerleşimi yoksa → yapıcı (CORELAP/ALDEP/BLOCPLAN); varsa iyileştirme → CRAFT.
> **Dikkat:** CRAFT mevcut yerleşim + akış matrisi ister; sıfırdan kuramaz.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Girdiyi yöntemin ihtiyacıyla eşliyoruz.
> Sonuç: **CORELAP** doğrudan uygulanabilir.
> Neden: CORELAP nitel REL tablosundan sıfırdan yerleşim kurabilir.
>
> **b)**
> Ne yapıyoruz: Gerekçeyi açıklıyoruz.
> Sonuç: CORELAP bir **yapıcı** algoritmadır; tek ihtiyacı REL ilişkileri ve alanlardır — ikisi de elde var.
> Neden: TCR ve PR yalnız ilişki ağırlıklarından hesaplanır; başlangıç yerleşimi gerekmez.
>
> **c)**
> Ne yapıyoruz: CRAFT'ın eksik girdisini belirtiyoruz.
> Sonuç: CRAFT **mevcut bir başlangıç yerleşimi** ve genelde **nicel from-to akış matrisi** ister; ikisi de yok.
> Neden: CRAFT iyileştiricidir — var olan bir çözümü takaslarla rötuşlar, sıfırdan üretmez.
>
> **ç)**
> Ne yapıyoruz: Hibrit akışı tanımlıyoruz.
> Sonuç: Önce CORELAP (veya ALDEP) ile başlangıç yerleşimi üret, sonra akış matrisi varsa CRAFT ile bu yerleşimi iyileştir.
> Neden: Yapıcı algoritma iyi bir başlangıç verir; iyileştirici onu yerel optimuma çeker — ikisi tamamlayıcıdır.
>
> **d)**
> Ne yapıyoruz: BLOCPLAN'ı konumlandırıyoruz.
> Sonuç: Evet, BLOCPLAN da yapıcıdır ve REL'den yerleşim kurar; farkı, bölümleri **2–3 yatay banda** dizmesi ve $Z_A$/ER/RD ölçütleriyle değerlendirmesidir. CORELAP serbest komşuluk büyütmesi yaparken BLOCPLAN bantlı yapı zorlar.
> Neden: Her ikisi de başlangıç yerleşimi gerektirmez; çözüm uzayı ve yerleştirme mantığı farklıdır.
>
> Paket: [[00 Pano/Yöntem Seçici#Karıştırılan yöntemler|Karşılaştırma]].

---

### K12 — Kolay — Amaç Modeli Seçimi (Minisum vs Minimax)

> [!question] Soru
> Ankara Büyükşehir Belediyesi yeni bir acil servis (112) istasyonu konumlandırıyor. Burada toplam mesafe değil, hizmet alanındaki **en uzak** talep noktasının erişim süresi kritiktir.
>
> a) Bu önceliğe uygun amaç modelini (minisum / minimax) seçin.
> b) Seçtiğiniz modelin amaç fonksiyonunu sözel tanımlayın.
> c) Eğer aynı belediye bir **kargo deposu** konumlandırsaydı hangi model uygun olurdu?
> ç) Aynı talep verisinde iki modelin neden farklı konum önerebileceğini açıklayın.
> d) "En uzak nokta" yerine "nüfusça ağırlıklı toplam erişim" istenseydi model nasıl değişirdi?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Uygulamaya göre amaç fonksiyonu seçimi.
> **Hangi yöntem:** Acil servis → minimax (en kötü durum); depo/lojistik → minisum (toplam).
> **Dikkat:** "Kimse çok uzakta kalmasın" = minimax; "ortalama maliyet düşsün" = minisum.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Önceliği modelle eşliyoruz.
> Sonuç: **Minimax** (merkez yaklaşımı).
> Neden: En uzak talep noktasının erişimini iyileştirmek = en kötü durumu küçültmek.
>
> **b)**
> Ne yapıyoruz: Amacı sözel yazıyoruz.
> Sonuç: $\min_{X} \max_j d(X, P_j)$ — tüm talep noktalarına olan **en büyük** uzaklığı minimize et.
> Neden: Acil hizmette kritik olan ortalama değil, en geç ulaşılan noktadır.
>
> **c)**
> Ne yapıyoruz: Depo senaryosunu değerlendiriyoruz.
> Sonuç: Kargo deposu için **minisum** (ağırlıklı medyan) uygundur.
> Neden: Depoda amaç toplam/ortalama taşıma maliyetini düşürmektir, en uzak tek nokta değil.
>
> **ç)**
> Ne yapıyoruz: İki modelin farklı optimum verme nedenini açıklıyoruz.
> Sonuç: Minisum talebin yoğunlaştığı yere (ağırlıklı medyan) çekilir; minimax uçtaki noktaları kollayıp geometrik merkeze/dengeye kayar. Farklı amaçlar farklı konum üretir.
> Neden: Minisum çoğunluğu, minimax en dezavantajlıyı önceler — bu iki hedef genelde çakışmaz.
>
> **d)**
> Ne yapıyoruz: Amaç değişimini modelliyoruz.
> Sonuç: "Nüfusça ağırlıklı toplam erişim" → **minisum**'a (ağırlıklı medyan) döner; her talep noktası nüfusuyla ağırlıklanır.
> Neden: "Toplam" ve "ağırlık" ifadeleri minisum imzasıdır; en kötü durum değil, ağırlıklı toplam minimize edilir.
>
> Paket: [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|HF11B]].

---

### K13 — Zor — Dinamik Kapasite Büyümesi

> [!question] Soru
> Petkim'in bir kimya tesisinde kapasite ilave maliyeti $f(y) = 0{,}03\,y^{0{,}60}$ milyon TL'dir (ölçek üssü $a = 0{,}60$). Talep yılda $D = 2.000$ ton artmaktadır; sürekli iskonto oranı $r = 0{,}10$ ve modelin çözümü $u^* \approx 0{,}9456$ olarak verilmiştir.
>
> a) Optimal kapasite ilave **aralığı** $x^* = u^*/r$'ı (yıl) hesaplayın.
> b) Her ilavede eklenecek optimal **kapasite miktarı** $y^* = x^* \cdot D$'yi (ton) hesaplayın.
> c) Kararı bir cümleyle özetleyin (kaç yılda bir, ne kadar).
> ç) Ölçek üssü $a$ küçüldükçe (güçlü ölçek ekonomisi) $x^*$ büyür mü küçülür mü? Sezgisel açıklayın.
> d) İskonto oranı $r$ iki katına çıksaydı ($0{,}20$) $x^*$ nasıl değişirdi (aynı $u^*$ ile)?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Sürekli büyüyen talepte optimal kapasite ilave zamanlaması ve büyüklüğü.
> **Hangi yöntem:** $x^* = u^*/r$; $y^* = x^* D$.
> **Dikkat:** $u^*$ ölçek üssüne bağlı boyutsuz çözüm; $x^*$ ona iskonto oranını uygular.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Boyutsuz çözümü iskonto oranına bölüyoruz.
> Hesap: $x^* = u^*/r = 0{,}9456 / 0{,}10 = 9{,}456$ yıl.
> Sonuç: $x^* \approx \mathbf{9{,}456}$ yıl.
> Neden: $u^*$ "kaç iskonto-periyodu" beklemek gerektiğini verir; $r$'ye bölünce yıla çevrilir.
>
> **b)**
> Ne yapıyoruz: Aralığı yıllık talep artışıyla çarpıyoruz.
> Hesap: $y^* = 9{,}456 \times 2.000 = 18.912$ ton.
> Sonuç: $y^* \approx \mathbf{18.912}$ ton.
> Neden: $x^*$ yılda biriken talep ($D$) kadar kapasite gerektirir.
>
> **c)**
> Ne yapıyoruz: Kararı özetliyoruz.
> Sonuç: Yaklaşık her **9,46 yılda bir, ~18.912 ton**'luk kapasite ilavesi yapılır.
> Neden: Büyük ama seyrek ilaveler, ölçek ekonomisi ile iskonto arasındaki dengeyi yakalar.
>
> **ç)**
> Ne yapıyoruz: Ölçek üssünün etkisini düşünüyoruz.
> Sonuç: $a$ küçüldükçe ölçek ekonomisi **güçlenir** → büyük ilave daha ucuz hale gelir → $x^*$ **büyür** (daha seyrek, daha büyük yatırım).
> Neden: Güçlü ölçek ekonomisinde "bir kerede büyük kur" stratejisi kazançlıdır: *güçlü ölçek = büyük ama sabırlı yatırım.*
>
> **d)**
> Ne yapıyoruz: İskonto oranını iki katına çıkarıyoruz.
> Hesap: $x^* = 0{,}9456 / 0{,}20 = 4{,}728$ yıl.
> Sonuç: $x^*$ **yarıya** iner (9,456 → 4,728 yıl).
> Neden: Yüksek iskonto, geleceği daha çok değersizleştirir; erken/küçük adımlarla yatırım yapmak (daha sık ilave) optimal olur.
>
> Paket: [[09 Öğrenme Paketleri/HF02C - Dinamik Kapasite Büyümesi|HF02C]].

---

### K14 — Orta — Alan Katsayısı Yöntemi

> [!question] Soru
> Ford Otosan'ın bir atölyesinde **12 adet** 8 m² tezgâh (alan katsayısı **3,20**), **10 adet** 15 m² tezgâh (katsayı **3,00**) ve **4 adet** 6 m² tezgâh (katsayı **3,50**) vardır. Destek alan oranları: ara depo **%20**, kalite kontrol **%13**, serbest alan **%18**, ulaşım yolları **%25**.
>
> a) Her tezgâh grubunun donanım alanını (adet × birim alan × katsayı) hesaplayıp toplam donanım alanını bulun.
> b) Destek oranlarını doğru biçimde birleştirin (toplam çarpan).
> c) Toplam gerekli alanı hesaplayın.
> ç) Yaygın bir tuzak olan "oranları art arda çarpma" ($1{,}20 \times 1{,}13 \times \dots$) yapsaydınız sonuç ne çıkardı; neden yanlış?
> d) Ulaşım yolu oranı %25 → %35'e çıksaydı toplam alan ne olurdu?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Alan katsayısı yöntemiyle toplam tesis alanı.
> **Hangi yöntem:** $A_{id} = \sum(\text{adet} \times \text{alan} \times \text{katsayı})$; $A_{top} = A_{id}(1 + \sum \text{oran})$.
> **Dikkat:** Destek oranları **toplanır**, sonra 1 eklenir — art arda çarpılmaz.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Her grup için adet × alan × katsayı topluyoruz.
> Hesap:
> $12 \times 8 \times 3{,}20 = 307{,}2$
> $10 \times 15 \times 3{,}00 = 450$
> $4 \times 6 \times 3{,}50 = 84$
> $A_{id} = 307{,}2 + 450 + 84 = 841{,}2$ m².
> Sonuç: Donanım alanı **841,2 m²**.
> Neden: Katsayı, makinenin işletme/operatör/erişim alanını birim alana ölçekler.
>
> **b)**
> Ne yapıyoruz: Destek oranlarını topluyoruz.
> Hesap: $0{,}20 + 0{,}13 + 0{,}18 + 0{,}25 = 0{,}76$ → çarpan $1 + 0{,}76 = 1{,}76$.
> Sonuç: Toplam çarpan **1,76**.
> Neden: Tüm destek alanları donanım alanının yüzdesi olarak eklenir.
>
> **c)**
> Ne yapıyoruz: Donanım alanını çarpanla çarpıyoruz.
> Hesap: $A_{top} = 841{,}2 \times 1{,}76 = 1.480{,}5$ m².
> Sonuç: Toplam alan **≈ 1.480,5 m²**.
> Neden: Donanım + destek alanlarının toplamı tesisin gerçek ihtiyacıdır.
>
> **ç)**
> Ne yapıyoruz: Yanlış yöntemi (art arda çarpma) deniyoruz.
> Hesap: $841{,}2 \times 1{,}20 \times 1{,}13 \times 1{,}18 \times 1{,}25 \approx 841{,}2 \times 1{,}9989 \approx 1.681{,}7$ m².
> Sonuç: Yanlış yöntem ~1.681,7 m² verir (≈200 m² fazla).
> Neden: Art arda çarpma oranları bileşik faize çevirir (oranın oranını ekler); oysa her destek alanı **aynı** donanım tabanının yüzdesidir, bu yüzden toplanıp bir kez uygulanır.
>
> **d)**
> Ne yapıyoruz: Yeni oranla yeniden hesaplıyoruz.
> Hesap: Yeni toplam oran $0{,}20+0{,}13+0{,}18+0{,}35 = 0{,}86$; çarpan $1{,}86$; $A_{top} = 841{,}2 \times 1{,}86 = 1.564{,}6$ m².
> Sonuç: Toplam alan **≈ 1.564,6 m²**.
> Neden: +%10 ulaşım payı, donanım tabanının %10'u kadar (84,12 m²) ek alan ekler.
>
> Paket: [[09 Öğrenme Paketleri/HF06B - Faaliyet İlişki Diyagramı ve Alan Hesabı|HF06B]].

---

### K15 — Zor — BLOCPLAN REL-DIST (Entegre)

> [!question] Soru
> Baykar'ın bir İHA montaj binasında dört bölüm arasındaki yönlü akışlar: $f_{12}=22,\ f_{21}=8$; $f_{13}=5,\ f_{31}=5$; $f_{24}=30,\ f_{42}=10$; $f_{34}=4,\ f_{43}=2$. Sayısal ağırlıklar **A=10, E=5, I=3, O=1, U=0**. Komşu mesafeler $d_{12}=2$, $d_{24}=2$, $d_{13}=3$'tür.
>
> a) Simetrik akış matrisini ($F_{ij}=f_{ij}+f_{ji}$) kurun.
> b) En büyük $F$ değerine göre A-E-I-O-U sınıf sınırlarını (5 eşit dilim) belirleyin ve her çifti kodlayın.
> c) Verilen mesafelerle REL-DIST puanını $RD = \sum w_{ij}\,d_{ij}$ hesaplayın.
> ç) Mühendis simetrikleştirmeyi atlayıp yalnız $f_{12}=22$'yi sınıflasaydı hangi kodu alırdı; gerçek kodla farkı nedir?
> d) RD ölçütünün yönü (büyük mü küçük mü iyi) nedir; $Z_A$'dan farkını açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Yönlü akış → simetrik → REL kodlama → REL-DIST puanı (entegre BLOCPLAN).
> **Hangi yöntem:** Simetrikleştir → $\max F/5$ ile sınıfla → $RD = \sum w\,d$.
> **Dikkat:** Önce **simetrikleştir** (tek yön sınıflama hatası); $RD$ küçük olsun istenir.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Her çiftin iki yönünü topluyoruz.
> Hesap:
>
> | Çift | $f_{ij}$ | $f_{ji}$ | $F_{ij}$ |
> |---|---:|---:|---:|
> | 1–2 | 22 | 8 | **30** |
> | 1–3 | 5 | 5 | **10** |
> | 2–4 | 30 | 10 | **40** |
> | 3–4 | 4 | 2 | **6** |
>
> Sonuç: En büyük simetrik akış $F_{24}=40$.
> Neden: BLOCPLAN yönü değil, çiftin toplam etkileşimini önemser.
>
> **b)**
> Ne yapıyoruz: $\max F = 40$'ı 5 eşit dilime bölüyoruz.
> Hesap: Dilim genişliği $40/5 = 8$. Bantlar: A:33–40, E:25–32, I:17–24, O:9–16, U:1–8.
> Kodlama: $F_{24}=40 \to$ **A**; $F_{12}=30 \to$ **E**; $F_{13}=10 \to$ **O**; $F_{34}=6 \to$ **U**.
> Sonuç: 2–4 → A, 1–2 → E, 1–3 → O, 3–4 → U.
> Neden: Sayısal akış bandı doğrudan nitel yakınlık koduna karşılık gelir.
>
> **c)**
> Ne yapıyoruz: Verilen mesafelerle ağırlık × mesafe topluyoruz (ağırlık: A=10, E=5, O=1).
> Hesap: $RD = w_{24}d_{24} + w_{12}d_{12} + w_{13}d_{13} = 10(2) + 5(2) + 1(3) = 20 + 10 + 3 = 33$.
> Sonuç: $RD = \mathbf{33}$.
> Neden: 3–4 çifti U (ağırlık 0) ve mesafesiz olduğundan toplama girmez.
>
> **ç)**
> Ne yapıyoruz: Simetrikleştirmeyi atlayan hatayı gösteriyoruz.
> Hesap: Yalnız $f_{12}=22$ alınırsa I bandına (17–24) düşer → **I (ağırlık 3)**; oysa simetrik $F_{12}=30$ ile gerçek kod **E (ağırlık 5)**.
> Sonuç: Tek yön sınıflama 1–2'yi I gösterir, gerçek kod E'dir — bir sınıf hata.
> Neden: Tek yönlü akış çiftin gerçek etkileşim şiddetini eksik gösterir; önce topla, sonra sınıfla.
>
> **d)**
> Ne yapıyoruz: RD'nin yönünü ve $Z_A$ farkını açıklıyoruz.
> Sonuç: $RD$ **küçük** olsun istenir (ağırlık × mesafe cezası); $Z_A$ ise **büyük** olsun istenir (komşuluk puanı). Güçlü ilişkili çiftleri uzak koymak RD'yi büyütür (kötü), komşu koymak $Z_A$'yı büyütür (iyi).
> Neden: $Z_A$ yalnız komşu olup olmadığına bakar (mesafe ölçeği yok); RD mesafeyi ağırlıkla çarpar — biri yakınlığı ödüllendirir, diğeri uzaklığı cezalandırır.
>
> Paket: [[09 Öğrenme Paketleri/HF09B - BLOCPLAN|HF09B]].

---

## Kayıt

| Tarih | Sorular | Çözülen / 15 | Süre | En sık hata kodu |
|---|---|---:|---:|---|
|  |  |  |  |  |
