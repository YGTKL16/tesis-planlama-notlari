---
tags: [ders/tesis-planlama, formül]
---

# Formül Föyü

> [!formula] Kullanım ilkesi
> Formülü yazmadan önce sembolleri ve birimleri tanımla; sonucu uygulanabilir karar değişkenine dönüştürürken yuvarlama ve kısıtları ayrıca değerlendir.

## Hızlı yöntem kontrolü

| Verilen | Aranan | Yöntem | Amaç |
|---|---|---|:---:|
| Fiyat, sabit ve değişken maliyet | Eşik miktar | Başa baş | Eşitle |
| Sağlamlık olasılığı, küçük $Q$ | Üretim kararı | Binom + beklenen kâr | Maksimum |
| Seri fire oranları | İlk giriş | Geriye verim hesabı | Hedefi karşıla |
| 0-1 makine-parça matrisi | Hücre | DCA / ROC | Bloklaştır |
| Rota ve yük | Yönlü akış | From-to | Matris kur |
| Akış, maliyet, uzaklık | Yerleşim | $\sum fcd$ / CRAFT | Minimum |
| A-E-I-O-U-X | Başlangıç yerleşimi | SLP / CORELAP / ALDEP | Puanı büyüt |
| Koordinat ve ağırlık | Tek tesis | Minisum | Toplamı küçült |
| Koordinatlar | Tek tesis | Minimax | En büyüğü küçült |
| Aday tesis ve sabit maliyet | Açılacak tesisler | Açma-atama | Minimum |

Tam karar ağacı: [[00 Pano/Yöntem Seçici|Yöntem Seçici]].

## Kapasite ve maliyet

$$U=\frac{Q_{gerçek}}{Q_{en\ iyi\ işletim}}$$

$$TR=Px,\quad TC=F+Vx,\quad \Pi=(P-V)x-F$$

$$x_{BB}=\frac{F}{P-V}$$

Uygulanabilir adet gerekiyorsa $\lceil x_{BB}\rceil$; fakat “başa baş noktası” kesirli olarak da raporlanır.

### Hedef kâr ve CMR

Tek ürün katkı payı oranı:

$$CMR=\frac{P-V}{P}=1-\frac{V}{P}$$

Satış tutarı cinsinden başa baş:

$$S_{BB}=\frac{F}{CMR}$$

Hedef kâr miktarı ve tutarı:

$$x_{hedef}=\frac{F+\Pi^*}{P-V},\qquad S_{hedef}=\frac{F+\Pi^*}{CMR}$$

İki süreç / makine alternatifi eşik miktarı ($A$ yüksek sabit, $B$ düşük sabit):

$$x^*=\frac{F_A-F_B}{V_B-V_A}$$

$V_B>V_A$ ve $F_A>F_B$ koşulu sağlanmalı; aksi hâlde eşik yoktur ve düşük sabit maliyetli süreç her hacimde avantajlıdır.

> [!tip] Sınav trick'i — “Paydayı kontrol et”
> Yap/satın alda $c_{satın}>c_{yap}$, iki süreçte $V_B>V_A$ zorunlu. Payda sıfır veya negatif çıkarsa eşik yoktur — hesaba geçmeden önce bu bir satırı yaz. Sınavda en çok puan bu adımı atlamaktan kaybedilir.

### Çok ürünlü başa baş

Gelir payı $W_i=S_i/\sum_j S_j$, katkı marjı oranı $CMR_i=(P_i-V_i)/P_i$ ise:

$$\overline{CMR}=\sum_iW_iCMR_i,\qquad S_{BB}=\frac{F}{\overline{CMR}}$$

Karışım değişirse eşik de değişir. Paket: [[09 Öğrenme Paketleri/HF02B - Çok Ürün Başa Baş ve Yap Satın Al|HF02B]].

Yap/satın al eşiği:

$$x^*=\frac{K}{c_{satın\ al}-c_{yap}}$$

Payda pozitif değilse yalnız bu formülle “yap” üstünlüğü kurulamaz.

### Dinamik kapasite büyümesi

$$y=xD,\qquad f(y)=ky^a,\qquad C(x)=\frac{f(xD)}{1-e^{-rx}}$$

$$u=rx,\qquad \frac{u}{e^u-1}=a,\qquad x^*=\frac{u}{r},\qquad y^*=x^*D$$

$0<a<1$ ölçek ekonomisidir. Paket: [[09 Öğrenme Paketleri/HF02C - Dinamik Kapasite Büyümesi|HF02C]].

## Rassal ıskarta

$$X\sim\operatorname{Bin}(Q,p),\qquad P(X=x)=\binom Qx p^x(1-p)^{Q-x}$$

$$E[\Pi(Q)]=\sum_{x=0}^{Q}P(X=x)\Pi(Q,x)$$

Kâr fonksiyonu soru sözleşmesinden kurulur; evrensel değildir. Hedefi yalnız tam parti karşılıyorsa örnek yapı:

$$E[\Pi(Q)]=R\,P(X\ge h)-cQ$$

Kontrol: başarı olasılığı $Q$ ile artabilir, fakat beklenen kâr sürekli artmak zorunda değildir. Paket: [[09 Öğrenme Paketleri/HF03 - Rassal Iskarta Payı|HF03]].

## Fire ve süreç miktarı

$$O_k=(1-s_k)I_k,\quad S_k=s_kI_k$$

$$I_1=\frac{O_n}{\prod_{k=1}^{n}(1-s_k)}$$

Her aşamada tam parça gerekirse:

$$I_k=\left\lceil\frac{O_k}{1-s_k}\right\rceil$$

Sürekli sonuç, yalnız son yuvarlama ve her operasyonu ayrı yuvarlama aynı şey değildir. Paket: [[09 Öğrenme Paketleri/HF04A - Fire ve Donanım Gereksinimi|HF04A]].

## Donanım gereksinimi

$$F=\frac{S\,Q}{E\,H\,R}$$

$S$: standart süre, $Q$: miktar, $E$: performans, $H$: mevcut süre, $R$: güvenilirlik.

$$F_m^{süreç}=\left\lceil\sum_p\frac{S_{pm}Q_p}{E_mH_mR_m}\right\rceil,
\qquad
F_m^{ürün}=\sum_p\left\lceil\frac{S_{pm}Q_p}{E_mH_mR_m}\right\rceil$$

### Operatör-makine atama

$$n'=\frac{a+t}{a+b},\qquad T(m)=\max\{a+t,m(a+b)\}$$

$$r(m)=\frac{m}{T(m)},\qquad C_u(m)=\frac{(c_o+mc_m)T(m)}{m}$$

$\lfloor n'\rfloor$ ve $\lceil n'\rceil$ adaylarını üretim ve maliyetle karşılaştır. Paket: [[09 Öğrenme Paketleri/HF04B - Operatör Makine Atama|HF04B]].

### Aylak süreler

$$I_O=T(m)-m(a+b),\qquad I_M=T(m)-(a+t)$$

$m<n'$ ise operatör aylaktır ($I_O>0$); $m>n'$ ise makineler aylaktır ($I_M>0$).

> [!tip] Sınav trick'i — "Kim bekliyor?"
> $n'$ bir kesim noktası: kaç makine atadıysan $n'$ ile karşılaştır. $m<n'$ → **O**peratör boş (O = altında); $m>n'$ → **M**akine boş (M = üstünde). İlk harf eşleşmesi: Operatör-altı, Makine-üstü.

## Hücre, akış ve alan

### ROC ikili sıralama

$m$ sütun için satır, $n$ satır için sütun puanı:

$$R_i=\sum_{p=1}^{m}b_{ip}2^{m-p},\qquad C_j=\sum_{p=1}^{n}b_{pj}2^{n-p}$$

Satır ve sütunları puanla, sırala, matris değişmeyene kadar tekrarla. Paket: [[09 Öğrenme Paketleri/HF05A - DCA ve ROC Hücre Oluşturma|HF05A]].

### Hollier

$$G_i=\sum_jf_{ij},\qquad A_i=\sum_jf_{ji},\qquad r_i=\frac{G_i}{A_i}$$

$r_i$ büyükten küçüğe sıralanır. Sınır koşulları:

> [!warning] Hollier sınır koşulları
> - $G_i>0,\;A_i=0$ → $r_i=\infty$ → makine **dizinin başına** gider
> - $G_i=0,\;A_i>0$ → $r_i=0$ → makine **dizinin sonuna** gider
> - $G_i=0,\;A_i=0$ → makine izole; hiçbir parça bu makineden geçmiyor (kontrol et)

İleri, atlamalı ve geri akış yüzdelerinin toplamı %100 olmalıdır. Paket: [[09 Öğrenme Paketleri/HF05B - Küme Maliyet Analizi ve Hollier|HF05B]].

### MAG ve from-to

$$A=A_1+\frac{V-V_1}{V_2-V_1}(A_2-A_1)$$

$$M=A\left[1+\frac14(B+C+D+E)\right],\qquad F=M Q h$$

$$f_{ij}=\sum_pQ_pe_pn_{ijp},\qquad F_{ij}=f_{ij}+f_{ji}\quad(i<j)$$

Rota yalnız ardışık yönlü çiftlere ayrılır. Paket: [[09 Öğrenme Paketleri/HF06A - MAG Akış Şiddeti ve From-To Matrisi|HF06A]].

### Alan

$$A_{id}=\sum_jM_jK_{A,j}A_{tb,j}$$

Destek oranları aynı taban üzerinden veriliyorsa:

$$A_{top}=A_{id}\left(1+\sum_kr_k\right)$$

Oranları art arda uygulama; aynı alanı iki kez sayma. Paket: [[09 Öğrenme Paketleri/HF06B - Faaliyet İlişki Diyagramı ve Alan Hesabı|HF06B]].

## Akış ve yerleşim maliyeti

$$C(L)=\sum_i\sum_j f_{ij}c_{ij}d_{ij}(L)$$

Yönlü akış kullanılıyorsa bütün $i\ne j$ hücreleri; birleşik çift akışı kullanılıyorsa yalnız $i<j$ sayılır. İkisini karıştırma.

Komşuluk puanı:

$$S_A=\sum_{i<j}w_{ij}x_{ij}$$

CORELAP toplam yakınlık derecesi:

$$TCR_i=\sum_{j\ne i}w_{ij}$$

CORELAP yerleştirme puanı:

$$PR(k,p)=\sum_{j\in yerleşmiş}w_{kj}q_{jp}$$

$q_{jp}$ tam/yarım komşuluk katsayısıdır. Paket: [[09 Öğrenme Paketleri/HF10A - CORELAP|HF10A]].

### BLOCPLAN

$$Z_A=\sum_{i<j}w_{ij}a_{ij},\qquad
ER=\frac{Z_A}{\sum_{i<j}\max(w_{ij},0)},\qquad
RD=\sum_{i<j}w_{ij}d_{ij}$$

$Z_A$ ve $ER$ büyütülür; $RD$ kullanılan işaret sözleşmesine göre yorumlanır.

$ER$ paydası = tüm pozitif ilişki ağırlıklarının toplamı: $\sum_{i<j}\max(w_{ij},0)$. Negatif (X) ilişkileri dışla, kalanı topla — bu değer sabit bir yerleşimde değişmez. Paket: [[09 Öğrenme Paketleri/HF09B - BLOCPLAN|HF09B]].

### ALDEP ve MULTIPLE

$$Z_{ALDEP}=\sum_{i<j}w_{ij}a_{ij}$$

$$n_i=\frac{A_i}{a_g},\qquad \sum_in_i=\text{toplam grid hücresi}$$

ALDEP ilişki puanını büyütür; MULTIPLE grid alanını koruyarak $\sum F_{ij}c_{ij}d_{ij}$ maliyetini küçültür. Paketler: [[09 Öğrenme Paketleri/HF10B - ALDEP|HF10B]], [[09 Öğrenme Paketleri/HF10C - MULTIPLE|HF10C]].

## Konum modelleri

Dikdoğrusal uzaklık:

$$d_1(P_i,X)=|x-a_i|+|y-b_i|$$

Öklid uzaklığı:

$$d_2(P_i,X)=\sqrt{(x-a_i)^2+(y-b_i)^2}$$

Minisum:

$$\min_{x,y}\sum_i w_i\left(|x-a_i|+|y-b_i|\right)$$

Her eksende ağırlıklı medyan bulunur. Kümülatif ağırlık $W/2$'ye tam eşitse o koordinat ile sonraki koordinat arasındaki **tüm aralık** optimumdur.

Minimax:

$$\min_{x,y}\max_i\left\{|x-a_i|+|y-b_i|\right\}$$

Minimax dönüşümü:

$$u=x+y,\quad v=x-y,\quad x=\frac{u+v}{2},\quad y=\frac{u-v}{2}$$

$$R^*=\frac12\max\{u_{max}-u_{min},v_{max}-v_{min}\}$$

$$U^*=[u_{max}-R^*,u_{min}+R^*],\qquad
V^*=[v_{max}-R^*,v_{min}+R^*]$$

Aralıkları geri dönüştür; yalnız orta noktayı yazmak optimum kümeyi eksik verir. Paket: [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|HF11B]].

## Kesikli tesis konumu

$$\min \sum_iF_iy_i+\sum_i\sum_jc_{ij}x_{ij}$$

$$\sum_i x_{ij}=1,\qquad x_{ij}\le y_i$$

Kapasite:

$$\sum_jq_jx_{ij}\le K_iy_i$$

$$x_{ij},y_i\in\{0,1\}$$

Kapasitesiz küçük problemde açık küme $S$ için:

$$TC(S)=\sum_{i\in S}F_i+\sum_j\min_{i\in S}c_{ij}$$

Boş olmayan bütün $S$ kümeleri karşılaştırılabilir. Paket: [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|HF12B]].

> [!tip] Master trick — "Formülü okumadan önce paydayı sorgula"
> Tesis Planlama sınavında en çok puan kaybı: formülü doğru yazmak ama payda koşulunu kontrol etmemek. Her formülde ilk adım: payda sıfır olabilir mi? Eşit mi? Negatif mi? Bunu bir satırda yaz. Başa baş, yap/satın al, dinamik kapasite, Hollier — hepsinde bu soruyu sor.

## Evrensel son kontrol

1. Amaç yönü doğru mu: minimum, maksimum veya eşitlik?
2. Matris satır ve sütunlarının anlamı yazıldı mı?
3. Yönlü çiftleri birleştirdim mi, ayrı mı tuttum? Soruyla tutarlı mı?
4. Birimler sadeleşiyor mu?
5. Tam sayı kararında yuvarlama yönü gerekçeli mi?
6. Amaç değeri ve karar cümlesi birlikte verildi mi?
7. Sonucu [[08 Hesaplamalar/Sınav Doğrulama Raporu|NumPy doğrulama raporu]] ile kontrol ettim mi?

## Sembol tablosu

| Sembol | Anlam |
|---|---|
| $f_{ij}$ | $i$'den $j$'ye akış |
| $c_{ij}$ | Birim akış-mesafe maliyeti |
| $d_{ij}$ | Bölümler/konumlar arası uzaklık |
| $w_{ij}$ | Yakınlık veya ilişki ağırlığı (küçük $w$ — yerleşim) |
| $W_i$ | Çok ürünlü başa başta ürün $i$'nin satış tutarı payı (büyük $W$ — maliyet) |
| $x_{ij}$ | Atama/komşuluk karar değişkeni |
| $y_i$ | Tesis açma karar değişkeni |
