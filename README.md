# linehaul-optimizasyon
TEKNOFEST 2026 - Yapay Zeka Destekli Lojistik Anahat Optimizasyonu | SANKA Takımı
# 🚛 Yapay Zeka Destekli Lojistik Anahat Optimizasyonu
**SANKA Takımı | TEKNOFEST 2026**

---

## 📊 Toplam Maliyet
| Maliyet Kalemi | Tutar |
|---|---|
| Kiralık Araç Maliyeti | 802,744 TL |
| Spot Araç Maliyeti | 10,543,956 TL |
| **TOPLAM MALİYET** | **11,346,700 TL** |

---

## 🎯 Proje Özeti
HepsiJET linehaul operasyonları için 11-17 Mayıs 2026 haftasının
talep tahmini ve spot araç optimizasyonu.

---

## 🤖 Tahmin Modeli
- **Algoritma:** LightGBM (XGBoost ile karşılaştırıldı, LightGBM kazandı)
- **Doğrulama:** Walk Forward Validation (10 pencere)
- **Ortalama MAE:** 2,862 desi
- **Naive Baseline MAE:** 5,073 desi
- **İyileşme:** %44
- **Anormal günler:** Bayram ve eksik veri günleri temizlendi (8 gün)
- **Feature'lar:** lag_7, lag_14, lag_21, rolling_mean_7, rolling_mean_14, rolling_std_7, HaftaninGunu, HaftaNo, Ay, YilinGunu, AyinGunu

---

## ⚙️ Optimizasyon
- **Yöntem:** Exhaustive Search (tüm araç tipleri karşılaştırılır, en ucuzu seçilir)
- **Kiralık araçlar:** Her zaman önce kullanılır (zorunlu)
- **Spot araçlar:** Min %10 doluluk kısıtı uygulandı
- **Mesafe:** Haversine (kuş uçuşu) formülü
- **Araç tipleri:** Tır, Kamyon, Hafif Kamyon, Kamyonet
- **Dönüş rotası:** Hesaba katılmadı (şartname gereği)

---

## 📁 Dosyalar
| Dosya | Açıklama |
|---|---|
| `linehaul_optimizasyon_final.ipynb` | Tüm kodlar (tahmin + optimizasyon) |
| `tahmin_11_17_mayis.xlsx` | 11-17 Mayıs tahmin çıktısı (623 satır) |
| `arac_planlama_11_17_mayis.xlsx` | Araç planlama çıktısı (667 satır) |

---

## 🔧 Varsayımlar
- Her araç günde tek sefer yapar
- Araçlar geri dönmez (tek yönlü)
- Her TM'de sınırsız spot araç mevcuttur
- Konsolidasyon uygulanmadı (MVP aşaması)
- Mesafe: Haversine (kuş uçuşu)
- Maliyet: Günlük Sabit + (Km × Km Maliyeti)

---

## 📦 Kurulum
```bash
pip install pandas numpy lightgbm xgboost scikit-learn openpyxl pulp
```

Google Colab'da çalıştırmak için:
1. Notebook'u Colab'da aç
2. Veri dosyalarını `/content/` dizinine yükle
3. `Runtime → Run all` tıkla
