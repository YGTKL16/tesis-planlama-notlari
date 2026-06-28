---
hafta: 11
durum: hazır
tags: [ders/tesis-planlama, konu/konum, model/minisum, model/minimax]
---

# HF11 - Tesis Konumu I

> [!summary] Ana fikir
> **Sürekli konum problemleri**, yeni tesisin düzlemde sonsuz olası nokta arasından herhangi bir $(x,y)$ koordinatına yerleşebildiğini varsayar; tek ve özel karar etmeni taşıma/nakliye maliyetidir.
> - **Minisum**: yeni tesis ile tüm mevcut tesisler arasındaki **toplam ağırlıklı uzaklığı** küçültür. Dikdoğrusal uzaklıkta $x$ ve $y$ birbirinden bağımsızdır ve her eksen ayrı bir **ağırlıklı medyan** hesabıyla bulunur.
> - **Minimax**: yeni tesis ile herhangi bir mevcut tesis arasındaki **maksimum uzaklığı** küçültür. $u=x+y$, $v=x-y$ dönüşümü problemi iki bağımsız aralık problemine çevirir.
> - Çözüm bazen tek bir nokta değil, bir **optimum aralık** (Minisum) veya bir **doğru parçası** (Minimax) olabilir.

## Sürekli konum problemi ne zaman kullanılır?

Bir problem aşağıdaki işaretlerin tümünü taşıyorsa sürekli konum modeli uygulanır:

- Yeni tesis için uzayda **herhangi bir bölge** seçilebilir (önceden belirlenmiş aday liste yoktur).
- Mevcut ilişki tesislerinin (tedarikçi, müşteri, üs vb.) $(x,y)$ koordinatları ve bunlarla yeni tesis arasındaki akışlar/maliyetler bilinmektedir.
- Tek ve özel düşünce **taşıma/nakliye maliyetidir**.

Aday noktalar önceden sınırlı ve sayılıysa problem **kesikli** (P-medyan, P-merkez) olur; bu derste değil HF12'de işlenir.

> [!info] Tipik uygulamalar
> Yeni havaalanı, hastane, okul; bir tesise yeni iş istasyonu eklenmesi; deponun konumu; bir tesiste banyo/lavaboların konumu; askeri ikmal/bakım merkezi.

## Uzaklık ölçüleri

$$d_1(P_i,X)=|x-a_i|+|y-b_i| \quad\text{(Dikdoğrusal / Rektiliner / Manhattan)}$$

$$d_2(P_i,X)=\sqrt{(x-a_i)^2+(y-b_i)^2} \quad\text{(Öklid)}$$

| Ölçü | Tanım | Kullanım yeri |
|---|---|---|
| Dikdoğrusal (Manhattan) | Önce yatay sonra dikey; yalnız dik/düşey hareket | Izgara yollar, koridorlar, şehir blokları |
| Öklid | İki nokta arası düz doğru | Doğrudan hareket veya kuş uçuşu yaklaşımı |
| Akış yolu | Gerçek yol/konveyör ağı boyunca kat edilen mesafe | Mevcut yol/konveyör ağı belirleyici olduğunda |

Bu notun tüm modelleri **dikdoğrusal** uzaklığı kullanır.

> [!info] Semboller
> - $X=(x,y)$ : yeni tesisin koordinatları (bulunacak)
> - $P_i=(a_i,b_i)$ : $i$'nci mevcut tesisin koordinatları (verilen)
> - $w_i$ : yeni tesis ile $i$'nci mevcut tesis arasındaki ağırlık (maliyet/akış) katsayısı [sefer/gün veya TL/birim uzaklık]
> - $d_i(X,P_i)$ : yeni tesisin $i$'nci tesise dikdoğrusal uzaklığı
> - $f(x,y)$ : amaç fonksiyonu (toplam ağırlıklı uzaklık)

---

## 1. Tek Tesis Minisum Problemi

### Amaç fonksiyonu

$$
\min_{x,y}\; f(x,y)=\sum_{i} w_i\,d_i(X,P_i)=\sum_{i} w_i\bigl(|x-a_i|+|y-b_i|\bigr)
$$

Mutlak değerli toplam, $x$ ve $y$ için iki **bağımsız** parçaya ayrılır:

$$
f(x,y)=\underbrace{\sum_i w_i\,|x-a_i|}_{f_x(x)}+\underbrace{\sum_i w_i\,|y-b_i|}_{f_y(y)}
$$

Bu ayrılabilirlik sayesinde $x^\*$ yalnız $a_i$ değerlerinden, $y^\*$ yalnız $b_i$ değerlerinden bulunur. Her eksen ayrı bir doğru üzerinde ağırlıklı medyan problemidir.

> [!note] Optimum koordinatın iki kuralı (slayt 9)
> **Kural 1 (Medyan/Ortanca):** Yeni tesisin $x$ koordinatı, mevcut tesislerden **birinin** $x$ koordinatıyla aynı olur.
> **Kural 2:** Seçilen $x$ koordinatının sağ veya sol tarafındaki toplam ağırlık, $W/2$'yi aşamaz.
> Aynı iki kural $y$ koordinatı için de geçerlidir.

### Ağırlıklı medyan algoritması

Her eksen ($x$ ve $y$) için ayrı ayrı uygulanır:

1. Mevcut tesisleri ilgili koordinatına göre **küçükten büyüğe** sırala (koordinat-ağırlık çiftini birlikte taşı).
2. Aynı koordinattaki ağırlıkları birleştir.
3. Toplam ağırlık $W=\sum_i w_i$ ve yarısı $W/2$ hesapla.
4. Koordinatlar boyunca **kümülatif ağırlığı** topla.
5. Kümülatif ağırlık ilk kez $W/2$'yi **aşıyorsa** → o koordinat **tek optimumdur**.
6. Kümülatif ağırlık bir koordinatta $W/2$'ye **tam eşitse** → o koordinat ile bir **sonraki büyük** koordinat arasındaki **her nokta optimumdur** (optimum aralık).
7. $y$ ekseni için 1-6 adımlarını tekrarla.
8. Bulunan $X^\*=(x^\*,y^\*)$ için amaç değerini $f(x^\*,y^\*)$ hesapla ve karar cümlesini yaz.

### Alternatif konumların değerlendirilmesi

Ağırlıklı medyanla bulunan optimum nokta fiziksel olarak kullanılamıyorsa (yapılaşma, arsa kısıtı), her uygulanabilir aday $A_k=(x_k,y_k)$ için $f(A_k)$ hesaplanır ve en küçük değeri veren seçilir. **Bu, optimumu en yakın adaya yuvarlamak değildir** — en yakın koordinat en düşük ağırlıklı maliyeti garanti etmez.

### Eş maliyet eğrileri (izomaliyet / iso-cost contour)

Eş maliyet eğrileri, amaç fonksiyonun değerini **değiştirmeyen** aday hareketleri gösterir ve yeni tesis için yaklaşık konumların belirlenmesine yardımcı olur. Mevcut tesislerin koordinat çizgileri arasında kalan bir hücrede $f$ doğrusaldır. Hücre içindeki net çekiş:

$$
G_x=\sum_{a_i<x}w_i-\sum_{a_i>x}w_i,\qquad
G_y=\sum_{b_i<y}w_i-\sum_{b_i>y}w_i
$$

(Sağa/yukarı çekiş pozitif, sola/aşağı çekiş negatif.) Amaç değerini değiştirmeyen küçük bir $(\Delta x,\Delta y)$ hareketi için $G_x\,\Delta x+G_y\,\Delta y=0$ olur; $G_y\ne 0$ ise eş maliyet doğrusunun eğimi:

$$
\frac{\Delta y}{\Delta x}=-\frac{G_x}{G_y}
$$

Bir tesisin $x$ veya $y$ koordinat çizgisi geçildiğinde çekiş dengesi değişir ve eğri kırılır.

> [!example]+ Örnek 1 — Minisum (Kaynak: slaytlar 12-18)
> Hava Kuvvetleri 5 farklı üsse malzeme desteği sağlamak için yeni bir **depo** konumu belirlemek istiyor. Üslerin $(a,b)$ koordinatları ve yeni depo ile aralarında günlük taşınacak malzeme ağırlıkları $w$ tabloda verilmiştir. Toplam ağırlıklı uzaklığı en aza indiren depo konumunu ve amaç değerini bulun. Optimum kullanılamıyorsa $(5,6)$, $(4,2)$, $(8,4)$ adaylarını karşılaştırın.
>
> | Tesis | $(a_i,b_i)$ | $w_i$ |
> |---:|---:|---:|
> | 1 | $(1,1)$ | 5 |
> | 2 | $(5,2)$ | 6 |
> | 3 | $(2,8)$ | 2 |
> | 4 | $(4,4)$ | 4 |
> | 5 | $(8,6)$ | 8 |
>
> **Adım 1 — Toplam ağırlık.**
> $$W=5+6+2+4+8=25,\qquad W/2=12{,}5$$
>
> **Adım 2 — $x$ ağırlıklı medyanı.** ($a_i$ küçükten büyüğe sıralanır)
>
> | $a_i$ | $w_i$ | Kümülatif |
> |---:|---:|---:|
> | 1 | 5 | 5 |
> | 2 | 2 | 7 |
> | 4 | 4 | 11 |
> | 5 | 6 | **17** |
> | 8 | 8 | 25 |
>
> Kümülatif ağırlık 12,5'i ilk kez $a=5$'te **aşar** (Tesis 2). Tek optimum: $x^\*=5$.
>
> **Adım 3 — $y$ ağırlıklı medyanı.** ($b_i$ küçükten büyüğe sıralanır)
>
> | $b_i$ | $w_i$ | Kümülatif |
> |---:|---:|---:|
> | 1 | 5 | 5 |
> | 2 | 6 | 11 |
> | 4 | 4 | **15** |
> | 6 | 8 | 23 |
> | 8 | 2 | 25 |
>
> Kümülatif ağırlık 12,5'i ilk kez $b=4$'te **aşar** (Tesis 4). Tek optimum: $y^\*=4$.
>
> $$\boxed{X^\*=(5,4)}$$
>
> **Adım 4 — Amaç değeri.** $d_i=|5-a_i|+|4-b_i|$
>
> | Tesis | $d_i$ | $w_i d_i$ |
> |---:|---:|---:|
> | 1 | $4+3=7$ | 35 |
> | 2 | $0+2=2$ | 12 |
> | 3 | $3+4=7$ | 14 |
> | 4 | $1+0=1$ | 4 |
> | 5 | $3+2=5$ | 40 |
> | **Toplam** | | **$f^\*=105$** |
>
> **Adım 5 — Alternatif adaylar.** Optimum $(5,4)$ kullanılamıyorsa, üç aday için $f$ yeniden hesaplanır:
>
> | Aday | f |
> |:---|---:|
> | (8,4) | 50+30+20+16+16 = 132 |
> | (5,6) | 45+24+10+12+24 = 115 |
> | (4,2) | 20+6+16+8+64 = **114** |
>
> > [!success] Karar
> > Serbest konumlandırmada optimum $(5,4)$, $f^\*=105$'tir. Bu nokta kullanılamıyor ve yalnız üç aday mümkünse, en küçük amaç değerini veren **$(4,2)$, $f=114$** seçilir (adaylar içindeki en iyi).

---

## 2. Tek Tesis Minimax Problemi

### Amaç fonksiyonu

$$
\min_{x,y}\;\max_{i}\bigl\{|x-a_i|+|y-b_i|\bigr\}
$$

Eşdeğer kısıt biçimi:

$$
\min R \qquad\text{öyle ki}\qquad |x-a_i|+|y-b_i|\le R\quad\forall i
$$

Optimum $R^\*$, herhangi bir mevcut tesise olan en büyük dikdoğrusal uzaklığın mümkün en küçük değeridir.

### $u$-$v$ dönüşümü

Dikdoğrusal uzaklığın "elmas" (dönmüş kare) biçimi, $45°$ döndürülerek eksenlere paralel kareye çevrilir:

$$
u=x+y,\qquad v=x-y
$$

Her mevcut nokta için:

$$
u_i=a_i+b_i,\qquad v_i=a_i-b_i
$$

Ters dönüşüm (sonuçları $(x,y)$'ye geri çevirmek için):

$$
x=\frac{u+v}{2},\qquad y=\frac{u-v}{2}
$$

Kritik özdeşlik:

$$
|x-a_i|+|y-b_i|=\max\bigl(|u-u_i|,\;|v-v_i|\bigr)
$$

### Optimum yarıçap

$$
\Delta_u=u_{\max}-u_{\min},\qquad \Delta_v=v_{\max}-v_{\min}
$$

$$
R^\*=\frac{1}{2}\max(\Delta_u,\Delta_v)
$$

Bunu açık koordinatlarla yazmak istersen, dönüştürülmüş uzayın orta noktaları:

$$
u^\*=\frac{u_{\max}+u_{\min}}{2},\qquad v^\*=\frac{v_{\max}+v_{\min}}{2}
$$

bir optimum nokta verir; geri dönüşüm $x^\*=\dfrac{u^\*+v^\*}{2}$, $y^\*=\dfrac{u^\*-v^\*}{2}$ ile yapılır. Maksimum uzaklık ise (slayttaki form):

$$
R^\*=\frac{(u_{\max}-u_{\min})+(v_{\max}-v_{\min})}{4}
$$

> [!warning] Bu son formül yalnız $\Delta_u=\Delta_v$ olduğunda $\tfrac12\max(\Delta_u,\Delta_v)$ ile birebir aynı sonucu verir
> Genel durumda $R^\*$, **iki yayılımdan büyük olanının yarısıdır** ($R^\*=\tfrac12\max(\Delta_u,\Delta_v)$). $\frac{\Delta_u+\Delta_v}{4}$ ifadesi yalnız iki yayılım eşitken doğru sayısal değeri verir; eşit değilse büyük yayılımın yarısını kullan. Aşağıdaki kaynak örneğinde $\Delta_u=16\ne\Delta_v=10$ olduğundan $R^\*=\tfrac12(16)=8$'dir.

### Tüm optimum çözüm kümesi

Yalnız $u^\*$ ve $v^\*$ orta noktalarını almak bir optimum nokta verir ama **diğer optimumları gizleyebilir**. $R^\*$ bulunduktan sonra uygulanabilir dönüştürülmüş koordinatlar şu aralıklardadır:

$$
U^\*=\bigl[u_{\max}-R^\*,\;u_{\min}+R^\*\bigr],\qquad
V^\*=\bigl[v_{\max}-R^\*,\;v_{\min}+R^\*\bigr]
$$

$R^\*$ büyük yayılımın yarısı olduğundan, **en az bir** aralık tek noktaya çöker; diğeri bir aralık kalabilir. Ters dönüşümle bu, $(x,y)$ düzleminde tek nokta veya bir **doğru parçası** verir.

### $u$-$v$ dönüşümü algoritması (çözüm sırası)

1. Her nokta için $u_i=a_i+b_i$ ve $v_i=a_i-b_i$ hesapla.
2. $u_{\min}, u_{\max}, v_{\min}, v_{\max}$ bul; $\Delta_u, \Delta_v$ hesapla.
3. $R^\*=\tfrac12\max(\Delta_u,\Delta_v)$ hesapla.
4. $U^\*$ ve $V^\*$ aralıklarını kur.
5. Aralıkların **uç/köşe** değerlerini ters dönüşümle $(x,y)$ düzlemine çevir (tek noktayı veya doğru parçasının uçlarını elde et).
6. En az bir adayda **tüm** Manhattan uzaklıklarını hesaplayıp maksimumun gerçekten $R^\*$ olduğunu doğrula.

> [!example]+ Örnek 2 — Minimax (Kaynak: slaytlar 30-32)
> 8 tesise sahip bir Hava İkmal Bakım Merkezi yeni bina inşa edecek ve mevcut tüm tesislere mümkün olduğunca yakın olmak istiyor. En iyi minimax konumunu ve herhangi bir tesisle olan maksimum uzaklığı bulun.
>
> | $i$ | $(a_i,b_i)$ | $u_i=a_i+b_i$ | $v_i=a_i-b_i$ |
> |---:|---:|---:|---:|
> | 1 | $(0,0)$ | 0 | 0 |
> | 2 | $(4,6)$ | 10 | -2 |
> | 3 | $(8,2)$ | 10 | 6 |
> | 4 | $(10,4)$ | 14 | 6 |
> | 5 | $(4,8)$ | 12 | -4 |
> | 6 | $(2,4)$ | 6 | -2 |
> | 7 | $(6,4)$ | 10 | 2 |
> | 8 | $(8,8)$ | 16 | 0 |
>
> **Adım 1 — Yayılımlar.**
> $$u_{\min}=0,\; u_{\max}=16 \;\Rightarrow\; \Delta_u=16$$
> $$v_{\min}=-4,\; v_{\max}=6 \;\Rightarrow\; \Delta_v=10$$
>
> **Adım 2 — Minimum maksimum uzaklık.**
> $$R^\*=\tfrac12\max(16,10)=8$$
>
> **Adım 3 — Optimum dönüştürülmüş koordinatlar.**
> $$U^\*=[16-8,\;0+8]=[8,8]\quad(\text{tek nokta: } u=8)$$
> $$V^\*=[6-8,\;-4+8]=[-2,4]\quad(\text{aralık: } -2\le v\le 4)$$
>
> **Adım 4 — Uçları geri dönüştür.**
> $v=-2$ için: $x=\dfrac{8+(-2)}{2}=3,\quad y=\dfrac{8-(-2)}{2}=5 \Rightarrow (3,5)$
> $v=4$ için: $x=\dfrac{8+4}{2}=6,\quad y=\dfrac{8-4}{2}=2 \Rightarrow (6,2)$
>
> > [!success] Karar
> > Optimum tek nokta değildir: $(3,5)$ ile $(6,2)$ arasındaki **$x+y=8$ doğru parçasının tamamı** optimumdur ve minimum maksimum uzaklık **$R^\*=8$ birimdir**.
>
> **Adım 5 — Uzaklık kontrolü.**
> $(3,5)$ noktasından 8 tesise uzaklıklar: $8,\,2,\,8,\,8,\,4,\,2,\,4,\,8$ → maks. 8 ✓
> $(6,2)$ noktasından 8 tesise uzaklıklar: $8,\,6,\,2,\,6,\,8,\,6,\,2,\,8$ → maks. 8 ✓
> Doğru parçasındaki diğer tüm noktalar $P_1=(0,0)$ ve $P_8=(8,8)$'den 8 birim uzaktadır.

---

## 3. Minisum vs Minimax — karar tablosu

| Ölçüt | Minisum | Minimax |
|---|---|---|
| **Amaç** | Toplam ağırlıklı uzaklık $\sum_i w_i d_i$ minimum | En büyük uzaklık $\max_i d_i$ minimum |
| **Hangi durum** | "Toplam taşıma/maliyet en küçük", "ağırlıklı mesafe toplamı" | "En uzaktaki nokta en yakın", "en kötü erişim/süre en küçük" |
| **Ağırlık** | Akış/maliyet ağırlıkları $w_i$ belirleyicidir | Klasik biçimde ağırlıksızdır (eşit önem) |
| **Çözüm yöntemi** | Ağırlıklı medyan (eksenler bağımsız) | $u$-$v$ dönüşümü + kapsama yarıçapı $R^\*$ |
| **Çözüm türü** | Tek nokta veya optimum aralık/dikdörtgen | Tek nokta veya doğru parçası |
| **Kullanım yeri** | Depo, üretim/dağıtım, taşıma maliyeti odaklı | Acil müdahale, ambulans, güvenlik/savunma, adil hizmet |
| **Sezgi** | "Ağırlık merkezine yaklaş" | "En uzak ikiliyi ortala / kapsama çemberini küçült" |

> [!warning] İki klasik hata
> **1. Eşit yarı durumu (Minisum):** Kümülatif ağırlık tam $W/2$'ye **eşit** olduğunda, "ilk kez yarıya eşit/büyük olan koordinatı seç" kısa kuralı tek bir nokta üretir; oysa doğru cevap o koordinat ile **sonraki büyük koordinat arasındaki tüm aralıktır**. İki eksende de eşitlik oluşursa optimum çözüm kümesi bir **dikdörtgendir**. Daima "Aşıyor mu, tam eşit mi?" kontrolünü ayrı yap.
> **2. $u$-$v$'den geri dönüşüm hatası (Minimax):** $v$ için $a-b$ ile başlayıp ters dönüşümde başka işaret/sözleşme kullanmak en sık yapılan hatadır. Dönüşüm ($u=x+y,\,v=x-y$) ve ters dönüşüm ($x=\tfrac{u+v}{2},\,y=\tfrac{u-v}{2}$) çiftini çözümün başında kutuya al ve sonuna kadar değiştirme. Ayrıca yalnız orta noktayı yazmak, doğru parçası biçimindeki diğer optimumları kaybeder; $U^\*$ ve $V^\*$ aralıklarını her zaman kur. Kontrolde Öklid değil, **Manhattan** uzaklığı kullan.

---

## 4. Pratik sorular

> [!question] Soru 1 (Minisum, tek eksen — temel)
> Bir doğru üzerindeki noktalar $x=(1,4,7)$ ve ağırlıklar $w=(2,5,3)$ olsun. Ağırlıklı medyanı ve minimum toplam ağırlıklı uzaklığı bulun.

> [!success]- Çözüm 1
> $W=2+5+3=10$, $W/2=5$. Kümülatif ağırlıklar: $2,\,7,\,10$. İlk aşım $x=4$'te → $x^\*=4$.
> $$f(4)=2|4-1|+5|4-4|+3|4-7|=6+0+9=15$$

> [!question] Soru 2 (Minisum, eşit yarı — optimum aralık)
> $P_1=(0,0),w_1=4$; $P_2=(4,2),w_2=2$; $P_3=(10,6),w_3=6$ verilsin. Dikdoğrusal minisum optimum çözüm **kümesini** ve minimum amaç değerini bulun.

> [!success]- Çözüm 2
> $W=4+2+6=12$, $W/2=6$.
> **$x$ ekseni:** sıralı $a=(0,4,10)$, ağırlık $(4,2,6)$, kümülatif $4,\,6,\,12$. $a=4$'te kümülatif tam 6 (= $W/2$) → eşit yarı! Sonraki koordinat 10 olduğundan $x^\*\in[4,10]$.
> **$y$ ekseni:** sıralı $b=(0,2,6)$, ağırlık $(4,2,6)$, kümülatif $4,\,6,\,12$. $b=2$'de kümülatif tam 6 → $y^\*\in[2,6]$.
> Optimum çözüm kümesi $[4,10]\times[2,6]$ **dikdörtgenidir**. Örneğin köşe $(4,2)$ için:
> $$f(4,2)=4(4+2)+2(0+0)+6(6+4)=24+0+60=84$$
> Bu dikdörtgendeki **her nokta** aynı minimumu ($f^\*=84$) verir.

> [!question] Soru 3 (Minimax — doğru parçası)
> $P_1=(0,0)$, $P_2=(8,0)$, $P_3=(2,6)$ için dikdoğrusal minimax optimum çözüm kümesini ve $R^\*$ değerini bulun.

> [!success]- Çözüm 3
> Dönüşümler: $(0,0)\to(u,v)=(0,0)$; $(8,0)\to(8,8)$; $(2,6)\to(8,-4)$.
> $u_{\min}=0,\,u_{\max}=8\Rightarrow\Delta_u=8$;  $v_{\min}=-4,\,v_{\max}=8\Rightarrow\Delta_v=12$.
> $$R^\*=\tfrac12\max(8,12)=6$$
> $$U^\*=[8-6,\,0+6]=[2,6],\qquad V^\*=[8-6,\,-4+6]=[2,2]$$
> Burada $v=2$ sabit, $u\in[2,6]$ aralık. Uçları geri dönüştür:
> $u=2,v=2 \to (x,y)=(2,0)$;  $u=6,v=2 \to (x,y)=(4,2)$.
> $(2,0)$ ile $(4,2)$ arasındaki doğru parçasının tamamı optimumdur; maksimum uzaklık **6**'dır.

> [!question] Soru 4 (Yöntem seçimi + tuzak)
> Aşağıdaki her durum için doğru yöntemi (Minisum/ağırlıklı medyan mı, Minimax/$u$-$v$ mi) ve nedenini yazın:
> 1. Bir depo için toplam günlük taşıma maliyeti küçültülecek; konum serbest, yollar ızgara.
> 2. Bir ambulans noktası için en uzaktaki mahallenin erişim mesafesi küçültülecek.
> 3. Ağırlıklı medyanla bulunan nokta yapılaşma nedeniyle kullanılamaz; üç izinli parsel verilmiş.
> 4. Her istasyonun akış ağırlığıyla çarpılmış **toplam** yolu azaltılacak.

> [!success]- Çözüm 4
> 1. **Minisum / ağırlıklı medyan** — amaç toplam ağırlıklı uzaklık.
> 2. **Minimax / $u$-$v$ dönüşümü** — amaç toplam değil, en kötü (maksimum) uzaklık.
> 3. Yöntem değil **adım** sorusu: üç izinli adayın **her biri için minisum amaç değeri $f$ hesaplanır**, en küçüğü seçilir. Optimumu en yakın adaya yuvarlamak yanlıştır.
> 4. **Ağırlıklı minisum / ağırlıklı medyan** — "ağırlıkla çarpılmış toplam" Minisum'un tanımıdır.

> [!question] Soru 5 (Minimax — tam mı, eksik mi?)
> Bir öğrenci Örnek 2'de dönüştürülmüş aralıkların orta noktalarını alıp $(u,v)=(8,1)$, $(x,y)=(4{,}5,\,3{,}5)$ buluyor. "Cevap doğru mu, tam mı?" sorusunu gerekçeli yanıtlayın.

> [!success]- Çözüm 5
> **Nokta doğru:** $u=8$ ve $v=1\in[-2,4]$ olduğundan bu nokta optimumdur ve maksimum uzaklığı 8'dir. **Ama cevap tam değil:** soru optimum *konumları* istiyorsa, $v\in[-2,4]$ aralığının ve buna karşılık gelen $(3,5)$–$(6,2)$ doğru parçasının tamamı yazılmalıdır. Tek merkez nokta, doğru parçasındaki diğer optimumları gizler.

---

## 5. Öğrenme paketleri ve kaynaklar

- [[HF11A - Minisum ve Ağırlıklı Medyan]] — ağırlıklı medyan algoritması, eşit yarı/optimum aralık, eş maliyet eğrileri ve kademeli alıştırmalar.
- [[HF11B - Minimax ve Optimum Çözüm Kümesi]] — $u$-$v$ dönüşümü, $R^\*$, optimum doğru parçası ve geri dönüşüm tuzakları.
- [[HF11-P11-Tesis Konumu I-2025.pptx|Ders sunumu]]
- [[05 Kaynaklar/MarkItDown/HF11 - Ham|MarkItDown ham metni]]
- [[03 Formüller/Formül Föyü#Konum modelleri|Formül föyü]]
- [[08 Hesaplamalar/Hesap Sonuçları#Grafikler|Minisum Python grafiği]]

Önceki: [[HF10 - Yerleşim Tasarımı IV]] · Sonraki: [[HF12 - Tesis Konumu II]]
