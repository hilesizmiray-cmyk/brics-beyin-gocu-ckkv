# Multi-Criteria Analysis of Youth Brain Drain Risk in BRICS Countries (MOORA & COPRAS)

> An indirect (proxy-based) assessment of brain drain risk among the young population of BRICS countries, using the MOORA and COPRAS methods with Entropy weighting.

[Türkçe](README.md) | **English**

---

## About the Project

This study evaluates the level of brain drain risk that BRICS countries (Brazil, China, India, Russia, South Africa) generate for their young populations, using **multi-criteria decision-making (MCDM)** methods within the framework of economic stability, labor market, and welfare indicators.

Because brain drain cannot be reduced to a single directly measurable indicator, macroeconomic and social indicators influencing a young person's decision to stay in or leave the country are used as **proxy variables**.

BRICS countries were chosen as alternatives because, despite being emerging economies at similar levels of development, they differ significantly in economic stability, labor market, and welfare indicators — forming a heterogeneous group well suited for comparison.

The originality of the study lies in combining these three methods (Entropy + MOORA + COPRAS) with this specific topic and criteria set, a combination with no direct precedent in the literature.

> **Academic context:** Haliç University, M.Sc. in Management Information Systems (thesis track) — Multi-Criteria Decision-Making Methods course, final project (Fall 2025). Supervisor: Prof. Dr. Nuray Tezcan.

---

## Dataset

- **Source:** World Bank database
- **Year:** 2023 (health expenditure as % of GDP uses 2022 data, as 2023 figures were unavailable)
- **Alternatives:** 5 BRICS countries
- **Criteria:** 6

---

## Criteria

| Code | Criterion | Type | Unit |
|------|-----------|------|------|
| K1 | Employment rate (ages 15+) | Benefit | % |
| K2 | GDP per capita (PPP) | Benefit | international $ |
| K3 | Inflation (consumer prices) | Cost | % |
| K4 | Life expectancy at birth | Benefit | years |
| K5 | Unemployment rate | Cost | % |
| K6 | Health expenditure as % of GDP | Benefit | % |

**Benefit criteria** (higher is better): K1, K2, K4, K6
**Cost criteria** (higher is worse): K3, K5

---

## Methodology

The analysis follows three stages:

**1. Entropy weighting.** Criterion weights were computed objectively with the Entropy method, independent of subjective judgment. Based on the distribution of the data, it assigns higher weights to criteria with greater discriminating power. The same weights were used in both MOORA and COPRAS to ensure consistency between methods.

**2. MOORA (Significance Coefficient approach).** Since the criteria are not equally important, the significance approach was used. The decision matrix was normalized by vector norm, multiplied by the entropy weights, and for each country `Yi = sum of benefit criteria − sum of cost criteria` was computed. A higher `Yi` indicates lower risk.

**3. COPRAS (Complex Proportional Assessment).** The decision matrix was normalized by column sums, weighted with entropy, then split into benefit (`Si+`) and cost (`Si−`) sums; the relative significance (`Qi`) and utility degree (`Ni = Qi / Qmax × 100`) were calculated. The country closest to 100 is the best (lowest-risk) alternative.

---

## Results

### Entropy Criterion Weights (wj)

| Criterion | Weight |
|-----------|--------|
| K5 — Unemployment rate | 0.5400 |
| K3 — Inflation | 0.2278 |
| K2 — GDP per capita | 0.1463 |
| K6 — Health expenditure/GDP | 0.0695 |
| K1 — Employment rate | 0.0145 |
| K4 — Life expectancy | 0.0019 |

The unemployment rate (K5) emerged as the most decisive criterion, carrying the most discriminating information across alternatives.

### MOORA Results (Yi)

| Rank | Country | Yi |
|------|---------|-----|
| 1 | China | 0.0159 |
| 2 | Russia | −0.0191 |
| 3 | Brazil | −0.1195 |
| 4 | India | −0.1345 |
| 5 | South Africa | −0.5546 |

### COPRAS Results (Ni)

| Rank | Country | Ni (%) |
|------|---------|--------|
| 1 | China | 99.99 |
| 2 | Russia | 55.92 |
| 3 | India | 50.53 |
| 4 | Brazil | 39.59 |
| 5 | South Africa | 13.10 |

### Conclusion

Both methods agree at the critical extremes: **China** has the **lowest** indirect brain drain risk for its young population, while **South Africa** has the **highest**. The fact that two independent MCDM methods converge at these extremes supports the reliability of the findings and the methodological consistency of the study. (In the middle of the ranking, Brazil and India swap positions between the two methods.)

The results reflect not direct brain drain figures, but the relative indirect risk levels of countries within the framework of the chosen proxy indicators.

---

## Files

| File | Description |
|------|-------------|
| `moora_ve_copras.xlsx` | Excel workbook with all computations (decision matrix, entropy, MOORA, COPRAS) |
| `moora_ve_copras.pdf` | Full text of the study (methodology, formulas, findings, references) |

---

## Roadmap

- [x] End-to-end MCDM analysis in Excel
- [x] Study report (PDF)
- [x] **Python implementation** — Entropy, MOORA and COPRAS coded from scratch with `pandas` / `numpy`, validated against the Excel results completed.

---

## Method Notes

- **MOORA** (Multi-Objective Optimization by Ratio Analysis): a ratio-based multi-objective optimization method introduced by Brauers and Zavadskas (2006).
- **COPRAS** (Complex Proportional Assessment): developed by Zavadskas and Kaklauskas (1996); expresses how much better or worse each alternative is relative to the others, as a percentage.
- **Entropy weighting:** an objective weighting method that derives criterion importance from the distribution of the data.

### Selected References

- Ayçin, E. (2023). *Çok Kriterli Karar Verme: Bilgisayar Uygulamalı Çözümler* (3rd ed.). Nobel Akademik Yayıncılık.
- Özbek, A., & Erol, E. (2016). Application of COPRAS and MOORA methods to the warehouse location selection problem. *Ekonomi, İşletme, Siyaset ve Uluslararası İlişkiler Dergisi*, 2(1), 23–42.
- Brauers, W. K. M., & Zavadskas, E. K. (2010). Project management by MULTIMOORA as an instrument for transition economies. *Technological and Economic Development of Economy*, 16(1), 5–24.

---

## Author

**Miray Hilesiz**
M.Sc. in Management Information Systems — Haliç University

Contact: [mirayhilesiz.com](https://mirayhilesiz.com) · hilesizmiray@gmail.com
