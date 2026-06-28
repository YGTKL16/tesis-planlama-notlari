---
tags: [ders/tesis-planlama, hesaplama, numpy, doğrulama]
üretilen: otomatik
---

# Sınav Doğrulama Raporu

> [!warning]
> Bu rapor öğrenmenin yerine geçmez. Soruyu önce elle çöz; motoru yalnız ara toplam ve sonuç denetimi için kullan.

Kaynak: [[08 Hesaplamalar/sinav_dogrulama.py|sinav_dogrulama.py]]  
Testler: [[08 Hesaplamalar/test_sinav_dogrulama.py|test_sinav_dogrulama.py]]

| Kontrol | Doğrulanmış sonuç | Paket |
|---|---:|---|
| HF03 rassal ıskarta | Q*=5; E[kâr]=35.224,80 TL | [[09 Öğrenme Paketleri/HF03 - Rassal Iskarta Payı|HF03]] |
| HF04 sürekli fire | 11.073,34 | [[09 Öğrenme Paketleri/HF04A - Fire ve Donanım Gereksinimi|HF04A]] |
| HF04 tek yuvarlama / aşamalı | 11074 / 11075 | [[09 Öğrenme Paketleri/HF04A - Fire ve Donanım Gereksinimi|HF04A]] |
| HF08 CRAFT başlangıç | 3.780 | [[09 Öğrenme Paketleri/HF08C - CRAFT Yöntemi|HF08C]] |
| HF08 CRAFT küresel tarama | 3.510; atama 3A-2B-1C-5D-4E | [[09 Öğrenme Paketleri/HF08C - CRAFT Yöntemi|HF08C]] |
| HF11 minisum | (5,4); amaç=105 | [[09 Öğrenme Paketleri/HF11A - Minisum ve Ağırlıklı Medyan|HF11A]] |
| HF11 eş-yarı medyan | x∈[4,10] | [[09 Öğrenme Paketleri/HF11A - Minisum ve Ağırlıklı Medyan|HF11A]] |
| HF11 minimax | R*=8; uçlar (3,5)-(6,2) | [[09 Öğrenme Paketleri/HF11B - Minimax ve Optimum Çözüm Kümesi|HF11B]] |
| HF12 açma-atama | 7.400; açık B+C | [[09 Öğrenme Paketleri/HF12B - Kesikli Tesis Konumu ve Açma Atama|HF12B]] |

## Özellikle korunan nüanslar

- Ağırlıklı medyanda kümülatif ağırlık tam yarıysa tek sayı değil **optimum aralık** döner.
- Firede sürekli değer, yalnız son yuvarlama ve operasyon bazlı tamsayı plan ayrı raporlanır.
- CRAFT maliyeti yönlü 20 hücreyle hesaplanır; 120 atama taraması kaynak slayttaki `3.310` yerine `3.510` sonucunu doğrular.
- Açma-atama küçük örneği bütün boş olmayan tesis alt kümelerini tarar.

## Çalıştırma

```bash
python "08 Hesaplamalar/sinav_dogrulama.py"
pytest -q "08 Hesaplamalar/test_sinav_dogrulama.py"
```
