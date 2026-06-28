---
tags: [ders/tesis-planlama, dizin]
---

# Kavram Dizini

> [!info]
> Dersin tüm kavramları sekiz bölümde toplanmıştır. Her kavram için kısa tanım, varsa formül ve ilgili ders notu / öğrenme paketi linki verilmiştir. Bağlantılar `01 Ders Notları` ve `09 Öğrenme Paketleri` klasörlerine gider.

---

## Bölüm 1 — Kapasite ve Ekonomik Analiz

- **Tesis planlama:** Bir tesisin yer, yapı, donanım ve akışının amaca göre tasarımı; stratejik, taktik ve operasyonel karar düzeyleri. [[01 Ders Notları/HF01 - Giriş ve Ürün, Süreç, Çizelgeleme Tasarımı I|HF01]]
- **Kapasite:** Bir sistemin birim zamanda üretebileceği en yüksek çıktı. Tasarım, etkin ve fiili kapasite ayrımı yapılır. [[01 Ders Notları/HF02 - Tesis Kapasite Planlama|HF02]]
- **Kullanım oranı (utilization):** Fiili çıktının tasarım kapasitesine oranı. $$\text{Kullanım}=\frac{\text{Fiili çıktı}}{\text{Tasarım kapasitesi}}$$ [[01 Ders Notları/HF02 - Tesis Kapasite Planlama#Temel ölçüler|HF02]]
- **Verimlilik (efficiency):** Fiili çıktının etkin kapasiteye oranı. $$\text{Verimlilik}=\frac{\text{Fiili çıktı}}{\text{Etkin kapasite}}$$ [[01 Ders Notları/HF02 - Tesis Kapasite Planlama#Temel ölçüler|HF02]]
- **Başa baş noktası (BEP):** Toplam gelir ile toplam maliyetin eşitlendiği üretim hacmi. $$Q_{BEP}=\frac{F}{P-V}$$ [[09 Öğrenme Paketleri/HF02A - Kapasite ve Tek Ürün Başa Baş|HF02A]]
- **Katkı payı oranı (CMR):** Birim katkı payının satış fiyatına oranı; çok ürünlü başa baş hesabının çekirdeği. $$CMR=\frac{P-V}{P}$$ [[09 Öğrenme Paketleri/HF02B - Çok Ürün Başa Baş ve Yap Satın Al|HF02B]]
- **Çok ürünlü başa baş:** Ürün karması sabit kabul edilerek ağırlıklı katkı payı oranıyla bulunan toplam ciro. $$\text{Ciro}_{BEP}=\frac{F}{CMR_{\text{ağırlıklı}}}$$ [[09 Öğrenme Paketleri/HF02B - Çok Ürün Başa Baş ve Yap Satın Al|HF02B]]
- **Yap–satın al (make-or-buy):** İki maliyet doğrusunun kesişim hacmiyle kendi üretme ve dışarıdan alma kararının karşılaştırılması. [[09 Öğrenme Paketleri/HF02B - Çok Ürün Başa Baş ve Yap Satın Al|HF02B]]
- **Öncü / takipçi strateji (lead/lag):** Kapasiteyi talepten önce (öncü) veya sonra (takipçi) ekleme tercihi; risk ve aylaklık dengesi. [[01 Ders Notları/HF02 - Tesis Kapasite Planlama#Temel ölçüler|HF02]]
- **Dinamik kapasite büyümesi:** Talep büyürken kapasite eklemelerinin zamanlaması ve büyüklüğünün maliyetle değerlendirilmesi. [[09 Öğrenme Paketleri/HF02C - Dinamik Kapasite Büyümesi|HF02C]]

---

## Bölüm 2 — Ürün ve Süreç Tasarımı

- **Süreç tasarımının üç kararı:** İşlemleri belirleme, makine/yöntem seçme ve sıralama. [[01 Ders Notları/HF03 - Ürün, Süreç ve Çizelgeleme Tasarımı II#Süreç tasarımının üç kararı|HF03]]
- **Rassal ıskarta payı:** Her parçanın bağımsız olasılıkla bozulması; iyi parça sayısı binom dağılımıyla modellenir. [[09 Öğrenme Paketleri/HF03 - Rassal Iskarta Payı|HF03]]
- **Binom yaklaşımı:** $n$ deneme, $p$ iyi olma olasılığı için beklenen iyi parça sayısı $np$; istenen çıktıyı garanti edecek girdi hesabı. $$E[\text{iyi}]=np$$ [[09 Öğrenme Paketleri/HF03 - Rassal Iskarta Payı|HF03]]
- **Deterministik fire (yield):** Her istasyonda sabit fire oranıyla geriye doğru girdi hesabı. $$\text{Girdi}=\frac{\text{Çıktı}}{\prod_k (1-f_k)}$$ [[09 Öğrenme Paketleri/HF04A - Fire ve Donanım Gereksinimi|HF04A]]
- **Makine (donanım) sayısı:** Talep, işlem süresi ve uygun süreden gerekli makine sayısı; yukarı yuvarlanır. $$m=\left\lceil\frac{\text{Talep}\times t}{\text{Uygun süre}\times \text{verim}}\right\rceil$$ [[09 Öğrenme Paketleri/HF04A - Fire ve Donanım Gereksinimi|HF04A]]
- **Operatör–makine atama:** Bir operatöre kaç makine atanacağının ekonomik dengesi; operatör ve makine aylak süreleri arasında. [[09 Öğrenme Paketleri/HF04B - Operatör Makine Atama|HF04B]]
- **Çevrim süresi $T(m)$:** $m$ makineli sistemin tekrarlanan çevrim süresi; servis ve makine süresinden türetilir. $$T(m)=\max\{\,l+w,\; m(l+s)\,\}$$ [[09 Öğrenme Paketleri/HF04B - Operatör Makine Atama|HF04B]]
- **İdeal makine sayısı $r(m)$:** Operatörün boş kalmadan idare edebileceği makine sayısı sınırı. $$r=\frac{l+w}{l+s}$$ [[09 Öğrenme Paketleri/HF04B - Operatör Makine Atama|HF04B]]

---

## Bölüm 3 — Hücresel İmalat ve Akış

- **Grup teknolojisi (GT):** Benzer parçaların ailelere, makinelerin hücrelere ayrılması ilkesi. [[01 Ders Notları/HF05 - Akış, Alan ve Etkinlik İlişkileri I#Grup teknolojisi|HF05]]
- **DCA (Direct Clustering Algorithm):** 0–1 makine-parça matrisini satır/sütun toplamlarıyla yeniden sıralayıp blok köşegen yapı arayan kümeleme. [[09 Öğrenme Paketleri/HF05A - DCA ve ROC Hücre Oluşturma|HF05A]]
- **ROC (Rank Order Clustering):** Satır ve sütunlara ikili (binary) ağırlık verip azalan sıralamayı yineleyen blok köşegenleştirme. [[09 Öğrenme Paketleri/HF05A - DCA ve ROC Hücre Oluşturma|HF05A]]
- **İkili (binary) ağırlık:** Bir satır/sütundaki 1'lerin konumuna $2^{k}$ ağırlığı verilerek hesaplanan sıralama değeri. $$w_{\text{satır}}=\sum_j a_{ij}\,2^{(n-j)}$$ [[09 Öğrenme Paketleri/HF05A - DCA ve ROC Hücre Oluşturma|HF05A]]
- **G/A (girdi-aykırı) oranı:** Hücre değerlendirmesinde hücre içi ve hücre dışı elemanların payı; gruplama verimliliği göstergesi. [[09 Öğrenme Paketleri/HF05B - Küme Maliyet Analizi ve Hollier|HF05B]]
- **Hücre (gruplama) verimliliği:** Köşegen blok içindeki 1'lerin tüm 1'lere ve boşluklara göre kalitesini ölçen oran. [[09 Öğrenme Paketleri/HF05B - Küme Maliyet Analizi ve Hollier|HF05B]]
- **Hollier yöntemi:** Makineleri çıkış/giriş oranına göre dizip geri akışı (backtracking) en aza indiren tek yönlü sıralama. $$\text{Oran}_i=\frac{\sum \text{çıkış}_i}{\sum \text{giriş}_i}$$ [[09 Öğrenme Paketleri/HF05B - Küme Maliyet Analizi ve Hollier|HF05B]]
- **MAG (malzeme akış grafiği) şiddeti:** Bölümler arası akış miktarının yük/dönem cinsinden ölçülmesi. [[09 Öğrenme Paketleri/HF06A - MAG Akış Şiddeti ve From-To Matrisi|HF06A]]
- **From-to matrisi:** Bölümler arası yönlü akış miktarını satır=kaynak, sütun=hedef olarak veren nicel tablo. [[01 Ders Notları/HF06 - Akış, Alan ve Etkinlik İlişkileri II#From-to matrisi|HF06]]

---

## Bölüm 4 — Alan ve İlişki

- **Faaliyet ilişki diyagramı (REL):** Bölümler arası yakınlık isteğini harf kodlarıyla gösteren üçgen şema. [[01 Ders Notları/HF06 - Akış, Alan ve Etkinlik İlişkileri II#Faaliyet ilişki şeması|HF06]]
- **A-E-I-O-U-X kodları:** Yakınlık derecesi — A (mutlak), E (çok önemli), I (önemli), O (sıradan), U (önemsiz), X (istenmez). [[09 Öğrenme Paketleri/HF06B - Faaliyet İlişki Diyagramı ve Alan Hesabı|HF06B]]
- **Alan gereksinimi:** Üretim, destek ve personel alanlarının toplamı; makine, pay ve koridorla hesaplanır. [[01 Ders Notları/HF06 - Akış, Alan ve Etkinlik İlişkileri II#Alan gereksinimi|HF06]]
- **Alan katsayısı (allowance):** Makine ayak izine eklenen bakım/operatör/koridor payı çarpanı. $$A_{\text{toplam}}=A_{\text{makine}}\,(1+\text{katsayı})$$ [[09 Öğrenme Paketleri/HF06B - Faaliyet İlişki Diyagramı ve Alan Hesabı|HF06B]]
- **Destek oranı:** Destek alanının üretim alanına oranı; yardımcı hizmet alanını boyutlamada kullanılır. [[09 Öğrenme Paketleri/HF06B - Faaliyet İlişki Diyagramı ve Alan Hesabı|HF06B]]

---

## Bölüm 5 — Yerleşim Algoritmaları: İyileştirme

- **İyileştirme (improvement) mantığı:** Var olan bir yerleşimden başlayıp takaslarla maliyeti düşürmek. [[01 Ders Notları/HF08 - Yerleşim Tasarımı II|HF08]]
- **İkili yer değiştirme (pairwise exchange):** İki bölümün yerini değiştirip toplam taşıma maliyetindeki değişimi sınamak. [[09 Öğrenme Paketleri/HF08A - İkili Yer Değişim Yöntemi|HF08A]]
- **CRAFT:** From-to ve uzaklık matrisleriyle çalışan, ağırlık merkezi tabanlı ikili/üçlü takas iyileştirme algoritması. [[01 Ders Notları/HF08 - Yerleşim Tasarımı II#CRAFT|HF08]] · [[09 Öğrenme Paketleri/HF08C - CRAFT Yöntemi|HF08C]]
- **Maliyet değişimi $\Delta C$:** Bir takasın getirdiği maliyet farkı; negatifse takas kabul edilir. $$\Delta C = C_{\text{yeni}}-C_{\text{eski}}$$ [[09 Öğrenme Paketleri/HF08A - İkili Yer Değişim Yöntemi|HF08A]]
- **Ağırlık merkezi (centroid):** Bir bölümün taşıma maliyeti hesabında kullanılan geometrik merkezi. $$(\bar x,\bar y)=\left(\tfrac{\sum A_k x_k}{\sum A_k},\tfrac{\sum A_k y_k}{\sum A_k}\right)$$ [[09 Öğrenme Paketleri/HF08C - CRAFT Yöntemi|HF08C]]
- **Grafik tabanlı yerleşim:** Komşuluk grafiğiyle ilişkili bölümleri bitişik yerleştiren iyileştirme yaklaşımı. [[09 Öğrenme Paketleri/HF08B - Grafik Tabanlı Yerleşim|HF08B]]

---

## Bölüm 6 — Yerleşim Algoritmaları: Kurma

- **Kurma (construction) mantığı:** Boş alana bölümleri sırayla ekleyerek yerleşim oluşturmak. [[01 Ders Notları/HF09 - Yerleşim Tasarımı III|HF09]]
- **MCRAFT:** CRAFT'ın bölümleri eşit genişlikte şeritlere yerleştiren kurma sürümü. [[09 Öğrenme Paketleri/HF09A - MCRAFT|HF09A]]
- **BLOCPLAN:** Bölümleri yatay bantlara yerleştirip REL puanı ($Z_A$) ve uzaklık oranı (ER) ile değerlendiren kurma/iyileştirme yöntemi. [[09 Öğrenme Paketleri/HF09B - BLOCPLAN|HF09B]]
- **$Z_A$ (yakınlık puanı):** BLOCPLAN'da bitişik bölümlerin REL değerlerinin toplamı. [[09 Öğrenme Paketleri/HF09B - BLOCPLAN|HF09B]]
- **ER (efficiency ratio / uzaklık oranı):** BLOCPLAN'da normalize edilmiş yerleşim kalite ölçütü. [[09 Öğrenme Paketleri/HF09B - BLOCPLAN|HF09B]]
- **LOGIC:** Bölümleri yinelemeli olarak dikey/yatay kesimlerle ikiye bölen kesim ağacı (slicing tree) tabanlı kurma yöntemi. [[09 Öğrenme Paketleri/HF09C - LOGIC ve Kesim Ağacı|HF09C]]
- **Kesim ağacı (slicing tree):** Yerleşimin ardışık yatay/dikey bölmelerle oluşturulduğu ağaç yapısı. [[09 Öğrenme Paketleri/HF09C - LOGIC ve Kesim Ağacı|HF09C]]
- **CORELAP:** TCR sırasına göre en yüksek yerleşim puanlı (PR) konuma bölüm ekleyen ilişki tabanlı kurma yöntemi. [[01 Ders Notları/HF10 - Yerleşim Tasarımı IV|HF10]] · [[09 Öğrenme Paketleri/HF10A - CORELAP|HF10A]]
- **TCR (Total Closeness Rating):** Bir bölümün diğerleriyle yakınlık değerlerinin toplamı; CORELAP giriş sırasını belirler. [[09 Öğrenme Paketleri/HF10A - CORELAP|HF10A]]
- **ALDEP:** Bölümleri rastgele tohumla başlatıp tarama deseniyle yerleştiren ve REL puanı veren kurma yöntemi. [[09 Öğrenme Paketleri/HF10B - ALDEP|HF10B]]
- **MULTIPLE:** Uzay doldurma eğrisiyle (space-filling curve) bölümleri yerleştiren ve takasla iyileştiren melez yöntem. [[09 Öğrenme Paketleri/HF10C - MULTIPLE|HF10C]]
- **$\alpha$ katsayısı:** ALDEP/MULTIPLE'da REL harf kodlarını sayısal puana çeviren ölçek (ör. A=64, E=16, …). [[09 Öğrenme Paketleri/HF10B - ALDEP|HF10B]]

---

## Bölüm 7 — Konum Modelleri: Sürekli

- **Minisum:** Toplam ağırlıklı uzaklığı en aza indiren tek tesis konumu. $$\min\sum_i w_i\bigl(|x-a_i|+|y-b_i|\bigr)$$ [[01 Ders Notları/HF11 - Tesis Konumu I#Tek tesis minisum|HF11]] · [[09 Öğrenme Paketleri/HF11A - Minisum ve Ağırlıklı Medyan|HF11A]]
- **Ağırlıklı medyan:** Minisum çözümünü her eksende kümülatif ağırlık $W/2$'ye ulaşınca veren koordinat. [[09 Öğrenme Paketleri/HF11A - Minisum ve Ağırlıklı Medyan|HF11A]]
- **Eşit yarı durumu:** Kümülatif ağırlık tam $W/2$ olduğunda optimum tek nokta değil bir aralıktır. [[09 Öğrenme Paketleri/HF11A - Minisum ve Ağırlıklı Medyan|HF11A]]
- **Minimax:** En büyük uzaklığı en aza indiren konum; acil hizmet yer seçiminde kullanılır. $$\min\max_i \bigl(|x-a_i|+|y-b_i|\bigr)$$ [[01 Ders Notları/HF11 - Tesis Konumu I#Tek tesis minimax|HF11]] · [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|HF11B]]
- **u-v dönüşümü:** Dikdoğrusal minimax'ı Chebyshev biçimine çeviren koordinat dönüşümü. $$u=x+y,\qquad v=x-y$$ [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|HF11B]]
- **$R^{*}$ (en küçük kapsama yarıçapı):** Minimax çözümünün minimum maksimum uzaklığı. $$R^{*}=\tfrac{1}{2}\max\{c_5-c_1,\,c_6-c_2\}$$ [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|HF11B]]
- **Optimum çözüm aralığı/kümesi:** Minimax'ta aynı $R^{*}$'ı veren noktaların oluşturduğu doğru parçası veya bölge. [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|HF11B]]

---

## Bölüm 8 — Konum Modelleri: Kesikli

- **Kesikli konum:** Yeni tesisin yalnız önceden belirlenmiş aday yerlere konabildiği durum. [[01 Ders Notları/HF12 - Tesis Konumu II|HF12]]
- **Açma-atama modeli:** Hangi adayların açılacağını ($y_i$) ve müşterilerin hangi tesise atanacağını ($x_{ij}$) belirleyen tamsayılı model. [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|HF12B]]
- **$y_i$ (açma değişkeni):** Aday $i$ açılırsa 1, açılmazsa 0 olan ikili karar değişkeni. [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|HF12B]]
- **$x_{ij}$ (atama değişkeni):** Müşteri $j$, tesis $i$'ye atanırsa 1 olan değişken; $x_{ij}\le y_i$ kısıtına bağlıdır. [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|HF12B]]
- **Enümerasyon (tam sayım):** Tüm açma kombinasyonlarını tek tek değerlendirip en düşük maliyetliyi seçen çözüm. [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|HF12B]]
- **Net tasarruf:** Bir tesisi açmanın getirdiği taşıma tasarrufundan açma maliyeti çıkarıldığında kalan değer. [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|HF12B]]
- **$p$-medyan:** Tam $p$ tesis açıp toplam ağırlıklı uzaklığı en aza indiren model ailesi. [[01 Ders Notları/HF12 - Tesis Konumu II#Model ailesi|HF12]] · [[09 Öğrenme Paketleri/HF12A - Konum Atama ve Tesis Sayısı|HF12A]]
- **$p$-merkez:** Tam $p$ tesis açıp en uzak müşterinin uzaklığını en aza indiren (minimax türü) model. [[01 Ders Notları/HF12 - Tesis Konumu II#Model ailesi|HF12]] · [[09 Öğrenme Paketleri/HF12A - Konum Atama ve Tesis Sayısı|HF12A]]

---

## İlgili

- [[09 Öğrenme Paketleri/Öğrenme Paketleri|Öğrenme paketleri dizini]]
- [[07 Ekler/Diyagramlar/Görsel Atlas|Görsel Atlas]]
