# BRICS Ülkelerinde Genç Beyin Göçü Riskinin Çok Kriterli Analizi (MOORA & COPRAS)

> Entropi ağırlıklandırması ile MOORA ve COPRAS yöntemleri kullanılarak, BRICS ülkelerinin genç nüfus açısından beyin göçü riskinin dolaylı (proxy) olarak değerlendirilmesi.

**Türkçe** | [English](README.en.md)

---

## Proje Hakkında

Bu çalışma, BRICS ülkelerinin (Brezilya, Çin, Hindistan, Rusya, Güney Afrika) genç nüfus açısından beyin göçü riski üretme düzeyini; ekonomik istikrar, işgücü piyasası ve refah göstergeleri çerçevesinde **çok kriterli karar verme (ÇKKV)** yöntemleriyle dolaylı olarak değerlendirmektedir.

Beyin göçü doğrudan ölçülebilen tek bir göstergeye indirgenemediği için, analizde genç nüfusun ülkede kalma ya da ülkeden ayrılma kararını etkileyen makroekonomik ve sosyal göstergeler **proxy (dolaylı) değişkenler** olarak kullanılmıştır.

BRICS ülkelerinin alternatif olarak seçilme nedeni, benzer gelişmişlik düzeyine sahip yükselen ekonomiler olmalarına rağmen ekonomik istikrar, işgücü piyasası ve refah göstergeleri açısından belirgin farklılıklar göstermeleri, dolayısıyla heterojen ve karşılaştırmaya elverişli bir grup oluşturmalarıdır.

Çalışmanın özgünlüğü, bu üç yöntemin (Entropi + MOORA + COPRAS) bu konu ve kriter setiyle birlikte kullanılmasının literatürde doğrudan bir öncülüne rastlanmamış olmasıdır.

> **Akademik bağlam:** Haliç Üniversitesi, Yönetim Bilişim Sistemleri Tezli Yüksek Lisans Programı — Çok Kriterli Karar Verme Yöntemleri dersi final çalışması (Güz 2025). Danışman: Prof. Dr. Nuray Tezcan.

---

## Veri Seti

- **Kaynak:** Dünya Bankası (World Bank) veri tabanı
- **Yıl:** 2023 (sağlık harcamalarının GSYH içindeki payı için 2023 verisi bulunmadığından 2022 yılı verisi kullanılmıştır)
- **Alternatifler:** 5 BRICS ülkesi
- **Kriter sayısı:** 6

---

## Kriterler

| Kod | Kriter | Yön | Birim |
|-----|--------|-----|-------|
| K1 | İstihdam oranı (15 yaş ve üzeri) | Fayda | % |
| K2 | Kişi başına düşen GSYH (SGP) | Fayda | uluslararası $ |
| K3 | Enflasyon (tüketici fiyatları) | Maliyet | % |
| K4 | Doğuşta beklenen yaşam süresi | Fayda | yıl |
| K5 | İşsizlik oranı | Maliyet | % |
| K6 | Sağlık harcamalarının GSYH içindeki payı | Fayda | % |

**Fayda kriterleri** (değeri arttıkça ülke performansı iyileşir): K1, K2, K4, K6
**Maliyet kriterleri** (değeri arttıkça performans olumsuz etkilenir): K3, K5

---

## Yöntem

Analiz üç aşamadan oluşmaktadır:

**1. Entropi ile kriter ağırlıklandırma.** Kriter ağırlıkları öznel yargılardan bağımsız, nesnel bir biçimde belirlenebilmesi için Entropi yöntemiyle hesaplanmıştır. Verilerin dağılımına dayanan bu yaklaşım, ayırt ediciliği (farklılaşması) yüksek kriterlere daha yüksek ağırlık atar. Aynı ağırlıklar hem MOORA hem COPRAS hesaplamalarında kullanılarak yöntemler arası tutarlılık sağlanmıştır.

**2. MOORA (Önem Katsayısı Yaklaşımı).** Kriterler eşit önemde kabul edilmediği için MOORA'nın önem yaklaşımı tercih edilmiştir. Karar matrisi vektör normuna göre normalize edilmiş, entropi ağırlıklarıyla çarpılmış ve her ülke için `Yi = Fayda kriterleri toplamı − Maliyet kriterleri toplamı` değeri hesaplanmıştır. Yüksek `Yi` daha düşük riski ifade eder.

**3. COPRAS (Complex Proportional Assessment).** Karar matrisi sütun toplamlarına bölünerek normalize edilmiş, entropi ile ağırlıklandırılmış, fayda (`Si+`) ve maliyet (`Si−`) toplamları ayrıştırılmış; göreli önem (`Qi`) ve fayda derecesi (`Ni = Qi / Qmax × 100`) hesaplanmıştır. Fayda derecesi 100'e en yakın olan ülke en iyi (en düşük riskli) alternatiftir.

---

## Bulgular

### Entropi Kriter Ağırlıkları (wj)

| Kriter | Ağırlık |
|--------|---------|
| K5 — İşsizlik oranı | 0,5400 |
| K3 — Enflasyon | 0,2278 |
| K2 — Kişi başına GSYH | 0,1463 |
| K6 — Sağlık harcamaları/GSYH | 0,0695 |
| K1 — İstihdam oranı | 0,0145 |
| K4 — Yaşam süresi | 0,0019 |

İşsizlik oranı (K5), alternatifler arasında en fazla ayırt edici bilgiyi taşıdığı için karar sürecindeki en belirleyici kriter olarak öne çıkmıştır.

### MOORA Sonuçları (Yi)

| Sıra | Ülke | Yi |
|------|------|-----|
| 1 | Çin | 0,0159 |
| 2 | Rusya | −0,0191 |
| 3 | Brezilya | −0,1195 |
| 4 | Hindistan | −0,1345 |
| 5 | Güney Afrika | −0,5546 |

### COPRAS Sonuçları (Ni)

| Sıra | Ülke | Ni (%) |
|------|------|--------|
| 1 | Çin | 99,99 |
| 2 | Rusya | 55,92 |
| 3 | Hindistan | 50,53 |
| 4 | Brezilya | 39,59 |
| 5 | Güney Afrika | 13,10 |

### Sonuç

Her iki yöntem de en kritik noktalarda örtüşmektedir: **Çin**, kullanılan göstergeler çerçevesinde genç nüfus açısından **en düşük dolaylı beyin göçü riskine** sahip ülke; **Güney Afrika** ise **en yüksek riske** sahip ülke olarak belirlenmiştir. İki bağımsız ÇKKV yönteminin uçlarda aynı sonucu vermesi, bulguların güvenilirliğini ve çalışmanın yöntemsel tutarlılığını desteklemektedir. (Ara sıralamada Brezilya ve Hindistan iki yöntemde yer değiştirmektedir.)

Elde edilen sonuçlar doğrudan beyin göçü verilerini değil, proxy göstergeler çerçevesinde ülkelerin göreli dolaylı risk düzeylerini yansıtmaktadır.

---

## Dosyalar

| Dosya | Açıklama |
|-------|----------|
| `moora_ve_copras.xlsx` | Tüm hesaplamaların yer aldığı Excel çalışma dosyası (karar matrisi, entropi, MOORA, COPRAS) |
| `moora_ve_copras.pdf` | Çalışmanın tam metni (yöntem, formüller, bulgular, kaynakça) |

---

## Yol Haritası

- [x] Excel ile uçtan uca ÇKKV analizi
- [x] Çalışma raporu (PDF)
- [x] **Python implementasyonu** — Entropi, MOORA ve COPRAS yöntemlerinin `pandas` / `numpy` ile sıfırdan kodlanması ve Excel sonuçlarıyla doğrulanması tamamlandı.

---

## Yöntemler Hakkında Kısa Notlar

- **MOORA** (Multi-Objective Optimization by Ratio Analysis): Brauers ve Zavadskas (2006) tarafından geliştirilen, oransal analize dayalı çok amaçlı optimizasyon yöntemi.
- **COPRAS** (Complex Proportional Assessment): Zavadskas ve Kaklauskas (1996) tarafından geliştirilen, alternatiflerin birbirlerine göre ne kadar iyi/kötü olduğunu yüzdesel olarak ortaya koyan yöntem.
- **Entropi ağırlıklandırma:** Kriterlerin önem derecelerini verinin dağılımına göre nesnel olarak belirleyen ağırlıklandırma yöntemi.

### Seçilmiş Kaynaklar

- Ayçin, E. (2023). *Çok Kriterli Karar Verme: Bilgisayar Uygulamalı Çözümler* (3. Baskı). Nobel Akademik Yayıncılık.
- Özbek, A., & Erol, E. (2016). COPRAS ve MOORA yöntemlerinin depo yeri seçim problemine uygulanması. *Ekonomi, İşletme, Siyaset ve Uluslararası İlişkiler Dergisi*, 2(1), 23–42.
- Brauers, W. K. M., & Zavadskas, E. K. (2010). Project management by MULTIMOORA as an instrument for transition economies. *Technological and Economic Development of Economy*, 16(1), 5–24.

---

## Yazar

**Miray Hilesiz**
Yönetim Bilişim Sistemleri, Yüksek Lisans — Haliç Üniversitesi

İletişim: [mirayhilesiz.com](https://mirayhilesiz.com) · hilesizmiray@gmail.com
