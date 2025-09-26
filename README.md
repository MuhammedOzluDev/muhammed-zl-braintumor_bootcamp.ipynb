# muhammed-zl-braintumor_bootcamp.ipynb
🧠 Brain Tumor MRI Classification
📌 Projenin Amacı

Bu projenin amacı, MRI beyin görüntülerinden tümör varlığını ve türünü otomatik olarak sınıflandırabilen bir derin öğrenme modeli geliştirmektir. Proje, radyologlara yardımcı tanı desteği sunmayı, hızlı ön tarama ve ikinci görüş sistemi gibi klinik uygulamalara katkı sağlamayı hedefler.

📂 Veri Seti

Kaynak: Brain Tumor MRI Dataset (Kaggle)

Toplam: 7.023 MRI görüntüsü

Sınıflar:

Glioma (1621)

Meningioma (1645)

No Tumor (2000)

Pituitary (1757)

Görseller farklı boyutlarda olup, eğitim sürecinde 224x224 boyutuna dönüştürülmüştür.

Sınıf dağılımı dengeli olduğu için modelin öğrenme süreci daha sağlıklı gerçekleşmiştir.

⚙️ Kullanılan Yöntemler

Veri Ön İşleme: Stratified split (train/val/test), yeniden boyutlandırma

Veri Artırma (Augmentation): Rotation, shift, zoom, shear, brightness değişimi, horizontal & vertical flip

Model: EfficientNetB0 (ImageNet önceden eğitilmiş ağırlıklarla) + özel dense katmanlar (512 → 256 → output)

Eğitim Stratejisi:

EarlyStopping, ModelCheckpoint

ReduceLROnPlateau

Cosine Learning Rate Scheduler

Değerlendirme: Accuracy/Loss grafikleri, Confusion Matrix, Classification Report

Açıklanabilirlik: Grad-CAM için altyapı kuruldu, fakat test aşamasında tam anlamıyla stabil görselleştirme alınamadı.

📊 Elde Edilen Sonuçlar

Final Test Accuracy: %92.82

Classification Report:

Sınıf	Precision	Recall	F1-Score	Support
Glioma	0.94	0.89	0.91	203
Meningioma	0.88	0.85	0.86	205
No Tumor	0.99	0.97	0.98	250
Pituitary	0.90	0.98	0.94	220
Macro Avg	0.93	0.92	0.92	878
Accuracy			0.93	

Model Parametreleri: 4.8M toplam, ~1.3M trainable

Eğitim Süresi: ~45 dakika (GPU ortamında)

💡 Gelişmiş Özellikler

EfficientNetB0 transfer learning

Yoğun veri artırma (heavy augmentation)

Fine-tuning stratejisi

Grad-CAM implementasyonu (altyapı hazır, görselleştirme aşamasında hata alındı)

İleri seviye callback’ler ve öğrenme oranı planlaması (scheduling)

KAGGLE LİNKİ:https://www.kaggle.com/code/muhammedzl/muhammed-zl-braintumor
