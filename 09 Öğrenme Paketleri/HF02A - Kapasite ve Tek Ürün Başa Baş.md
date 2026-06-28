---
hafta: 2
konu: kapasite kullanımı ve tek ürün başa baş analizi
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, kapasite, başa-baş, hedef-kar]
kaynak: HF02 slayt 13-40
---

# HF02A - Kapasite ve Tek Ürün Başa Baş

![[07 Ekler/Grafikler/basa-bas-grafigi.svg]]

> [!summary] Bir cümlede
> Kapasite kullanım oranı mevcut çıktının işletim düzeyine oranını; başa baş analizi ise toplam gelir ile toplam maliyetin eşitlendiği minimum satış hacmini gösterir.

## Öğrenme hedefleri

- [ ] Kapasite kullanım oranının pay ve paydasını doğru seçebilirim.
- [ ] Sabit ve değişken maliyeti ayırabilirim.
- [ ] Başa baş miktarı, başa baş satış tutarı ve hedef kâr miktarını bulabilirim.
- [ ] Kesirli miktarı uygulanabilir karara doğru yuvarlayabilirim.
- [ ] İki süreç/makine alternatifinin maliyet eşiklerini karşılaştırabilirim.

## 0 - Soğuk başlangıç

> [!question]
> Bir ürünün satış fiyatı 80 TL, değişken maliyeti 50 TL'dir. Sabit maliyet bilinmeden başa baş miktarı bulunabilir mi? Neden?

> [!answer]- Beklenen açıklama
> Bulunamaz. Her satış sabit maliyeti karşılamak için 30 TL katkı sağlar; ancak kaç satış gerektiği toplam sabit maliyete bağlıdır.

## 1 - Öğreten not

### Kapasite kullanım oranı

Sunumdaki tanım:

$$
U=\frac{Q_{kullanılan}}{Q_{en\ iyi\ işletim}}
$$

Oran yüzde olarak raporlanacaksa 100 ile çarpılır. Payda soruda verilen **en iyi işletim düzeyi** olmalıdır; tasarım kapasitesi veya başka bir kapasite tanımıyla sessizce değiştirilmez.

### Tek ürün maliyet ve gelir modeli

| Sembol | Anlam |
|---|---|
| $F$ | Toplam sabit maliyet |
| $P$ | Birim satış fiyatı |
| $V$ | Birim değişken maliyet |
| $x$ | Üretim/satış miktarı |
| $TR$ | Toplam gelir |
| $TC$ | Toplam maliyet |
| $\Pi$ | Kâr |

$$
TR=Px
$$

$$
TC=F+Vx
$$

$$
\Pi=TR-TC=(P-V)x-F
$$

$P-V$ birim katkı payıdır. Pozitif değilse satış arttıkça sabit maliyet karşılanamaz.

### Miktar cinsinden başa baş

Başa başta $TR=TC$ ve $\Pi=0$:

$$
x_{BB}=\frac{F}{P-V}
$$

Kesikli ürünlerde minimum zararsız adet:

$$
x_{uygulanabilir}=\left\lceil\frac{F}{P-V}\right\rceil
$$

### Satış tutarı cinsinden başa baş

Katkı payı oranı:

$$
CMR=\frac{P-V}{P}=1-\frac VP
$$

$$
S_{BB}=\frac{F}{CMR}
$$

### Hedef kâr

Hedef kâr $\Pi^*$ ise:

$$
x_{hedef}=\frac{F+\Pi^*}{P-V}
$$

### Alternatif süreçlerin eşik miktarı

İki alternatifin maliyetleri:

$$
TC_A=F_A+V_Ax,\qquad TC_B=F_B+V_Bx
$$

Eşik miktarı maliyetleri eşitleyerek bul:

$$
x^*=\frac{F_B-F_A}{V_A-V_B}
$$

Sonra eşiğin iki tarafında hangi doğrunun daha düşük olduğunu kontrol et. Formülü ezberlemek yerine maliyetleri eşitlemek işaret hatasını önler.

## 2 - Tam çözümlü kaynak örnekleri

### Kapasite kullanımı

> [!example] Kaynak: HF02, slayt 14
> Tesis bir haftada 83 birim üretmiş; tarihsel en iyi işletim düzeyi 120 birim/haftadır.

$$
U=\frac{83}{120}=0{,}6917\approx\%69{,}17
$$

> [!success] Yorum
> Tesis, verilen en iyi işletim düzeyinin yaklaşık %69,17'sini kullanmıştır. Oranın düşük olmasının nedeni bu hesapla tek başına belirlenemez.

### Kitap başa baş örneği

> [!example] Kaynak: HF02, slayt 34-36
> Satış fiyatı 500 TL; telif, resim ve dizgi sabit maliyetleri toplam 530.000 TL; birim değişken maliyet toplam 200 TL'dir.

Birim katkı:

$$
P-V=500-200=300\text{ TL/kitap}
$$

Matematiksel başa baş:

$$
x_{BB}=\frac{530.000}{300}=1.766{,}67
$$

Kitap bölünemediği ve 1.766 adet zarar bıraktığı için:

$$
x_{uygulanabilir}=1.767\text{ kitap}
$$

1.767 adette:

$$
TR=500(1.767)=883.500\text{ TL}
$$

$$
TC=530.000+200(1.767)=883.400\text{ TL}
$$

Uygulanabilir ilk tam adette 100 TL kâr oluşur; gerçek eşitlik 1.766,67 birimdedir.

> [!warning] Yuvarlama
> “Başa baş 1.766,67 birim” matematiksel eşiği; “zarar etmeyecek en az 1.767 birim” uygulanabilir kararı ifade eder.

### Öz-açıklama

1. Sabit maliyet neden birim sayısıyla çarpılmadı?
2. 1.766 adedin yeterli olmadığını kâr formülüyle gösterin.
3. Satış fiyatı düşerse başa baş miktarı hangi yönde değişir?

## 3 - Kademeli örnek

> [!question]
> Sabit maliyet 75.000 TL, birim değişken maliyet 10 TL ve satış fiyatı 15 TL'dir.
>
> 1. Katkı payı $=\_\_-\_\_=\_\_$ TL.
> 2. $x_{BB}=\_\_/\_\_=\_\_$ adet.
> 3. 20.000 adette kârı hesaplayın.

> [!answer]- Tam çözüm
> Katkı payı $15-10=5$ TL'dir.
> $$x_{BB}=75.000/5=15.000\text{ adet}$$
> $$\Pi(20.000)=5(20.000)-75.000=25.000\text{ TL}$$

## 4 - Bağımsız sorular

### L1 - Temel

> [!question]
> $F=480.000$ TL, $P=120$ TL/birim ve $V=72$ TL/birim için başa baş miktarını bulun.

> [!answer]- Çözüm
> $$x_{BB}=\frac{480.000}{120-72}=10.000\text{ birim}$$

### L2 - Hedef kâr

> [!question]
> Sabit maliyet 360.000 TL, fiyat 150 TL, değişken maliyet 90 TL ve hedef kâr 240.000 TL'dir. Gereken satış miktarını bulun.

> [!answer]- Çözüm
> $$x_{hedef}=\frac{360.000+240.000}{150-90}=10.000\text{ birim}$$
> Kontrol: $\Pi=60(10.000)-360.000=240.000$ TL.

### L3 - Süreç seçimi

> [!question]
> A sürecinin sabit maliyeti 100.000 TL, değişken maliyeti 60 TL/birimdir. B sürecinin sabit maliyeti 300.000 TL, değişken maliyeti 35 TL/birimdir. Maliyet eşiğini ve eşiğin iki tarafındaki seçimi bulun.

> [!answer]- Çözüm
> $$100.000+60x=300.000+35x$$
> $$25x=200.000\Rightarrow x^*=8.000$$
> 8.000'in altında düşük sabit maliyetli A; üstünde düşük değişken maliyetli B daha ucuzdur. 8.000'de maliyetler eşittir.

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. Kullanım oranı formülünü yaz.
2. Kâr ve başa baş miktarı formüllerini türet.
3. Katkı payı ile katkı payı oranını ayır.
4. Kesirli başa baş miktarı neden yukarı yuvarlanır?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Hedef kâr |  |  |  |
| D3 |  | Süreç seçimi |  |  |  |
| D7 |  | HF02 karma test |  |  |  |
| D14 |  | Aktarım sorusu |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| $P/V$ ile başa baş bulmak | Sabit maliyet ve katkı payı kaybolur | Önce $P-V$ yaz |
| Sabit maliyeti $x$ ile çarpmak | Sabit maliyet hacimden bağımsızdır | $TC=F+Vx$ kur |
| Kesirli adedi en yakına yuvarlamak | Aşağı yuvarlama zarar bırakabilir | Minimum zararsız adet için tavan kullan |
| İki süreçte yalnız değişken maliyeti karşılaştırmak | Sabit yatırım farkı gözden kaçar | İki toplam maliyet doğrusunu eşitle |

## Kaynaklar

- [[HF2-P2-Tesis Kapasite Planlama-2025.pptx|Ders sunumu]], slayt 13-40
- [[05 Kaynaklar/MarkItDown/HF02 - Ham|HF02 ham metni]], yaklaşık satır 148-548
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]
