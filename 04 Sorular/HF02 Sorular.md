---
hafta: 2
tags: [ders/tesis-planlama, sorular]
soru_sayısı: 5
---

# HF02 — Tesis Kapasite Planlama — Soruları

> [!info] Nasıl kullan?
> Soruyu gör → cevaplamayı dene (kapalı kitap) → `[!answer]-` kutusunu aç → hataları hata koduyla işaretle.

---

### S01 — Kolay — Kapasite kullanımı ve verimlilik

> [!question] Soru
> Bir gıda işleme tesisinin üretim müdürü olarak haftalık performans raporu hazırlıyorsunuz. Tesisin tasarım kapasitesi 200 birim/gün, planlı bakım ve kurulum kayıpları nedeniyle etkin kapasitesi 165 birim/gün, geçen haftaki gerçek üretimi ise 130 birim/gündür.
>
> a) Kapasite kullanım oranını ($U$) hesaplayın.
> b) Verimlilik oranını ($E_{ff}$) hesaplayın.
> c) Neden her zaman $U < E_{ff}$ çıktığını açıklayın.
> ç) Etkin kapasite bakım iyileştirmesiyle 150 birim/güne düşseydi verimlilik nasıl değişirdi?
> d) Tasarım ile etkin kapasite arasındaki 35 birim/günlük farkın hangi orana etki ettiğini yorumlayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Üç kapasite katmanından iki oran ve yorumu.
> **Hangi yöntem:** $U = Q_{gerçek}/Q_{tasarım}$; $E_{ff} = Q_{gerçek}/Q_{etkin}$
> **Dikkat:** Paydayı karıştırma — kullanım = tasarım (en büyük), verimlilik = etkin (orta). Etkin < Tasarım olduğu için verimlilik her zaman kullanımdan yüksektir.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Kullanım oranını hesaplıyoruz.
> Formül/Yöntem: $U = Q_{gerçek}/Q_{tasarım}$
> Hesap: $U = \dfrac{130}{200} = 0{,}65$
> Sonuç: $U = \%65{,}0$
> Neden: Kullanım, gerçek üretimi teorik tavanla (tasarım) kıyaslar.
>
> **b)**
> Ne yapıyoruz: Verimlilik oranını hesaplıyoruz.
> Formül/Yöntem: $E_{ff} = Q_{gerçek}/Q_{etkin}$
> Hesap: $E_{ff} = \dfrac{130}{165} = 0{,}7879$
> Sonuç: $E_{ff} \approx \%78{,}8$
> Neden: Verimlilik, gerçek üretimi gerçekçi (etkin) kapasiteyle kıyaslar.
>
> **c)**
> Ne yapıyoruz: İki oranı karşılaştırıyoruz.
> Formül/Yöntem: Aynı pay, farklı payda.
> Hesap: Pay her ikisinde de 130; payda kullanımda 200 (büyük), verimlilikte 165 (küçük). Büyük payda → küçük oran.
> Sonuç: $U < E_{ff}$ her zaman geçerlidir.
> Neden: Etkin kapasite hiçbir zaman tasarım kapasitesini aşamaz, bu yüzden verimlilik kullanımdan büyük çıkar.
>
> **ç)**
> Ne yapıyoruz: What-if — etkin kapasite 150'ye düşüyor.
> Formül/Yöntem: $E_{ff} = 130/Q_{etkin}$
> Hesap: $E_{ff} = \dfrac{130}{150} = 0{,}8667$
> Sonuç: $E_{ff} \approx \%86{,}7$ (kullanım %65 sabit kalır).
> Neden: Etkin kapasite düşünce payda küçülür, verimlilik yükselir; ancak bu gerçek bir iyileşme değil, paydanın daralmasıdır.
>
> **d)**
> Ne yapıyoruz: 35 birimlik farkı yorumluyoruz.
> Formül/Yöntem: Tasarım − Etkin = planlı kayıp.
> Hesap: $200 - 165 = 35$ birim/gün; bu fark bakım/kurulum gibi planlı kayıplardır.
> Sonuç: 35 birim, kullanımı düşürür ama verimliliği etkilemez.
> Neden: Planlı kayıplar etkin kapasitenin dışında bırakıldığı için verimlilik paydasına girmez, yalnız kullanım paydasını (tasarım) şişirir.

---

### S02 — Kolay — Tek ürün başa baş analizi

> [!question] Soru
> Bir kitap yayınevinin finans müdürü, yeni bir kitabın kârlılığını değerlendiriyor. Sabit maliyetler (telif, baskı hazırlık, dizgi) toplamda 270.000 TL, satış fiyatı 120 TL/kitap, birim değişken maliyet 75 TL/kitap'tır.
>
> a) Birim katkı payını ve matematiksel başa baş miktarını ($x_{BB}$) hesaplayın.
> b) 45.000 TL hedef kâr için gereken satış adedini hesaplayın.
> c) Katkı payı oranını (CMR) ve satış tutarı cinsinden başa baş noktasını ($S_{BB}$) hesaplayın.
> ç) Sabit maliyet 270.000 TL'den 315.000 TL'ye çıksaydı $x_{BB}$ ne olurdu?
> d) Başa baş analizinin 2 temel varsayımını/sınırlamasını yazın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Tek ürün başa baş analizinin farklı biçimleri ve duyarlılığı.
> **Hangi yöntem:** $x_{BB}=F/(P-V)$; $x_{hedef}=(F+\Pi^*)/(P-V)$; $CMR=(P-V)/P$; $S_{BB}=F/CMR$.
> **Dikkat:** Kitap kesikli üründür; "minimum zararsız adet" için yukarı yuvarla, matematiksel BBN ise kesirli yazılır.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Katkı payı ve BBN miktarını buluyoruz.
> Formül/Yöntem: $P-V$; $x_{BB}=F/(P-V)$
> Hesap: $P-V = 120-75 = 45$ TL/kitap; $x_{BB} = \dfrac{270.000}{45} = 6.000$ kitap.
> Sonuç: Birim katkı payı 45 TL, $x_{BB} = 6.000$ kitap.
> Neden: Her kitap 45 TL katkı sağlar; sabit maliyeti karşılamak için 6.000 kitap gerekir.
>
> **b)**
> Ne yapıyoruz: Hedef kâr için satış adedini buluyoruz.
> Formül/Yöntem: $x_{hedef}=(F+\Pi^*)/(P-V)$
> Hesap: $x_{hedef} = \dfrac{270.000+45.000}{45} = \dfrac{315.000}{45} = 7.000$ kitap.
> Sonuç: $x_{hedef} = 7.000$ kitap.
> Neden: 45.000 TL kâr, ek $45.000/45 = 1.000$ kitaba karşılık gelir; $6.000+1.000=7.000$.
>
> **c)**
> Ne yapıyoruz: CMR ve satış tutarı BBN'sini buluyoruz.
> Formül/Yöntem: $CMR=(P-V)/P$; $S_{BB}=F/CMR$
> Hesap: $CMR = \dfrac{45}{120} = 0{,}375 = \%37{,}5$; $S_{BB} = \dfrac{270.000}{0{,}375} = 720.000$ TL.
> Sonuç: $CMR = \%37{,}5$, $S_{BB} = 720.000$ TL.
> Doğrulama: $6.000 \times 120 = 720.000$ ✓
> Neden: Her 1 TL ciroda 0,375 TL katkı kalır; sabit maliyeti karşılamak için 720.000 TL ciro gerekir.
>
> **ç)**
> Ne yapıyoruz: What-if — sabit maliyet artıyor.
> Formül/Yöntem: $x_{BB}=F/(P-V)$
> Hesap: $x_{BB} = \dfrac{315.000}{45} = 7.000$ kitap.
> Sonuç: BBN 6.000'den 7.000 kitaba çıkar.
> Neden: Sabit maliyet %16,7 arttığı için BBN de aynı oranda artar; katkı payı değişmediğinden ilişki doğrusaldır.
>
> **d)**
> Ne yapıyoruz: Varsayımları/sınırlamaları yazıyoruz.
> Formül/Yöntem: Model varsayımları.
> Hesap: (1) Satış fiyatı ve birim değişken maliyet hacimden bağımsız sabittir (doğrusallık). (2) Üretilen her birim satılır, stok birikmez; tek ürün veya sabit ürün karması varsayılır.
> Sonuç: Model basitleştirilmiş bir doğrusal yaklaşımdır.
> Neden: Gerçekte ölçek indirimleri ve talep doygunluğu doğrusallığı bozar, bu yüzden BBN yaklaşık bir karar aracıdır.

---

### S03 — Orta — Çok ürünlü başa baş

> [!question] Soru
> Bir tekstil firması üç ürün üretmektedir. Ürün bilgileri ve satış gelir payları aşağıdaki gibidir. Toplam sabit maliyet 480.000 TL'dir.
>
> | Ürün | Satış fiyatı (TL) | Birim değişken maliyet (TL) | Satış geliri payı |
> |---|---|---|---|
> | A | 80 | 50 | %40 |
> | B | 120 | 70 | %35 |
> | C | 200 | 90 | %25 |
>
> a) Her ürünün katkı payı oranını ($CMR_i$) hesaplayın.
> b) Ağırlıklı ortalama katkı payı oranını ($\overline{CMR}$) hesaplayın.
> c) Başa baş satış tutarını ($S_{BB}$) hesaplayın.
> ç) Her ürünün başa baş cirosundaki TL payını hesaplayın.
> d) Ürün karması yüksek marjlı C lehine kaysaydı (C %50) $\overline{CMR}$ ve $S_{BB}$ nasıl değişir, yorumlayın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Sabit ürün karmasında çok ürünlü BBN ve karma duyarlılığı.
> **Hangi yöntem:** $CMR_i=(P_i-V_i)/P_i$; $\overline{CMR}=\sum W_i \cdot CMR_i$; $S_{BB}=F/\overline{CMR}$.
> **Dikkat:** Ağırlıklar satış tutarı payıdır ($W_i$) — adet payı değil.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Ürün bazında CMR hesaplıyoruz.
> Formül/Yöntem: $CMR_i=(P_i-V_i)/P_i$
> Hesap: $CMR_A = \dfrac{30}{80}=0{,}375$; $CMR_B = \dfrac{50}{120}=0{,}4167$; $CMR_C = \dfrac{110}{200}=0{,}550$.
> Sonuç: A %37,5; B %41,67; C %55,0.
> Neden: Her ürünün her 1 TL cirosunda kalan katkı oranıdır.
>
> **b)**
> Ne yapıyoruz: Ağırlıklı ortalama CMR'yi buluyoruz.
> Formül/Yöntem: $\overline{CMR}=\sum W_i \cdot CMR_i$
> Hesap: $0{,}40 \times 0{,}375 + 0{,}35 \times 0{,}4167 + 0{,}25 \times 0{,}550 = 0{,}1500 + 0{,}1458 + 0{,}1375 = 0{,}4333$
> Sonuç: $\overline{CMR} \approx 0{,}4333$ (%43,33).
> Neden: Karmadaki her ürün, ciro payı kadar ortalamaya katkı verir.
>
> **c)**
> Ne yapıyoruz: Başa baş ciroyu buluyoruz.
> Formül/Yöntem: $S_{BB}=F/\overline{CMR}$
> Hesap: $S_{BB} = \dfrac{480.000}{0{,}4333} \approx 1.107.690$ TL.
> Sonuç: $S_{BB} \approx 1.107.690$ TL.
> Neden: Ortalama katkı oranıyla 480.000 TL sabit maliyeti karşılayacak ciro budur.
>
> **ç)**
> Ne yapıyoruz: BBN cirosunu ürünlere dağıtıyoruz.
> Formül/Yöntem: $S_{BB} \times W_i$
> Hesap:
>
> | Ürün | Pay | BBN cirosu (TL) |
> |---|---|---|
> | A | %40 | $1.107.690 \times 0{,}40 = 443.076$ |
> | B | %35 | $1.107.690 \times 0{,}35 = 387.692$ |
> | C | %25 | $1.107.690 \times 0{,}25 = 276.922$ |
>
> Sonuç: A 443.076; B 387.692; C 276.922 TL.
> Neden: Her ürün toplam ciroya gelir payı oranında katkı vermek zorundadır.
>
> **d)**
> Ne yapıyoruz: What-if — karma C lehine kayıyor (örn. A %30, B %20, C %50).
> Formül/Yöntem: $\overline{CMR}$'yi yeni ağırlıklarla hesapla.
> Hesap: $0{,}30 \times 0{,}375 + 0{,}20 \times 0{,}4167 + 0{,}50 \times 0{,}550 = 0{,}1125 + 0{,}0833 + 0{,}2750 = 0{,}4708$; $S_{BB} = \dfrac{480.000}{0{,}4708} \approx 1.019.500$ TL.
> Sonuç: $\overline{CMR}$ yükselir (~%47,1), $S_{BB}$ düşer (~1.019.500 TL).
> Neden: Yüksek marjlı C'nin payı arttıkça ortalama katkı artar, daha düşük ciroyla başa başa ulaşılır; ürün karması BBN'yi doğrudan değiştirir.

---

### S04 — Orta — Yap / Satın al kararı

> [!question] Soru
> Bir beyaz eşya üreticisinin satın alma müdürü, bir makine parçasını içeride üretmek mi yoksa dışarıdan almak mı gerektiğine karar verecek. İç üretim için 150.000 TL sabit kurulum maliyeti ve 40 TL birim değişken maliyet öngörülmüştür; aynı parça dışarıdan birim başına 65 TL'ye temin edilebilmektedir (dışarıda sabit maliyet yok). Yıllık ihtiyaç 8.000 adettir.
>
> a) Eşik üretim miktarını ($x^*$) hesaplayın.
> b) 8.000 adette "yap" ve "satın al" toplam maliyetlerini hesaplayın.
> c) 8.000 adette hangi seçenek ekonomik, fark ne kadardır?
> ç) Dış birim maliyet 38 TL'ye düşseydi karar nasıl değişir?
> d) Yap/satın al kararında maliyet dışı 2 faktör yazın.

> [!info] Sezgi & Strateji
> **Ne soruluyor:** İki maliyet doğrusunun kesişimi ve payda işareti kontrolü.
> **Hangi yöntem:** $x^* = K/(c_{satın}-c_{yap})$ (payda = dış birim maliyet − iç birim maliyet).
> **Dikkat:** Payda negatif veya sıfır çıkarsa eşik yoktur; karar değişir.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Eşik miktarı buluyoruz.
> Formül/Yöntem: $x^* = K/(c_{satın}-c_{yap})$
> Hesap: $x^* = \dfrac{150.000}{65-40} = \dfrac{150.000}{25} = 6.000$ adet.
> Sonuç: $x^* = 6.000$ adet ($x<6.000$ → satın al, $x>6.000$ → yap).
> Neden: 6.000 adette iki seçenek eşit maliyetlidir; altında sabit maliyet yükü ağır basar, üstünde birim avantajı devreye girer.
>
> **b)**
> Ne yapıyoruz: 8.000 adet için iki maliyeti hesaplıyoruz.
> Formül/Yöntem: $TC_{yap}=K+c_{yap}\cdot x$; $TC_{satın}=c_{satın}\cdot x$
> Hesap: $TC_{yap} = 150.000 + 40 \times 8.000 = 470.000$ TL; $TC_{satın} = 65 \times 8.000 = 520.000$ TL.
> Sonuç: Yap 470.000 TL, Satın al 520.000 TL.
> Neden: 8.000 > 6.000 olduğundan iç üretimin birim avantajı sabit maliyeti baskılamıştır.
>
> **c)**
> Ne yapıyoruz: İki maliyeti karşılaştırıyoruz.
> Formül/Yöntem: Fark = $TC_{satın}-TC_{yap}$
> Hesap: $520.000 - 470.000 = 50.000$ TL.
> Sonuç: İç üretim 50.000 TL daha ucuzdur.
> Neden: Talep eşik miktarın üzerinde olduğu için "yap" baskındır.
>
> **ç)**
> Ne yapıyoruz: What-if — dış birim maliyet 38 TL.
> Formül/Yöntem: Payda işaret kontrolü.
> Hesap: $c_{satın}-c_{yap} = 38-40 = -2 < 0$ → payda negatif, eşik anlamsız. Dış birim maliyet içeridekinden düşük olduğundan her hacimde satın al üstündür.
> Sonuç: Her miktarda satın al.
> Neden: Dış birim maliyet hem düşükken sabit maliyet de yokken iç üretim hiçbir hacimde kazanamaz.
>
> **d)**
> Ne yapıyoruz: Maliyet dışı faktörleri yazıyoruz.
> Formül/Yöntem: Stratejik değerlendirme.
> Hesap: (1) Tedarik güvenliği ve kalite kontrolü — kritik parçada dışa bağımlılık riski. (2) Kapasite/uzmanlık ve gizlilik — iç üretim know-how ve fikrî mülkiyeti korur.
> Sonuç: Karar yalnız maliyetle verilmez.
> Neden: Tedarik riski, kalite ve stratejik gizlilik uzun vadede maliyet farkından önemli olabilir.

---

### S05 — Zor — Dinamik kapasite büyümesi

> [!question] Soru
> Bir kimyasal hammadde fabrikasının yatırım planlama uzmanı, kapasiteyi ne sıklıkla ve ne büyüklükte artırması gerektiğini hesaplıyor. Kapasite ilave maliyeti $f(y) = 0{,}04\, y^{0{,}70}$ milyon TL ($k=0{,}04$, $a=0{,}70$), talep yılda $D=1.500$ ton artmakta, sürekli iskonto oranı $r=0{,}12$'dir. $g(u)=u/(e^u-1)=0{,}70$ denkleminin çözümü $u^* \approx 0{,}7550$ verilmiştir.
>
> a) Optimal ilave aralığını ($x^*$) hesaplayın.
> b) Her ilavenin büyüklüğünü ($y^*$) hesaplayın.
> c) Sonucu ölçek ekonomisi açısından yorumlayın.
> ç) Ölçek ekonomisi güçlenip $a=0{,}50$ olsaydı $x^*$ ve $y^*$ nasıl değişir?
> d) Bu modelde en hassas parametre hangisidir, neden?

> [!info] Sezgi & Strateji
> **Ne soruluyor:** Dinamik kapasite modelinin temel sonuçları ve $a$ parametresinin yorumu.
> **Hangi yöntem:** $u^* = rx^*$ → $x^* = u^*/r$; $y^* = x^* \cdot D$. Ölçek ekonomisi: $0 < a < 1$.
> **Dikkat:** $u^*$ verilmiş — denklemi çözmene gerek yok, doğrudan $x^* = u^*/r$ kullan.

> [!answer]- Adım adım çözüm
> **a)**
> Ne yapıyoruz: Optimal ilave aralığını buluyoruz.
> Formül/Yöntem: $x^* = u^*/r$
> Hesap: $x^* = \dfrac{0{,}7550}{0{,}12} = 6{,}292$ yıl.
> Sonuç: $x^* \approx 6{,}29$ yıl.
> Neden: İskonto oranı, optimal yatırım periyodunu $u^*$ üzerinden belirler.
>
> **b)**
> Ne yapıyoruz: İlave büyüklüğünü buluyoruz.
> Formül/Yöntem: $y^* = x^* \cdot D$
> Hesap: $y^* = 6{,}292 \times 1.500 = 9.438$ ton.
> Sonuç: $y^* \approx 9.438$ ton.
> Neden: Her periyotta biriken talebi karşılayacak kapasite eklenir.
>
> **c)**
> Ne yapıyoruz: Sonucu yorumluyoruz.
> Formül/Yöntem: $0<a<1$ → ölçek ekonomisi.
> Hesap: Fabrika ~her 6,3 yılda bir 9.438 ton ekler; $a=0{,}70<1$ olduğundan büyük ilaveler birim başına daha ucuzdur.
> Sonuç: Seyrek ama büyük yatırım optimaldir.
> Neden: Ölçek ekonomisi, kapasiteyi toplu eklemeyi tekil eklemekten ekonomik kılar.
>
> **ç)**
> Ne yapıyoruz: What-if — $a=0{,}50$ (ölçek ekonomisi güçleniyor).
> Formül/Yöntem: $g(u)=u/(e^u-1)$ azalan; $a\downarrow \Rightarrow u^*\uparrow \Rightarrow x^*\uparrow, y^*\uparrow$.
> Hesap: $g(u)$ azalan olduğundan daha küçük $a$, eğri üzerinde daha büyük $u^*$'a karşılık gelir; $x^*=u^*/r$ büyür, $y^*=x^*D$ de büyür.
> Sonuç: Hem ilave aralığı hem ilave büyüklüğü artar.
> Neden: Ölçek ekonomisi güçlendikçe büyük ve seyrek toplu yatırım ("güçlü ölçek = büyük ama sabırlı fabrika") ekonomikleşir.
>
> **d)**
> Ne yapıyoruz: En hassas parametreyi belirliyoruz.
> Formül/Yöntem: Duyarlılık.
> Hesap: $a$, hem $u^*$'ı (dolayısıyla $x^*$'ı) hem ölçek davranışını belirler; küçük değişimi $g(u)=a$ çözümünü ve tüm yatırım stratejisini kaydırır.
> Sonuç: En hassas parametre ölçek ekonomisi katsayısı $a$'dır.
> Neden: $r$ ve $D$ doğrusal etki ederken $a$ denklem çözümünü değiştirdiği için sonucu doğrusal olmayan biçimde etkiler.
