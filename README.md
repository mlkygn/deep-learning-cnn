🦋 Butterfly Image Classification with CNN

## Projenin Amacı 
Bu proje, derin öğrenme tabanlı bir görüntü sınıflandırma modeli geliştirerek farklı kelebek türlerini tanımayı amaçlamaktadır.
Convolutional Neural Network (CNN) mimarisi kullanılarak, verilen bir kelebek görselinin doğru sınıfa atanması hedeflenmiştir.

## Veri Seti Hakkında

Veri setinde 75 farklı kelebek türü bulunmaktadır.
Eğitim, doğrulama ve test için toplamda ~10.000 etiketli görüntü kullanılmıştır.
Görseller .jpg formatında olup her sınıf yalnızca bir kelebek türünü temsil etmektedir.
Eğitim için veriler %80 train – %20 validation olacak şekilde ayrılmıştır.
Test setinde etiketsiz görüntüler yer almakta ve model performansını bağımsız değerlendirmek için kullanılmaktadır.

## Kullanılan Yöntemler 

Veri Ön İşleme ve Artırma (Data Augmentation):
    Görseller [0,1] aralığında normalize edildi.
    Döndürme, yakınlaştırma, kaydırma, yatay çevirme gibi yöntemlerle veri artırma yapıldı.
CNN Modeli:
    3 adet Conv2D + MaxPooling blokları kullanıldı.
    Dropout ve Batch Normalization ile overfitting azaltıldı.
    Çıkış katmanında softmax aktivasyonu ile 75 sınıflı sınıflandırma yapıldı.
Optimizer & Callback’ler:
    Adam optimizasyon algoritması
    EarlyStopping, ReduceLROnPlateau, ModelCheckpoint callback’leri
Değerlendirme Yöntemleri:
    Eğitim/Doğrulama doğruluk ve kayıp grafiklerinin incelenmesi
    Confusion Matrix
    Classification Report (precision, recall, f1-score)
    Grad-CAM (heatmap) ile modelin dikkat ettiği bölgelerin görselleştirilmesi

## Elde Edilen Sonuçlar 

Model, eğitim sonunda ~%79 doğrulama doğruluğu elde etmiştir.
Çoğu sınıfta precision/recall > %80 seviyelerine ulaşılmıştır.
En zorlayıcı sınıflarda bile f1-score %60 üzerindedir.

## Sonuç 

Bu proje ile CNN tabanlı bir derin öğrenme mimarisinin çok sınıflı görüntü sınıflandırma probleminde başarılı şekilde uygulanabileceği gösterilmiştir. Modelin doğruluk oranı artırılmak istenirse:
Daha derin bir CNN mimarisi (ör. ResNet, EfficientNet),
Hiperparametre optimizasyonu (Keras Tuner, Optuna),
Daha fazla veri artırma teknikleri kullanılarak performans geliştirilebilir.
