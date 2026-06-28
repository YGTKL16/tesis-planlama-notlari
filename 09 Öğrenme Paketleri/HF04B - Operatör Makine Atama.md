---
hafta: 4
konu: operatöre makine atama
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, operatör, makine-atama, çevrim-süresi]
kaynak: HF04 slayt 33-61
---

# HF04B - Operatör Makine Atama

> [!summary] Bir cümlede
> Yarı otomatik üretimde bir operatöre atanacak makine sayısı, operatör tur süresi ile makinenin doğal çevrim süresi dengelenerek; gerekiyorsa üretim ve maliyet açısından karşılaştırılarak seçilir.

## Öğrenme hedefleri

- [ ] Eşzamanlı, operatöre özgü ve makineye özgü süreleri ayırabilirim.
- [ ] İdeal makine sayısını hesaplayabilirim.
- [ ] Tamsayı adaylarda gerçek çevrim süresini bulabilirim.
- [ ] Operatör ve makine aylak sürelerini doğru yorumlayabilirim.
- [ ] Üretim oranı ve birim maliyetle uygun atamayı seçebilirim.

## 0 - Soğuk başlangıç

> [!question]
> Bir operatöre daha fazla otomatik makine atamak üretim hızını her zaman artırır mı? Kısa bir gerekçe yazın.

> [!answer]- Beklenen açıklama
> Hayır. Operatörün bütün makineleri yükleme, boşaltma, kontrol etme ve aralarında yürüme turu makinenin otomatik çevriminden uzun hâle gelirse makineler operatörü beklemeye başlar. Ek makinenin marjinal üretim katkısı azalabilir ve maliyeti artabilir.

## 1 - Öğreten not

### Süre bileşenleri

| Sembol | Etkinlik | Kim meşgul? |
|---|---|---|
| $a$ | Yükleme ve boşaltma gibi eşzamanlı etkinlikler | Operatör + makine |
| $b$ | Yürüme, muayene ve paketleme gibi bağımsız operatör işleri | Yalnız operatör |
| $t$ | Otomatik işleme | Yalnız makine |
| $m$ | Bir operatöre gerçekten atanacak tamsayı makine sayısı | Karar |

Bir makinenin kendi doğal çevrim süresi:

$$
T_M=a+t
$$

Operatörün bir makine için harcadığı zaman:

$$
T_O=a+b
$$

$m$ makineyi dolaştığı bir turun süresi:

$$
T_{tur}=m(a+b)
$$

### İdeal makine sayısı

Makine çevrimi ile operatör turu tam dengelendiğinde:

$$
n'=\frac{a+t}{a+b}
$$

$n'$ çoğunlukla kesirlidir. Bu sayı doğrudan uygulanabilir karar değil, denge noktasını gösterir. Genellikle $\lfloor n'\rfloor$ ve $\lceil n'\rceil$ adayları karşılaştırılır.

### Gerçek tekrarlı çevrim

Sistemin çevrimini yavaş olan taraf belirler:

$$
T(m)=\max\{a+t,\;m(a+b)\}
$$

Bir çevrimde $m$ parça tamamlandığından üretim oranı:

$$
r(m)=\frac{m}{T(m)}\quad\text{parça/zaman}
$$

### Aylak süreler

#### $m<n'$ ise

Operatör bütün makineleri erken dolaşır ve ilk makinenin bitmesini bekler:

$$
I_O=T(m)-m(a+b)
$$

Makine aylak süresi yoktur.

#### $m>n'$ ise

Operatör turu uzar; makineler işini bitirip operatörü bekler. Makine başına:

$$
I_M=T(m)-(a+t)
$$

Operatör aylak süresi yoktur.

#### $m=n'$ ise

İdeal deterministik koşullarda iki taraf da beklemez.

### Operatör gereksinimi

Toplam doğrudan işçilik süresiyle operatör sayısı sorulursa:

$$
N=\frac{T\,P}{H\,C}
$$

Burada $T$ bir operasyon için standart operatör zamanı, $P$ dönemsel operasyon miktarı, $H$ kişi başına mevcut süre ve $C$ personel performans/kullanılabilirlik oranıdır.

### Maliyet karşılaştırması

Operatör maliyet oranı $c_o$, makine maliyet oranı $c_m$ ise birim zaman başına sistem maliyeti:

$$
c_o+mc_m
$$

Bir çevrimde $m$ ürün çıktığı için birim maliyet:

$$
C_u(m)=\frac{(c_o+mc_m)T(m)}{m}
$$

> [!warning] Karar tuzağı
> $n'=2{,}67$ bulunması otomatik olarak “3 makine seç” demek değildir. Üretim hedefi, makine/işçilik maliyeti ve uygulanabilir tamsayı adaylar karşılaştırılmalıdır.

### C_u(m) — Tam Çözümlü Maliyet Örneği

> [!example] Birim başına maliyet kararı
> Bir operatörün saatlik maliyeti $c_o = 15$ TL, her makinenin saatlik maliyeti $c_m = 5$ TL'dir. Görev döngüsü: $a = 2$ dk (yükleme/boşaltma), $t = 6$ dk (makine çalışma), $b = 1$ dk (taşıma). $m = 2$ mi, $m = 3$ mü daha ekonomik?

**Adım 1:** İdeal makine sayısı

$$n' = \frac{a+t}{a+b} = \frac{2+6}{2+1} = 2{,}67$$

$m = 2 < n'$ → operatör aylak (2 makineyle operatör boş kalır)
$m = 3 > n'$ → makineler aylak (3 makineyle makineler boş kalır)

**Adım 2:** $m = 2$ için çevrim süresi

$$T(2) = \max\{a+t,\; 2(a+b)\} = \max\{8,\; 6\} = 8 \text{ dk}$$

**Adım 3:** $m = 3$ için çevrim süresi

$$T(3) = \max\{a+t,\; 3(a+b)\} = \max\{8,\; 9\} = 9 \text{ dk}$$

**Adım 4:** Birim başına maliyet

$$C_u(m) = \frac{(c_o + m \cdot c_m) \cdot T(m)}{m}$$

$$C_u(2) = \frac{(15 + 2 \times 5) \times 8}{2} = \frac{200}{2} = 100 \text{ TL/çevrim}$$

$$C_u(3) = \frac{(15 + 3 \times 5) \times 9}{3} = \frac{270}{3} = 90 \text{ TL/çevrim}$$

**Karar:** $m = 3$ seçilir ($90 < 100$). Makine maliyeti artmış ama çevrim başına oran düşmüş.

> [!warning] Çelişkili gibi görünen durum
> $m=3$ ile çevrim süresi $m=2$'den uzun (9 dk > 8 dk), yani üretim oranı daha düşük. Ama birim maliyet daha az. Sınavda **maliyet sorarsa** $C_u$'ya bak, **kapasite sorarsa** $T(m)$'ye bak. Her ikisi aynı $m$'yi işaret etmeyebilir.

> [!tip] Akılda kalıcı — “Ortak kira”
> $C_u(m)$'yi şöyle düşün: bir işçi + $m$ makine ortak kirada çalışıyor, toplam kira $c_o + m \cdot c_m$, ama her çevrimde $m$ parça çıkıyor. **Ortak gideri paylaşacak makine sayısı arttıkça birim düşer** — ta ki makineler boş beklemeye başlayana kadar. $n'$ o sınırdır.

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF04, slayt 48-56
> Bir makineyi yükleme ve boşaltma toplam 2 dk, otomatik işlem 6 dk, yürüme ile muayene/paketleme toplam 1 dk sürmektedir. Bir operatöre kaç makine atanacağını ve 2 ile 3 makine seçeneklerinin çevrimlerini bulun.

### Verilenler

$$
a=2\text{ dk},\qquad t=6\text{ dk},\qquad b=1\text{ dk}
$$

### İdeal sayı

$$
n'=\frac{a+t}{a+b}
=\frac{2+6}{2+1}
=\frac83
=2{,}67
$$

Tamsayı adaylar $m=2$ ve $m=3$'tür.

### Aday 1: $m=2$

$$
T(2)=\max\{8,2(3)\}=8\text{ dk}
$$

$$
r(2)=\frac28=0{,}25\text{ parça/dk}
$$

$m<n'$ olduğundan operatör bekler:

$$
I_O=8-2(3)=2\text{ dk/çevrim}
$$

Makineler otomatik çevrimini kesintisiz sürdürür; makine aylak süresi sıfırdır.

### Aday 2: $m=3$

$$
T(3)=\max\{8,3(3)\}=9\text{ dk}
$$

$$
r(3)=\frac39=0{,}333\text{ parça/dk}
$$

$m>n'$ olduğundan operatör tam doludur, makineler bekler:

$$
I_M=9-8=1\text{ dk/makine-çevrim}
$$

### Karşılaştırma

| $m$ | Çevrim $T(m)$ | Üretim oranı | Operatör aylak | Makine başına aylak |
|---:|---:|---:|---:|---:|
| 2 | 8 dk | 0,250 parça/dk | 2 dk | 0 dk |
| 3 | 9 dk | 0,333 parça/dk | 0 dk | 1 dk |

> [!success] Sonuç
> Yalnız üretim oranı amaçlanırsa 3 makine daha yüksek çıktı sağlar. Nihai “optimum” karar için makine ve operatör maliyetleri de karşılaştırılmalıdır.

### Öz-açıklama

1. Çevrim süresinde neden toplam değil, maksimum kullanıldı?
2. Üç makinede operatör boş kalmazken makineler neden bekliyor?
3. Operatör maliyeti çok yüksekse hangi seçeneğin avantajı artar?

## 3 - Kademeli örnek

> [!question]
> $a=1{,}5$ dk, $b=0{,}5$ dk ve $t=7$ dk olsun.
>
> 1. $n'=\dfrac{\_\_+\_\_}{\_\_+\_\_}$
> 2. İki komşu tamsayı adayı belirleyin.
> 3. Her aday için $T(m)$, üretim oranı ve aylak süreyi bulun.

> [!answer]- Tam çözüm
> $$n'=\frac{1{,}5+7}{1{,}5+0{,}5}=4{,}25$$
> Adaylar 4 ve 5 makinedir.
>
> | $m$ | $T(m)$ | Üretim oranı | Operatör aylak | Makine başına aylak |
> |---:|---:|---:|---:|---:|
> | 4 | $\max(8{,}5,8)=8{,}5$ | $4/8{,}5=0{,}471$ | 0,5 dk | 0 dk |
> | 5 | $\max(8{,}5,10)=10$ | $5/10=0{,}500$ | 0 dk | 1,5 dk |
>
> Beş makine daha yüksek üretim oranı verir; maliyet bilgisi olmadan en düşük birim maliyetli seçeneğin hangisi olduğu söylenemez.

## 4 - Bağımsız sorular

### L1 - Çevrim ve aylak süre

> [!question]
> $a=3$ dk, $b=1$ dk, $t=9$ dk için ideal makine sayısını bulun. $m=3$ atanırsa çevrim, üretim oranı ve aylak süre nedir?

> [!answer]- Çözüm
> $$n'=\frac{3+9}{3+1}=3$$
> $$T(3)=\max\{12,3(4)\}=12\text{ dk}$$
> $$r(3)=3/12=0{,}25\text{ parça/dk}$$
> İdeal dengede operatör ve makinelerin aylak süresi sıfırdır.

### L2 - Maliyetle seçim

> [!question]
> Tam çözümlü örnekteki $a=2$, $b=1$, $t=6$ değerlerini kullanın. Operatör maliyeti 1,20 TL/dk ve makine maliyeti 0,30 TL/makine-dk olsun. $m=2$ ve $m=3$ için birim maliyetleri karşılaştırın.

> [!answer]- Çözüm
> $m=2$ için $T=8$:
> $$C_u(2)=\frac{(1{,}20+2(0{,}30))8}{2}=7{,}20\text{ TL/parça}$$
>
> $m=3$ için $T=9$:
> $$C_u(3)=\frac{(1{,}20+3(0{,}30))9}{3}=6{,}30\text{ TL/parça}$$
>
> Bu maliyetlerde 3 makine daha düşük birim maliyetlidir. Operatör maliyetinin yüksek olması, operatörü daha dolu kullanan seçeneği desteklemiştir.

### L3 - Yöntemi seç

> [!question]
> Aşağıdaki ifadeyi değerlendirin: “İdeal makine sayısı 2,67 çıktığı için sonuç 3'tür; başka hesap gerekmez.”

> [!answer]- Çözüm
> Yanlıştır. 2,67 denge noktasını gösterir. Uygulanabilir 2 ve 3 seçeneklerinin çevrimleri, üretim oranları ve maliyetleri karşılaştırılmalıdır. Kapasite hedefi 2 makineyle karşılanabiliyor ve makine maliyeti yüksekse 2; operatör maliyeti veya üretim hedefi baskınsa 3 tercih edilebilir.

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. $a$, $b$ ve $t$'yi tanımla.
2. $n'$ ve $T(m)$ formüllerini yaz.
3. $m<n'$ ve $m>n'$ durumlarında kimin beklediğini yaz.
4. Üretim oranını ve birim maliyet formülünü yaz.

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Yeni çevrim sorusu |  |  |  |
| D3 |  | Maliyet karşılaştırması |  |  |  |
| D7 |  | HF04A-HF04B karma test |  |  |  |
| D14 |  | Aktarım sorusu |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| $a+b+t$ değerlerini doğrudan toplamak | Bazı faaliyetler eşzamanlıdır | Makine çevrimi ve operatör turunu ayrı yaz |
| $n'$ değerini otomatik tavana yuvarlamak | Denge noktası kararın kendisi değildir | Alt ve üst tamsayıyı karşılaştır |
| Çevrimde küçük süreyi seçmek | Sistem yavaş tarafı bekler | $T(m)=\max\{a+t,m(a+b)\}$ kullan |
| Toplam çıktı oranını $1/T$ almak | Bir çevrimde $m$ makine $m$ parça üretir | $r=m/T$ yaz |
| $m>n'$ iken operatör bekler demek | Uzun operatör turu makineleri bekletir | İki süreyi sayısal karşılaştır |

## Kaynaklar

- [[HF4-P4-Ürün, Süreç ve Çizelgeleme Tasarımı III-2025.pptx|Ders sunumu]], slayt 33-61
- [[05 Kaynaklar/MarkItDown/HF04 - Ham|HF04 ham metni]], yaklaşık satır 370-628
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]

