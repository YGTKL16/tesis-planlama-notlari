---
hafta: 11
tags: [ders/tesis-planlama, sorular]
soru_sayısı: 5
---

# HF11 — Tesis Konumu I Soruları
## Minisum (Ağırlıklı Medyan) · Minimax (u-v Dönüşümü)

> [!info] Nasıl kullan?
> Soruyu gör → her alt soruyu (a–d) kapalı kitap çöz → `[!answer]-` kutusunu aç → hataları not et.

---

### S01 — Kolay — Minisum Tek Eksen

> [!question] Soru
> Aras Kargo, bir otoyol koridoru (tek eksen) boyunca dizilmiş 5 dağıtım noktasına hizmet verecek tek bir aktarma deposu konumlandıracaktır. Lojistik planlama uzmanı, toplam ağırlıklı taşıma mesafesini en küçükleyen konumu ağırlıklı medyan ile bulacaktır.
>
> | Müşteri | $a_i$ | $w_i$ |
> |---|---:|---:|
> | 1 | 2 | 3 |
> | 2 | 5 | 5 |
> | 3 | 8 | 2 |
> | 4 | 11 | 4 |
> | 5 | 14 | 1 |
>
> a) Toplam ağırlığı ve yarısını ($W/2$) hesaplayın.
> b) Kümülatif ağırlık tablosunu kurup optimum konum $x^*$'ı bulun.
> c) $f(x^*) = \sum_i w_i |x^* - a_i|$ amaç değerini hesaplayın.
> ç) Depo yerine $x=8$ konulsaydı maliyet ne olurdu; neden $x^*$ daha iyi?
> d) Bu yöntemin neden "ağırlıklı medyan" olarak adlandırıldığını, basit ortalamadan farkını açıklayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Tek eksende ağırlıklı medyan → toplam ağırlıklı uzaklığı minimize eden koordinat.
> **Yöntem:** Koordinatı küçükten büyüğe sırala, kümülatif ağırlık; $W/2$'yi aşan ilk koordinat = $x^*$.
> **Dikkat:** Kümülatif ağırlık tam $W/2$'ye eşitse tek nokta değil ARALIK çıkar (S03'e bak).

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Tüm ağırlıkları toplayıp yarısını alıyoruz.
> Hesap: $W = 3+5+2+4+1 = 15$, $W/2 = 7{,}5$.
> Sonuç: $W=15$, eşik $7{,}5$.
> Neden: Medyan, ağırlığın yarısının solda yarısının sağda kaldığı noktadır.
>
> **b)**
> Ne yapıyoruz: Koordinatları sırayla toplayıp eşiği ilk aşan noktayı buluyoruz.
> Hesap:
>
> | Sıra | $a_i$ | $w_i$ | Kümülatif |
> |---:|---:|---:|---:|
> | 1 | 2 | 3 | 3 |
> | 2 | 5 | 5 | **8** ← 7,5'i ilk kez aşar |
> | 3 | 8 | 2 | 10 |
> | 4 | 11 | 4 | 14 |
> | 5 | 14 | 1 | 15 |
>
> Sonuç: $x^* = 5$.
> Neden: Kümülatif ağırlık $a=5$'te 8'e çıkıp 7,5'i aşar (eşit değil, aşıyor → tek nokta).
>
> **c)**
> Ne yapıyoruz: $x^*=5$ için ağırlıklı uzaklıkları topluyoruz.
> Hesap:
>
> | Müşteri | $|5-a_i|$ | $w_i$ | $w_i|5-a_i|$ |
> |---|---:|---:|---:|
> | 1 | 3 | 3 | 9 |
> | 2 | 0 | 5 | 0 |
> | 3 | 3 | 2 | 6 |
> | 4 | 6 | 4 | 24 |
> | 5 | 9 | 1 | 9 |
> | **Toplam** | | | **48** |
>
> Sonuç: $f(x^*)=48$.
> Neden: En ağır müşteri (2, w=5) tam üstünde olduğundan o terim sıfır.
>
> **ç)**
> Ne yapıyoruz: $x=8$ için maliyeti hesaplayıp kıyaslıyoruz.
> Hesap: $3(6)+5(3)+2(0)+4(3)+1(6)=18+15+0+12+6=51$.
> Sonuç: $f(8)=51 > f(5)=48$.
> Neden: $x^*=5$ ağırlığın çoğunu (8 birim) soluna alıp dengeyi sağlar; 8'e kayınca ağır müşteri 2'den uzaklaşılır.
>
> **d)**
> Ne yapıyoruz: İsimlendirmeyi gerekçelendiriyoruz.
> Sonuç: Her müşteriyi $w_i$ kez tekrarlanmış gibi düşünürsek, ağırlıklı medyan bu genişletilmiş listenin ortanca koordinatıdır.
> Neden: Mutlak değer (L1) amacını minimize eden nokta medyandır; ağırlıklar talebi temsil eder. Basit ortalama kareli (L2) uzaklığı minimize eder ve uç değerlere duyarlıdır — burada amaç toplam mutlak mesafe olduğundan medyan doğru ölçüttür.

---

### S02 — Kolay — Minisum İki Eksen

> [!question] Soru
> Bir e-ticaret firması Ankara organize sanayide yeni bir mikro-depo açacaktır. Dört yoğun müşteri bölgesinin koordinatları ve haftalık sevkiyat ağırlıkları aşağıdadır. Dikdoğrusal (Manhattan) mesafe geçerlidir ve iki eksen bağımsız çözülür.
>
> | Müşteri | $(a_i, b_i)$ | $w_i$ |
> |---|---:|---:|
> | A | (1, 2) | 3 |
> | B | (4, 5) | 2 |
> | C | (6, 1) | 4 |
> | D | (3, 8) | 1 |
>
> a) Toplam ağırlığı ve eşiği hesaplayın.
> b) x ekseni için kümülatif tablo kurup $x^*$'ı bulun.
> c) y ekseni için $y^*$'ı bulun.
> ç) $(x^*, y^*)$ konumunun toplam ağırlıklı uzaklık $f$'ini hesaplayın.
> d) İki eksenin bağımsız çözülebilmesi neden geçerli; Öklid mesafede de aynı şey yapılabilir miydi?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Dikdoğrusal minisum'da iki eksen bağımsızdır — her eksen için ayrı tablo.
> **Yöntem:** x için $a_i$ sırala, y için $b_i$ sırala; her eksenin kümülatif ağırlık tablosunu kur.
> **Dikkat:** Koordinat-ağırlık çiftini birlikte taşı — sıralamada ağırlıklar karışmasın.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Ağırlık toplamı ve yarısı.
> Hesap: $W=3+2+4+1=10$, $W/2=5$.
> Sonuç: $W=10$, eşik 5.
> Neden: Her eksen aynı toplam ağırlığı paylaşır.
>
> **b)**
> Ne yapıyoruz: $a_i$'leri sıralayıp kümülatif kuruyoruz.
> Hesap:
>
> | Müşteri | $a_i$ | $w_i$ | Kümülatif |
> |---|---:|---:|---:|
> | A | 1 | 3 | 3 |
> | D | 3 | 1 | 4 |
> | B | 4 | 2 | **6** ← 5'i ilk aşar |
> | C | 6 | 4 | 10 |
>
> Sonuç: $x^*=4$.
> Neden: Kümülatif 6 > 5, $a=4$'te aşılır.
>
> **c)**
> Ne yapıyoruz: $b_i$'leri sıralayıp kümülatif kuruyoruz.
> Hesap:
>
> | Müşteri | $b_i$ | $w_i$ | Kümülatif |
> |---|---:|---:|---:|
> | C | 1 | 4 | 4 |
> | A | 2 | 3 | **7** ← 5'i ilk aşar |
> | B | 5 | 2 | 9 |
> | D | 8 | 1 | 10 |
>
> Sonuç: $y^*=2$, dolayısıyla $X^*=(4,2)$.
> Neden: y eksenindeki sıralama ağırlıkları x'tekinden farklı; bağımsız çözülür.
>
> **ç)**
> Ne yapıyoruz: $(4,2)$ için Manhattan uzaklıklarını ağırlıklayıp topluyoruz.
> Hesap:
>
> | Müşteri | $|4-a_i|+|2-b_i|$ | $w_i$ | $w_i d_i$ |
> |---|---:|---:|---:|
> | A(1,2) | 3+0=3 | 3 | 9 |
> | B(4,5) | 0+3=3 | 2 | 6 |
> | C(6,1) | 2+1=3 | 4 | 12 |
> | D(3,8) | 1+6=7 | 1 | 7 |
> | **Toplam** | | | **34** |
>
> Sonuç: $f^*=34$.
> Neden: Manhattan'da toplam, x-bileşeni + y-bileşeni şeklinde ayrışır.
>
> **d)**
> Ne yapıyoruz: Bağımsızlığın geçerliliğini ve Öklid ile farkını açıklıyoruz.
> Sonuç: Dikdoğrusal mesafe $|x-a|+|y-b|$ olarak x ve y terimlerine tam ayrıştığından her eksen ayrı minimize edilebilir. Öklid mesafede ($\sqrt{(x-a)^2+(y-b)^2}$) terimler ayrışmaz, bu yüzden eksen bağımsızlığı geçmez — orada Weiszfeld gibi iteratif yöntem gerekir.
> Neden: Toplanabilir (separable) amaç fonksiyonu, koordinat bazında ayrı ayrı optimize edilebilir; karekök bunu bozar.

---

### S03 — Orta — Minisum Eşit Yarı Tuzağı (Optimum Aralık)

> [!question] Soru
> Bir akaryakıt dağıtım şirketi, eşit talepli (her biri $w=2$) dört istasyona hizmet edecek tek bir tanker dolum noktasını tek eksen üzerinde konumlandıracaktır. Stajyer mühendis ilk hesabında tek nokta bulduğunu sansa da kümülatif ağırlık tam yarıya eşit çıkmaktadır.
>
> | Müşteri | $a_i$ |
> |---|---:|
> | 1 | 2 |
> | 2 | 6 |
> | 3 | 10 |
> | 4 | 14 |
>
> a) Toplam ağırlığı ve eşiği hesaplayın.
> b) Kümülatif ağırlık tablosunu kurup "eşit yarı" durumunu tespit edin.
> c) Optimum çözümün tek nokta mı aralık mı olduğunu belirleyin.
> ç) Aralığın uç noktalarında ve ortasında $f$ değerini hesaplayıp eşitliği doğrulayın.
> d) Kümülatif ağırlık $W/2$'yi "aşmak" ile "eşit olmak" arasındaki kuralı genel bir cümleyle ifade edin.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Kümülatif ağırlık tam $W/2$'ye eşit olunca çıkan optimum aralık.
> **Kritik kural:** Aşıyorsa → tek nokta. Tam eşitse → o koordinat ile sonraki koordinat arası aralık.
> **Tuzak:** "İlk W/2'ye eşit/aşan koordinatı seç" deyip tek nokta yazmak.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Eşit ağırlıkları topluyoruz.
> Hesap: $W=2+2+2+2=8$, $W/2=4$.
> Sonuç: Eşik 4.
> Neden: Tüm talepler eşit olduğundan medyan tam ortaya düşme eğiliminde.
>
> **b)**
> Ne yapıyoruz: Kümülatif tabloyu kurup eşik durumunu işaretliyoruz.
> Hesap:
>
> | Sıra | $a_i$ | $w_i$ | Kümülatif | Durum |
> |---:|---:|---:|---:|---|
> | 1 | 2 | 2 | 2 | < 4 |
> | 2 | 6 | 2 | **4** | **= W/2 (eşit!)** |
> | 3 | 10 | 2 | 6 | — |
> | 4 | 14 | 2 | 8 | — |
>
> Sonuç: $a=6$'da kümülatif tam 4'e eşit.
> Neden: Solda 4, sağda 4 birim ağırlık kalır — denge noktası tek değil.
>
> **c)**
> Ne yapıyoruz: Eşitlik durumunun sonucunu belirliyoruz.
> Sonuç: $x^* \in [6,\,10]$ aralığı (tek nokta değil).
> Neden: $a=6$ ile bir sonraki koordinat $a=10$ arasındaki her noktada solda ve sağda kalan ağırlık eşit kalır → $f$ sabit.
>
> **ç)**
> Ne yapıyoruz: Üç noktada $f$ hesaplayıp eşitliği gösteriyoruz.
> Hesap:
> $x=6$: $2(4)+2(0)+2(4)+2(8)=8+0+8+16=\mathbf{32}$
> $x=8$: $2(6)+2(2)+2(2)+2(6)=12+4+4+12=\mathbf{32}$
> $x=10$: $2(8)+2(4)+2(0)+2(4)=16+8+0+8=\mathbf{32}$
> Sonuç: Üç noktada da $f=32$.
> Neden: Aralık içinde sağa hareket = sağdan kazanılan, soldan kaybedilen; net değişim sıfır.
>
> **d)**
> Ne yapıyoruz: Kuralı genelliyoruz.
> Sonuç: Kümülatif ağırlık bir koordinatta $W/2$'yi *kesin aşıyorsa* optimum o tek koordinattır; *tam eşitse* optimum, o koordinat ile bir sonraki koordinat arasındaki kapalı aralıktır.
> Neden: Strict aşma tek bir denge noktası, eşitlik ise düz (eğimi sıfır) bir bölge yaratır.
>
> > [!warning] Neden aralık?
> > Eşit-yarı durumunda tek nokta yazmak eksik cevaptır; tüm aralığı belirtmek gerekir.

---

### S04 — Orta — Minimax u-v Dönüşümü

> [!question] Soru
> İstanbul Büyükşehir Belediyesi, dört mevcut hastaneye en uzak erişim süresini en küçükleyen bir merkezî acil müdahale istasyonu konumlandıracaktır. Bu bir minimax problemidir ve u-v dönüşümüyle çözülür.
>
> | Tesis | $(a_i, b_i)$ |
> |---|---:|
> | P1 | (1, 4) |
> | P2 | (6, 1) |
> | P3 | (8, 7) |
> | P4 | (3, 9) |
>
> $u_i = a_i+b_i$, $v_i = a_i-b_i$.
>
> a) $u_i$, $v_i$ değerlerini tablolaştırın.
> b) $\Delta u$, $\Delta v$ yayılımlarını ve minimax yarıçapı $R^*$'ı hesaplayın.
> c) $U^*$ ve $V^*$ optimum aralıklarını kurun.
> ç) Geriye dönüşümle optimum çözüm kümesini (nokta veya doğru parçası) bulun.
> d) Bir iç noktada en uzak hastane uzaklığını hesaplayıp $R^*$'a eşit olduğunu doğrulayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Tüm tesislere en büyük uzaklığı minimize eden konum.
> **Yöntem:** u-v dönüşümü → $R^* = \frac{1}{2}\max(\Delta u, \Delta v)$ → aralıkları kur → geri dönüştür.
> **Dikkat:** $R^*$ için toplam değil maksimum alınır. Büyük yayılım ilgili ekseni tek noktaya çökertir.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Her tesis için $u=a+b$, $v=a-b$ buluyoruz.
> Hesap:
>
> | Tesis | $(a_i,b_i)$ | $u_i$ | $v_i$ |
> |---|---:|---:|---:|
> | P1 | (1,4) | **5** | −3 |
> | P2 | (6,1) | 7 | **5** |
> | P3 | (8,7) | **15** | 1 |
> | P4 | (3,9) | 12 | **−6** |
>
> Sonuç: $u\in\{5,7,15,12\}$, $v\in\{-3,5,1,-6\}$.
> Neden: 45° döndürme Manhattan'ı Chebyshev'e çevirir, eksenleri ayrıştırır.
>
> **b)**
> Ne yapıyoruz: Yayılımları ve yarıçapı hesaplıyoruz.
> Hesap: $\Delta u = 15-5 = 10$; $\Delta v = 5-(-6) = 11$; $R^* = \tfrac{1}{2}\max(10,11)=\mathbf{5{,}5}$.
> Sonuç: $R^*=5{,}5$.
> Neden: Minimax yarıçapı, baskın (büyük) yayılımın yarısıdır.
>
> **c)**
> Ne yapıyoruz: Optimum u ve v aralıklarını kuruyoruz.
> Hesap:
> $$U^* = [u_{\max}-R^*,\; u_{\min}+R^*] = [15-5{,}5,\; 5+5{,}5] = [9{,}5,\;10{,}5]$$
> $$V^* = [v_{\max}-R^*,\; v_{\min}+R^*] = [5-5{,}5,\; -6+5{,}5] = [-0{,}5,\;-0{,}5]$$
> Sonuç: $u^* \in [9{,}5,\,10{,}5]$ (aralık), $v^*=-0{,}5$ (tek nokta).
> Neden: $\Delta v > \Delta u$ olduğundan v ekseni tek noktaya çöker, u aralık kalır.
>
> **ç)**
> Ne yapıyoruz: $x=\tfrac{u+v}{2}$, $y=\tfrac{u-v}{2}$ ile geri dönüyoruz.
> Hesap:
>
> | $(u,v)$ | $x$ | $y$ |
> |---|---|---|
> | $(9{,}5,-0{,}5)$ | 4,5 | 5 |
> | $(10{,}5,-0{,}5)$ | 5 | 5,5 |
>
> Sonuç: Optimum, $(4{,}5;5)$ ile $(5;5{,}5)$ arasındaki doğru parçası.
> Neden: Tek nokta + aralık → ters dönüşümde doğru parçası.
>
> **d)**
> Ne yapıyoruz: İç nokta $(4{,}75;\,5{,}25)$ için en uzak hastaneyi buluyoruz.
> Hesap:
>
> | Tesis | $|4{,}75-a|+|5{,}25-b|$ |
> |---|---:|
> | P1(1,4) | 3,75+1,25=5 |
> | P2(6,1) | 1,25+4,25=**5,5** |
> | P3(8,7) | 3,25+1,75=5 |
> | P4(3,9) | 1,75+3,75=**5,5** |
>
> Sonuç: Maks = 5,5 = $R^*$ ✓.
> Neden: Optimum kümede en uzak nokta tam $R^*$ kadardır; doğrulama tutar.
>
> > [!tip] Büyük Δ → tek nokta, küçük Δ → aralık
> > $\Delta v > \Delta u$ olduğu için $V^*$ tek noktaya çöker, $U^*$ aralık olur → doğru parçası.

---

### S05 — Zor — Minimax Optimum Küme (Doğru Parçası)

> [!question] Soru
> Bir itfaiye teşkilatı, kentin beş kritik tesisine en uzak erişim mesafesini en küçükleyecek yeni bir istasyon konumlandıracaktır. Minimax çözümünde büyük yayılım bir ekseni tek noktaya çökertip diğerini aralığa dönüştürür; bu da optimumu doğru parçası yapar.
>
> | Tesis | $(a_i, b_i)$ |
> |---|---:|
> | P1 | (0, 0) |
> | P2 | (10, 0) |
> | P3 | (5, 5) |
> | P4 | (2, 8) |
> | P5 | (8, 4) |
>
> a) Tüm $u_i, v_i$ değerlerini tablolaştırın.
> b) Yayılımları ve $R^*$'ı hesaplayın; belirleyici ekseni belirtin.
> c) $U^*$ ve $V^*$ aralıklarını kurup geri dönüşümle uç noktaları bulun.
> ç) İki uç noktada da en uzak tesis uzaklığının $R^*$ olduğunu doğrulayın.
> d) $\Delta u = \Delta v$ olsaydı optimum kümenin biçimi nasıl değişirdi? Genel kuralı yazın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Büyük $\Delta v$, $V^*$'ı tek noktaya çökertir; $U^*$ aralık → doğru parçası.
> **Dikkat:** Sadece merkez nokta yazmak eksiktir — tüm optimum kümeyi (doğru parçasını) tanımla.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: $u=a+b$, $v=a-b$ tablosunu kuruyoruz.
> Hesap:
>
> | Tesis | $(a_i,b_i)$ | $u_i$ | $v_i$ |
> |---|---:|---:|---:|
> | P1 | (0,0) | **0** | 0 |
> | P2 | (10,0) | 10 | **10** |
> | P3 | (5,5) | 10 | 0 |
> | P4 | (2,8) | 10 | **−6** |
> | P5 | (8,4) | **12** | 4 |
>
> Sonuç: $u\in\{0,10,10,10,12\}$, $v\in\{0,10,0,-6,4\}$.
> Neden: Dönüşüm köşe değerleri (uç tesisler) belirginleştirir.
>
> **b)**
> Ne yapıyoruz: Yayılım ve yarıçap.
> Hesap: $\Delta u = 12-0 = 12$; $\Delta v = 10-(-6) = 16$; $R^* = \tfrac{1}{2}\max(12,16)=\mathbf{8}$.
> Sonuç: $R^*=8$; belirleyici eksen $\Delta v$ (16, daha büyük).
> Neden: En büyük yayılım minimax yarıçapını ve hangi eksenin çökeceğini belirler.
>
> **c)**
> Ne yapıyoruz: Aralıkları kurup geri dönüştürüyoruz.
> Hesap:
> $$V^* = [v_{\max}-R^*,\; v_{\min}+R^*] = [10-8,\;-6+8] = [2,\,2] \Rightarrow v^*=2$$
> $$U^* = [u_{\max}-R^*,\; u_{\min}+R^*] = [12-8,\;0+8] = [4,\,8]$$
>
> | $(u,v)$ | $x=\tfrac{u+v}{2}$ | $y=\tfrac{u-v}{2}$ |
> |---|---|---|
> | $(4,2)$ | 3 | 1 |
> | $(8,2)$ | 5 | 3 |
>
> Sonuç: Optimum doğru parçası $(3,1)$–$(5,3)$, doğrultusu $y=x-2$.
> Neden: $v$ sabit (2), $u$ aralık → ters dönüşümde doğru parçası.
>
> **ç)**
> Ne yapıyoruz: İki uçta en uzak tesisi hesaplıyoruz.
> Hesap:
> $(3,1)$: P2→8, P4→8, P5→4, P1→4, P3→6 → maks **8**.
> $(5,3)$: P1→8, P2→8, P4→8, P3→2, P5→4 → maks **8**.
> Sonuç: İki uçta da maks = 8 = $R^*$ ✓.
> Neden: Optimum küme boyunca en uzak uzaklık sabit $R^*$ kalır.
>
> **d)**
> Ne yapıyoruz: $\Delta u=\Delta v$ durumunu genelliyoruz.
> Sonuç: $\Delta u=\Delta v$ ise her iki eksen de tek noktaya çöker → optimum **tek nokta** olur. $\Delta u \ne \Delta v$ ise büyük yayılım tek noktaya, küçük yayılım aralığa dönüşür → optimum **doğru parçası**.
> Neden: Yarıçap her iki aralığın yarı-genişliğini eşitler; yayılımlar eşitse iki aralık da sıfır uzunluğa iner.
>
> > [!tip] Sınav notu
> > Δu ≠ Δv → doğru parçası; Δu = Δv → tek nokta. Optimum kümeyi tam yazmadan "merkez nokta" demek eksik puandır.
