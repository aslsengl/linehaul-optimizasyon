# linehaul-optimizasyon
TEKNOFEST 2026 - Yapay Zeka Destekli Lojistik Anahat Optimizasyonu | SANKA Takımı

# 🚛 Yapay Zeka Destekli Lojistik Anahat Optimizasyonu
**SANKA Takımı | TEKNOFEST 2026**

---

## 📊 Temel İşlevli Çözüm (MVP) Toplam Maliyeti
| Maliyet Kalemi | Tutar |
|---|---|
| Kiralık Araç Maliyeti | 802,744 TL |
| Spot Araç Maliyeti | 10,543,956 TL |
| **TOPLAM MALİYET** | **11,346,700 TL** |

---

## 🚀 Gelişmiş Çözüm Toplam Maliyeti
| Maliyet Kalemi | Tutar |
|---|---|
| Kiralık Araç Maliyeti | 649,491 TL |
| Spot Araç Maliyeti | 27,436,248 TL |
| SLA Ceza | 0 TL |
| **TOPLAM MALİYET** | **28,085,738.85 TL** |

---

## 🎯 Proje Özeti
HepsiJET linehaul operasyonları için yapay zeka destekli talep tahmini ve spot araç optimizasyonu.

- **MVP:** 11-17 Mayıs 2026 haftası
- **Gelişmiş:** 29 Haziran - 5 Temmuz 2026

---

## 🤖 Tahmin Modeli

### MVP
- **Algoritma:** LightGBM (XGBoost ile karşılaştırıldı)
- **Doğrulama:** Walk Forward Validation (10 pencere)
- **Ortalama MAE:** 2,862 desi | **Naive Baseline:** 5,073 desi | **İyileşme:** %44

### Gelişmiş Çözüm
- **Algoritma:** LightGBM (XGBoost ile karşılaştırıldı)
- **Doğrulama:** Walk Forward Validation (17 pencere)
- **Ortalama MAE:** 797 desi | **Naive Baseline:** 978 desi | **İyileşme:** %18
- **Anormal günler:** Bayram ve eksik veri günleri temizlendi (14 gün)
- **Feature'lar:** lag_7, lag_14, lag_21, rolling_mean_7, rolling_mean_14, rolling_std_7, HaftaninGunu, HaftaNo, Ay, YilinGunu, AyinGunu, saat_kodu

---

## ⚙️ Optimizasyon

### MVP
- Kiralık araçlar önce kullanılır
- En ucuz spot araç seçimi
- Min %10 doluluk kısıtı
- Mesafe: Haversine

### Gelişmiş Çözüm
- Kiralık araçlar önce kullanılır (zorunlu)
- 09:00 + 17:00 talepleri birleştirilerek maliyet düşürülür
- Tır kapasitesi kısıtı ✅
- Elleçleme kapasitesi kısıtı ✅
- SLA ceza: 0.00 TL ✅
- Maliyet: (Saatlik Kira × Kullanım Süresi) + (Km × Km Maliyeti)
- Maliyet desi oranında dağıtılır

---

## 📁 Dosyalar

| Dosya | Açıklama |
|---|---|
| `linehaul_optimizasyon_final.ipynb` | MVP kodları |
| `tahmin_11_17_mayis.xlsx` | MVP tahmin çıktısı (623 satır) |
| `arac_planlama_11_17_mayis.xlsx` | MVP araç planı (667 satır) |
| `SANKA_gelismis_cozum_FINAL.ipynb` | Gelişmiş çözüm kodları |
| `SANKA_talep_tahmini_FINAL.xlsx` | Gelişmiş tahmin (4046 satır) |
| `SANKA_tasima_plani_FINAL.xlsx` | Gelişmiş taşıma planı (4198 satır) |

---

## 📦 Kurulum
```bash
pip install pandas numpy lightgbm xgboost scikit-learn openpyxl
```

Google Colab'da çalıştırmak için:
1. Notebook'u Colab'da aç
2. Veri dosyalarını `/content/` dizinine yükle
3. `Runtime → Run all` tıkla
