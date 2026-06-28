---
hafta: 11
konu: dikdoğrusal tek tesis minimax ve u-v dönüşümü
durum: hazır
tags: [ders/tesis-planlama, hesap-paketi, konum, minimax, u-v-dönüşümü]
kaynak: HF11 slayt 28-32
---

# HF11B - Minimax ve Optimum Çözüm Kümesi

![[07 Ekler/Diyagramlar/minimax-cozum-kumesi.svg]]

> [!summary] Bir cümlede
> Dikdoğrusal minimax problemi, en uzak mevcut tesise olan uzaklığı küçültür; $u=x+y$, $v=x-y$ dönüşümü optimum yarıçapı ve **tek nokta olabilen veya bir doğru parçası oluşturabilen** tüm optimum konumları verir.

## Öğrenme hedefleri

- [ ] Minisum ile minimax amaçlarını soru metninden ayırabilirim.
- [ ] Noktaları $u$-$v$ koordinatlarına dönüştürebilirim.
- [ ] Minimum maksimum uzaklık $R^*$ değerini hesaplayabilirim.
- [ ] Dönüştürülmüş optimum aralıkları bulup $(x,y)$ düzlemine geri çevirebilirim.
- [ ] Tek bir merkez yazmak yerine tüm optimum çözüm kümesini kontrol edebilirim.

## 0 - Soğuk başlangıç

> [!question]
> Dikdoğrusal uzaklık altında yalnız $(0,0)$ ve $(6,4)$ noktalarına hizmet verilecektir. “İki noktanın koordinat ortalaması $(3,2)$'dir; tek optimum budur” iddiasını sınayın. Aynı maksimum uzaklığı veren başka bir nokta bulabilir misiniz?

> [!answer]- Beklenen açıklama
> $(3,2)$ için iki noktaya uzaklık da 5'tir; fakat tek optimum değildir. Örneğin $(5,0)$ noktasının uzaklıkları 5 ve 5'tir. Aslında $(1,4)$ ile $(5,0)$ arasındaki $x+y=5$ doğru parçasının tamamı optimumdur.

## 1 - Öğreten not

### Ne zaman kullanılır?

- bir yeni tesis düzlemde serbestçe konumlandırılacaktır,
- yollar dikdoğrusal/Manhattan biçimindedir,
- amaç toplam uzaklık değil, **en kötü durumdaki uzaklığı** küçültmektir,
- soruda “maksimum mesafeyi”, “en uzak müşteriyi” veya “en kötü erişim süresini minimize et” denir.

Tipik uygulamalar acil müdahale birimi, güvenlik tesisi ve adil hizmet merkezidir.

### Model

Mevcut noktalar $P_i=(a_i,b_i)$ ve yeni tesis $X=(x,y)$ olsun:

$$
\min R
$$

$$
|x-a_i|+|y-b_i|\le R \qquad \forall i
$$

Burada optimum $R^*$, herhangi bir mevcut tesise olan en büyük dikdoğrusal uzaklığın mümkün en küçük değeridir.

### $u$-$v$ dönüşümü

$$
u=x+y,\qquad v=x-y
$$

Her mevcut nokta için:

$$
u_i=a_i+b_i,\qquad v_i=a_i-b_i
$$

Ters dönüşüm:

$$
x=\frac{u+v}{2},\qquad y=\frac{u-v}{2}
$$

Kritik özdeşlik:

$$
|x-a_i|+|y-b_i|=
\max\left(|u-u_i|,|v-v_i|\right)
$$

Dolayısıyla Manhattan çemberi, dönüştürülmüş düzlemde eksenlere paralel bir kareye dönüşür.

### Optimum yarıçap

$$
\Delta_u=u_{\max}-u_{\min},
\qquad
\Delta_v=v_{\max}-v_{\min}
$$

$$
R^*=\frac12\max(\Delta_u,\Delta_v)
$$

### Tüm optimum çözüm kümesi

Yalnız $u$ ve $v$ aralıklarının orta noktalarını almak bir optimum nokta verir; fakat diğer optimumları gizleyebilir. $R^*$ bulunduktan sonra uygulanabilir dönüştürülmüş koordinatlar:

$$
U^*=\left[u_{\max}-R^*,\;u_{\min}+R^*\right]
$$

$$
V^*=\left[v_{\max}-R^*,\;v_{\min}+R^*\right]
$$

aralıklarındadır. Her $(u,v)\in U^*\times V^*$ ters dönüşümle optimum bir $(x,y)$ verir.

> [!note] Geometrik sonuç
> $R^*$ iki yayılımdan büyük olanının yarısıdır; bu nedenle en az bir dönüştürülmüş aralık tek noktaya çöker. Ağırlıksız düzlemsel durumda optimum küme çoğunlukla tek nokta veya bir doğru parçasıdır.

### Çözüm sırası

1. Her nokta için $u_i=a_i+b_i$ ve $v_i=a_i-b_i$ hesapla.
2. $u_{\min},u_{\max},v_{\min},v_{\max}$ değerlerini bul.
3. $R^*=\max(\Delta_u,\Delta_v)/2$ hesapla.
4. $U^*$ ve $V^*$ aralıklarını kur.
5. Aralıkların uç/köşe değerlerini ters dönüşümle $(x,y)$ düzlemine çevir.
6. En az bir adayda bütün Manhattan uzaklıklarını hesaplayıp maksimumun $R^*$ olduğunu doğrula.

> [!warning] Kapsam sınırı
> Bu kısa yöntem, slayttaki **ağırlıksız ve sabit ek yol içermeyen** tek tesis problemine aittir. $w_i d_i$ veya tesise özgü sabit $g_i$ içeren bir minimax modeli verilirse aynı aralık formülü doğrudan kullanılmaz.

### Minisumdan farkı

| Sorudaki ifade | Yöntem |
|---|---|
| “Toplam ağırlıklı mesafe/maliyet en küçük” | Minisum, ağırlıklı medyan |
| “En uzaktaki noktaya mesafe en küçük” | Minimax, $u$-$v$ dönüşümü |

## 2 - Tam çözümlü kaynak örneği

> [!example] Kaynak: HF11, slayt 30-32
> Sekiz mevcut tesis için yeni bir binanın, herhangi bir tesise olan maksimum dikdoğrusal uzaklığını küçülten konumlarını ve maksimum uzaklığı bulun.

| $i$ | $(a_i,b_i)$ | $u_i=a_i+b_i$ | $v_i=a_i-b_i$ |
|---:|---:|---:|---:|
| 1 | $(0,0)$ | 0 | 0 |
| 2 | $(4,6)$ | 10 | -2 |
| 3 | $(8,2)$ | 10 | 6 |
| 4 | $(10,4)$ | 14 | 6 |
| 5 | $(4,8)$ | 12 | -4 |
| 6 | $(2,4)$ | 6 | -2 |
| 7 | $(6,4)$ | 10 | 2 |
| 8 | $(8,8)$ | 16 | 0 |

> [!note] İşaret sözleşmesi
> Slayt tablosu ikinci dönüştürülmüş sütunda $-a_i+b_i$ kullanır. Burada $v_i=a_i-b_i$ seçildi. İki seçim de tutarlılıkla kullanılırsa aynı $(x,y)$ çözüm kümesini verir.

### Adım 1 - Yayılımlar

$$
u_{\min}=0,\quad u_{\max}=16,\quad \Delta_u=16
$$

$$
v_{\min}=-4,\quad v_{\max}=6,\quad \Delta_v=10
$$

### Adım 2 - Minimum maksimum uzaklık

$$
R^*=\frac12\max(16,10)=8
$$

### Adım 3 - Optimum dönüştürülmüş koordinatlar

$$
U^*=[16-8,0+8]=[8,8]
$$

$$
V^*=[6-8,-4+8]=[-2,4]
$$

Yani $u=8$ sabit, $v$ ise $-2$ ile 4 arasında değişebilir.

### Adım 4 - Uç noktaları geri dönüştür

$v=-2$ için:

$$
x=\frac{8-2}{2}=3,\qquad y=\frac{8-(-2)}2=5
$$

$v=4$ için:

$$
x=\frac{8+4}{2}=6,\qquad y=\frac{8-4}2=2
$$

> [!success] Karar
> Optimum konum tek nokta değildir. $(3,5)$ ile $(6,2)$ arasındaki $x+y=8$ doğru parçasının tamamı optimumdur ve minimum maksimum uzaklık 8 birimdir.

### Adım 5 - Uzaklık kontrolü

$(3,5)$ noktasından sekiz tesise uzaklıklar:

$$8,\;2,\;8,\;8,\;4,\;2,\;4,\;8$$

ve maksimum 8'dir. $(6,2)$ noktasında uzaklıklar:

$$8,\;6,\;2,\;6,\;8,\;6,\;2,\;8$$

ve maksimum yine 8'dir. Doğru parçasındaki diğer noktalar da $P_1=(0,0)$ ve $P_8=(8,8)$ noktalarına 8 birim uzaktadır.

### Öz-açıklama

1. Neden yalnız dönüştürülmüş aralıkların orta noktasını yazmak eksik olurdu?
2. Bu örnekte $U^*$ neden tek noktaya çöktü, $V^*$ neden aralık kaldı?
3. Amaç toplam uzaklık olsaydı hangi yöntem kullanılmalıydı?

## 3 - Kademeli örnek

> [!question]
> $P_1=(0,0)$, $P_2=(8,0)$ ve $P_3=(2,6)$ için dikdoğrusal minimax çözüm kümesini bulun.
>
> 1. $(u_i,v_i)$ değerleri: $\_\_\_$.
> 2. $\Delta_u=\_\_$, $\Delta_v=\_\_$.
> 3. $R^*=\_\_$.
> 4. $U^*=\_\_$, $V^*=\_\_$.
> 5. Optimum doğru parçasının uçlarını $(x,y)$ düzlemine çevirin.

> [!answer]- Tam çözüm
> Dönüşümler:
>
> | Nokta | $u=a+b$ | $v=a-b$ |
> |---:|---:|---:|
> | $(0,0)$ | 0 | 0 |
> | $(8,0)$ | 8 | 8 |
> | $(2,6)$ | 8 | -4 |
>
> $$\Delta_u=8,\qquad \Delta_v=12,\qquad R^*=6$$
>
> $$U^*=[8-6,0+6]=[2,6]$$
> $$V^*=[8-6,-4+6]=[2,2]$$
>
> $(u,v)=(2,2)$ için $(x,y)=(2,0)$; $(6,2)$ için $(x,y)=(4,2)$ bulunur. Bu iki nokta arasındaki doğru parçasının tamamı optimumdur ve maksimum uzaklık 6'dır.

## 4 - Bağımsız sorular

### L1 - Temel

> [!question]
> $P_1=(0,0)$ ve $P_2=(6,4)$ için $R^*$ değerini ve tüm optimum konumları bulun.

> [!answer]- Çözüm
> Dönüşmüş noktalar $(u,v)=(0,0)$ ve $(10,2)$'dir.
> $$R^*=\tfrac12\max(10,2)=5$$
> $$U^*=[5,5],\qquad V^*=[-3,5]$$
> Ters dönüşüm uçları $(1,4)$ ve $(5,0)$'dır. Bu iki nokta arasındaki $x+y=5$ doğru parçasının tamamı optimumdur.

### L2 - Tuzaklı / aktarım

> [!question]
> Bir öğrenci kaynak örneğinde dönüştürülmüş aralıkların orta değerlerini alıp $(u,v)=(8,1)$ ve $(x,y)=(4{,}5,3{,}5)$ buluyor. “Cevap doğru mu, tam mı?” sorusunu gerekçeli yanıtlayın.

> [!answer]- Çözüm
> Nokta doğrudur: $u=8$ ve $v=1\in[-2,4]$ olduğundan maksimum uzaklığı 8'dir. Fakat cevap tam değildir. Soru optimum konumları soruyorsa $v\in[-2,4]$ aralığının ve buna karşılık gelen $(3,5)$-$(6,2)$ doğru parçasının tamamı yazılmalıdır.

### L3 - Yöntemi seç

> [!question]
> Aşağıdaki amaçlardan hangisinde ağırlıklı medyan, hangisinde $u$-$v$ minimax dönüşümü gerekir?
>
> 1. Günlük toplam forklift yolunu azaltmak.
> 2. En uzaktaki iş istasyonunun güvenlik noktasına uzaklığını azaltmak.
> 3. Her istasyonun akış ağırlığıyla çarpılmış toplam yolunu azaltmak.

> [!answer]- Çözüm
> 1. Minisum; ağırlıklar eşitse sıradan medyan özel durumudur.
> 2. Ağırlıksız dikdoğrusal minimax ve $u$-$v$ dönüşümü.
> 3. Ağırlıklı minisum ve ağırlıklı medyan.

## 5 - Çıkış bileti

Notu kapatıp cevapla:

1. $u$ ve $v$ nasıl tanımlanır, ters dönüşüm nedir?
2. $R^*$ hangi iki yayılımdan bulunur?
3. Neden yalnız bir “merkez noktası” yazmak bazen eksik cevaptır?

## 6 - Tekrar kaydı

| Oturum | Tarih | Soru | Puan / 10 | Süre | Hata kodu |
|---|---|---|---:|---:|---|
| D0 |  | Kademeli örnek |  |  |  |
| D1 |  | L1 |  |  |  |
| D3 |  | L2 + minisum sorusu |  |  |  |
| D7 |  | Kaynak örneğini kapalı kitap çöz |  |  |  |
| D14 |  | Karma konum testi |  |  |  |

## Hata kartı

| Yanlış adım | Neden yanlış? | Sonraki kontrolde ne yapacağım? |
|---|---|---|
| $v=a-b$ ile başlayıp ters dönüşümde başka işaret kullandım. | İşaret sözleşmeleri karıştı. | Dönüşüm ve ters dönüşümü çözümün başında kutuya alacağım. |
| $R^*$ için iki aralık uzunluğunu topladım. | Minimax kare yarıçapı büyük yayılımın yarısıdır. | $R^*=\max(\Delta_u,\Delta_v)/2$ yazacağım. |
| Yalnız aralık orta noktasını verdim. | Diğer optimum konumları kaybettim. | $U^*$ ve $V^*$ aralıklarını her zaman kuracağım. |
| Öklid uzaklığıyla kontrol ettim. | Model Manhattan uzaklığı kullanıyor. | Kontrolde $|x-a|+|y-b|$ yazacağım. |

## Kaynaklar

- Ders sunumu: [[HF11-P11-Tesis Konumu I-2025.pptx|HF11]], slayt 28-32; sayısal örnek slayt 30-32.
- [[05 Kaynaklar/MarkItDown/HF11 - Ham|HF11 ham metni]]
- Ders kitabı: Bölüm 10.2.1.3, tek tesis dikdoğrusal minimax modeli.
