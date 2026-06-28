---
tags: [ders/tesis-planlama, algoritma, özet]
---

# Yerleşim Algoritmaları — Master Karşılaştırma Tablosu

> [!summary] Tek bakışta 8 algoritma
> Bu tablo sınav sabahı 10 dakikada tüm algoritmaları kafada canlandırmak için tasarlandı. Her algoritmayı yöntem grubu, veri türü, amaç ve ayırt edici özelliğiyle ezberle.

## Ana Karşılaştırma

| Algoritma | Tür | Veri Türü | Amaç/Ölçüt | Ayırt Edici Özellik |
|---|---|---|---|---|
| **Grafik Tabanlı** | Kurma | Nitel (REL) | $\sum w_{ij}$ → max | Düzlemsel grafik; yüz puanı; görsel |
| **CORELAP** | Kurma | Nitel (REL) | TCR → PR → max | Çekirdekten dışa; tek "en iyi" çözüm |
| **ALDEP** | Kurma | Nitel (REL + eşik) | Komşuluk puanı → max | Rassal sıra; çok alternatif; dikey süpürme |
| **BLOCPLAN** | Melez | Nitel+Nicel | $Z_A$/ER → max, RD → min | Dikdörtgen bantlar; akış→REL dönüşümü |
| **LOGIC** | Melez | Alan+İlişki | $\sum f_{ij}d_{ij}$ → min | Giyotin kesim ağacı; BLOCPLAN'ı kapsar |
| **CRAFT** | İyileştirme | Nicel (akış+maliyet) | $\sum f_{ij}c_{ij}d_{ij}$ → min | İkili/üçlü takas; ağırlık merkezi |
| **MCRAFT** | İyileştirme | Nicel (akış+maliyet) | $\sum f_{ij}c_{ij}d_{ij}$ → min | Bitişiklik kısıtı yok; yılan süpürme |
| **MULTIPLE** | Melez | Nicel (akış+kat) | $\sum f_{ij}(d_{ij}+\alpha\|z_i-z_j\|)$ → min | SFC; çok katlı bina; kat ağırlığı $\alpha$ |

## Kurma vs İyileştirme

| | **Kurma (Construction)** | **İyileştirme (Improvement)** |
|---|---|---|
| **Başlangıç** | Boş alan | Mevcut yerleşim |
| **Algoritmalar** | Grafik, CORELAP, ALDEP | CRAFT, MCRAFT |
| **Melez** | BLOCPLAN, LOGIC, MULTIPLE | — |
| **Risk** | Başlangıç seçimine bağlı değil | Yerel optimuma takılabilir |

## Nitel vs Nicel Veri

| Sadece REL (nitel) | REL + Akış (melez) | Sadece Akış/Maliyet (nicel) |
|---|---|---|
| Grafik tabanlı | BLOCPLAN, LOGIC | CRAFT, MCRAFT |
| CORELAP | MULTIPLE (+ kat) | — |
| ALDEP | | |

## REL Simetri — Kritik Uyarı

> [!warning] REL ≠ From-to
> **REL (ilişki) matrisi her zaman simetriktir:** $r_{ij}=r_{ji}$ — "A ile B'nin yakınlığı" yönsüzdür, üst üçgen yeterlidir.
> **From-to akış matrisi yönlüdür:** $f_{ij}\neq f_{ji}$ olabilir.
> BLOCPLAN'da önce from-to → $F_{ij}=f_{ij}+f_{ji}$ simetrikleştirmesi yapılır, sonra REL sınıfına çevrilir. Bu iki adımı karıştırma.

## Sınav Öncesi Yöntem Seçici

> [!tip] Hangi algoritmayı ne zaman?
> - **"Sadece REL var, sayısal akış yok"** → CORELAP veya ALDEP
> - **"Akış matrisi + maliyet/uzaklık var, başlangıç yerleşimi de var"** → CRAFT
> - **"REL + akış var, dikdörtgen bantlar"** → BLOCPLAN
> - **"Çok katlı bina"** → MULTIPLE
> - **"Kesim ağacı / giyotin"** → LOGIC
> - **"Çok alternatif iste, rassal başlangıç"** → ALDEP

## Akılda Kalıcı — "GAC + BLM + CM"

> [!tip] Mnemonik
> **G**rafik → **A**LDEP → **C**ORELAP = **kurma** (REL, içeriden dışarıya)
> **B**LOCPLAN → **L**OGIC → **M**ULTIPLE = **melez** (hem nitel hem nicel)
> **C**RAFT / M**C**RAFT = **iyileştirme** (başlangıca bağımlı, takas yap)

Tam karşılaştırma ve yöntem seçim ağacı: [[00 Pano/Yöntem Seçici|Yöntem Seçici]]
