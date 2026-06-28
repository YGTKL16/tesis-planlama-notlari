---
başlık: "{{başlık}}"
hafta: "{{hafta}}"
konu: "{{konu}}"
düzey: "{{L1|L2|L3}}"
durum: 🔴
tags:
  - öğrenme-paketi
  - "{{konu-etiketi}}"
---

# {{başlık}}

> [!info] Şablonun kullanımı
> Bu bir **hesap (sayısal) öğrenme paketi** iskeletidir. `{{...}}` yer tutucularını ilgili haftanın verisiyle doldur, doldurduktan sonra `durum`u 🔴 → 🟡 → 🟢 olarak ilerlet. Örnek tam paket: [[09 Öğrenme Paketleri/HF11A - Minisum ve Ağırlıklı Medyan|HF11A]].
> İsteğe bağlı: en üste ilgili grafiği göm — `![[07 Ekler/Grafikler/{{görsel}}.svg]]`

> [!summary] Bir cümlede
> Bu yöntem **{{hangi koşulda}}** kullanılır ve **{{hangi değeri/kararı}}** bulur.

## Öğrenme hedefleri

- [ ] Sorunun verilerinden doğru yöntemi seçebilirim.
- [ ] Formülü / algoritmayı ezberden kurabilirim.
- [ ] Ara adımları birimleriyle yürütebilirim.
- [ ] Sonucu kontrol edip karar cümlesiyle yorumlayabilirim.

---

## 0 - Soğuk başlangıç sorusu

> [!tip] Nasıl kullanılır?
> Bu soruyu **çözümü açmadan** 3-5 dakika dene. Amaç doğru cevap değil, kafandaki ön kavramı ve sezgini ortaya çıkarmaktır. Yanıldığın yer, öğreten notta en çok dikkat etmen gereken yerdir.

> [!question]
> {{Yöntemi henüz görmemiş birinin sezgisini test eden kısa bir soru. Tek bir kritik kavrama (ör. eşitlik durumu, birim, yön) odaklan.}}

> [!answer]- Beklenen açıklama
> {{Doğru sezgi + neden. "Şu durumda şöyle olur çünkü ..." biçiminde.}}

---

## 1 - Öğreten not

### Ne zaman kullanılır?

Şu işaretler birlikte görülüyorsa bu yöntem kullanılır:

- {{koşul 1 — ör. düzlemde tek tesis konumlandırılacak}}
- {{koşul 2 — ör. uzaklık dikdoğrusal/Öklid}}
- {{koşul 3 — ör. amaç toplam mı, en kötü mü}}
- {{koşul 4 — ör. kapasite kısıtı var mı}}

Tipik uygulama: {{örnek bağlam — depo, hücre, atölye vb.}}

### Verilenler ve semboller

| Sembol | Anlam | Birim |
|---|---|---|
| {{sem}} | {{anlam}} | {{birim}} |
| {{sem}} | {{anlam}} | {{birim}} |
| {{sem}} | {{anlam}} | {{birim}} |

### Formül

$$
{{ana formül}}
$$

{{Gerekirse türetme / ayrıştırma açıklaması bir-iki cümle.}}

### Algoritma adımları

1. {{Adım 1 — veriyi hazırla / sırala}}
2. {{Adım 2 — ara büyüklüğü hesapla}}
3. {{Adım 3 — kuralı/koşulu uygula}}
4. {{Adım 4 — kararı oku}}
5. {{Adım 5 — amaç değerini hesapla ve kontrol et}}

> [!warning] Kritik nokta
> {{En sık yapılan hatanın olduğu adım — ör. eşitlik durumu, yuvarlama yönü, birim karışması.}}

### Sonuç kontrolü

{{Bulunan sonuç hangi formülle/mantıkla doğrulanır? Karar cümlesi nasıl yazılır?}}

### Benzer yöntemlerden farkı

| {{Bu yöntem}} | {{Karıştırılan yöntem}} |
|---|---|
| {{ayırt edici özellik}} | {{ayırt edici özellik}} |
| {{ne zaman}} | {{ne zaman}} |

---

## 2 - Kaynak örnek (tam çözüm)

> [!example] Kaynak: {{HF__}}, slayt {{__}}
> **Verilenler:** {{veri tablosu / metin}}
>
> **İstenen:** {{ne bulunacak}}

### Adım 1 - {{başlık}}

$$
{{hesap}}
$$

### Adım 2 - {{başlık}}

| {{sütun}} | {{sütun}} | {{sütun}} |
|---|---|---|
| {{}} | {{}} | {{}} |

### Adım 3 - {{başlık}}

$$
{{ara sonuç}}
$$

### Adım 4 - Amaç değeri ve karar

$$
{{amaç fonksiyonu değeri}}
$$

> [!success] Karar
> {{Sonucu birimiyle ve karar cümlesiyle yaz: "Optimum konum ... ve amaç değeri ...".}}

### Öz-açıklama

1. {{Bu yöntem neden seçildi?}}
2. {{En kritik ara adım hangisi ve neden?}}
3. {{Hangi varsayım değişirse çözüm değişir?}}

---

## 3 - Kademeli örnek (iskeleli)

> [!question]
> {{Soru metni.}} Boşlukları çözümü açmadan tamamla:
>
> 1. {{verilen}} → $\_\_$
> 2. {{ara büyüklük}} = $\_\_$
> 3. {{kural uygulanır}} → $\_\_$
> 4. {{karar}} = $\_\_$
> 5. Amaç değeri $f=\_\_$

> [!answer]- Tam çözüm
> 1. Yöntem seçimi: {{}}
> 2. Kurulum: {{}}
> 3. Ara hesaplar: {{}}
> 4. Birim ve yuvarlama: {{}}
> 5. Karar: {{}}

---

## 4 - Bağımsız sorular

### L1 - Temel

> [!question]
> {{Yöntem adı verilir; tek aşamalı düz uygulama.}}

> [!answer]- Çözüm
> {{kısa çözüm + sonuç}}

### L2 - Tuzaklı / aktarım

> [!question]
> {{Eşitlik, birim değişimi, eksik veri veya aktarım gerektiren varyant.}}

> [!answer]- Çözüm
> {{çözüm + neden tuzak olduğu}}

### L3 - Yöntemi seç

> [!question]
> Yöntem adı verilmez. Her durum için verilenlerden uygun yaklaşımı seç:
>
> 1. {{durum}}
> 2. {{durum}}
> 3. {{durum}}

> [!answer]- Çözüm
> 1. {{yöntem + gerekçe}}
> 2. {{yöntem + gerekçe}}
> 3. {{yöntem + gerekçe}}

---

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. {{Bu yöntem ne zaman kullanılır? (tek cümle)}}

---

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli örnek |  |  |  |
| D1 |  | L1 |  |  |  |
| D3 |  | L2 |  |  |  |
| D7 |  | Kaynak örneğini kapalı kitap çöz |  |  |  |
| D14 |  | L3 + karma test |  |  |  |

---

## Hata kartı

> [!note] Kod anahtarı
> **YÖN** yön/işaret · **MOD** yanlış model/yöntem · **VER** veri okuma · **İŞL** işlem/aritmetik · **BİR** birim · **YUV** yuvarlama · **YOR** yorum/karar

| Tarih | YÖN | MOD | VER | İŞL | BİR | YUV | YOR | Yanlış adım | Sonraki kontrolde ne yapacağım? |
|---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|---|---|
|  |  |  |  |  |  |  |  | {{}} | {{}} |
|  |  |  |  |  |  |  |  | {{}} | {{}} |

---

## Kaynaklar

- Ders sunumu: {{HF__}}, slayt {{__-__}}
- Ham metin: `05 Kaynaklar/MarkItDown/{{HF__}} - Ham.md`
- Kavram: [[02 Kavramlar/Kavram Dizini|Kavram Dizini]]
