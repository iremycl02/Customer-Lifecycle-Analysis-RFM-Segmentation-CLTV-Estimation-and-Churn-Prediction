# Customer-Lifecycle-Analysis-RFM-Segmentation-CLTV-Estimation-and-Churn-Prediction
Bu proje, e-ticaret müşterilerinin geçmiş davranışlarını analiz ederek RFM segmentasyonu oluşturur, müşteri yaşam boyu değerini (CLTV) tahmin eder ve Random Forest ile churn riskini öngörür; böylece hedefli pazarlama ve müşteri sadakati stratejilerini destekler. Müşterilerin geçmiş davranışlarına dayanarak:

Hangi müşterilerin kaybedilme riski taşıdığını belirleme
Müşterileri RFM (Recency, Frequency, Monetary) analizine göre segmentlere ayırma
Müşteri yaşam boyu değerini (CLTV) tahmin etme
Proaktif pazarlama stratejileri geliştirme


Teknolojiler

Python 3.x
pandas - Veri manipülasyonu ve analizi
lifetimes - BG/NBD ve Gamma-Gamma modelleri ile CLTV tahmini
scikit-learn - Machine Learning modelleri ve değerlendirme metrikleri
datetime - Tarih işlemleri


Veri Seti

Kayıt Sayısı: 19,945 müşteri
Zaman Aralığı: 2013-2021
Özellikler: Sipariş tarihleri, sipariş sayıları, müşteri değerleri, ilgilenilen kategoriler


Metodoloji

1. RFM Analizi

Recency: Son alışverişten bu yana geçen gün sayısı
Frequency: Toplam sipariş sayısı
Monetary: Toplam harcama tutarı
RFM skorlarına göre 10 segment oluşturuldu (Champions, Loyal Customers, At Risk, vb.)

2. CLTV Tahmini

BG/NBD Modeli: Müşteri satın alma sıklığını modelleme
Gamma-Gamma Modeli: Müşteri başına ortalama kazancı tahmin etme
3 ve 6 aylık satış tahminleri yapıldı

3. Churn Tahmini

Hedef Değişken: 90 günden uzun süredir alışveriş yapmayan müşteriler (Churn=1)
Model: Random Forest Classifier
Özellikler: Frequency, T (müşteri yaşı), CLTV, online/offline oranları, kategori sayısı


Sonuçlar

Model Performansı

Accuracy: %61.53
Precision (Churn): 0.62
Recall (Churn): 0.86
F1-Score (Churn): 0.72
5-Fold CV Accuracy: %62.09


Özellik Önem Sıralaması

CLTV (29.9%)
Müşteri Yaşı - T (27.7%)
Online Harcama (12.7%)
Frequency (9.3%)
Offline Harcama (5.1%)


RFM Segmentleri

Champions: 1,920 müşteri (ortalama 8.96 sipariş, 1,410 TL harcama)
Loyal Customers: 3,375 müşteri
At Risk: 3,152 müşteri
Hibernating: 3,589 müşteri


Örnek Kullanım

python# Yeni müşteri için churn olasılığı hesaplama
yeni_musteri = pd.DataFrame({
    'Frequency': [3],
    'T': [200],
    'CLTV': [500.0],
    'order_num_total_ever_online': [1.0],
    'order_num_total_ever_offline': [2.0],
    # ... diğer özellikler
})

churn_olasiligi = rf_model.predict_proba(yeni_musteri)[:, 1]
print(f"Churn Olasılığı: {churn_olasiligi[0]:.2%}")


İş Değeri

Bu model sayesinde:
Yüksek riskli müşteriler erken tespit edilebilir
Hedefli retention kampanyaları düzenlenebilir
Müşteri segmentlerine özel pazarlama stratejileri geliştirilebilir
Kaynak optimizasyonu yapılabilir (değerli müşterilere odaklanma)


