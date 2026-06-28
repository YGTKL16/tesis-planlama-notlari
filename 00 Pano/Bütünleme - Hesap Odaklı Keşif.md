---
tags: [ders/tesis-planlama, bütünleme, keşif, hesap]
durum: hazır
---

# Bütünleme - Hesap Odaklı Keşif

> [!warning] Kapsam henüz açıklanmadı
> Bu sayfa kesin sınav kapsamı değildir. Range açıklanana kadar ders sunumlarındaki hesap türlerini kaybetmemek ve hazırlığı önceliklendirmek için oluşturulmuştur.

## Başlangıç kararı

- Mevcut kısa ders notları **konu haritası** olarak kullanılabilir; hesap çalışmasının ana kaynağı kabul edilmez.
- Her yöntem, ilgili PPTX slaytı ve slayt görselleri üzerinden doğrulanır.
- Ham Markdown metinleri arama için kullanılır; `Resim*.jpg` olarak kalan denklem, tablo ve yerleşimler doğrudan PPTX'ten okunur.
- Her hesap için kaynak hafta ve slayt numarası kaydedilir.

## Öncelik sırası

| Öncelik | Konu kümesi | Gerekçe |
|:---:|---|---|
| P0 | HF03-HF04 | Rassal ıskarta, fire, donanım ve operatör-makine soruları çok adımlı; mevcut notlarda ciddi eksik var. |
| P0 | HF07-HF10 | Yerleşim puanları ve algoritmalar sunumlarda uzun hesaplarla işlenmiş; mevcut soru bankasında uygulama yok. |
| P0 | HF11-HF12 | Minisum, minimax, location-allocation ve tesis konum modelleri hesap/model kurma gerektiriyor. |
| P1 | HF02 | Tek/çok ürün başa baş, yap-satın al ve dinamik kapasite büyümesi. |
| P1 | HF05-HF06 | Hücre oluşturma, Hollier, akış şiddeti, from-to, ilişki ve alan hesapları. |
| P2 | HF01 | Ağırlıklı olarak kavramsal temel ve tesis planlama süreci. |

## Hesap türü envanteri

| Hafta | Hesap / uygulama ailesi | Kaynaktaki belirgin örnekler | Mevcut durum |
|---:|---|---|---|
| HF02 | Kapasite kullanım oranı | Kullanım oranı örneği | Temel formül var |
| HF02 | Tek ürün başa baş ve kâr | Örnek 3-5, çalışma soruları | Yalnız bir basit soru var |
| HF02 | Çok ürünlü başa baş | Ham metin yaklaşık 552-630 | Eksik |
| HF02 | Yap veya satın al | Örnek 6 | Formül var, yeterli soru yok |
| HF02 | Dinamik kapasite büyümesi | Örnek 7 | Eksik |
| HF03 | Düşük hacimde rassal ıskarta | Binom olasılığı, net gelir ve beklenen kârla optimal üretim miktarı | Kritik eksik |
| HF04 | Yüksek hacimde fireyi geriye yürütme | Örnek 1-3 | Temel formül var, işlem tablosu yok |
| HF04 | Donanım / makine gereksinimi | Örnek 4-7 ve çözümlü sorular | Tek basit örnek var |
| HF04 | Operatör-makine atama | Örnek 8-12 | Kritik eksik |
| HF05 | DCA ve ROC | Matris satır-sütun sıralama ve iterasyon | Eksik |
| HF05 | Küme tanılama ve maliyet analizi | Parça-makine hücresi örnekleri | Eksik |
| HF05 | Hollier | Bölüm sırası ve ileri/geri akış yüzdeleri | Eksik |
| HF06 | MAG akış şiddeti | Dönüşüm tablosu ve 137.000 MAG örneği | Eksik |
| HF06 | From-to matrisi | Yönlü ve toplam akış örnekleri | Formül var, matris kurma sorusu yok |
| HF06 | Faaliyet ilişki ve alan hesabı | İlişki diyagramı ile alan katsayısı örnekleri | Eksik |
| HF07 | Süreç yerleşim maliyeti | Maliyeti 570'ten 480'e indiren örnek | Eksik |
| HF07 | Komşuluk ve uzaklık puanı | Örnek 2-4 | Yalnız genel formüller var |
| HF07 | İlişki diyagramı yerleştirme | Metot I ve II | Eksik |
| HF08 | İkili yer değişimi | Aday değişim ve yeni maliyet hesabı | Eksik |
| HF08 | Grafik tabanlı yöntem | Komşuluk grafiği ve blok yerleşim | Eksik |
| HF08 | CRAFT | Merkez, uzaklık ve maliyet matrisi; iterasyonlar | Kritik eksik |
| HF09 | MCRAFT | Değişim ve nihai maliyet örnekleri | Eksik |
| HF09 | BLOCPLAN | Toplam akış, etkinlik oranı ve REL-DIST | Kritik eksik |
| HF09 | LOGIC | Giyotin kesimler ve uzaklık esaslı yerleşim | Mevcut not hatalı/eksik |
| HF10 | CORELAP | TCR, bölüm sırası, yerleştirme puanı ve bağ bozma | Kritik eksik |
| HF10 | ALDEP | Sıra üretme, alan doldurma ve yerleşim puanı | Eksik |
| HF10 | MULTIPLE | Doldurma eğrisi, değişim ve çok katlı yerleşim | Mevcut not yöntemi temsil etmiyor |
| HF11 | Ağırlıklı medyan / minisum | Konum, toplam maliyet ve alternatif adaylar | Yalnız temel örnek var |
| HF11 | Eş maliyet eğrileri | Altı adımlı prosedür | Eksik |
| HF11 | Minimax | Dönüşüm, optimum çözüm kümesi ve maksimum uzaklık | Kritik eksik |
| HF12 | Location-allocation | Tesis sayısı, müşteri kümeleri ve her kümede minisum | Kritik eksik |
| HF12 | Kesikli tesis konum modeli | Açma-atama, sabit ve hizmet maliyeti | Model eksik temsil edilmiş |

## Minimum keşif paketi

Range açıklanana kadar her hesap ailesi için yüzlerce soru üretmek yerine önce şunlar hazırlanır:

1. **Yöntem kartı:** Ne zaman kullanılır, verilenler, formül/algoritma ve çözüm sırası.
2. **Bir kaynak örneği:** Hocanın slaytındaki örnek, bütün ara adımlarıyla yeniden yazılır.
3. **Bir temel varyant:** Aynı beceriyi farklı sayılarla ölçer.
4. **Bir tuzaklı varyant:** Yöntem seçimi, yuvarlama, birim veya bağ bozma içerir.
5. **Hata kartı:** En sık yapılabilecek iki hata ve sonuç kontrolü.

## Çözüm standardı

Her çözüm şu sırayı izler:

1. Verilenler ve istenen.
2. Yöntemin seçilme gerekçesi.
3. Formül, model veya algoritma adımları.
4. Ara hesaplar ve tablolar.
5. Birim ve gerekiyorsa yukarı yuvarlama.
6. Sonucun karar cümlesiyle yorumu.
7. Kaynak: hafta ve slayt numarası.

## Bilinen doğruluk riskleri

- Ağırlıklı medyanda kümülatif ağırlık toplamın tam yarısına eşitse tek nokta yerine bir **optimum aralık** oluşabilir.
- Başa baş miktarı kesirliyse uygulanabilir en küçük adet için sonuç yukarı yuvarlanır.
- Fire hesabında yalnız son toplamı yukarı yuvarlamak, her operasyonda tam parça zorunluluğu varsa hedefi karşılamayabilir.
- Kesikli tesis konum modelinde `x_{ij}` ve `y_i` değişkenlerinin ikili olduğu yazılmalıdır.
- A-E-I-O-U-X sayısal ağırlıkları evrensel değildir; soruda verilen dönüşüm kullanılır.
- LOGIC, mevcut kısa nottaki anlatımın aksine kaynak sunumda uzaklık esaslı ve giyotin kesimli bir yöntemdir.

## Keşif ilerlemesi

| Küme | Kaynak örnekleri çıkarıldı | Yöntem kartları | Temel sorular | Tuzaklı sorular |
|---|:---:|:---:|:---:|:---:|
| HF02 | ☑ | ☑ | ☑ | ☑ |
| HF03-HF04 | ☑ | ☑ | ☑ | ☑ |
| HF05-HF06 | ☑ | ☑ | ☑ | ☑ |
| HF07-HF08 | ☑ | ☑ | ☑ | ☑ |
| HF09-HF10 | ☑ | ☑ | ☑ | ☑ |
| HF11-HF12 | ☑ | ☑ | ☑ | ☑ |

## Hazır öğrenme paketleri

- [[09 Öğrenme Paketleri/Öğrenme Paketleri|Öğrenme Paketleri Dizini]]

HF02-HF12 arasındaki hesap yoğun 26 paket ile [[09 Öğrenme Paketleri/HF01 - Kavramsal Aktif Geri Getirme|HF01 kavramsal geri getirme paketi]] tamamlandı.

## Range açıklandığında

1. Kapsam dışı haftalar dondurulur; hazırlanmış içerik silinmez.
2. Kapsam içindeki her hesap ailesi L1-L2-L3 sorularla genişletilir.
3. Yanlışlar `yöntem`, `formül/model`, `veri aktarımı`, `işlem`, `birim`, `yuvarlama`, `yorum` olarak kodlanır.
4. Konu kümelerinden sonra süreli karma denemelere geçilir.

## Bağlantılar

- [[Ders Haritası]]
- [[Çalışma Takibi]]
- [[Kanıta Dayalı Öğrenme Sistemi]]
- [[06 Şablonlar/Hesap Öğrenme Paketi Şablonu|Hesap Öğrenme Paketi Şablonu]]
- [[03 Formüller/Formül Föyü|Formül Föyü]]
- [[04 Sorular/Soru Bankası|Mevcut Soru Bankası]]
- [[05 Kaynaklar/Kaynaklar|Kaynaklar]]
