---
hafta: 4
durum: hazır
tags: [ders/tesis-planlama, konu/donanım, konu/operatör]
---

# HF04 - Ürün, Süreç ve Çizelgeleme Tasarımı III

> [!summary] Ana fikir
> Talep ve süreç süreleri; fire, performans, güvenilirlik ve kullanılabilir zamanla birlikte makine ve operatör gereksinimine dönüştürülür; bu sayılar daha sonra yerleşim ve alan hesabının girdisi olur.

## Kavramsal açıklama — neden, nasıl, nerede?

Önceki haftalarda **ne** üreteceğimizi (ürün tasarımı) ve **nasıl** üreteceğimizi (süreç tasarımı) belirledik. Bu hafta üçüncü soruyu yanıtlıyoruz: **kaç adet** ve **kaç kaynakla**? Buna **çizelge tasarımı** denir ve üç alt karara ayrılır:

1. **Ürün miktarı** — fire ve ıskartayı hesaba katarak gerçekte planlanacak miktar.
2. **Donanım gereksinimi** — bu miktarı üretmek için kaç makine gerekir.
3. **Operatör gereksinimi** — makineleri kim, kaç kişi çalıştıracak.

> [!info] Neden önemli?
> Bir hatadan dolayı makine sayısını 2 yerine 1 planlarsanız fabrika kapasite açığı verir, siparişler gecikir. Fazla planlarsanız atıl yatırım oluşur. Aynı şekilde fireyi göz ardı etmek, vardiya sonunda "iyi ürün" hedefini tutturamamak demektir. Bu hesaplar yatırım ve teslimat sözlerinin temelidir.

**Gerçek hayat örneği:** Bir otomotiv yan sanayi 100.000 sağlam conta teslim edecek. Pres, taşlama ve kontrol hatlarının her birinde belli bir fire oranı vardır. Eğer hat girişine sadece 100.000 hammadde koyarsanız, fireler nedeniyle çıkışta 100.000'in altına düşersiniz. Bu yüzden **geriye doğru** yürüyüp girişe daha fazla hammadde koymak gerekir.

---

## 1. Aşamalı fire hesabı (Yüksek hacimli üretim)

### Fire nedir, neye bağlıdır?

Fire (ıskarta / scrap), geometrik veya kalite faktörlerine bağlı olarak imalat sürecinde ortaya çıkan **malzeme israfıdır**. Gerçek üretim miktarını belirlemek için zorunlu olarak göz önüne alınır. Genel ıskarta oranı şu durumlarda **azalır**:

- Süreç ne kadar otomatikse,
- Parça toleransları ne kadar bolsa,
- Sertifikalı tedarikçi sayısı ne kadar fazlaysa,
- Kaynak/malzeme kalitesi ne kadar yüksekse,
- Hata önleme (poka-yoke) teknikleri uygulanıyorsa.

### Tek operasyonun fire modeli

$k$ operasyonunda girdi $I_k$, iyi çıktı $O_k$, fire $S_k$ ve fire oranı $s_k$ ($P_{sk}$) ise:

$$
S_k = s_k\,I_k, \qquad O_k = I_k - S_k = (1-s_k)\,I_k
$$

| Sembol | Açıklama |
|---|---|
| $k$ | Süreç (operasyon) numarası |
| $I_k$ | $k$. operasyona giren miktar (girdi) |
| $O_k$ | $k$. operasyondan çıkan **iyi** ürün (çıktı) |
| $S_k$ | $k$. operasyondaki fire (ıskarta) miktarı |
| $s_k$ (veya $P_{sk}$) | $k$. operasyonun fire (ıskarta) oranı |
| $y_k = 1-s_k$ | Verim (iyi ürün) oranı |
| $n$ | Toplam operasyon sayısı |

### Geriye doğru yürütme

Nihai iyi ürün hedefinden başlanır ve her operasyon için gerekli girdi şöyle bulunur:

$$
I_k = \frac{O_k}{1 - s_k}
$$

Seri süreçte bir operasyonun gerekli girdisi, **önceki** operasyonun gerekli iyi çıktısıdır: $O_{k-1} = I_k$.

$n$ operasyon ve nihai hedef $O_n$ için zincir tek formülle özetlenir:

$$
I_1 = \frac{O_n}{\displaystyle\prod_{k=1}^{n}(1 - s_k)}
$$

> [!warning] Sık yapılan hata — fire oranlarını toplamak
> %3, %2 ve %4 fireyi "%9 toplam fire" gibi düşünmek **yanlıştır**. Seri operasyonlarda **verimler çarpılır**: $(1-0{,}03)(1-0{,}02)(1-0{,}04)$. Her oranı $1-s_k$ yapıp çarpın.

> [!tip] Yön kuralı
> Hesaba **her zaman son (iyi ürün) hedeften** başlanır ve geriye gidilir. Son operasyona kaç sağlam girdi gerektiğini bilmeden, ondan önceki operasyonun hedef çıktısını belirleyemezsiniz.

---

## 2. Donanım (makine) gereksinimi

### Formül ve semboller

$$
F = \frac{S\,Q}{E\,H\,R}
$$

| Sembol | Açıklama | Tipik birim |
|---|---|---|
| $F$ | Gerekli makine sayısı (kapasitesi) | makine |
| $S$ | 1 birim ürünü imal etme standart süresi | dk/parça |
| $Q$ | Dönem (vardiya/yıl) başına üretilecek miktar | parça |
| $E$ | Gerçek performans (standart zamanın yüzdesi) | boyutsuz |
| $H$ | Makine başına mevcut kullanım süresi | dk |
| $R$ | Makinenin güvenilirliği/kullanılabilirliği | boyutsuz |

Pay $S\,Q$ = toplam standart iş yükü. Payda $E\,H\,R$ = düzeltilmiş **etkin** makine süresidir.

> [!warning] Sık yapılan hata — $E$ ve $R$'yi paya yazmak
> Düşük performans ve güvenilirlik kapasiteyi **azaltır**, dolayısıyla ihtiyacı **artırır**. Bu yüzden $E$ ve $R$ daima **paydaya** yazılır. Paya yazarsanız makine sayısını olduğundan az bulursunuz.

### Yuvarlama ve yerleşim tipi farkı

Kesirli sonuç gerçek bir kapasite ihtiyacını gösterir; bu yüzden makine kararı için **tavana yuvarlanır** ($\lceil \cdot \rceil$). Ancak yuvarlama sırası yerleşim tipine göre değişir:

| | Sürece göre yerleşim | Ürüne göre yerleşim |
|---|---|---|
| Mantık | Aynı tip makinedeki tüm ürün yükleri **önce birleştirilir**, sonra toplam yukarı yuvarlanır | Her ürün hattının makine gereksinimi **ayrı yuvarlanır**, sonra tamsayılar toplanır |
| Formül | $F_m=\left\lceil \sum_p \dfrac{S_{pm}Q_p}{E_m H_m R_m}\right\rceil$ | $F_m=\sum_p \left\lceil \dfrac{S_{pm}Q_p}{E_m H_m R_m}\right\rceil$ |
| Sonuç | Genelde daha az makine (paylaşım mümkün) | Genelde daha çok makine (kapasite paylaşılamaz) |

Örnek-7'nin kıyaslama tablosu bu farkı doğrular: ürüne göre toplam **26**, sürece göre **23** makine.

> [!warning] Sık yapılan hata — makine kesrini en yakına yuvarlamak
> $F = 1{,}40$ çıktığında "1 makine yeter" demek yanlıştır. Kesir de gerçek kapasite ihtiyacıdır; karar için **tavana** yuvarlanır. Alternatif olarak fazla mesai veya fason düşünülürse bu ayrıca maliyetle gerekçelendirilmelidir.

---

## 3. Operatör-makine atama (Makine Assignment Problem)

### Ne zaman gerekir?

Otomatik/yarı otomatik çevrimde bir operatör birden çok makineye bakabilir (örn. CNC). Ama bazı işler operatörü %100 meşgul eder (forklift gibi). Bir operatöre kaç makine atanacağını **insan-makine (çoklu faaliyet) şeması** ile çözeriz.

### Süre bileşenleri ve formüller

| Sembol | Etkinlik | Kim meşgul? |
|---|---|---|
| $a$ | Yükleme + boşaltma (eşzamanlı) | Operatör + makine |
| $b$ | Yürüme + muayene + paketleme | Yalnız operatör |
| $t$ | Otomatik işleme | Yalnız makine |
| $m$ | Bir operatöre atanan tamsayı makine sayısı | Karar |

İdeal (teorik) makine sayısı — makine çevrimi ile operatör turunun tam dengelendiği nokta:

$$
n' = \frac{a + t}{a + b}
$$

Gerçek tekrarlı çevrim süresini **yavaş olan taraf** belirler:

$$
T(m) = \max\{\,a + t,\; m(a + b)\,\}
$$

Bir çevrimde $m$ parça tamamlandığından üretim oranı (hızı):

$$
r(m) = \frac{m}{T(m)} \quad [\text{parça/zaman}]
$$

Aylak (idle) süreler:

$$
m < n' \Rightarrow \text{Operatör bekler: } I_O = T(m) - m(a+b)
$$
$$
m > n' \Rightarrow \text{Makineler bekler: } I_M = T(m) - (a+t)
$$
$$
m = n' \Rightarrow \text{İdeal: iki taraf da beklemez}
$$

Birim maliyet (operatör maliyet oranı $c_o$, makine maliyet oranı $c_m$):

$$
C_u(m) = \frac{(c_o + m\,c_m)\,T(m)}{m}
$$

> [!warning] Sık yapılan hata — $n'$'ü otomatik tavana yuvarlamak
> $n' = 2{,}67$ bulunması doğrudan "3 makine seç" demek **değildir**. $n'$ yalnızca denge noktasıdır. $\lfloor n'\rfloor$ ve $\lceil n'\rceil$ adayları üretim hedefi ve maliyet açısından **karşılaştırılmalıdır**.

---

## Tam çözümlü örnek 1 — Donanım gereksinimi (Slayt 19, Örnek-4)

> [!example] Soru
> Bir parçanın freze tezgâhında işlenme süresi 2,8 dk'dır. 8 saatlik vardiyada 200 parça üretilecektir. Makine 480 dakikanın %80'inde çalışır; çalışırken standart hızın %95'i ile üretir. Kaç freze tezgâhı gerekir?

**Verilenler:** $S=2{,}8$ dk/parça, $Q=200$, $H=480$ dk, $E=0{,}95$, $R=0{,}80$.

**Kurulum:**
$$
F = \frac{S\,Q}{E\,H\,R} = \frac{2{,}8 \times 200}{0{,}95 \times 480 \times 0{,}80} = \frac{560}{364{,}8} = 1{,}535
$$

**Karar:** 0,535 makine satın alınamaz; normal vardiyada
$$
\lceil 1{,}535 \rceil = \mathbf{2 \text{ freze tezgâhı}}
$$

> [!success] Sonuç
> En az 2 freze gerekir. 1'e yuvarlamak kapasite açığı yaratır. İkinci makine yerine fazla mesai/fason tercih edilecekse ayrıca maliyetle gerekçelendirilmelidir.

---

## Tam çözümlü örnek 2 — Aşamalı fire + parça girdisi (Slayt 25-28, Örnek-7)

> [!example] Soru
> Bir A ürünü 3 tip parçadan monte edilerek yılda **2.500 adet** üretilecek. Temel süreç şemasındaki 1-2-3-4 muayenelerinin kusurlu oranları sırasıyla **%3-%2-%4-%5**'tir. Parçaların sisteme girmesi gereken hammadde miktarlarını bulun.

Her parça yalnız kendi rotasındaki muayenelerden geçer. Verim oranları $1-s$ ile çarpılır ve geriye doğru çözülür:

**1. Parça** (3 ve 4 No.lu muayeneler: %4 ve %5):
$$
(1-0{,}04)(1-0{,}05)\,X_1 = 2.500 \;\Rightarrow\; (0{,}96)(0{,}95)\,X_1 = 2.500 \;\Rightarrow\; X_1 = \frac{2.500}{0{,}912} = \mathbf{2.741 \text{ adet/yıl}}
$$

**2. Parça** (2 ve 4 No.lu muayeneler: %2 ve %5):
$$
(0{,}98)(0{,}95)\,X_2 = 2.500 \;\Rightarrow\; X_2 = \frac{2.500}{0{,}931} = \mathbf{2.685 \text{ adet/yıl}}
$$

**3. Parça** (1 ve 4 No.lu muayeneler: %3 ve %5):
$$
(0{,}97)(0{,}95)\,X_3 = 2.500 \;\Rightarrow\; X_3 = \frac{2.500}{0{,}9215} = \mathbf{2.713 \text{ adet/yıl}}
$$

> [!success] Sonuç
> Hammadde girişleri: 1. parça 2.741, 2. parça 2.685, 3. parça 2.713 adet/yıl. Bu değerler her parçanın makine gereksinimi formülünde $Q$ olarak kullanılır. Yıllık çalışma 2.400 saat alınarak makine sayıları $F=SQ/(EHR)$ ile bulunur ve yerleşim tipine göre yuvarlanır.

---

## Tam çözümlü örnek 3 — Operatör-makine atama (Slayt 51-52, Örnek-10)

> [!example] Soru
> Yükleme + boşaltma $a=2$ dk, otomatik işlem $t=6$ dk, yürüme + muayene/paketleme $b=1$ dk. İdeal makine sayısı kaçtır? $m=2$ ve $m=3$ seçeneklerinin çevrimini ve aylak sürelerini karşılaştırın.

**İdeal sayı:**
$$
n' = \frac{a+t}{a+b} = \frac{2+6}{2+1} = \frac{8}{3} = 2{,}67
$$
Kesirli makine atanamayacağından adaylar $m=2$ ve $m=3$'tür.

**Aday $m=2$:** $T(2)=\max\{8,\,2(3)\}=\max\{8,6\}=8$ dk
$$
r(2) = \frac{2}{8} = 0{,}25 \text{ parça/dk}, \qquad m<n' \Rightarrow I_O = 8 - 2(3) = 2 \text{ dk (operatör bekler)}
$$

**Aday $m=3$:** $T(3)=\max\{8,\,3(3)\}=\max\{8,9\}=9$ dk
$$
r(3) = \frac{3}{9} = 0{,}333 \text{ parça/dk}, \qquad m>n' \Rightarrow I_M = 9 - 8 = 1 \text{ dk/makine (makineler bekler)}
$$

| $m$ | Çevrim $T(m)$ | Üretim oranı | Operatör aylak | Makine başına aylak |
|---:|---:|---:|---:|---:|
| 2 | 8 dk | 0,250 parça/dk | 2 dk | 0 dk |
| 3 | 9 dk | 0,333 parça/dk | 0 dk | 1 dk |

> [!success] Sonuç
> Yalnız üretim oranı amaçlanırsa **3 makine** daha yüksek çıktı verir. Kesin "optimum" karar için makine ve operatör maliyetleri de $C_u(m)$ ile karşılaştırılmalıdır. (Çözümlü Soru-3'te $m<n'$ iken birim maliyetin $\$20{,}66$ çıktığı gösterilir.)

---

## Karşılaştırma ve karar noktaları

| Karar | Soru | Kural |
|---|---|---|
| Fire yönü | Baştan mı, sondan mı? | Daima **nihai iyi üründen geriye** |
| Fire birleştirme | Toplama mı, çarpma mı? | **Verimleri çarp** ($\prod(1-s_k)$) |
| Makine kesri | En yakın mı, tavan mı? | Kapasite için **tavana** yuvarla |
| Yerleşim & yuvarlama | Önce mi topla, önce mi yuvarla? | Sürece göre: önce topla; ürüne göre: önce yuvarla |
| Operatör atama | $n'$ tam sayı mı? | $\lfloor n'\rfloor$ ve $\lceil n'\rceil$ adaylarını **karşılaştır** |
| Çevrim süresi | Toplam mı, maksimum mu? | $T(m)=\max\{a+t,\,m(a+b)\}$ |

---

## Pratik sorular

> [!question] Soru 1 — Donanım
> $S=4$ dk/parça, $Q=300$ parça/vardiya, $H=480$ dk, $E=0{,}90$, $R=0{,}85$. Gereken makine kapasite kesrini ve uygulanabilir tam makine sayısını bulun.

> [!answer]- Çözüm
> $$F = \frac{4(300)}{0{,}90(480)(0{,}85)} = \frac{1200}{367{,}2} = 3{,}268$$
> $\lceil 3{,}268 \rceil = \mathbf{4 \text{ makine}}$ gerekir.

> [!question] Soru 2 — Fire + makine zinciri
> Son operasyondan 240 iyi parça isteniyor; bu operasyonun fire oranı %4. Standart süre 3,2 dk/parça, vardiya 480 dk, performans %90, güvenilirlik %85. Planlanacak giriş miktarını ve makine sayısını bulun.

> [!answer]- Çözüm
> Giriş: $Q = \left\lceil \dfrac{240}{1-0{,}04}\right\rceil = \left\lceil \dfrac{240}{0{,}96}\right\rceil = 250$ parça.
> $$F = \frac{3{,}2(250)}{0{,}90(480)(0{,}85)} = \frac{800}{367{,}2} = 2{,}179 \;\Rightarrow\; \lceil 2{,}179 \rceil = \mathbf{3 \text{ makine}}$$

> [!question] Soru 3 — Sürece vs. ürüne göre yerleşim
> A ve B ürünleri aynı tip frezede işleniyor. A: $Q_A=500$, $S_A=4$ dk; B: $Q_B=300$, $S_B=7$ dk. Ayda 22 gün, günde 8 saat. $E=0{,}80$, $R=0{,}90$. (a) Sürece göre yerleşimde, (b) her ürün ayrı hatta olduğu ürüne göre yerleşimde gereken toplam freze sayısını bulun.

> [!answer]- Çözüm
> Aylık mevcut süre: $H = 22 \times 8 \times 60 = 10.560$ dk.
> **(a) Sürece göre** (yükler birleştirilir, sonra yuvarlanır):
> $$F = \frac{4(500)+7(300)}{0{,}80(10.560)(0{,}90)} = \frac{2000+2100}{7603{,}2} = \frac{4100}{7603{,}2} = 0{,}539 \;\Rightarrow\; \mathbf{1 \text{ freze}}$$
> **(b) Ürüne göre** (ayrı yuvarlanıp toplanır):
> $$F_A = \frac{4(500)}{7603{,}2} = 0{,}263 \Rightarrow 1, \qquad F_B = \frac{7(300)}{7603{,}2} = 0{,}276 \Rightarrow 1$$
> Toplam **2 freze**. Fark, kapasite parçalarının ayrı hatlar arasında paylaşılamamasından doğar.

> [!question] Soru 4 — Operatör/makine kim bekler?
> $a=1{,}5$ dk, $b=0{,}5$ dk, $t=7$ dk. (a) $n'$ kaçtır? (b) $m=4$ ve $m=5$ için çevrim, üretim oranı ve aylak süreyi bulun.

> [!answer]- Çözüm
> (a) $n' = \dfrac{1{,}5+7}{1{,}5+0{,}5} = \dfrac{8{,}5}{2} = 4{,}25$. Adaylar 4 ve 5.
> (b) $m=4$: $T=\max\{8{,}5,\,4(2)\}=\max\{8{,}5,8\}=8{,}5$; $r=4/8{,}5=0{,}471$; $m<n'$, operatör aylak $=8{,}5-8=0{,}5$ dk.
> $m=5$: $T=\max\{8{,}5,\,5(2)\}=\max\{8{,}5,10\}=10$; $r=5/10=0{,}500$; $m>n'$, makine başına aylak $=10-8{,}5=1{,}5$ dk.
> 5 makine daha yüksek üretim oranı verir; maliyet bilgisi olmadan birim maliyeti en düşük seçenek söylenemez.

---

## Tesis tasarımında 7 yönetim ve planlama aracı

Ürün-süreç-çizelge tasarımı bittiğinde tesisi tasarlamaya geçilir. Sistem planlamada kullanılan araçlar:

| Araç | Kullanım |
|---|---|
| Yakınlık (Affinity) diyagramı | Sözel fikir ve sorunları gruplama/sınıflandırma |
| İlişki (Interrelationship) diyagramı | Faktörler arası neden-sonuç bağlarını gösterme |
| Ağaç diyagramı | Hedefi alt görev/gereksinimlere ayırma |
| Matris diyagramı | İki değişken kümesi arasındaki ilişki |
| Olası durum (Contingency) diyagramı | Risk ve alternatif senaryoları haritalama |
| Etkinlik ağ diyagramı | İş sırası ve proje zamanı çizelgesi |
| Önceliklendirme matrisi | Alternatifleri ağırlıklı ölçütlerle sıralama |

Önceliklendirme matrisinde tipik ağırlıklar: 1 = eşit önemli, 5 = önemli, 10 = çok önemli (ve karşılıkları 1/5, 1/10). Tipik kriterler: toplam taşıma mesafesi, imalat alanı, esneklik, mevcut ekipman kullanımı, yatırım gereksinimi, WIP etkisi, insan faktörü riski, tahmini maliyet.

---

## İlgili öğrenme paketleri ve bağlantılar

- [[HF04A - Fire ve Donanım Gereksinimi]] — aşamalı fire, geriye yürütme, tamsayı planlama ve makine gereksinimi alıştırmaları
- [[HF04B - Operatör Makine Atama]] — çevrim süresi $T(m)$, üretim hızı $r(m)$, birim maliyet $C_u(m)$ ve maliyetle karar
- [[03 Formüller/Formül Föyü#Donanım gereksinimi|Formül föyü — Donanım gereksinimi]]

## Kaynaklar

- [[HF4-P4-Ürün, Süreç ve Çizelgeleme Tasarımı III-2025.pptx|Ders sunumu]]
- [[05 Kaynaklar/MarkItDown/HF04 - Ham|MarkItDown ham metni]]

Önceki: [[HF03 - Ürün, Süreç ve Çizelgeleme Tasarımı II]] · Sonraki: [[HF05 - Akış, Alan ve Etkinlik İlişkileri I]]
