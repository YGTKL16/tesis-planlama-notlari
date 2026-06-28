---
aliases: [Görsel Atlas, Diyagram Atlası]
tags: [ders/tesis-planlama, görsel, mermaid, tikz]
---

# Görsel Atlas

> [!info]
> Mermaid diyagramları Obsidian içinde canlıdır. TikZ kaynakları `07 Ekler/TikZ Kaynakları`, derlenmiş SVG'ler bu klasördedir.

## Dersin bütünü

![[07 Ekler/Diyagramlar/tesis-planlama-sureci.svg]]

![[07 Ekler/Diyagramlar/yontem-uzayi.svg]]

## Kapasite ve ilişki

![[07 Ekler/Diyagramlar/kapasite-stratejileri.svg]]

![[07 Ekler/Diyagramlar/faaliyet-iliski-diyagrami.svg]]

## ROC döngüsü

```mermaid
flowchart LR
    A[0-1 makine-parça matrisi] --> B[Satır ikili değerlerini hesapla]
    B --> C[Satırları azalan sırala]
    C --> D[Sütun ikili değerlerini hesapla]
    D --> E[Sütunları azalan sırala]
    E --> F{Sıra değişti mi?}
    F -- Evet --> B
    F -- Hayır --> G[Blok köşegen hücreleri yorumla]
```

Paket: [[09 Öğrenme Paketleri/HF05A - DCA ve ROC Hücre Oluşturma|HF05A]]

## Yerleşim iyileştirme döngüsü

```mermaid
flowchart TD
    A[Başlangıç yerleşimi] --> B[Merkez ve uzaklıkları hesapla]
    B --> C[Mevcut maliyet Z]
    C --> D[Uygun bölüm çiftlerini üret]
    D --> E[Her takas için yeni Z]
    E --> F{En iyi takas iyileştiriyor mu?}
    F -- Evet --> G[Takası uygula]
    G --> B
    F -- Hayır --> H[Yerel optimumda dur]
```

Paketler: [[09 Öğrenme Paketleri/HF08A - İkili Yer Değişim Yöntemi|İkili değişim]], [[09 Öğrenme Paketleri/HF08C - CRAFT Yöntemi|CRAFT]], [[09 Öğrenme Paketleri/HF09A - MCRAFT|MCRAFT]]

## CORELAP kurma mantığı

```mermaid
flowchart LR
    A[REL tablosu] --> B[TCR değerleri]
    B --> C[İlk bölümü seç]
    C --> D[En güçlü ilişkili sıradaki bölüm]
    D --> E[Olası konumların PR puanı]
    E --> F[En yüksek PR konumuna yerleştir]
    F --> G{Bölüm kaldı mı?}
    G -- Evet --> D
    G -- Hayır --> H[Blok yerleşim]
```

Paket: [[09 Öğrenme Paketleri/HF10A - CORELAP|HF10A]]

## Konum modelleri

```mermaid
flowchart TD
    A[Konum sorusu] --> B{Aday yerler sabit mi?}
    B -- Evet --> C[Açma-atama: ikili y ve x]
    B -- Hayır --> D{Tek tesis mi?}
    D -- Hayır --> E[Konum-atama iterasyonu]
    D -- Evet --> F{Amaç toplam mı?}
    F -- Evet --> G[Minisum: ağırlıklı medyan]
    F -- Hayır --> H[Minimax: u=x+y, v=x-y]
```

Paketler: [[09 Öğrenme Paketleri/HF11A - Minisum ve Ağırlıklı Medyan|Minisum]], [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|Minimax]], [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|Açma-atama]]

### Minimax çözüm kümesi

![[07 Ekler/Diyagramlar/minimax-cozum-kumesi.svg]]

## Haftalık konu haritası (HF01–HF12)

Dersin akışı: her hafta bir öncekinin üzerine kurulur. Kapasite ve süreç kararları ürünü tanımlar, akış ve alan analizi yerleşimi besler, yerleşim algoritmaları tesis içini çözer, konum modelleri ise tesisin dış dünyadaki yerini belirler.

```mermaid
flowchart LR
    H01[HF01<br/>Giriş ve ürün-süreç-çizelgeleme] --> H02[HF02<br/>Kapasite planlama / BEP]
    H02 --> H03[HF03<br/>Süreç tasarımı II / ıskarta]
    H03 --> H04[HF04<br/>Süreç III / makine-operatör]
    H04 --> H05[HF05<br/>Akış I / grup teknolojisi]
    H05 --> H06[HF06<br/>Akış II / from-to ve alan]
    H06 --> H07[HF07<br/>Yerleşim I / SLP]
    H07 --> H08[HF08<br/>Yerleşim II / CRAFT]
    H08 --> H09[HF09<br/>Yerleşim III / MCRAFT-BLOCPLAN-LOGIC]
    H09 --> H10[HF10<br/>Yerleşim IV / CORELAP-ALDEP-MULTIPLE]
    H10 --> H11[HF11<br/>Konum I / minisum-minimax]
    H11 --> H12[HF12<br/>Konum II / kesikli ve p-medyan]

    subgraph KAP[Kapasite ve süreç]
        H01
        H02
        H03
        H04
    end
    subgraph AKIS[Akış ve alan]
        H05
        H06
    end
    subgraph YER[Yerleşim algoritmaları]
        H07
        H08
        H09
        H10
    end
    subgraph KON[Konum modelleri]
        H11
        H12
    end
```

## Minisum vs Minimax karar akışı

Tek tesis sürekli konum probleminde amaç fonksiyonu yöntemi belirler: **toplam** maliyet minisum'a, **en kötü** uzaklık minimax'a götürür.

```mermaid
flowchart TD
    A[Tek tesis, sürekli düzlem<br/>uzaklık dikdoğrusal] --> B{Amaç nedir?}
    B -- Toplam ağırlıklı<br/>uzaklığı küçült --> C[Minisum]
    B -- En büyük<br/>uzaklığı küçült --> D[Minimax]
    C --> E[Her eksende<br/>ağırlıklı medyan]
    E --> F["x*: kümülatif ağırlık ilk kez W/2'yi aşan koordinat<br/>(eşitse aralık)"]
    F --> G["f = Σ wᵢ (|x−aᵢ|+|y−bᵢ|)"]
    D --> H["u = x+y, v = x−y dönüşümü"]
    H --> I["R* = ½ · max{c₅−c₁, c₆−c₂}"]
    I --> J[Optimum çözüm kümesi:<br/>doğru parçası / bölge]
```

Paketler: [[09 Öğrenme Paketleri/HF11A - Minisum ve Ağırlıklı Medyan|Minisum]], [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|Minimax]]

## Yerleşim algoritmaları karar ağacı

Önce **iyileştirme mi kurma mı** sorusu sorulur: elde bir yerleşim varsa iyileştir, yoksa sıfırdan kur. Sonra veri türü (from-to mu, REL mi) alt yöntemi belirler.

```mermaid
flowchart TD
    A[Yerleşim problemi] --> B{Başlangıç yerleşimi<br/>var mı?}

    B -- Evet, iyileştir --> C{Veri türü?}
    C -- Nicel akış<br/>from-to + uzaklık --> C1[CRAFT<br/>ağırlık merkezi takası]
    C -- İki bölüm dene --> C2[İkili yer değiştirme]
    C -- İlişki grafiği --> C3[Grafik tabanlı]

    B -- Hayır, sıfırdan kur --> D{Yerleştirme mantığı?}
    D -- Şerit / bant --> D1{Hangi şerit yöntemi?}
    D1 -- Eşit genişlik şerit --> D1a[MCRAFT]
    D1 -- Yatay bant + REL --> D1b[BLOCPLAN]
    D -- Kesim ağacı --> D2[LOGIC<br/>slicing tree]
    D -- İlişki TCR sırası --> D3[CORELAP<br/>en yüksek PR konumu]
    D -- Rastgele tohum + tarama --> D4[ALDEP]
    D -- Uzay doldurma eğrisi --> D5[MULTIPLE]
```

Paketler: [[09 Öğrenme Paketleri/HF08C - CRAFT Yöntemi|CRAFT]], [[09 Öğrenme Paketleri/HF09A - MCRAFT|MCRAFT]], [[09 Öğrenme Paketleri/HF09B - BLOCPLAN|BLOCPLAN]], [[09 Öğrenme Paketleri/HF09C - LOGIC ve Kesim Ağacı|LOGIC]], [[09 Öğrenme Paketleri/HF10A - CORELAP|CORELAP]], [[09 Öğrenme Paketleri/HF10B - ALDEP|ALDEP]], [[09 Öğrenme Paketleri/HF10C - MULTIPLE|MULTIPLE]]

## Kesikli vs sürekli konum karar akışı

Yeni tesisin yerleşebileceği nokta kümesi modeli belirler: **her koordinat** serbestse sürekli, yalnız **sayılı aday** varsa kesikli model kullanılır.

```mermaid
flowchart TD
    A[Konum sorusu] --> B{Yeni tesis nereye<br/>konabilir?}
    B -- Sayılı aday yer<br/>+ açma maliyeti --> C[Kesikli model]
    B -- Düzlemde<br/>herhangi bir nokta --> D[Sürekli model]

    C --> C1{Tesis sayısı<br/>kararı?}
    C1 -- Açılacak sayı<br/>serbest --> C2[Açma-atama modeli<br/>yᵢ açma, x_ij atama]
    C1 -- Tam p tesis,<br/>toplam uzaklık --> C3[p-medyan]
    C1 -- Tam p tesis,<br/>en kötü uzaklık --> C4[p-merkez]
    C2 --> C5[Enümerasyon /<br/>net tasarruf]

    D --> D1{Tesis sayısı?}
    D1 -- Tek tesis --> D2{Amaç?}
    D2 -- Toplam --> D2a[Minisum / ağırlıklı medyan]
    D2 -- En kötü --> D2b[Minimax / u-v dönüşümü]
    D1 -- Çoklu tesis --> D3[Konum-atama iterasyonu]
```

Paketler: [[09 Öğrenme Paketleri/HF12A - Konum Atama ve Tesis Sayısı|Konum-atama]], [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|Açma-atama]]

## NumPy Grafikleri ve Hesap Görselleri

Bu bölümdeki grafikler, ders notlarındaki matematiksel algoritmaların sayısal sonuçlarını görsel olarak anlamanıza yardımcı olması için Python ve NumPy ile üretilmiştir.

### 1. Kapasite ve Finans
#### Başa Baş Noktası Analizi
![[07 Ekler/Grafikler/basa-bas-grafigi.svg]]
* **Açıklama:** Sabit maliyetler ($F$), birim satış fiyatı ($P$) ve birim değişken maliyet ($V$) arasındaki ilişkiyi gösterir. Katkı payı doğrusu ve toplam maliyet doğrusunun kesişim noktası **Başa Baş Satış Hacmi** ($BEP = F/(P-V)$) olarak işaretlenmiştir.

#### Operatör-Makine Atama Maliyet Eğrisi
![[07 Ekler/Grafikler/operator-makine-maliyet.svg]]
* **Açıklama:** Bir operatöre atanan makine sayısı ($m$) arttıkça, birim başına düşen toplam üretim maliyetinin değişimini gösterir. Operatör aylak süresi ile makine aylak süresi arasındaki ekonomik dengenin minimum noktasını ($m^*$) görselleştirir.

---

### 2. Hücre Tasarımı ve Akış
#### DCA / ROC Hücre Oluşturma
![[07 Ekler/Grafikler/roc-kumeleme.svg]]
* **Açıklama:** Sol tarafta unclustered (düzensiz) 0-1 makine-parça matrisi, sağ tarafta ise **ROC (Rank Order Clustering)** algoritması çalıştırıldıktan sonra blok-köşegen yapısına kavuşan matris görülmektedir. Kırmızı ve yeşil kesikli çizgiler, bağımsız imalat hücrelerini (Machine-Part Cells) temsil eder.

#### Hollier Akış Şeması (Backtracking Analizi)
![[07 Ekler/Grafikler/hollier-akis-semasi.svg]]
* **Açıklama:** Makinelerin Hollier sıralama oranına ($Ratio = Toplam Çıkış / Toplam Giriş$) göre soldan sağa dizilimini ve aralarındaki malzeme akışlarını ($f_{ij}$) gösterir. Üstteki yeşil yaylar ileri akışları, alttaki kırmızı yaylar ise geriye akışları (backtracking) temsil eder. Amaç, kırmızı yayların toplam şiddetini minimize etmektir.

#### Akış Şiddeti (From-To Matrisi)
![[07 Ekler/Grafikler/from-to-matrisi.svg]]
* **Açıklama:** Bölümler arasındaki akış yoğunluğunu (yük/dönem) sayısal ve renk yoğunluğuyla gösteren From-To ısı haritasıdır.

---

### 3. Tesis Konumu
#### Dikdoğrusal Minisum Konumu
![[07 Ekler/Grafikler/minisum-konum.svg]]
* **Açıklama:** Düzlemdeki mevcut tesislere olan toplam ağırlıklı mesafeyi minimize eden tek yeni tesisin konumunu gösterir. Optimal koordinat, her eksende bağımsız olarak ağırlıklı medyan ile bulunur.

#### Dikdoğrusal Minimax Geometrisi
![[07 Ekler/Grafikler/minimax-geometri.svg]]
* **Açıklama:** Maksimum dikdoğrusal mesafeyi minimize eden optimum noktaların kümesini gösterir. U-V koordinat dönüşümüyle elde edilen optimum çözüm, bu örnekte kırmızı renkli doğru parçasıdır. Çözüm kümesinin sınırları Manhattan çemberleriyle çevrelenmiştir.

#### Kesikli Tesis Konumu (Açma ve Atama Çözümü)
![[07 Ekler/Grafikler/kesikli-konum-atama.svg]]
* **Açıklama:** Sabit açma maliyeti olan aday konumlar arasından hangilerinin seçildiğini (açık yeşil üçgenler) ve hangi müşterilerin (mavi daireler) hangi açık tesislere atandığını (kesikli çizgilerle yönlendirmeler) gösterir.
