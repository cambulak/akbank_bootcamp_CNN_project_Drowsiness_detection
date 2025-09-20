# 💤 CNN Tabanlı Drowsiness (Uyku Hali) Tespiti
**Akbank Derin Öğrenme Bootcamp Projesi – Eylül 2025**

Bu proje kapsamında, **MRL Eye Dataset** kullanılarak sürücülerin göz açıklık/kapalı durumlarını sınıflandıran bir **Convolutional Neural Network (CNN)** tabanlı model geliştirilmiştir.  
Amaç, **uyku hali (drowsiness detection)** tespiti yaparak sürücü güvenliğine katkıda bulunmaktır.  

🔗 **Kaggle Notebook:** [Projeyi Kaggle’da incele](https://www.kaggle.com/code/sedatakda/akbank-bootcamp-project-cnn-drowsiness-detection)  

---

## 📂 Kullanılan Veri Seti
- **Kaynak:** [MRL Eye Dataset](http://mrl.cs.vsb.cz/eyedataset)  
- **Özellikler:**
  - 84,898 görüntü
  - Açık/Kapalı göz sınıfları
  - Farklı ışık koşulları, cihazlar ve yansıma seviyeleri
  - Ek anotasyonlar: cinsiyet, gözlük durumu, ışık koşulu, sensör ID
<img width="1182" height="242" alt="image" src="https://github.com/user-attachments/assets/860c91be-f840-4536-8ecd-a10eae66f5cd" />
<img width="1182" height="242" alt="image" src="https://github.com/user-attachments/assets/7e5a1ea2-b88a-465d-b1a9-285fe030659b" />
<img width="1182" height="242" alt="image" src="https://github.com/user-attachments/assets/e3bf8d2d-9a48-4e24-893a-3d9570fce4cd" />
<img width="1182" height="242" alt="image" src="https://github.com/user-attachments/assets/1ada80cf-a534-4294-8fb2-e05031b54714" />
<img width="1182" height="242" alt="image" src="https://github.com/user-attachments/assets/0649fdd8-2c0c-4fce-bdd5-10e3f266a143" />

---

## 🛠️ Kullanılan Teknolojiler
- **Python 3.11**
- **TensorFlow / Keras**
- **OpenCV**
- **scikit-learn**
- **Matplotlib / Seaborn**
- **Keras Tuner** (Hiperparametre optimizasyonu)
- **TensorBoard** (Model izleme)

---

## 🔎 Çalışma Adımları

### 1. Veri Önişleme
- Görseller yeniden boyutlandırıldı (96x96).
- Normalizasyon yapıldı.
- Train/Validation/Test split oluşturuldu.
- Data Augmentation (rotation, flip, zoom, color jitter) uygulandı.

### 2. Model Mimarisi
- CNN tabanlı model:  
  - Convolutional Layers  
  - Pooling Layers  
  - Dropout  
  - Dense Layers  
  - Aktivasyon: ReLU, Sigmoid  
- Transfer Learning ile performans artırma denemeleri yapıldı.

### 3. Hiperparametre Optimizasyonu
Keras Tuner kullanılarak aşağıdaki parametreler optimize edildi:
- Filtre sayısı
- Kernel boyutu
- Dense layer boyutları
- Dropout oranı
- Learning rate

**En iyi sonuç veren kombinasyon:**
- Kernel Size: **5**
- Filters: **64**
- Dense Units: **64**
- Dropout: **0.5**
- Learning Rate: **0.001**
- Val Accuracy: **%96.55**

### 4. Model Değerlendirmesi
- **Accuracy & Loss Grafikleri** (overfitting / underfitting kontrolü)  
- **Confusion Matrix**  
- **Classification Report**

<img width="576" height="455" alt="image" src="https://github.com/user-attachments/assets/d12a3638-a9fb-420e-a92f-dc3c35469f02" />


<img width="576" height="455" alt="image" src="https://github.com/user-attachments/assets/3ae05ce0-db3e-443a-9d3a-1af930882a8d" />

1. Accuracy Grafiği

Eğitim (mavi) ve validasyon (turuncu) accuracy değerlerin çok yakın ilerliyor.

Validasyon eğrisi eğitimden biraz daha yüksek (bu normal olabilir, dropout ve regularization etkisiyle).

Overfitting yok ✅ Çünkü validasyon accuracy’si eğitim accuracy’sinden kopmamış.

2. Loss Grafiği

Eğitim kaybı (mavi) ve validasyon kaybı (turuncu) sürekli azalarak birbirine yakın ilerliyor.

Validasyon kaybı da düzenli şekilde düşüyor.

Underfitting de yok ✅ Çünkü loss yüksek kalmamış, hızlıca düşmüş.

📊 **Sonuçlar:**
- Test Accuracy: **%98**
- Closed: Precision 0.98, Recall 0.99
- Open: Precision 0.99, Recall 0.98

### 5. Grad-CAM Görselleştirmesi
Modelin karar verirken hangi bölgeleri dikkate aldığı Grad-CAM yöntemi ile görselleştirilmiştir.  
Model, açık/kapalı göz tespitinde doğru bölgelere odaklanmaktadır.

---

## 📊 Sonuçlar ve Çıkarımlar
- CNN tabanlı model + Transfer Learning ile **yüksek doğruluk** elde edilmiştir.
- Data Augmentation, modelin genelleme kapasitesini artırmıştır.
- Keras Tuner ile yapılan hiperparametre optimizasyonu, doğruluğu **%96.55**’e çıkarmıştır.
- Test setinde **%98 başarı** sağlanarak modelin güvenilirliği kanıtlanmıştır.


