# Bütünleme Çalışma Kitabı

## Bölüm 1: Giriş ve Kurumsal Tesis Stratejisi

Tesis planlaması, kurumsal bir organizasyonun fiziksel varlıklarının (bina, arazi, makine, iş gücü vb.) hedeflenen amaçları en verimli ve esnek şekilde destekleyecek düzeyde tasarlanması ve yönetilmesi sürecidir. Bu süreç, stratejik düzeyden operasyonel düzeye kadar uzanan hiyerarşik kararları barındırır.

### 1.1 Karar Düzeyleri (Stratejik, Taktik, Operasyonel)

Tesis tasarlama kararları, işletmenin rekabetçi gücünü belirleyen ve geri dönüşü zor olan kararlar bütünüdür. Karar seviyeleri hiyerarşik olarak üç ana grupta ele alınır:

1.  **Stratejik Düzey (Uzun Vadeli Kararlar):**
    *   **Kapsam:** Tesisin kurulup kurulmaması, kurulacaksa hangi ülkede veya coğrafi bölgede konumlanacağı (global tesis yeri seçimi), dikey entegrasyon seviyesi (kendi bünyesinde üretim yapılması veya fason yaptırma stratejisi) ve tesisin genel vizyonunun/misyonunun kurumsal stratejilerle entegrasyonudur.
    *   **Zaman Ufku:** Genellikle 5 ila 10 yıl ve üzeridir.
    *   **Özellik:** Yüksek sermaye yatırımı gerektirir, geri dönüşü son derece zor ve maliyetlidir.

2.  **Taktik Düzey (Orta Vadeli Kararlar):**
    *   **Kapsam:** Kapasitenin belirlenmesi (tesis büyüklüğü), üretim teknolojilerinin ve donanımlarının seçimi, depo/dağıtım merkezlerinin sayısının belirlenmesi, tesisin içindeki departmanların konumlandırılması (blok yerleşim planı - *block layout*) ve malzeme taşıma sistemlerinin entegrasyonudur.
    *   **Zaman Ufku:** 1 ila 5 yıl arasındadır.
    *   **Özellik:** Stratejik kararların çizdiği sınırları takip eder ve kaynak planlamasına odaklanır.

3.  **Operasyonel Düzey (Kısa Vadeli Kararlar):**
    *   **Kapsam:** Detay yerleşim düzeni (*detailed layout* - tezgahların, masaların ve ara stok alanlarının santim santim yerleşimi), günlük ve haftalık iş çizelgeleme, operatör-makine atamaları, iş istasyonu dengeleme, anlık envanter yönetimi ve günlük malzeme taşıma operasyonlarının yürütülmesidir.
    *   **Zaman Ufku:** Günlük, haftalık veya aylık periyotlardır.
    *   **Özellik:** Esnekliği en yüksek olan, operasyonel verimliliği maksimize etmeyi amaçlayan kararlardır.

### 1.2 Ürün Tasarım Değişikliklerinin Tesis Yerleşimine Etkileri

Bir tesisin yerleşim düzeni, doğrudan üretilecek ürünün fiziksel özelliklerine (boyut, ağırlık, malzeme vb.) ve üretim hacmine dayanır. Ürün tasarımında yapılacak bir değişiklik, tesis yerleşiminde köklü revizyonlara neden olabilir:

*   **Boyut ve Ağırlık Değişimi:** Ürünün daha ağır veya büyük tasarlanması, kullanılan konveyör veya forklift gibi taşıma sistemlerinin kapasitelerini aşabilir. Bu durum, koridor genişliklerinin artırılmasını ve daha güçlü zemin mukavemeti gerektiren özel alanların kurulmasını zorunlu kılar.
*   **Parça ve Malzeme Çeşitliliği:** Ürüne yeni bileşenler eklenmesi, montaj hattında yeni iş istasyonlarının açılmasını gerektirir. Malzeme türünün değişmesi (örn. ahşaptan metale geçiş) tamamen yeni üretim süreçlerinin (örn. kaynak, döküm, sac büküm) tesise eklenmesine ve dolayısıyla yerleşim tipinin *ürün esaslı yerleşimden süreç esaslı yerleşime* kaymasına neden olabilir.
*   **Tasarım Aşaması ve Maliyet İlişkisi:** İmalat maliyetlerinin %70-80'i tasarım aşamasında kilitlenir. Eş zamanlı mühendislik (*concurrent engineering*) uygulanmayan, ardışık tasarım süreçlerinde son anda yapılan tasarım değişiklikleri süreç maliyetlerini katlanarak artırır.

### 1.3 Müfredat Bağlamı ve Süreç Akışı

Tesis planlama ve tasarımı, ardışık kararlar zinciridir. Bir önceki aşamanın çıktısı, bir sonraki aşamanın girdisini oluşturur:

```mermaid
flowchart LR
  S[Kurumsal strateji] --> U[Ürün / hizmet]
  U --> P[Süreç seçimi]
  P --> C[Çizelge ve kapasite]
  C --> A[Akış ve alan]
  A --> Y[Yerleşim]
  Y --> K[Konum ve tesis sistemi]
  K --> D[Devreye alma]
  D --> I[Sürekli iyileştirme]
```

---

## Bölüm 2: Kapasite, Fire ve Kaynak Planlama

Kapasite planlaması, bir tesisin belirli bir zaman diliminde üretebileceği, depolayabileceği veya işleyebileceği maksimum çıktı miktarını belirleme sürecidir. Bu süreçte maliyet yapıları, fire oranları ve operatör verimlilikleri matematiksel olarak modellenmelidir.

### 2.1 Kapasite ve Başa Baş Analizi

İşletmelerde maliyetler üç ana grupta incelenir:
*   **Sabit Maliyetler ($F$):** Üretim hacminden bağımsız olarak ödenen (kira, sigorta, amortisman, bazı sabit telif ve dizgi giderleri vb.) maliyetlerdir.
*   **Değişken Maliyetler ($V \cdot x$):** Üretim miktarıyla doğrudan (doğrusal) değişen (ham madde, işçilik, enerji, iskontolar vb.) maliyetlerdir.
*   **Yarı Değişken Maliyetler:** Belirli bir üretim hacmine kadar sabit kalan, ardından üretimle birlikte artan maliyetlerdir (örn. bakım giderleri).

#### Başa Baş Noktası (BBN) Formülleri

Tek ürün durumunda miktar cinsinden başa baş noktası ($x_{BB}$):

$$x_{BB} = \frac{F}{P - V}$$

Burada $P$ birim satış fiyatı, $V$ birim değişken maliyet, $(P-V)$ ise birim katkı payıdır. Satış tutarı (para birimi) cinsinden başa baş noktası ($BEP_{TL}$):

$$BEP_{TL} = \frac{F}{1 - \frac{V}{P}}$$

#### Çok Ürünlü Durum ve Ağırlıklı Katkı Payı Oranı ($WCM$)

Çok ürün üreten işletmelerde, her ürünün toplam satış geliri içindeki ağırlığı ($w_i$) ve katkı payı oranı ($CMR_i$) kullanılarak ağırlıklı katkı payı oranı ($\overline{CMR}$) hesaplanır:

$$CMR_i = \frac{P_i - V_i}{P_i}$$

$$w_i = \frac{P_i \cdot Q_i}{\sum_j P_j \cdot Q_j}$$

$$\overline{CMR} = \sum_i w_i \cdot CMR_i$$

Para birimi cinsinden çok ürünlü başa baş noktası ($BEP_{TL}$):

$$BEP_{TL} = \frac{F}{\overline{CMR}}$$

#### Çok Ürünlü Başa Baş Çözümlü Örnek Walkthrough

Aylık sabit maliyeti $3.000$ USD (yıllık $F = 36.000$ USD) olan ve yılda $312$ gün çalışan bir restoran için veri seti şu şekildedir:

*   **Sandviç:** Yıllık Talep = 9.000 adet, Fiyat = 5,00 USD, Değişken Maliyet = 3,00 USD.
*   **İçecek:** Yıllık Talep = 9.000 adet, Fiyat = 1,50 USD, Değişken Maliyet = 0,50 USD.
*   **Fırın Patates:** Yıllık Talep = 7.000 adet, Fiyat = 2,00 USD, Değişken Maliyet = 1,00 USD.

**Adım 1: Her Ürünün Yıllık Satış Tutarı ($S_i$) ve Satış Payı Ağırlığı ($w_i$)**
*   $S_{Sandvic} = 9.000 \times 5,00 = 45.000$ USD
*   $S_{Icecek} = 9.000 \times 1,50 = 13.500$ USD
*   $S_{Patates} = 7.000 \times 2,00 = 14.000$ USD
*   $S_{Toplam} = 45.000 + 13.500 + 14.000 = 72.500$ USD
*   $w_{Sandvic} = 45.000 / 72.500 \approx 0,6207$
*   $w_{Icecek} = 13.500 / 72.500 \approx 0,1862$
*   $w_{Patates} = 14.000 / 72.500 \approx 0,1931$

**Adım 2: Katkı Payı Oranları ($CMR_i$)**
*   $CMR_{Sandvic} = (5,00 - 3,00) / 5,00 = 0,40$
*   $CMR_{Icecek} = (1,50 - 0,50) / 1,50 = 0,6667$
*   $CMR_{Patates} = (2,00 - 1,00) / 2,00 = 0,50$

**Adım 3: Ağırlıklı Katkı Payı Oranı ($\overline{CMR}$)**
*   Restoran sunumundaki gibi ara basamak yuvarlamaları kullanılarak ($0,470$):
    $$\overline{CMR} = (0,621 \times 0,40) + (0,186 \times 0,67) + (0,193 \times 0,50) = 0,248 + 0,125 + 0,097 = 0,470$$
*   **Başa Baş Yıllık Satış Tutarı:**
    $$BEP_{TL} = \frac{36.000}{0,470} \approx 76.596\text{ USD}$$
*   **Başa Baş Günlük Satış Tutarı:**
    $$BEP_{gunluk} = \frac{76.596}{312} \approx 245,50\text{ USD}$$

*(Not: Ara basamak yuvarlaması yapılmadan tam hassasiyetle hesaplandığında $\overline{CMR} \approx 0,4690$, $BEP_{TL} \approx 76.765$ USD ve $BEP_{gunluk} \approx 246,04$ USD çıkacaktır.)*

![[07 Ekler/Grafikler/basa-bas-grafigi.svg]]

---

### 2.2 Dinamik Kapasite Büyümesi

Kapasite artış kararları talep büyümesiyle birlikte ele alınmalıdır. Yatırım ve işletim maliyetlerinde ölçek ekonomisi bulunurken, paranın sürekli bir iskonto oranıyla zaman değeri de hesaba katılmalıdır.

#### Sonsuz Yatırım Serisinin Şimdiki Değeri

Talebin doğrusal artış hızı $D$ (kapasite/yıl) ve iki yatırım arası süre $x$ (yıl) olsun. Her $x$ yılında bir yapılması gereken kapasite ilavesi $y = x \cdot D$ olacaktır. $y$ büyüklüğünde bir tesis kurmanın maliyeti $f(y) = k \cdot y^a$ ($0 < a < 1$ ölçek ekonomisi faktörü) ise, $0, x, 2x, 3x, \ldots$ anlarında yapılan yatırımların sürekli iskonto oranı $r$ altındaki bugünkü değerler toplamı $C(x)$:

$$C(x) = f(x D) + f(x D) e^{-rx} + f(x D) e^{-2rx} + \cdots = \frac{f(x D)}{1 - e^{-rx}} = \frac{k(x D)^a}{1 - e^{-rx}}$$

#### Optimal Zaman Aralığı $x^*$ ve $u$ Dönüşümü Derivasyonu

$C(x)$ fonksiyonunu minimize etmek için $x$'e göre türevini alıp sıfıra eşitleriz:

$$\frac{d C(x)}{d x} = k D^a \left( \frac{a \cdot x^{a-1}(1 - e^{-rx}) - x^a(r e^{-rx})}{(1 - e^{-rx})^2} \right) = 0$$

Payı sıfıra eşitlediğimizde:

$$a \cdot x^{a-1}(1 - e^{-rx}) = r \cdot x^a e^{-rx}$$

Her iki tarafı $x^{a-1} e^{-rx}$ ile bölersek:

$$a(e^{rx} - 1) = r \cdot x \implies a = \frac{r \cdot x}{e^{rx} - 1}$$

$u = r \cdot x$ boyutsuz değişken dönüşümü yaparsak optimal denge koşulu elde edilir:

$$g(u) = \frac{u}{e^u - 1} = a$$

#### Çözümlü Örnek Walkthrough (Ders Çalışma Sorusu-2)
*   **Verilenler:** $f(y) = 0,0205 y^{0,58}$ milyon TL ($k = 0,0205$, $a = 0,58$), $D = 3.000$ ton/yıl, $r = 0,12$.
*   **Adım 1:** $g(u) = \frac{u}{e^u - 1} = 0,58$ denklemini çözeriz. Sayısal çözümle (veya tablodan) $u^* \approx 1,00584$ bulunur.
*   **Adım 2 (Optimal Zaman Aralığı):**
    $$x^* = \frac{u^*}{r} = \frac{1,00584}{0,12} \approx 8,3820\text{ yıl}$$
*   **Adım 3 (Optimal İlave Kapasite Büyüklüğü):**
    $$y^* = x^* \cdot D = 8,3820 \times 3.000 \approx 25.146,1\text{ ton}$$
*   **Adım 4 (Her İlavenin Nominal Maliyeti):**
    $$f(y^*) = 0,0205 \times (25.146,1)^{0,58} \approx 7,3118\text{ milyon TL}$$
*   **Adım 5 (İlk 4 Yatırımın Şimdiki Değeri - $t = 0, x, 2x, 3x$):**
    $$PV_4 = f(y^*) \cdot \sum_{n=0}^{3} (e^{-r x^*})^n = f(y^*) \left( \frac{1 - e^{-4 u^*}}{1 - e^{-u^*}} \right) = 7,3118 \times \left( \frac{1 - e^{-4,02336}}{1 - e^{-1,00584}} \right) \approx 11,3218\text{ milyon TL}$$

---

### 2.3 Düşük Hacimde Olasılıklı/Rassal Iskarta Payı (Binom Dağılımı)

Yüksek hacimli seri üretimde ortalama fire oranlarını kullanmak uygunken, düşük hacimli siparişe dayalı özel üretimlerde rassal ıskartaların varlığı, beklenen kârı maksimize edecek optimal parti büyüklüğünü ($Q$) hesaplamak için Binom olasılık modelini gerektirir.

#### Matematiksel Model ve Kâr Eşitliği

Siparişi tamamlamak için en az $d$ adet hatasız/sağlam parçaya ihtiyaç duyulmaktadır. Eğer üretilen $Q$ adet parçadan sağlam çıkanların sayısı $X \ge d$ ise müşteri siparişi kabul eder ve toplam gelir ($Revenue_{total}$) elde edilir. Aksi halde ($X < d$) sipariş teslim edilemez ve gelir elde edilemez. Bir parçanın sağlam çıkma olasılığı $p$ ise sağlam parça sayısı $X \sim \operatorname{Bin}(Q, p)$ dağılımına uyar.
Beklenen kâr formülü:

$$E[\Pi(Q)] = Revenue_{total} \times P(X \ge d) - UnitCost \times Q$$

$$P(X \ge d) = \sum_{x=d}^{Q} \binom{Q}{x} p^x (1-p)^{Q-x}$$

#### Adım Adım Slayt Örneği Çözümü
*   **Verilenler:** Müşteri siparişi için tam $d = 4$ sağlam parça gerek. Başarı olasılığı $p = 0,90$. Kabul edilirse toplam gelir $120.000$ TL. Bir adet dökümün birim maliyeti $15.000$ TL.
*   **Adaylar:** $Q \in \{4, 5, 6, 7\}$ için hesaplama:

1.  **$Q=4$ için:**
    $$P(X \ge 4) = P(X=4) = 0,90^4 = 0,6561$$
    $$E[\Pi(4)] = 120.000 \times 0,6561 - 15.000 \times 4 = 78.732 - 60.000 = 18.732\text{ TL}$$

2.  **$Q=5$ için:**
    $$P(X \ge 4) = \binom{5}{4} 0,90^4 \times 0,10^1 + \binom{5}{5} 0,90^5 = 5 \times 0,6561 \times 0,10 + 0,59049 = 0,32805 + 0,59049 = 0,91854$$
    $$E[\Pi(5)] = 120.000 \times 0,91854 - 15.000 \times 5 = 110.224,80 - 75.000 = 35.224,80\text{ TL}$$

3.  **$Q=6$ için:**
    $$P(X \ge 4) = \binom{6}{4} 0,90^4 \times 0,10^2 + \binom{6}{5} 0,90^5 \times 0,10^1 + \binom{6}{6} 0,90^6 = 0,098415 + 0,354294 + 0,531441 = 0,98415$$
    $$E[\Pi(6)] = 120.000 \times 0,98415 - 15.000 \times 6 = 118.098 - 90.000 = 28.098\text{ TL}$$

4.  **$Q=7$ için:**
    $$P(X \ge 4) \approx 0,99727$$
    $$E[\Pi(7)] = 120.000 \times 0,99727 - 15.000 \times 7 = 119.672,40 - 105.000 = 14.672,40\text{ TL}$$

#### Karar Analizi ve Risk Değerlendirmesi
En yüksek beklenen kârı ($35.224,80$ TL) veren **$Q^* = 5$** optimal ekonomik üretim miktarıdır.
*   **Sezgisel Tuzak:** Sadece ortalama fire oranı göz önüne alınsaydı, $d / p = 4 / 0,90 = 4,44 \implies 5$ adet üretilirdi. Ancak matematiksel modelleme, bu kararın arkasındaki risk ve maliyet dengesini (eksik üretip siparişi kaybetme riski ile fazla üretip ekstra birim maliyete katlanma riski arasındaki takası) tam olarak ortaya koyar.
*   **Zarar Olasılığı Hesabı:** $Q = 5$ seçildiğinde zarar etme durumu, sağlam parça sayısının $X < 4$ olması ve siparişin reddedilmesidir.
    $$P(\text{Zarar}) = P(X < 4) = 1 - P(X \ge 4) = 1 - 0,91854 = 0,08146\text{ yani }\%8,15$$

---

### 2.4 Aşamalı Fire ve Donanım Gereksinimi

Seri bağlı süreçlerde fire oluşumu, donanım kapasitesi ve operatör gereksinimlerinin planlanmasını doğrudan etkiler.

#### Sürekli (Continuous) ve Aşamalı (Stage-wise) Yuvarlama Farkı

*   **Sürekli Yaklaşım (Continuous):** Sürecin başından sonuna kadar fire oranları kesirli olarak taşınır ve toplam girdi tek bir formülle hesaplanarak en son aşamada yukarı yuvarlanır:
    $$I_1 = \frac{O_N}{\prod_{i=1}^{N} (1 - s_i)}$$
*   **Aşamalı Yaklaşım (Stage-wise):** Her bir ara operasyonda yarım/kesirli parça imal edilemeyeceğinden, her bir aşamanın girdi ihtiyacı ayrı ayrı yukarı yuvarlanarak geriye doğru yürütülür:
    $$I_k = \left\lceil \frac{I_{k+1}}{1 - s_k} \right\rceil,\qquad I_{N+1} \equiv O_N$$

#### Çözümlü Örnek Walkthrough (Geriye Yürütme)
Nihai çıktı hedefi $O_3 = 10.000$ adet olan 3 aşamalı bir süreçte fire oranları sırasıyla $s_1 = 0,02$, $s_2 = 0,03$, $s_3 = 0,05$'tir.

*   **Sürekli Plan:**
    $$I_1 = \frac{10.000}{(1-0,02)(1-0,03)(1-0,05)} = \frac{10.000}{0,98 \times 0,97 \times 0,95} = \frac{10.000}{0,90307} \approx 11.073,34 \implies \lceil 11.073,34 \rceil = 11.074\text{ adet}$$
*   **Aşamalı Plan:**
    1.  **3. Aşama Girdisi:** $I_3 = \lceil 10.000 / 0,95 \rceil = \lceil 10.526,32 \rceil = 10.527$ adet.
    2.  **2. Aşama Girdisi:** $I_2 = \lceil 10.527 / 0,97 \rceil = \lceil 10.852,58 \rceil = 10.853$ adet.
    3.  **1. Aşama Girdisi:** $I_1 = \lceil 10.853 / 0,98 \rceil = \lceil 11.074,49 \rceil = 11.075$ adet.

**Analiz:** Aşamalı yuvarlama, her istasyonda tam sayı kısıtını korumak için ilk aşamada **$11.075$** birim planlamayı gerektirirken; sürekli yuvarlama **$11.074$** birim verir. Aradaki 1 birimlik fark, ara istasyonlardaki tamsayılık gereksiniminin kümülatif etkisinden kaynaklanır.

#### Operatör-Makine Atama Modelleri

Operatör ve makinelerin birlikte çalıştığı yarı otomatik ortamlarda aşağıdaki değişkenler tanımlanır:
*   $a$: Eşzamanlı işler (yükleme, boşaltma süresi - hem operatör hem makine meşgul).
*   $b$: Bağımsız operatör işleri (yürüme, kontrol etme, paketleme süresi - yalnız operatör meşgul).
*   $t$: Bağımsız makine işleme süresi (otomatik çevrim süresi - yalnız makine meşgul).
*   $m$: Bir operatöre atanan makine sayısı (tamsayı karar değişkeni).

1.  **İdeal Makine Sayısı ($n'$):**
    $$n' = \frac{a + t}{a + b}$$
2.  **Gerçek Çevrim Süresi ($T(m)$):**
    $$T(m) = \max\{a + t,\; m(a + b)\}$$
3.  **Sistem Üretim Hızı ($r(m)$):**
    $$r(m) = \frac{m}{T(m)}$$
4.  **Birim Üretim Maliyeti ($C(m)$):**
    $$C(m) = \frac{(c_o + m \cdot c_m) T(m)}{m}$$
    Burada $c_o$ operatörün birim zaman maliyeti, $c_m$ ise makinenin birim zaman maliyetidir.

![[07 Ekler/Grafikler/operator-makine-maliyet.svg]]

---

## Bölüm 3: Akış, Hücre ve Faaliyet İlişkileri

Tesis içi bölümlerin, makinelerin ve iş istasyonlarının birbirleriyle olan ilişkileri, malzeme ve insan akışlarının yoğunluğu ile faaliyetlerin nitel yakınlık derecelerine göre belirlenir. Bu bölümde, hücre oluşturmada kullanılan doğrudan kümeleme ve ikili sıralama (ROC) algoritmaları, makine sıralamada kullanılan Hollier yöntemi, malzeme akış şiddetini ölçen MAG analizi ve alan planlama yaklaşımları matematiksel ve pedagojik olarak ele alınmaktadır.

### 3.1 DCA ve ROC (Rank Order Clustering) Algoritmaları

Grup Teknolojisi (Group Technology) ve Hücresel İmalat (Cellular Manufacturing) düzeninde temel amaç, benzer imalat süreçlerine sahip parçaları ürün aileleri (part families) halinde, bu parçaları işleyen makineleri ise imalat hücreleri (manufacturing cells) olarak gruplandırmaktır. Bu gruplandırma, makine-parça matrisinin $1$ ve $0$'lardan oluşan yapısını köşegen boyunca bloklaştırmak suretiyle gerçekleştirilir.

#### Doğrudan Kümeleme Algoritması (DCA)
DCA, makine-parça matrisindeki satır ve sütunların toplam $1$ sayılarına göre ön sıralanması ve ardından $1$'leri sola ve yukarıya doğru öteleyerek hücreleri görünür kılan sezgisel bir yaklaşımdır.

#### İkili Sıralama Algoritması (Rank Order Clustering - ROC)
ROC, her satır ve sütunu ikili sayı sistemindeki (binary) basamaklar olarak ele alıp ondalık (decimal) karşılıklarına göre ağırlıklandırarak sıralayan sistematik bir algoritmadır. 

$C$ sütunlu (parçalı) bir matriste $i$. satırın (makinenin) skoru $\text{Satır Skoru}_i$:
$$\text{Satır Skoru}_i = \sum_{j=1}^{C} a_{ij} 2^{C - j}$$

$R$ satırlı (makineli) bir matriste $j$. sütunun (parçanın) skoru $\text{Sütun Skoru}_j$:
$$\text{Sütun Skoru}_j = \sum_{i=1}^{R} a_{ij} 2^{R - i}$$

Burada $a_{ij}$ değeri, $i$ makinesinin $j$ parçasını işlemesi durumunda $1$, aksi halde $0$ değerini alır.

#### Algoritmanın Adımları
1. Her satır (makine) için soldan sağa doğru ikili ağırlıklar ($2^{C-1}, 2^{C-2}, \ldots, 2^0$) atanarak ondalık satır skorları hesaplanır.
2. Satırlar, ondalık skorlarına göre azalan sırada yeniden dizilir.
3. Yeniden dizilmiş matriste her sütun (parça) için yukarıdan aşağıya doğru ikili ağırlıklar ($2^{R-1}, 2^{R-2}, \ldots, 2^0$) atanarak ondalık sütun skorları hesaplanır.
4. Sütunlar, ondalık skorlarına göre azalan sırada yeniden dizilir.
5. Herhangi bir adımda matris yapısı değişmeyene kadar (yakınsama sağlanana kadar) 1-4 adımları tekrarlanır.

#### Çözümlü Örnek Walkthrough (DCA ve ROC)
Başlangıç parça-makine ilişkileri (5 makine, 6 parça):
* P1: M1, M3
* P2: M1
* P3: M2, M4, M5
* P4: M1, M3
* P5: M2
* P6: M4, M5

**Adım 1: Başlangıç Matrisi ve Satır Skorlarının Hesaplanması**
Sütun (parça) sayısı $C = 6$ olduğundan ikili ağırlıklar soldan sağa $2^5=32$, $2^4=16$, $2^3=8$, $2^2=4$, $2^1=2$, $2^0=1$'dir.

| Makineler | P1 | P2 | P3 | P4 | P5 | P6 | Hesaplama | Satır Skoru |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- | :---: |
| **M1** | 1 | 1 | 0 | 1 | 0 | 0 | $1(32) + 1(16) + 0(8) + 1(4) + 0(2) + 0(1)$ | **52** |
| **M2** | 0 | 0 | 1 | 0 | 1 | 0 | $0(32) + 0(16) + 1(8) + 0(4) + 1(2) + 0(1)$ | **10** |
| **M3** | 1 | 0 | 0 | 1 | 0 | 0 | $1(32) + 0(16) + 0(8) + 1(4) + 0(2) + 0(1)$ | **36** |
| **M4** | 0 | 0 | 1 | 0 | 0 | 1 | $0(32) + 0(16) + 1(8) + 0(4) + 0(2) + 1(1)$ | **9** |
| **M5** | 0 | 0 | 1 | 0 | 0 | 1 | $0(32) + 0(16) + 1(8) + 0(4) + 0(2) + 1(1)$ | **9** |

**Adım 2: Satırların Azalan Skora Göre Sıralanması**
Makinelerin yeni sırası: **M1 (52)**, **M3 (36)**, **M2 (10)**, **M4 (9)**, **M5 (9)**.

| Sıralı Mak. | P1 | P2 | P3 | P4 | P5 | P6 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **M1** | 1 | 1 | 0 | 1 | 0 | 0 |
| **M3** | 1 | 0 | 0 | 1 | 0 | 0 |
| **M2** | 0 | 0 | 1 | 0 | 1 | 0 |
| **M4** | 0 | 0 | 1 | 0 | 0 | 1 |
| **M5** | 0 | 0 | 1 | 0 | 0 | 1 |

**Adım 3: Sütun Skorlarının Hesaplanması**
Satır (makine) sayısı $R = 5$ olduğundan ikili ağırlıklar yukarıdan aşağıya $2^4=16$, $2^3=8$, $2^2=4$, $2^1=2$, $2^0=1$'dir.

* **P1 Skoru:** $1(16) + 1(8) + 0(4) + 0(2) + 0(1) = 24$
* **P2 Skoru:** $1(16) + 0(8) + 0(4) + 0(2) + 0(1) = 16$
* **P3 Skoru:** $0(16) + 0(8) + 1(4) + 1(2) + 1(1) = 7$
* **P4 Skoru:** $1(16) + 1(8) + 0(4) + 0(2) + 0(1) = 24$
* **P5 Skoru:** $0(16) + 0(8) + 1(4) + 0(2) + 0(1) = 4$
* **P6 Skoru:** $0(16) + 0(8) + 0(4) + 1(2) + 1(1) = 3$

**Adım 4: Sütunların Azalan Skora Göre Sıralanması**
Eşit skorlarda başlangıç sırası korunur. Yeni parça sırası: **P1 (24)**, **P4 (24)**, **P2 (16)**, **P3 (7)**, **P5 (4)**, **P6 (3)**.

| Sıralı Mak. \ Parça | P1 | P4 | P2 | P3 | P5 | P6 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **M1** | 1 | 1 | 1 | 0 | 0 | 0 |
| **M3** | 1 | 1 | 0 | 0 | 0 | 0 |
| **M2** | 0 | 0 | 0 | 1 | 1 | 0 |
| **M4** | 0 | 0 | 0 | 1 | 0 | 1 |
| **M5** | 0 | 0 | 0 | 1 | 0 | 1 |

**Adım 5: Yakınsama Kontrolü**
Yeniden satır skorları hesaplanırsa: M1=56, M3=48, M2=6, M4=5, M5=5. Sıralama değişmemiştir. Sütun skorları hesaplanırsa: P1=24, P4=24, P2=16, P3=7, P5=4, P6=3. Sıralama yine sabittir. Algoritma yakınsamıştır ve durulur.

Matris incelendiğinde net iki hücre bloğu oluşmuştur:
* **Hücre 1:** Makineler {M1, M3} ve Parçalar {P1, P2, P4}
* **Hücre 2:** Makineler {M2, M4, M5} ve Parçalar {P3, P5, P6}

#### Darboğaz Makineler (Bottleneck Machines)
Eğer bir makine birden fazla hücredeki parçaların imalatı için ortak kullanılmak zorundaysa köşegende tam bir blok ayrımı yapılamaz. Bu durumda ortaya çıkan ortak makineler darboğaz yaratır. Çözüm olarak:
1. Darboğaz makinenin hücre sınırına yerleştirilmesi,
2. Ortak kullanılan makineden tesise bir adet daha alınarak hücreler bazında kopyalanması (çoğaltma),
3. Parçaların imalat süreçlerinin veya tasarımlarının değiştirilerek o makineye olan ihtiyacın elimine edilmesi,
4. İlgili işlemler için fason imalat (outsource) yoluna gidilmesi seçenekleri değerlendirilir.

![[07 Ekler/Grafikler/roc-kumeleme.svg]]

---

### 3.2 Hollier Yöntemi (Sıralama Oranı)

İmalat hücreleri belirlendikten sonra, hücre içi malzeme akış yolunu en kısa kılmak amacıyla makinelerin mantıksal sıralamasının (flow sequencing) yapılması gerekir. Hollier Yöntemi, makineler arası taşıma sıklıklarını temel alan bir sezgisel algoritmadır.

#### Matematiksel Gösterim ve Değişkenler
Hücredeki her bir $i$ makinesi için:
* **Giden Toplam Akış ($O_i$ - Outgoing Flow):** $i$ makinesinden diğer makinelere doğru giden toplam parça hareket sayısı.
  $$O_i = \sum_{j=1}^{n} f_{ij}$$
* **Gelen Toplam Akış ($I_i$ - Incoming Flow):** Diğer makinelerden $i$ makinesine doğru gelen toplam parça hareket sayısı.
  $$I_i = \sum_{j=1}^{n} f_{ji}$$
* **Rasyonel Sıralama Oranı ($Ratio_i$):** Giden akışın gelen akışa oranı.
  $$Ratio_i = \frac{O_i}{I_i}$$

*Burada $f_{ij}$, $i$'den $j$'ye olan akış miktarını göstermektedir. Matris asimetriktir.*

#### Algoritma Kuralları
1. Oranı en yüksek olan makine, iş akışının en başına (girişe) yerleştirilir (çünkü çok iş dağıtır, az iş alır).
2. Oranı en düşük olan makine, iş akışının en sonuna (çıkışa) konumlandırılır.
3. Eğer bir makinenin $I_i = 0$ ise oranı $Ratio_i = \infty$ kabul edilir ve bu makine kesinlikle en başa gelir.
4. Eşit oran ($Ratio$) durumunda, gelen akış ($I_i$) değeri daha büyük olan makine, küçük olanın önüne konumlandırılır.

#### Çözümlü Örnek Walkthrough
4 makineli bir hücrede 50 parçanın akış verileriyle oluşturulmuş From-To (Geliş-Gidiş) matrisi şu şekildedir:

| From \ To | M1 | M2 | M3 | M4 |
| :--- | :---: | :---: | :---: | :---: |
| **M1** | 0 | 5 | 0 | 25 |
| **M2** | 30 | 0 | 0 | 15 |
| **M3** | 10 | 40 | 0 | 0 |
| **M4** | 10 | 0 | 0 | 0 |

**Adım 1: Satır ve Sütun Toplamlarının (Giden/Gelen) Hesaplanması**
* M1: $O_1 = 5 + 25 = 30$, $I_1 = 30 + 10 + 10 = 50$
* M2: $O_2 = 30 + 15 = 45$, $I_2 = 5 + 40 = 45$
* M3: $O_3 = 10 + 40 = 50$, $I_3 = 0$
* M4: $O_4 = 10$, $I_4 = 25 + 15 = 40$

**Adım 2: Sıralama Oranlarının Bulunması ve Sıralama**
* $Ratio_1 = 30 / 50 = 0,60$
* $Ratio_2 = 45 / 45 = 1,00$
* $Ratio_3 = 50 / 0 = \infty$
* $Ratio_4 = 10 / 40 = 0,25$

Oranlar büyükten küçüğe sıralandığında: $Ratio_3 (\infty) > Ratio_2 (1,00) > Ratio_1 (0,60) > Ratio_4 (0,25)$.
Optimal makine yerleşim sırası: **M3 → M2 → M1 → M4** olarak elde edilir.

**Adım 3: Hücre İçi Akış Performans Analizi**
Sıralama elde edildikten sonra (M3 → M2 → M1 → M4), akışlar üç kategoride analiz edilir:
1. **İleri Sıralı Akış (Forward Sequential Flow):** Sıralamada hemen sağdaki makineye geçişler ($3 \to 2$, $2 \to 1$, $1 \to 4$).
   * $3 \to 2 = 40$
   * $2 \to 1 = 30$
   * $1 \to 4 = 25$
   * Toplam İleri Sıralı = $40 + 30 + 25 = 95$ parça.
2. **Atlamalı İleri Akış (Forward Skipping Flow):** Sıralamada sağa doğru fakat araya en az bir makine girerek yapılan geçişler ($3 \to 1$, $2 \to 4$).
   * $3 \to 1 = 10$
   * $2 \to 4 = 15$
   * Toplam Atlamalı = $10 + 15 = 25$ parça.
3. **Geriye Akış (Backtracking Flow):** Sıralamada sola doğru yapılan geçişler ($1 \to 2$, $4 \to 1$).
   * $1 \to 2 = 5$
   * $4 \to 1 = 10$
   * Toplam Geriye Dönüş = $5 + 10 = 15$ parça.

Toplam Akış Hareket Sayısı: $T = 95 + 25 + 15 = 135$ parça.

**Yüzdesel Değerlendirme:**
* İleri Sıralı Akış Yüzdesi = $95 / 135 \approx \%70,37$ (Slayt: $\%70,4$)
* Atlamalı İleri Akış Yüzdesi = $25 / 135 \approx \%18,52$ (Slayt: $\%18,5$)
* Geriye Akış Yüzdesi = $15 / 135 \approx \%11,11$ (Slayt: $\%11,1$)

#### Tasarım Yorumu
Hücresel yerleşimlerde her zaman yüksek ileri yönlü akış yüzdesi istenir. Geriye akışlar (backtracking), malzeme taşıma sistemlerinde zıt yönlü tıkanmalara, daha karmaşık konveyör tasarımlarına ve ek ara stoklama ihtiyaçlarına neden olacağı için minimize edilmelidir.

![[07 Ekler/Grafikler/hollier-akis-semasi.svg]]

---

### 3.3 MAG Akış Şiddeti ve From-To Matrisi

Tesis planlamasında, farklı fiziksel özelliklere (boyut, ağırlık, durum) sahip ürünlerin akış yoğunluğunu ortak bir paydada birleştirmek için **MAG (Material Flow Intensity / Malzeme Akış Şiddeti)** taşınabilirlik ölçütü kullanılır.

#### MAG Akış Şiddeti Formülü
Bir parçanın birim taşıma zorluğunu gösteren MAG değeri ($M$):
$$M = A \left[1 + \frac{1}{4}(B + C + D + E)\right]$$

Burada:
* **$A$ (Temel Hacim Katsayısı):** Parçanın fiziksel hacmine göre interpolasyonla belirlenen katsayı.
* **$B$ (Yoğunluk / Ağırlık Katsayısı):** Parçanın birim ağırlığına göre düzeltme katsayısı.
* **$C$ (Biçim Katsayısı):** Düzgünlük, yuvarlaklık gibi geometrik yapı katsayısı.
* **$D$ (Zarar Riski Katsayısı):** Hassaslık ve kırılganlık düzeltmesi.
* **$E$ (Durum / Taşıma Güçlüğü Katsayısı):** Yağlılık, sıcaklık, tutuş zorluğu vb. zorlaştırıcı etkenler.

*Hacim ara değerleri için $A$ katsayısı doğrusal interpolasyonla bulunur:*
$$A = A_1 + \frac{V - V_1}{V_2 - V_1}(A_2 - A_1)$$

Dönemsel (örneğin yıllık veya haftalık) hareket akış şiddeti ($F$):
$$F = M \times Q \times h$$
Burada $Q$ dönemsel üretim miktarı, $h$ ise ilgili rota geçişinin parça başına tekrarlanma sayısıdır.

#### Tam Çözümlü MAG Örneği
Taban çapı 6 cm ($r = 3\text{ cm}$), yüksekliği 17 cm olan silindirik bir kalıp merkezleme mili. Ağırdır ve yoğundur ($B=2$). Uzundur, yuvarlatılmış ve düzensizdir ($C=1$). Kolaylıkla zarar görmez ($D=-1$). Yağlıdır ve elle taşıması zordur ($E=1$). Yılda 50.000 adet üretilmektedir. ($\pi=3$ alınacaktır).

**Adım 1: Hacim ($V$) Hesabı**
$$V = \pi r^2 h = 3 \times 3^2 \times 17 = 459\text{ cm}^3$$

**Adım 2: Hacim Katsayısı ($A$) İnterpolasyonu**
MAG referans tablosunda $150\text{ cm}^3 \to 1,0\text{ MAG}$ ve $1500\text{ cm}^3 \to 3,5\text{ MAG}$ olarak verilmiştir. 459 değeri bu iki aralıktadır:
$$A = 1,0 + \frac{459 - 150}{1500 - 150}(3,5 - 1,0) = 1,0 + \frac{309}{1350}(2,5) \approx 1,5722$$

**Adım 3: Parça Başına MAG Değerinin Hesabı**
$$M = 1,5722 \left[1 + \frac{2 + 1 - 1 + 1}{4}\right] = 1,5722 \times 1,75 \approx 2,7514\text{ MAG}$$

**Adım 4: Yıllık Akış Şiddeti ($F$) Hesabı**
$$F = 2,7514 \times 50.000 = 137.569\text{ MAG/yıl}$$

> [!NOTE]
> **Yuvarlama Ayrımı:** Slayt örneğinde $A \approx 1,57$ ve $M \approx 2,74$ alınmış olup yıllık akış $137.000$ MAG/yıl olarak hesaplanmıştır. Matematiksel olarak tam interpolasyonla hassas sonuç $137.569$ MAG/yıl'dır. Sınavda bu yuvarlama kabulleri belirtilmelidir.

#### Ürün Rotalarından Yönlü From-To Matrisi Kurulması
MAG gibi ortak akış birimleri veya doğrudan taşıma miktarları kullanılarak, ürünlerin üretim rotaları üzerinden yönlü bir From-To matrisi oluşturulur. Sadece **ardışık geçişler** (rota üzerindeki peş peşe gelen departman çiftleri) matrise eklenir.

**Örnek Rotalar ve Akış Verileri:**
* P1: Günlük Miktar = 30, Rota = A-C-B-D-E, Eşdeğer Taşıma Faktörü = 1
* P2: Günlük Miktar = 12, Rota = A-B-D-E, Eşdeğer Taşıma Faktörü = 1
* P3: Günlük Miktar = 7, Rota = A-C-D-B-E, Eşdeğer Taşıma Faktörü = 2 (boyutu 2 kat büyük, eşdeğer akış = $7 \times 2 = 14$)

**Adım Adım Geçişlerin Belirlenmesi:**
* **A → B:** P2 = 12
* **A → C:** P1 + P3 = $30 + 14 = 44$
* **B → D:** P1 + P2 = $30 + 12 = 42$
* **B → E:** P3 = 14 *(Not: Bu akış slayt 84'teki tablolarda gözden kaçırılarak 0 yazılmıştır. Doğru analizde yer almalıdır.)*
* **C → B:** P1 = 30
* **C → D:** P3 = 14
* **D → B:** P3 = 14
* **D → E:** P1 + P2 = $30 + 12 = 42$

**Yönlü Akış Matrisi:**
| From \ To | A | B | C | D | E |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **A** | - | 12 | 44 | 0 | 0 |
| **B** | 0 | - | 0 | 42 | 14 |
| **C** | 0 | 30 | - | 14 | 0 |
| **D** | 0 | 14 | 0 | - | 42 |
| **E** | 0 | 0 | 0 | 0 | - |

**Toplam Akış Matrisi (Yönsüz / Simetrikleştirilmiş):**
Departmanlar arası yön gözetmeksizin toplam akışları ($F_{ij} = f_{ij} + f_{ji}$) bulmak için üst üçgen veya birleşik matris kurulur. Örneğin B ile D arasındaki toplam akış: $f_{BD} + f_{DB} = 42 + 14 = 56$ olur.
* B-D: 56
* A-C: 44
* D-E: 42
* B-C: 30
* C-D: 14
* A-B: 12
* B-E: 14

![[07 Ekler/Grafikler/from-to-matrisi.svg]]

---

### 3.4 Faaliyet İlişki Diyagramı (REL Chart) ve Alan Hesabı

Tesis planlamasında nicel akış verilerinin (malzeme akışı) yanında, bilgi akışı, ortak ekipman kullanımı ve kirlilik/gürültü gibi nitel etkenler de yerleşim tasarımını şekillendirir. Bu nitel yakınlık gereksinimleri **REL Chart (Relationship Chart / Faaliyet İlişki Şeması)** kullanılarak modellenir.

#### Yakınlık Dereceleri (Closeness Ratings) ve Sayısal Skorları
Muther (1973) tarafından önerilen yakınlık ilişkisi kodları, sayısal puanları ve genel frekans dağılımları şu şekildedir:

| Kod | İlişkinin Önemi | Puanı | Kabul Edilen Dağılım (%) | Standart Gerekçe Kodları |
| :---: | :--- | :---: | :---: | :--- |
| **A** | Kesinlikle Gerekli (Absolutely Necessary) | 4 | %5 | 01: Ortak Ekipman Kullanımı |
| **E** | Özellikle Önemli (Especially Important) | 3 | %10 | 02: Malzeme Hareketi |
| **I** | Önemli (Important) | 2 | %15 | 03: Personel Hareketi |
| **O** | Sıradan Yakınlık (Ordinary Closeness) | 1 | %20 | 04: Denetim / Gözetim |
| **U** | Önemsiz (Unimportant) | 0 | %50 | 05: Ortak Evrak / Bilgi Akışı |
| **X** | Arzu Edilmez (Undesirable) | -1 | - | 06: Gürültü, Toz, Yangın Riski |
| **XX** | Kesinlikle İstenmez (Extremely Undesirable) | -2 ila -4 | - | 07: İletişim Sıklığı |

#### Alan Hesabı ve Alan Katsayısı Yöntemi
Tesis alan planlamasında, her bir $j$ donanım türü için net taban alanı ($A_{\text{tb},j}$), makine sayısı ($M_j$) ve bakım/operasyonel çalışma boşluklarını içeren alan katsayısı ($K_{A,j}$) kullanılarak net **İşletme Donanım Alanı ($A_{\text{id}}$)** hesaplanır:
$$A_{\text{id}} = \sum_j M_j \cdot K_{A,j} \cdot A_{\text{tb},j}$$

İşletme donanım alanına ek olarak, tesis genelinde paylaşılan veya destekleyici nitelikteki diğer alan gereksinimleri (ara depolar, kalite kontrol, serbest alan ve ulaşım yolları) belirli katsayılarla $A_{\text{id}}$ üzerinden sisteme dahil edilir:
* **Ara Depo Alanı ($A_{\text{ad}}$):** $A_{\text{id}} \times 0,20$
* **Kalite Kontrol Alanı ($A_{\text{kk}}$):** $A_{\text{id}} \times 0,13$
* **Serbest Alan ($A_{\text{sa}}$):** $A_{\text{id}} \times 0,18$
* **Ulaşım Yolları ($A_{\text{uy}}$):** $A_{\text{id}} \times 0,25$

Tüm bu destek kalemlerinin dahil edildiği toplam alan gereksinimi ($A_{\text{top}}$):
$$A_{\text{top}} = A_{\text{id}} (1 + 0,20 + 0,13 + 0,18 + 0,25) = 1,76 \cdot A_{\text{id}}$$

**Çözümlü Alan Katsayısı Örneği:**
Bir tesiste 20 adet 10 m² (katsayısı 3,11), 15 adet 13 m² (katsayısı 3,00) ve 5 adet 7 m² (katsayısı 3,42) tezgah bulunmaktadır.
$$A_{\text{id}} = (20 \times 10 \times 3,11) + (15 \times 13 \times 3,00) + (5 \times 7 \times 3,42) = 622 + 585 + 119,7 = 1326,7\text{ m}^2$$
$$A_{\text{top}} = 1,76 \times 1326,7 = 2334,992 \approx 2335,0\text{ m}^2$$

#### Kritik Akademik ve Sınav Uyarıları
1. **Sınıf Sınırlarındaki Çakışmalar:** Slayt 84-85'te akış miktarlarını yakınlık ilişkilerine çevirirken sınıf aralıkları `0-11` (U) ve `11-22` (O) gibi çakışan sınırlar içermektedir. Bu tür çakışmaları önlemek için aralıkların ayrık tanımlanması gerekir (örn. `0-11` U, `12-22` O).
2. **Akışsız Çiftlerin Doğrudan X Yapılması Hatası:** Slaytlarda akışsız departman çiftleri doğrudan `X` (Arzu Edilmez) ilişkisi ile kodlanmıştır. Oysa akışın sıfır olması tek başına olumsuz bir yakınlık gerekçesi değildir; bu durum sadece `U` (Önemsiz) ilişkisini gösterir. `X` kodunun verilmesi için gürültü, toz, kimyasal tehlike gibi olumsuz bir gerekçe (örneğin 06 gerekçe kodu) bulunmalıdır. Sınavda bu ayrım net şekilde yazılmalıdır.

![[07 Ekler/Diyagramlar/faaliyet-iliski-diyagrami.svg]]

---

## Bölüm 4: Yerleşim Tasarımı ve İyileştirme Algoritmaları

Tesis içi yerleşim tasarımı, departmanların fiziksel sınırlarını ve konumlarını belirleyen süreçtir. Yerleşim problemleri çoğunlukla NP-hard sınıfında yer aldığından, çözüm için matematiksel modellerin yanı sıra bilgisayarlı sezgisel ve meta-sezgisel algoritmalar kullanılmaktadır. Bu algoritmalar temel olarak "Kurucu (Construction)" ve "Geliştirici (Improvement)" olmak üzere iki gruba ayrılır.

### 4.1 Süreç Yerleşim Taşıma Maliyeti ve SLP

Sürece göre yerleşim tasarımlarında temel amaç, departmanlar arasındaki malzeme taşıma maliyetini en aza indirmektir.

#### Toplam Taşıma Maliyeti Amaç Fonksiyonu

Bir tesis yerleşiminin toplam malzeme taşıma maliyeti $Z$ aşağıdaki formülle hesaplanır:

$$Z = \sum_{i=1}^{n} \sum_{j=1}^{n} f_{ij} \cdot d_{p(i), p(j)} \cdot c_{ij}$$

Burada:
*   $n$: Tesisteki toplam departman veya iş merkezi sayısı.
*   $i, j$: Departman indisleri.
*   $f_{ij}$: $i$ departmanından $j$ departmanına birim dönemdeki malzeme akış miktarı (yük/hafta, gezi/gün vb.).
*   $d_{p(i), p(j)}$: $i$ departmanının atandığı $p(i)$ konumu ile $j$ departmanının atandığı $p(j)$ konumu arasındaki mesafe (genellikle dik doğrusal - *rectilinear* mesafe kullanılır).
*   $c_{ij}$: $i$ departmanından $j$ departmanına birim yükü birim mesafe taşımanın maliyeti (genellikle $c_{ij} = 1$ kabul edilir).

#### Değerlendirme Skorları
*   **Komşuluk Esaslı Puan (Adjacency Score):** Nitel ilişki matrislerine (REL Chart) dayanır. Birbirine sınırdaş (komşu) olan departmanların yakınlık derecesi katsayılarının (A, E, I, O vb.) sayısal değerlerinin toplamıdır. Bu skorun maksimize edilmesi hedeflenir.
*   **Uzaklık Esaslı Puan (Distance Score):** Nicel akış matrislerine dayanır. Departmanların ağırlık merkezleri arasındaki mesafe ile akış şiddetlerinin çarpımlarının toplamıdır (yukarıdaki $Z$ maliyet fonksiyonu). Bu skorun minimize edilmesi hedeflenir.

#### Sistematik Yerleşim Planlama (SLP - Systematic Layout Planning)
Richard Muther tarafından geliştirilen SLP, nitel ve nicel ilişkileri entegre eden 10 adımlı, disiplinli bir planlama prosedürüdür:
1.  **Girdi Verileri ve Faaliyetlerin Belirlenmesi:** P (Ürün), Q (Miktar), R (Rota), S (Destek Servisleri) ve T (Zaman) verilerinin toplanması.
2.  **Malzeme Akış Analizi (Flow of Materials):** Ürün rotaları üzerinden From-To matrislerinin oluşturulması.
3.  **Faaliyet İlişkileri Analizi (Activity Relationships):** Nitel REL şemasının çıkarılması.
4.  **İlişki Diyagramı (Relationship Diagram):** Departmanlar arasındaki yakınlık bağlarının çizgisel olarak görselleştirilmesi.
5.  **Alan Gereksinimleri (Space Requirements):** Makine boyutları ve operasyonel boşluklara göre alan ihtiyaçlarının hesabı.
6.  **Varolan Alan (Space Available):** Tesis binasının fiziksel sınırlarının ve kullanılabilir alanının belirlenmesi.
7.  **Alan İlişki Diyagramı (Space Relationship Diagram):** İlişki diyagramındaki bloklara gerçek alan boyutlarının giydirilmesi.
8.  **Düzenleyici Hususların Değerlendirilmesi (Modifying Considerations):** Malzeme taşıma sistemleri, depolama pratikleri ve güvenlik gibi faktörlerin entegrasyonu.
9.  **Pratik Kısıtlar (Practical Limitations):** Bütçe, yasal mevzuatlar ve kolon yerleşimleri gibi kısıtların yansıtılması.
10. **Alternatiflerin Değerlendirilmesi ve Seçim (Evaluation & Selection):** Geliştirilen alternatif yerleşim planlarının puanlama veya maliyet analiziyle karşılaştırılarak nihai planın seçilmesi.

---

### 4.2 İkili Yer Değiştirme Yöntemi ve CRAFT Algoritması

CRAFT (Computerized Relative Allocation of Facilities Technique), mevcut bir başlangıç yerleşim planını geliştirmek için kullanılan hücresel tabanlı bir iyileştirme (improvement) algoritmasıdır.

#### Departman Değişim (Swap) Kuralları
CRAFT, iki departmanın yerini değiştirebilmek için şu kurallardan en az birinin sağlanmasını şart koşar:
1.  **Eşit Alana Sahip Olma:** İki departmanın alan büyüklükleri aynı ise, tesisin diğer departmanlarının geometrik yapısını bozmadan doğrudan yer değiştirebilirler.
2.  **Ortak Sınıra (Border) Sahip Olma:** Departmanların alanları farklı olsa bile ortak bir sınır paylaşıyorlarsa (komşu iseler), sınır çizgileri kaydırılarak yer değiştirmeleri gerçekleştirilebilir.

Bu kuralların amacı, yer değişimleri sırasında departmanların geometrik bütünlüğünün bozulmasını (parçalanmış veya tek tek kalmış adacıklar oluşmasını) önlemektir.

#### CRAFT Algoritmasının Çalışma Mantığı
1.  **Ağırlık Merkezlerinin Tespiti:** Mevcut yerleşimin grid yapısı üzerinde her departmanın ağırlık merkezi koordinatları ($x_i, y_i$) hesaplanır.
2.  **Uzaklık Matrisinin Çıkarılması:** Merkez koordinatlar arasındaki dik doğrusal (rectilinear) mesafeler hesaplanır: $d_{ij} = |x_i - x_j| + |y_i - y_j|$.
3.  **Aday Çiftlerin Belirlenmesi:** Eşit alanlı veya ortak sınırlı olan tüm olası ikili (veya üçlü) departman çiftleri listelenir.
4.  **Tahmini Maliyet Değişimin Hesaplanması:** Aday departmanlar yer değiştirdiğinde, sınırları fiilen çizmeden, sadece ağırlık merkezlerinin yer değiştireceği varsayımıyla yeni yerleşim maliyeti tahmin edilir.
5.  **En İyi Değişimin Seçilmesi:** En fazla tahmini tasarrufu sağlayan departman çifti seçilir.
6.  **Sınırlar Fiilen Taşınarak Değişimin Uygulanması:** Grid üzerinde departman sınırları fiilen kaydırılarak yer değişim uygulanır.
7.  **Gerçek Merkezlerin ve Gerçek Maliyetin Hesabı:** Oluşan yeni yerleşim için ağırlık merkezleri yeniden hesaplanır ve gerçek maliyet bulunur. Bu aşamada yeni iterasyon başlar. İyileşme durana kadar süreç tekrarlanır.

#### Çözümlü Örnek Walkthrough (5 Departman, 5 Konum)

Beş departman (1-5) ve beş konum (A-E) için verilmiş olan mesafe ve akış matrislerini inceleyelim.

**Mesafe Matrisi ($d_{ij}$ - Konumlar Arası Mesafe):**
| Konumlar | A | B | C | D | E |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **A** | 0 | 5 | 6 | 7 | 8 |
| **B** | 5 | 0 | 7 | 8 | 10 |
| **C** | 6 | 7 | 0 | 6 | 5 |
| **D** | 7 | 8 | 6 | 0 | 7 |
| **E** | 8 | 10 | 5 | 7 | 0 |

**Orijinal İş Akış Matrisi ($f_{ij}$ - Departmanlar Arası Akış - Slayt 74):**
*(Not: Slayt 74'teki tablonun sütun başlıkları A, B, C, D, E olarak yazılmıştır ancak bunlar aslında 1, 2, 3, 4, 5 departman numaralarıdır.)*
| Departmanlar | 1 | 2 | 3 | 4 | 5 | Satır Toplamı |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **1** | 0 | 250 | 180 | 280 | 80 | **790** |
| **2** | 100 | 0 | 175 | 40 | 450 | **765** |
| **3** | 240 | 315 | 0 | 180 | 75 | **810** |
| **4** | 420 | 40 | 120 | 0 | 245 | **825** |
| **5** | 440 | 30 | 15 | 105 | 0 | **590** |
| **Sütun Toplamı** | **1200** | **635** | **490** | **605** | **850** | **3780 (Matris Toplam Akışı)** |

**Slayt 73'teki Normalize Edilmiş Akış Matrisi ($F'_{ij}$):**
CRAFT ders sunumunda, başlangıç yerleşimi `1A, 2B, 3C, 4D, 5E` iken, akış matrisi olarak şu değerler verilmiştir. Bu matris, orijinal akışların başlangıç mesafelerine bölünmesiyle ($F'_{ij} = f_{ij} / d_{\text{başlangıç}}(i,j)$) elde edilmiş olan bir ara matristir:
| Departmanlar | 1 | 2 | 3 | 4 | 5 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **1** | 0 | 50 | 30 | 40 | 10 |
| **2** | 20 | 0 | 25 | 5 | 45 |
| **3** | 40 | 45 | 0 | 30 | 15 |
| **4** | 60 | 5 | 20 | 0 | 35 |
| **5** | 55 | 3 | 3 | 15 | 0 |

##### Adım 1: Başlangıç Maliyeti ($Z_0$) Hesabı
Başlangıç yerleşimi `1A, 2B, 3C, 4D, 5E` şeklindedir (1. departman A'da, 2. B'de vb.). 
Slayt sistematiğine göre, maliyet formülü $Z = \sum_{i,j} F'_{ij} \cdot d_{p(i), p(j)}$ şeklinde işletilir. Başlangıçta $p(i)$ konumları doğrudan $i$'nin ilk konumları olduğundan, $d_{p(i), p(j)}$ mesafeleri başlangıç mesafelerine eşittir. Dolayısıyla ilk maliyet doğrudan orijinal akışların toplamına eşit çıkar:

$$Z_0 = \sum_{i=1}^{5} \sum_{j=1}^{5} F'_{ij} \cdot d_{\text{başlangıç}}(i,j) = \sum_{i=1}^{5} \sum_{j=1}^{5} f_{ij} = 3780\text{ birim}$$

*(Slayt 74'te 3.780 olarak yazılan bu değer, 3.78 değil, binlik basamak ayracı kullanılarak yazılmış 3780 birimdir.)*

##### Adım 2: Departman 1 ve 3 Yer Değişimi (1. İterasyon)
Eğer 1 ve 3 departmanları yer değiştirirse, konum atamaları `3A, 2B, 1C, 4D, 5E` olur.
Yeni konum atamalarına göre mesafeler güncellenir. Maliyet hesabı ($Z = \sum_{i,j} F'_{ij} \cdot d_{\text{new}}(i,j)$) satır satır şu şekilde gerçekleştirilir:

*   **1. Departman Satırı (C Konumunda):**
    *   $F'_{12} \cdot d(C,B) = 50 \times 7 = 350$
    *   $F'_{13} \cdot d(C,A) = 30 \times 6 = 180$
    *   $F'_{14} \cdot d(C,D) = 40 \times 6 = 240$
    *   $F'_{15} \cdot d(C,E) = 10 \times 5 = 50$
    *   *Satır 1 Toplamı:* $350 + 180 + 240 + 50 = 820$
*   **2. Departman Satırı (B Konumunda):**
    *   $F'_{21} \cdot d(B,C) = 20 \times 7 = 140$
    *   $F'_{23} \cdot d(B,A) = 25 \times 5 = 125$
    *   $F'_{24} \cdot d(B,D) = 5 \times 8 = 40$
    *   $F'_{25} \cdot d(B,E) = 45 \times 10 = 450$
    *   *Satır 2 Toplamı:* $140 + 125 + 40 + 450 = 755$
*   **3. Departman Satırı (A Konumunda):**
    *   $F'_{31} \cdot d(A,C) = 40 \times 6 = 240$
    *   $F'_{32} \cdot d(A,B) = 45 \times 5 = 225$
    *   $F'_{34} \cdot d(A,D) = 30 \times 7 = 210$
    *   $F'_{35} \cdot d(A,E) = 15 \times 8 = 120$
    *   *Satır 3 Toplamı:* $240 + 225 + 210 + 120 = 795$
*   **4. Departman Satırı (D Konumunda):**
    *   $F'_{41} \cdot d(D,C) = 60 \times 6 = 360$
    *   $F'_{42} \cdot d(D,B) = 5 \times 8 = 40$
    *   $F'_{43} \cdot d(D,A) = 20 \times 7 = 140$
    *   $F'_{45} \cdot d(D,E) = 35 \times 7 = 245$
    *   *Satır 4 Toplamı:* $360 + 40 + 140 + 245 = 785$
*   **5. Departman Satırı (E Konumunda):**
    *   $F'_{51} \cdot d(E,C) = 55 \times 5 = 275$
    *   $F'_{52} \cdot d(E,B) = 3 \times 10 = 30$
    *   $F'_{53} \cdot d(E,A) = 3 \times 8 = 24$
    *   $F'_{54} \cdot d(E,D) = 15 \times 7 = 105$
    *   *Satır 5 Toplamı:* $275 + 30 + 24 + 105 = 434$

**Yeni Toplam Maliyet:**
$$Z_{\text{yeni}} = 820 + 755 + 795 + 785 + 434 = 3589\text{ birim}$$

Slayt 81'de yer alan ve 10 farklı ikili yer değişimini tarayan ilk iterasyon tablosu bu şekilde doldurulur. Minimum maliyeti veren **1-3 değişimi (3589)** seçilerek 2. iterasyona bu düzenle geçilir.

##### Adım 3: İkinci İterasyon ve Slayt Hata Doğrulaması
2. İterasyonda başlangıç düzeni `3A, 2B, 1C, 4D, 5E` (maliyet = 3589) olarak alınır. Yapılan tüm ikili aramalar sonucunda en iyi gelişme, 4 ve 5 departmanlarının yer değiştirmesiyle (`3A, 2B, 1C, 5D, 4E`) elde edilir.

> [!WARNING]
> **Slayt 83 Yazım Hatası:** Ders slaytlarının 83. sayfasında, bu yer değişimi sonucunda minimum maliyetin **3.310** birim olduğu iddia edilmiştir. Oysa bu yerleşim için yukarıdaki yöntemle yapılan bağımsız matematiksel hesaplama (ve Python simülasyonu doğrulaması) maliyetin tam olarak **3510** birim olduğunu göstermektedir. Sınavda bu ayrım belirtilerek, hesaplanan gerçek değerin **3510** olduğu gösterilmelidir.

---

### 4.3 MCRAFT, BLOCPLAN ve LOGIC

CRAFT algoritmasının belirli varsayımlarını (komşuluk zorunluluğu, blok şekillerinin bozulması vb.) aşmak amacıyla daha gelişmiş bilgisayarlı algoritmalar tasarlanmıştır.

#### MCRAFT (Micro-CRAFT)
*   **Bitişik Olmayan Değişimler:** Bitişik olmayan veya eşit alana sahip olmayan departmanların da yer değiştirmesine izin verir.
*   **Süpürme Deseni (Sweep Pattern):** Bir yerleşim vektörüne dayanarak, alanı doldurmak için yılan gibi kıvrılan (zigzag) bir süpürme çizgisi kullanır. İki departman yer değiştirdiğinde, arkalarından gelen diğer departmanlar süpürme eğrisi boyunca otomatik olarak kaydırılır (shifting) ve alan sınırları yeniden çizilir.
*   **Mesafe Metrikleri:** Öklid (Euclidean) veya kullanıcının tanımladığı farklı mesafe ölçütlerini kullanabilir.

#### BLOCPLAN
*   **Melez Yapı:** Hem sıfırdan yerleşim kurabilen (construction) hem de mevcut yerleşimi iyileştirebilen (improvement) melez bir algoritmadır.
*   **Bant Yapısı:** Bölümleri 2 veya 3 bant (strip) halinde yerleştirir. Tüm bölümler dikdörtgen geometrisini korur.
*   **Yakınlık Kodlaması:** From-To matrisindeki sayısal akışları, en yüksek akışı baz alıp dilimleyerek nitel A, E, I, O, U ilişkilerine dönüştürür.
*   **İki Yönlü Puanlama:**
    1.  *Komşuluk Esaslı Puan (Etkinlik Oranı - Efficiency Rating):* Sınırdaş olan departmanların sayısal yakınlık derecelerinin ($A=10, E=5, I=2, O=1, U=0, X=-10$) toplamı.
    2.  *Uzaklık Esaslı Puan (REL-DIST Score):* Sayısal yakınlık oranları ile departman ağırlık merkezleri arasındaki dik doğrusal uzaklıkların çarpımlarının toplamıdır:
        $$\text{REL-DIST Score} = \sum_{i < j} R_{ij} \cdot d_{ij}$$

#### LOGIC (Layout Optimization with Guillotine Induced Cuts)
*   **Giyotin Kesimi (Guillotine Cuts):** Dikdörtgen şeklindeki bina alanını, uçtan uca kesintisiz dikey (V) veya yatay (H) çizgilerle (giyotin gibi) dilimleyerek yerleşim planı oluşturur. Bu sayede tüm departmanların dikdörtgen kalması garanti edilir.
*   **Kesim Ağacı (Cut Tree):** Arama uzayı bir ikili ağaç yapısıyla temsil edilir. Ağacın iç düğümleri kesim yönlerini (V veya H), yaprak düğümleri ise departmanları gösterir.
*   **Kapsayıcılık:** Tüm BLOCPLAN yerleşimleri aynı zamanda birer LOGIC yerleşimidir. LOGIC'in çözüm kümesi BLOCPLAN'ı kapsar.

#### Pedagojik Örnek Walkthrough (LOGIC Alan Bölünmesi)

$12 \times 10$ boyutlarında toplam 120 m² alana sahip bir bina verilsin. Bölümlerin alan gereksinimleri:
*   $A = 20\text{ m}^2$, $B = 30\text{ m}^2$, $C = 28\text{ m}^2$, $D = 42\text{ m}^2$.

Kesim ağacı yapısı: `V(H(A,B), H(C,D))` olsun.

##### Adım 1: Kök Düğüm `V` (Dikey Kesim)
Ağacın kökü `V` olduğundan, bina dikey olarak sol ve sağ olmak üzere iki ana bloğa bölünür.
*   **Sol Çocuk Alanı (A+B):** $20 + 30 = 50\text{ m}^2$
*   **Sağ Çocuk Alanı (C+D):** $28 + 42 = 70\text{ m}^2$
*   **Yükseklik (Sabit):** $10\text{ m}$
*   **Sol Çocuğun Genişliği:** $W_{\text{sol}} = \text{Alan} / \text{Yükseklik} = 50 / 10 = 5\text{ m}$
*   **Sağ Çocuğun Genişliği:** $W_{\text{sağ}} = 12 - 5 = 7\text{ m}$ (veya $70 / 10 = 7\text{ m}$)

##### Adım 2: Sol Alt Ağaç `H(A,B)` (Yatay Kesim)
Sol blok ($5\times10$ boyutlarında) yatay olarak ikiye bölünür.
*   **Genişlik (Sabit):** $5\text{ m}$
*   **A Bölümünün Yüksekliği:** $H_A = \text{Alan}_A / \text{Genişlik} = 20 / 5 = 4\text{ m}$
*   **B Bölümünün Yüksekliği:** $H_B = \text{Alan}_B / \text{Genişlik} = 30 / 5 = 6\text{ m}$
*   *Kontrol:* $4 + 6 = 10\text{ m}$ (yükseklik doğrulandı).

##### Adım 3: Sağ Alt Ağaç `H(C,D)` (Yatay Kesim)
Sağ blok ($7\times10$ boyutlarında) yatay olarak ikiye bölünür.
*   **Genişlik (Sabit):** $7\text{ m}$
*   **C Bölümünün Yüksekliği:** $H_C = \text{Alan}_C / \text{Genişlik} = 28 / 7 = 4\text{ m}$
*   **D Bölümünün Yüksekliği:** $H_D = \text{Alan}_D / \text{Genişlik} = 42 / 7 = 6\text{ m}$
*   *Kontrol:* $4 + 6 = 10\text{ m}$ (yükseklik doğrulandı).

**Oluşan Blok Boyutları:**
A ($5\times4$), B ($5\times6$), C ($7\times4$), D ($7\times6$).

##### Adım 4: D ve A Departmanlarının Yer Değişimi (Swap)
Yer değişimi sonrası yeni kesim ağacı: `V(H(D,B), H(C,A))` haline gelir. Boyutları yeniden hesaplayalım:
*   **Yeni Sol Çocuk Alanı (D+B):** $42 + 30 = 72\text{ m}^2$
*   **Yeni Sağ Çocuk Alanı (C+A):** $28 + 20 = 48\text{ m}^2$
*   **Yeni Sol Genişlik:** $W_{\text{sol}} = 72 / 10 = 7,2\text{ m}$
*   **Yeni Sağ Genişlik:** $W_{\text{sağ}} = 12 - 7,2 = 4,8\text{ m}$
*   **Sol Blokta Yatay Kesim `H(D,B)` (Genişlik = 7,2 m):**
    *   $H_D = 42 / 7,2 = 5,833\text{ m}$
    *   $H_B = 30 / 7,2 = 4,167\text{ m}$
*   **Sağ Blokta Yatay Kesim `H(C,A)` (Genişlik = 4,8 m):**
    *   $H_C = 28 / 4,8 = 5,833\text{ m}$
    *   $H_A = 20 / 4,8 = 4,167\text{ m}$

**Yeni Blok Boyutları:**
D ($7,2 \times 5,833$), B ($7,2 \times 4,167$), C ($4,8 \times 5,833$), A ($4,8 \times 4,167$). Kesim ağacındaki basit bir yer değişimi, tüm koordinat sınırlarını ve departman boyutlarını dinamik olarak otomatik güncellemiştir.

---

### 4.4 CORELAP, ALDEP ve MULTIPLE

Bu algoritmalar, faaliyet ilişkilerini ve alanları kullanarak yerleşim planlarının sıfırdan oluşturulması veya çok katlı binalarda optimize edilmesi süreçlerini yönetir.

#### CORELAP (Computerized Relationship Layout Planning)
Bölümleri ilişki derecelerine göre adım adım yerleşim alanına ekleyen kurucu (construction) bir algoritmadır. Tesis sınırları serbesttir.
*   **Giriş Öncelik Sıralaması (Placement Sequence):**
    1.  Tüm departmanların **Toplam Yakınlık Derecesi (TCR)** hesaplanır. En büyük TCR değerine sahip departman yerleşime giren ilk bölüm olur.
    2.  Yerleşime girmiş bölümlerle sırasıyla en yüksek (A, E, I, O vb.) ilişkiye sahip olan departmanlar seçilir. Eşitlik halinde TCR değeri büyük olan, o da eşitse alanı büyük olan departman öncelik kazanır.
    3.  Negatif ilişkili (X) departmanlar yerleşim sırasının en sonuna itilir.
*   **Grid Yerleştirme Kuralları (Placing Rating - PR):**
    *   Bölümün yerleşeceği konum, aday bölümün komşu olacağı yerleşmiş bölümlerle olan ilişkilerinin sayısal katsayıları toplamına (PR puanı) göre belirlenir.
    *   **Tam komşuluk (Adjacent):** Kenardan temas eden komşuluklarda ilişki puanının tamamı eklenir.
    *   **Yarı komşuluk (Touching):** Sadece köşeden temas eden durumlarda puanın yarısı hesaba katılır.
    *   İlk seçilen bölüm merkeze konur, sonra gelenler saat yönünün tersi yönünde dış çeperi tarayarak en yüksek PR veren konuma yerleştirilir.

#### ALDEP (Automated Layout Design Program)
CORELAP gibi kurucu bir algoritmadır ancak deterministik değildir, rastgelelik barındırır.
*   **Alternatif Üretimi:** Giriş sırasını ve ilk yerleştirilen bölümleri rastgele seçerek çok sayıda alternatif yerleşim taslağı üretir.
*   **Süpürme Dolgusu (Sweep-Filling):** Belirlenmiş bir bant genişliği (süpürme genişliği) parametresine göre bölümleri yukarı-aşağı veya sağa-sola doğru yılan kıvrımları çizerek gridlere doldurur.
*   **Değerlendirme Eşiği (Cutoff):** Kullanıcının belirlediği minimum kabul edilebilir bir ilişki katsayısına (örneğin sadece "E" ve üzeri dereceler) göre yerleşimler puanlanır ve en iyiler raporlanır.

#### MULTIPLE (Multi-floor Plant Layout Evaluation)
Çok katlı endüstriyel tesislerin yerleşimini tasarlamak ve geliştirmek için geliştirilmiş bir algoritmadır.
*   **Alan Doldurma Eğrisi (Space-Filling Curve - SFC):** 2 boyutlu grid yerleşimini tek boyutlu bir yerleşim vektörüne dönüştürür. Bu matematiksel haritalandırma sayesinde, komşu olmayan ve eşit büyüklükte olmayan departmanlar arasında dahi ikili yer değişimlerinin gerçekleştirilmesine olanak tanır.
*   **Çok Katlı Yapı Entegrasyonu:** Katlar arası dikey taşımaların (asansörler, spiral konveyörler) maliyet katsayılarını da amaç fonksiyonuna dahil eder.
*   **Sınır Masajı (Massage):** SFC çıktısı olan yerleşim planlarının sınırlarında pürüzler veya girintili çıkıntılı yapılar oluşabilir. Bu nedenle nihai yerleşimi elde etmek için mühendislik "masajı" (sınır düzgünleştirme düzeltmeleri) uygulanması gerekir.

---

## Bölüm 5: Tesis Konumu Belirleme

Tesis konumunu belirleme kararları, hem yeni kurulacak bir tesisin (fabrika, depo, istasyon vb.) coğrafi veya düzlemsel yerinin tayin edilmesini hem de mevcut ve yeni tesisler arasındaki koordinasyonu ve atamaları kapsar. Bu kararlar sürekli düzlem modelleri ve kesikli matematiksel programlama modelleri olmak üzere iki ana çerçevede incelenir.

### 5.1 Tek Tesis Minisum (Ağırlıklı Medyan Yöntemi)

#### Amaç ve Mesafe Formülasyonu
Minisum konum problemi, yeni kurulacak tek bir tesisin, konumları önceden bilinen mevcut tesislere/müşterilere olan ağırlıklı mesafelerinin toplamını minimize etmeyi amaçlar. Mesafe ölçütü olarak dik doğrusal (rectilinear / Manhattan) uzaklık kullanıldığında amaç fonksiyonu aşağıdaki şekilde tanımlanır:

$$\min f(x,y) = \sum_{i=1}^{m} w_i \left( |x - a_i| + |y - b_i| \right)$$

Burada:
*   $(x, y)$: Kurulacak yeni tesisin koordinatları (karar değişkenleri).
*   $(a_i, b_i)$: Mevcut $i$. tesisin koordinatları ($i = 1, \ldots, m$).
*   $w_i$: Yeni tesis ile mevcut $i$. tesis arasındaki ağırlık (sevkiyat sıklığı, talep miktarı, maliyet katsayısı vb.).

Manhattan uzaklık ölçütünün matematiksel yapısı gereği, amaç fonksiyonu $x$ ve $y$ bileşenlerine göre doğrusal olarak ayrıştırılabilir:

$$f(x, y) = f(x) + f(y) = \sum_{i=1}^{m} w_i |x - a_i| + \sum_{i=1}^{m} w_i |y - b_i|$$

Bu özellik sayesinde, optimum koordinatlar ($x^*$ ve $y^*$) birbirlerinden tamamen bağımsız olarak iki ayrı tek boyutlu problem şeklinde çözülebilir.

#### Ağırlıklı Medyan Sıralama Yöntemi
Optimal koordinatları belirlemek için kullanılan en yaygın ve hızlı yöntem Ağırlıklı Medyan (Weighted Median) sıralama prosedürüdür. $X$ ekseni için adımlar şu şekildedir:
1.  Mevcut tesislerin $x$-koordinatları ($a_i$) küçükten büyüğe (artan sırada) sıralanır.
2.  Sıralı her koordinatın karşısına ilişkili ağırlık ($w_i$) yazılır.
3.  Koordinatlar boyunca kümülatif ağırlıklar ($\sum w_i$) hesaplanır.
4.  Kümülatif ağırlık değeri, toplam ağırlığın yarısını ($\sum_{i=1}^{m} w_i / 2$) **ilk kez aşan** veya bu değere **eşit olan** ilk koordinat optimal $x^*$ koordinatı olarak seçilir.

Aynı adımlar mevcut tesislerin $y$-koordinatları ($b_i$) kullanılarak tekrarlanır ve optimal $y^*$ elde edilir.

#### Eş-Yarı Medyan (Tie-Breaking) Sınır Durumu
Eğer koordinatlar boyunca kümülatif ağırlık toplanırken, bir koordinat noktasında kümülatif ağırlık değeri **tam olarak** toplam ağırlığın yarısına ($\sum w_i / 2$) eşit çıkarsa, tek bir optimum koordinat noktası yerine bir **optimum koordinat aralığı** oluşur.
Bu durumda, eşitliğin sağlandığı koordinat ($x_k$) ile bir sonraki daha büyük koordinat ($x_{k+1}$) arasındaki kapalı aralıkta yer alan tüm noktalar optimaldir:

$$x^* \in [x_k, \; x_{k+1}]$$

Bu aralıktaki herhangi bir koordinat seçimi, aynı minimum toplam taşıma maliyetini verir. Sınav senaryolarında sıklıkla karşılaşılan ve "tek optimum vardır" yanılgısını düzelten bu yapı, akademik titizlikle hesaplamalara yansıtılmalıdır.

#### Çözümlü Depo Örneği (Hava Kuvvetleri Komutanlığı)
5 farklı üs noktasına malzeme desteği sağlayacak yeni bir deponun optimal konumunu bulalım. Üs koordinatları ve günlük sevkiyat ağırlıkları ($w$) tablodaki gibidir:
*   $P_1 = (1, 1)$, $w_1 = 5$
*   $P_2 = (5, 2)$, $w_2 = 6$
*   $P_3 = (2, 8)$, $w_3 = 2$
*   $P_4 = (4, 4)$, $w_4 = 4$
*   $P_5 = (8, 6)$, $w_5 = 8$

Toplam ağırlık: $\sum_{i=1}^{5} w_i = 5 + 6 + 2 + 4 + 8 = 25$  
Toplam ağırlığın yarısı (Medyan Sınırı): $25 / 2 = 12,5$

**1. Optimum $x^*$ Koordinatı:**
$x$-koordinatlarını ($a_i$) artan sıraya dizip kümülatif ağırlıkları toplayalım:

| Sıralı Tesis | Koordinat ($a_i$) | Ağırlık ($w_i$) | Kümülatif Ağırlık | Değerlendirme |
| :---: | :---: | :---: | :---: | :--- |
| $P_1$ | 1 | 5 | 5 | $< 12,5$ |
| $P_3$ | 2 | 2 | 7 | $< 12,5$ |
| $P_4$ | 4 | 4 | 11 | $< 12,5$ |
| **$P_2$** | **5** | **6** | **17** | **$\ge 12,5$ (Sınırı Aşan İlk Değer)** |
| $P_5$ | 8 | 8 | 25 | |

Kümülatif toplamı $12,5$ değerini ilk aşan koordinat $5$'tir. Dolayısıyla: **$x^* = 5$**

**2. Optimum $y^*$ Koordinatı:**
$y$-koordinatlarını ($b_i$) artan sıraya dizip kümülatif ağırlıkları toplayalım:

| Sıralı Tesis | Koordinat ($b_i$) | Ağırlık ($w_i$) | Kümülatif Ağırlık | Değerlendirme |
| :---: | :---: | :---: | :---: | :--- |
| $P_1$ | 1 | 5 | 5 | $< 12,5$ |
| $P_2$ | 2 | 6 | 11 | $< 12,5$ |
| **$P_4$** | **4** | **4** | **15** | **$\ge 12,5$ (Sınırı Aşan İlk Değer)** |
| $P_5$ | 6 | 8 | 23 | |
| $P_3$ | 8 | 2 | 25 | |

Kümülatif toplamı $12,5$ değerini ilk aşan koordinat $4$'tür. Dolayısıyla: **$y^* = 4$**

Optimal yeni depo konumu **$(x^*, y^*) = (5, 4)$** koordinatıdır.

**3. Toplam Optimal Taşıma Maliyeti ($f(5,4)$):**
$$f(5,4) = 5(|5-1| + |4-1|) + 6(|5-5| + |4-2|) + 2(|5-2| + |4-8|) + 4(|5-4| + |4-4|) + 8(|5-8| + |4-6|)$$
$$f(5,4) = 5(4+3) + 6(0+2) + 2(3+4) + 4(1+0) + 8(3+2)$$
$$f(5,4) = 35 + 12 + 14 + 4 + 40 = 105\text{ birim-maliyet}$$

![[07 Ekler/Grafikler/minisum-konum.svg]]

---

### 5.2 Tek Tesis Minimax (U-V Dönüşümü Yöntemi)

#### Amaç ve Geometrik Karakteristik
Minimax konum modeli, kurulacak yeni tesis ile mevcut tesisler arasındaki **maksimum uzaklığı** minimize etmeyi hedefler. Acil servis istasyonları (itfaiye, ambulans vb.) veya askeri koruma radar konumlandırmaları gibi "en kötü durum" mesafesinin en iyilenmesi gereken hayati sistemlerde bu yöntem kullanılır. Dik doğrusal uzaklık altındaki minimax amaç fonksiyonu:

$$\min_{x,y}\max_i\left\{|x-a_i|+|y-b_i|\right\}$$

#### Koordinat Döndürme (U-V) Dönüşümü ve Eşitsizlik Çözümü
Mutlak değerli Manhattan uzaklıklarının minimax formulasyonu geometrik olarak zorlayıcıdır. Ancak koordinat eksenlerini $45^\circ$ döndüren bir doğrusal dönüşümle problem doğrusal olarak ayrıştırılabilir. Her mevcut tesis koordinatı $(a_i, b_i)$ için yeni dönüşüm koordinatları $u_i$ ve $v_i$ tanımlanır:

$$u_i = a_i + b_i \qquad \text{ve} \qquad v_i = a_i - b_i$$

Aynı şekilde yeni tesis koordinatları da $u = x+y$ ve $v = x-y$ olur. Bu dönüşüm sayesinde maksimum uzaklık yarıçapı $R^*$ doğrudan aşağıdaki formülle hesaplanır:

$$R^* = \frac{1}{2} \max \left( u_{\max} - u_{\min}, \; v_{\max} - v_{\min} \right)$$

Burada:
*   $u_{\max} = \max_i \{u_i\}$ ve $u_{\min} = \min_i \{u_i\}$
*   $v_{\max} = \max_i \{v_i\}$ ve $v_{\min} = \min_i \{v_i\}$

Yeni tesisin döndürülmüş eksenlerdeki optimal koordinat aralıkları ($U^*$ ve $V^*$) ise şöyledir:

$$U^* = [u_{\max} - R^*, \; u_{\min} + R^*]$$
$$V^* = [v_{\max} - R^*, \; v_{\min} + R^*]$$

Aralıklardan seçilen optimal $u \in U^*$ ve $v \in V^*$ değerleri, ters doğrusal dönüşüm uygulanarak orijinal koordinat sistemine geri taşınır:

$$x = \frac{u+v}{2} \qquad \text{ve} \qquad y = \frac{u-v}{2}$$

> [!NOTE]
> **Slayt Nüansı ve İşaret Farkı:** Ders slaytlarında koordinat dönüşümü yapılırken $v_i = b_i - a_i$ tanımı kullanılmıştır. Bu durumda $v$ koordinatlarının işaretleri tersine döner ve optimal $V^*$ aralığı $[v_{\max} - R^*, v_{\min} + R^*]$ şeklinde hesaplandığında ters dönüşüm formülü $x = (u-v)/2$ ve $y = (u+v)/2$ olarak uygulanır. Her iki yaklaşım da matematiksel olarak birbirine denktir ve orijinal koordinat sistemindeki sonuç geometrisini birebir korur.

#### Çözümlü Hava İkmal Bakım Merkezi Örneği
8 farklı askeri birime hizmet sunacak yeni bir minimax bina konumu belirlenecektir. Mevcut birimlerin koordinatları:
$P_1(0,0)$, $P_2(4,6)$, $P_3(8,2)$, $P_4(10,4)$, $P_5(4,8)$, $P_6(2,4)$, $P_7(6,4)$, $P_8(8,8)$.

**1. U-V Dönüşüm Tablosu ($v_i = a_i - b_i$ ve $v_i = b_i - a_i$ karşılaştırmalı):**

| Tesis | $a_i$ | $b_i$ | $u_i = a_i+b_i$ | $v_{i} = a_i-b_i$ (Standart) | $v_{i} = b_i-a_i$ (Slayt) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $P_1$ | 0 | 0 | 0 | 0 | 0 |
| $P_2$ | 4 | 6 | 10 | -2 | 2 |
| $P_3$ | 8 | 2 | 10 | 6 | -6 |
| $P_4$ | 10 | 4 | 14 | 6 | -6 |
| $P_5$ | 4 | 8 | 12 | -4 | 4 |
| $P_6$ | 2 | 4 | 6 | -2 | 2 |
| $P_7$ | 6 | 4 | 10 | 2 | -2 |
| $P_8$ | 8 | 8 | 16 | 0 | 0 |

**2. Sınır Değerlerin Tespiti ve $R^*$ Hesabı ($v_i = a_i - b_i$ temel alınmıştır):**
*   $u_{\max} = 16$, $u_{\min} = 0 \implies \Delta_u = 16 - 0 = 16$
*   $v_{\max} = 6$, $v_{\min} = -4 \implies \Delta_v = 6 - (-4) = 10$

$$R^* = \frac{1}{2} \max(16, 10) = 8\text{ birim}$$

En uzak birime olan minimax seyahat yarıçapı $R^* = 8$ birim olarak kesinleşir.

**3. Optimal U-V Aralıkları:**
*   $U^* = [16 - 8, \; 0 + 8] = [8, 8] \implies u^* = 8$ (Tek bir değer)
*   $V^* = [6 - 8, \; -4 + 8] = [-2, 4] \implies v^* \in [-2, 4]$ (Sonsuz sayıda değer içeren aralık)

**4. Orijinal Koordinatlara Geri Dönüş ($x, y$):**
*   **$v^* = -2$ sınır noktası için:**
    $$x = \frac{u+v}{2} = \frac{8 - 2}{2} = 3 \qquad y = \frac{u-v}{2} = \frac{8 - (-2)}{2} = 5 \implies (3, 5)$$
*   **$v^* = 4$ sınır noktası için:**
    $$x = \frac{u+v}{2} = \frac{8 + 4}{2} = 6 \qquad y = \frac{u-v}{2} = \frac{8 - 4}{2} = 2 \implies (6, 2)$$

Optimal çözüm tek bir nokta değildir; döndürülmüş koordinat aralığının sınır uçları olan **$(3, 5)$** ve **$(6, 2)$** noktalarını birleştiren ve $x + y = 8$ doğrusu üzerinde yer alan tüm doğru parçasıdır. Bu segment üzerindeki herhangi bir koordinata kurulacak yeni tesis, 8 birimlik maksimum mesafe kısıtını tam olarak sağlayacaktır.

![[07 Ekler/Grafikler/minimax-geometri.svg]]

---

### 5.3 Konum-Atama (Location-Allocation) Modelleri

#### Sezgisel İteratif Algoritma Yapısı
Birden fazla yeni tesisin kurulacağı ve müşterilerin bu tesislere hizmet almak üzere paylaştırılacağı problemlerde konum ve atama kararları eşanlı çözülmelidir. Bu amaçla Cooper tarafından önerilen iteratif konum-atama sezgiseli uygulanır:

```mermaid
graph TD
    Start[1. Başlangıç Tesis Konumlarını Seç] --> Assign[2. Her müşteriyi en yakın tesise ata]
    Assign --> SolveMinisum[3. Her küme için bağımsız Minisum çöz]
    SolveMinisum --> Check{Konumlar değişti mi?}
    Check -- Evet -- > Assign
    Check -- Hayır --> Stop[4. Algoritmayı Sonlandır ve Raporla]
```

Bu döngü, yerel bir optimuma yakınsayana kadar devam eder. Başlangıç konumlarının seçimi nihai yerel optimumun kalitesini doğrudan etkiler.

---

### 5.4 Kesikli Tesis Konumu (Açma-Atama Modeli)

#### Karar Modeli Formülasyonu
Açma-atama modeli, kurulabilecek aday tesis konumlarının ve bunlara ait sabit açılış maliyetlerinin belirli olduğu kesikli (discrete) bir tesis yer seçimi modelidir. Kapasite kısıtsız modelin tam sayılı programlama formülasyonu şu şekildedir:

$$\min \sum_{i \in I} f_i y_i + \sum_{i \in I} \sum_{j \in J} c_{ij} x_{ij}$$

**Kısıtlar:**
1.  **$\sum_{i \in I} x_{ij} = 1 \qquad \forall j \in J$**: Her $j$ müşterisine mutlaka ve sadece bir açık tesisten hizmet verilmelidir.
2.  **$x_{ij} \le y_i \qquad \forall i \in I, j \in J$**: Bir $j$ müşterisinin $i$ tesisine atanabilmesi ($x_{ij}=1$) için o tesisin açılmış ($y_i=1$) olması zorunludur.
3.  **$y_i \in \{0, 1\} \qquad \forall i \in I$**: Tesis açma karar değişkeni binary (0: Kapalı, 1: Açık).
4.  **$x_{ij} \in \{0, 1\} \qquad \forall i \in I, j \in J$**: Atama karar değişkeni binary.

Burada $f_i$ aday tesis $i$'nin sabit açılış maliyeti, $c_{ij}$ ise $j$ müşterisine $i$ tesisinden hizmet vermenin değişken seyahat/taşıma maliyetidir.

#### Çözümlü 5-Müşteri 5-Aday Örneği
5 müşteri bölgesi ve kurulabilecek 5 aday konum (A, B, C, D, E) için maliyet matrisi ve sabit maliyetler tanımlanmıştır:

*   **Aday Sabit Açılış Maliyetleri ($f_i$):**
    $f_A = 3.000$ TL, $f_B = 2.000$ TL, $f_C = 2.000$ TL, $f_D = 3.000$ TL, $f_E = 4.000$ TL
*   **Hizmet Maliyetleri Matrisi ($c_{ij}$ - Müşteri $j$'den Aday $i$'ye):**

| Müşteri \ Aday | A | B | C | D | E |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **Müşteri 1 (j=0)** | 100 | 500 | 1800 | 1300 | 1700 |
| **Müşteri 2 (j=1)** | 1500 | 200 | 2600 | 1400 | 1800 |
| **Müşteri 3 (j=2)** | 2500 | 1200 | 1700 | 300 | 1900 |
| **Müşteri 4 (j=3)** | 2800 | 1800 | 700 | 800 | 800 |
| **Müşteri 5 (j=4)** | 10000 | 12000 | 800 | 8000 | 900 |

**Kombinasyon Değerlendirmeleri ve Optimal Çözüm:**

*   **Alternatif 1: Yalnızca Tek Bir Depo Açılması ($n=1$):**
    Eğer sadece bir depo açılmasına izin verilirse, tüm müşteriler o depoya atanacaktır. En düşük maliyetli seçenek C deposunun tek başına açılmasıdır:
    *   Sabit maliyet = $f_C = 2.000$ TL
    *   Hizmet maliyetleri toplamı = $1800 + 2600 + 1700 + 700 + 800 = 7.600$ TL  
        *Toplam Maliyet:* $2.000 + 7.600 = 9.600$ TL.
*   **Alternatif 2: B ve C Depolarının Açılması ($y_B = 1, y_C = 1$):**
    İki depo açıldığında her müşteri en ucuz hizmet alabildiği depoya yönlendirilir ($\min \{c_{Bj}, c_{Cj}\}$):
    *   Müşteri 1: $\min(500, 1800) = 500 \implies$ B'ye atandı.
    *   Müşteri 2: $\min(200, 2600) = 200 \implies$ B'ye atandı.
    *   Müşteri 3: $\min(1200, 1700) = 1200 \implies$ B'ye atandı.
    *   Müşteri 4: $\min(1800, 700) = 700 \implies$ C'ye atandı.
    *   Müşteri 5: $\min(12000, 800) = 800 \implies$ C'ye atandı.
    *   **Sabit Maliyet:** $f_B + f_C = 2.000 + 2.000 = 4.000$ TL
    *   **Değişken Maliyetler:** $500 + 200 + 1200 + 700 + 800 = 3.400$ TL
    *   **Toplam Optimal Maliyet:** $4.000 + 3.400 = 7.400$ TL.
    
    Bu kombinasyon, tüm olası kombinasyonlar arasında (tekli, ikili, üçlü vb.) global minimum maliyeti vererek optimal çözüm olduğunu kanıtlar.

![[07 Ekler/Grafikler/kesikli-konum-atama.svg]]
