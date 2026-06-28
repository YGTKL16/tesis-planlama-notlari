---
aliases: [Düzeltmeler, Kaynak Kontrolü]
tags: [ders/tesis-planlama, doğrulama, kaynak]
durum: aktif
---

# Kaynak Doğrulama ve Düzeltmeler

> [!warning]
> Bu kayıt “hocayı düzeltme” amacı taşımaz. Sınavda verilen veriyi doğru işlemeyi ve kaynakla bağımsız hesap ayrımını görünür kılar.

| Kaynak | Kaynaktaki ifade | Bağımsız kontrol | Kullanılacak sonuç | Ayrıntı |
|---|---|---|---|---|
| HF03 grafik, $Q=8$ | Küçük sayısal fark | Binom toplamı yeniden hesaplandı | $E[\Pi(8)]=-51{,}80$ TL | [[09 Öğrenme Paketleri/HF03 - Rassal Iskarta Payı#Adım 3 - Adayları karşılaştır|HF03]] |
| HF06 MAG örneği | $M=2{,}74$, yıllık 137.000 | $A=1{,}572222$, $M=2{,}751389$ | 137.569,444 MAG/yıl | [[09 Öğrenme Paketleri/HF06A - MAG Akış Şiddeti ve From-To Matrisi#Tam çözümlü kaynak örneği: MAG|HF06A]] |
| HF06 ilişki sınıfı | `0-11` ve `11-22` çakışıyor | Ayrık sınıf gerekir | İkinci aralık 12-22 yorumlandı | [[09 Öğrenme Paketleri/HF06B - Faaliyet İlişki Diyagramı ve Alan Hesabı#REL chart|HF06B]] |
| HF06 akışsız çift | Akışsız çiftler X gösterilmiş | X için olumsuz gerekçe gerekir | Sıfır akış tek başına U; X ayrıca gerekçelenir | [[09 Öğrenme Paketleri/HF06B - Faaliyet İlişki Diyagramı ve Alan Hesabı#Tam çözümlü kaynak örneği: akış ilişkileri|HF06B]] |
| HF08 slayt 83 | CRAFT sonucu 3.310 | 20 yönlü matris hücresi ve 120 permütasyon tarandı | **3.510** | [[09 Öğrenme Paketleri/HF08C - CRAFT Yöntemi#Tam çözümlü kaynak örneği|HF08C]] |
| Soru Bankası S6 | Tek optimum $x=4$ | Kümülatif ağırlık yarıya tam eşit | $x^*\in[4,7]$ | [[04 Sorular/Soru Bankası#S6 - Ağırlıklı medyan|Düzeltilmiş soru]] |

## Sınavda yazım kuralı

1. Soruda verilen yuvarlama/tablo yöntemi varsa onu açıkça belirt.
2. Ara hesabı göster; yalnız farklı son sayı yazma.
3. Kaynak sonucu ile bağımsız sonuç ayrışıyorsa “verilen matrislerle hesaplanan” ifadesini kullan.
4. İşlem varsayımını yaz: yönlü/birleşik akış, sürekli/tamsayı fire, kullanılan ilişki ölçeği.

NumPy kontrolleri: [[08 Hesaplamalar/Sınav Doğrulama Raporu|Sınav Doğrulama Raporu]].

