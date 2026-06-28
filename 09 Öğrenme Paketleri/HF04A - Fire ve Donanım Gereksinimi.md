---
hafta: 4
konu: yüksek hacimde fire ve donanım gereksinimi
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, fire, donanım, makine-sayısı]
kaynak: HF04 slayt 8-32
---

# HF04A - Fire ve Donanım Gereksinimi

> [!summary] Bir cümlede
> Nihai iyi ürün hedefinden operasyonlar boyunca geriye gidilerek planlanan miktarlar, ardından işlem süresi ve etkin kullanılabilir kapasiteyle makine gereksinimi bulunur.

## Öğrenme hedefleri

- [ ] Fire oranını verim oranına çevirebilirim.
- [ ] Seri operasyonlarda miktarları sondan başa hesaplayabilirim.
- [ ] Sürekli/beklenen miktar ile operasyon bazlı tamsayı planını ayırabilirim.
- [ ] Performans ve güvenilirliği makine kapasitesine doğru uygulayabilirim.
- [ ] Sürece ve ürüne göre yerleşimde yuvarlama sırasını ayırabilirim.

## 0 - Soğuk başlangıç

> [!question]
> Son operasyondan 1.000 iyi ürün isteniyor. Son iki operasyonun fire oranları sırasıyla %2 ve %5'tir. Hesaba ilk operasyondan mı, son operasyondan mı başlanmalıdır? Neden?

> [!answer]- Beklenen açıklama
> Son hedeften başlanıp geriye gidilir. Son operasyona kaç sağlam girdi gerektiği bilinmeden önceki operasyonun hedef çıktısı belirlenemez.

## 1 - Öğreten not

### Yüksek hacimde fire modeli

$k$ operasyonunda:

| Sembol | Anlam |
|---|---|
| $I_k$ | Operasyona giren miktar |
| $O_k$ | Operasyondan çıkan iyi miktar |
| $S_k$ | Fire miktarı |
| $s_k$ | Fire oranı |
| $y_k=1-s_k$ | Verim oranı |

Temel ilişkiler:

$$
S_k=s_kI_k
$$

$$
O_k=I_k-S_k=(1-s_k)I_k=y_kI_k
$$

Buradan gereken girdi:

$$
I_k=\frac{O_k}{1-s_k}
$$

Seri süreçte bir operasyonun gerekli girdisi, önceki operasyonun gerekli iyi çıktısı olur:

$$
O_{k-1}=I_k
$$

### Tek formülle sürekli yaklaşım

$n$ seri operasyon ve nihai hedef $O_n$ için:

$$
I_1=\frac{O_n}{\prod_{k=1}^{n}(1-s_k)}
$$

Bu değer yüksek hacimde beklenen/plansal miktardır. Ürünler bölünemiyorsa yalnız ilk girdiyi yuvarlamak her zaman yeterli değildir.

### Operasyon bazlı tamsayı yaklaşımı

Her aşamada tam ürün zorunluysa geriye doğru her adımda yukarı yuvarla:

$$
I_k=\left\lceil\frac{O_k}{1-s_k}\right\rceil
$$

> [!warning] Yuvarlama tuzağı
> Toplam formülden çıkan değeri yalnız bir kez tavana yuvarlamak, ara operasyonlardaki tamsayı kayıpları nedeniyle nihai hedefi eksik bırakabilir.

### Donanım oranı

Bir operasyon için gereken makine kapasitesi:

$$
F=\frac{S\,Q}{E\,H\,R}
$$

| Sembol | Anlam | Tipik birim |
|---|---|---|
| $F$ | Gerekli makine kapasitesi | makine |
| $S$ | Birim standart işlem süresi | dk/parça |
| $Q$ | Planlanan işlem miktarı | parça/dönem |
| $E$ | Gerçek performans oranı | boyutsuz |
| $H$ | Makine başına mevcut süre | dk/dönem |
| $R$ | Güvenilirlik/kullanılabilirlik | boyutsuz |

Pay $SQ$ toplam standart iş yüküdür. Payda $EHR$ ile düzeltilmiş etkin makine süresidir.

### Yuvarlama ve yerleşim tipi

- **Sürece göre yerleşim:** aynı tip makinedeki ürün yükleri önce birleştirilir, sonra toplam kapasite yukarı yuvarlanır.
- **Ürüne göre yerleşim:** her ürün hattının makine gereksinimi ayrı yukarı yuvarlanır, sonra tam sayılar toplanır.

Genel olarak:

$$
F_m^{süreç}
=\left\lceil
\sum_p\frac{S_{pm}Q_p}{E_mH_mR_m}
\right\rceil
$$

$$
F_m^{ürün}
=\sum_p
\left\lceil
\frac{S_{pm}Q_p}{E_mH_mR_m}
\right\rceil
$$

Bu nedenle ürün yerleşiminde kullanılmayan küçük kapasite parçaları farklı ürünler arasında kolayca paylaşılamaz.

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF04, slayt 19
> Bir parçanın freze tezgâhındaki standart işlem süresi 2,8 dk/parçadır. Sekiz saatlik vardiyada 200 parça üretilecektir. Makine zamanın %80'inde kullanılabilir ve çalışırken standart hızın %95'i ile üretir. Kaç freze gerekir?

### Verilenler

$$
S=2{,}8\text{ dk/parça},\quad Q=200\text{ parça/vardiya}
$$

$$
H=480\text{ dk/vardiya},\quad E=0{,}95,\quad R=0{,}80
$$

### Kurulum

$$
F=\frac{SQ}{EHR}
$$

$$
F=\frac{2{,}8(200)}{0{,}95(480)(0{,}80)}
=\frac{560}{364{,}8}
=1{,}535
$$

### Karar

1,535 bir kapasite ihtiyacıdır; 0,535 makine satın alınamaz. Normal vardiya planında:

$$
\lceil1{,}535\rceil=2\text{ freze}
$$

> [!success] Sonuç
> En az 2 freze tezgâhı gerekir. Bir makineye yuvarlamak kapasite açığı oluşturur; ikinci makine yerine fazla mesai veya fason üretim düşünülüyorsa bu ayrıca maliyetle gerekçelendirilmelidir.

### Öz-açıklama

1. %80 kullanılabilirlik ve %95 performans neden paydaya yazıldı?
2. $F=1{,}535$ sonucunu 1'e yuvarlamak neden yanlış?
3. Aynı iş iki ürün için aynı frezede yapılacaksa yükler hangi aşamada birleştirilir?

## 3 - Fire ve tamsayı planlama örneği

> [!example]
> Üç seri operasyondan sonra 10.000 iyi ürün isteniyor. Fire oranları sırayla %2, %3 ve %5'tir. İlk giriş miktarını bulun.

### Sürekli/beklenen miktar

$$
I_1=\frac{10.000}{0{,}98(0{,}97)(0{,}95)}
=11.073{,}34
$$

Yalnız toplam değeri tavana yuvarlarsak 11.074 bulunur.

### Operasyon bazlı tamsayı plan

Sondan geriye:

$$
I_3=\left\lceil\frac{10.000}{0{,}95}\right\rceil=10.527
$$

$$
I_2=\left\lceil\frac{10.527}{0{,}97}\right\rceil=10.853
$$

$$
I_1=\left\lceil\frac{10.853}{0{,}98}\right\rceil=11.075
$$

> [!important]
> Beklenen/sürekli yaklaşım 11.073,34; yalnız son yuvarlamayla 11.074; her aşamada tam ürün zorunluysa güvenli geriye doğru plan 11.075'tir. Sorunun varsayımı belirtilmelidir.

## 4 - Kademeli örnek

> [!question]
> Son operasyondan 240 iyi parça isteniyor. Öncesindeki operasyonda fire %4'tür. Bu operasyondaki standart süre 3,2 dk/parça; vardiya 480 dk; performans %90; güvenilirlik %85'tir. Planlanacak giriş miktarını ve gereken makine sayısını bulun.
>
> 1. $Q=\left\lceil240/(1-\_\_)\right\rceil$
> 2. $F=\dfrac{\_\_\times Q}{\_\_\times\_\_\times\_\_}$
> 3. Uygulanabilir makine sayısını yazın.

> [!answer]- Tam çözüm
> $$Q=\left\lceil\frac{240}{0{,}96}\right\rceil=250\text{ parça}$$
>
> $$F=\frac{3{,}2(250)}{0{,}90(480)(0{,}85)}=2{,}179$$
>
> Normal vardiyada gereken sayı $\lceil2{,}179\rceil=3$ makinedir.

## 5 - Bağımsız sorular

### L1 - Temel donanım

> [!question]
> $S=4$ dk/parça, $Q=300$ parça/vardiya, $H=480$ dk, $E=0{,}90$, $R=0{,}85$ için makine kapasite kesrini ve gereken tam makine sayısını bulun.

> [!answer]- Çözüm
> $$F=\frac{4(300)}{0{,}90(480)(0{,}85)}=3{,}268$$
> En az 4 makine gerekir.

### L2 - Süreç ve ürün yerleşimi

> [!question]
> A ve B ürünleri aynı tip frezede işlenmektedir. A için $Q_A=500$, $S_A=4$ dk; B için $Q_B=300$, $S_B=7$ dk'dır. Ayda 22 gün ve günde 8 saat çalışılmaktadır. $E=0{,}80$, $R=0{,}90$ olsun.
>
> 1. Sürece göre yerleşimde gereken freze sayısını bulun.
> 2. Her ürünün ayrı hattı olduğu ürüne göre yerleşimde gereken toplam freze sayısını bulun.

> [!answer]- Çözüm
> Aylık mevcut süre:
> $$H=22(8)(60)=10.560\text{ dk}$$
>
> Sürece göre yerleşimde yükler birleştirilir:
> $$F=\frac{4(500)+7(300)}{0{,}80(10.560)(0{,}90)}
> =0{,}539\Rightarrow1\text{ freze}$$
>
> Ürüne göre ayrı hatlarda:
> $$F_A=0{,}263\Rightarrow1,\qquad F_B=0{,}276\Rightarrow1$$
> Toplam 2 freze gerekir. Fark, kapasite parçalarının ayrı hatlar arasında paylaşılamamasından doğar.

### L3 - Yöntemi seç

> [!question]
> Aşağıdaki iki çözümden hangisinin varsayımını seçmeniz gerektiğini açıklayın:
>
> 1. $I=O/\prod(1-s_k)$ hesaplanır ve yalnız ilk giriş tavana yuvarlanır.
> 2. Her operasyonda $I_k=\lceil O_k/(1-s_k)\rceil$ uygulanır.

> [!answer]- Çözüm
> Birinci yaklaşım yüksek hacimde beklenen/sürekli plan için uygundur. Her aşamada bölünemeyen tam ürün sayısı ve hedefi kesin karşılama zorunluluğu varsa ikinci yaklaşım gerekir. Soru varsayımı belirsizse kullanılan yaklaşım açıkça yazılmalıdır.

## 6 - Çıkış bileti

Notu kapatıp cevapla:

1. $O_k$, $I_k$, $s_k$ arasındaki ilişkiyi yaz.
2. Makine gereksinimi formülünü ve bütün sembolleri yaz.
3. Süreç ve ürün yerleşiminde yuvarlama sırası neden farklıdır?
4. $F=2{,}01$ çıkarsa neden 2 makine yeterli değildir?

## 7 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli + L1 |  |  |  |
| D1 |  | Yeni fire + makine sorusu |  |  |  |
| D3 |  | Süreç/ürün karşılaştırması |  |  |  |
| D7 |  | HF03-HF04 karma mini test |  |  |  |
| D14 |  | Aktarım sorusu |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| Fire oranlarını toplamak | Seri verimler çarpılır | Her oranı $1-s_k$ yapıp çarp |
| Baştan sona ilerlemek | Ara hedefler henüz bilinmez | Nihai iyi üründen geriye git |
| $E$ ve $R$'yi paya yazmak | Düşük performans kapasiteyi azaltır, ihtiyacı artırır | Etkin süreyi $EHR$ olarak paydaya yaz |
| Makine kesrini en yakına yuvarlamak | Küçük kesir de gerçek kapasite ihtiyacıdır | Kapasite kararı için tavana yuvarla |
| Her ürün kesrini süreç yerleşiminde ayrı yuvarlamak | Ortak makinelerde yükler paylaşılabilir | Önce aynı makine yüklerini birleştir |

## Kaynaklar

- [[HF4-P4-Ürün, Süreç ve Çizelgeleme Tasarımı III-2025.pptx|Ders sunumu]], slayt 8-32
- [[05 Kaynaklar/MarkItDown/HF04 - Ham|HF04 ham metni]], yaklaşık satır 72-366
- [[00 Pano/Kanıta Dayalı Öğrenme Sistemi|Kanıta Dayalı Öğrenme Sistemi]]

