# Robotic Toolpath Generation for ABB IRB 1600

## 🚀 Proje Hakkında
Bu proje, dijital görselleri endüstriyel robotlar için işlenebilir yörüngelere dönüştüren uçtan uca bir sistemdir. Geleneksel CNC yöntemlerine alternatif olarak, Python tabanlı algoritmalar ile görsel veriyi robotik bir üretim hattına (milling/drawing) uygun `RAPID` koduna dönüştürmeyi hedefler.

## 🛠 Teknik Mimari
Yazılım mimarisi, görüntü verisinin analiz edilip koordinat sistemine eşlenmesi üzerine kurulmuştur:
- **Görüntü İşleme Pipeline'ı:** OpenCV kütüphanesi kullanılarak; *Grayscale*, *Gaussian Blur* ve *Canny Edge Detection* filtreleri ile kontur analizi yapılmıştır.
- **Koordinat Haritalama:** Piksel tabanlı koordinatlar, robotun çalışma uzayına (kartesyen sistem) `OFFSET` ve `OLCEK` parametreleri ile dönüştürülmüştür.
- **Yörünge Optimizasyonu:** `fine` ve `z1` (zone) parametreleri optimize edilerek; geçişlerdeki sarsıntısız hareket (smooth motion) ve köşelerdeki duruş hassasiyeti dengelenmiştir.
- **Güvenli Geçiş:** `Z_SAFE` (150mm) ve `Z_DRAW` (50mm) parametreleri ile takımın kağıt/yüzey üzerindeki dikey hareketleri (hayalet çizgi engelleme) yönetilmiştir.

## 🤖 Simülasyon ve Test
- **Robot Platformu:** ABB IRB 1600 (8kg / 1.45m).
- **Simülasyon Ortamı:** ABB RobotStudio (RobotWare 6).
- **Çıktı Kapasitesi:** Tek bir görselden 10.655 satırlık hatasız `RAPID` kodu üretim başarımı.

## 📚 Dokümantasyon
Projenin tüm matematiksel modellemesi, kod dizinleri ve simülasyon aşamalarını incelemek için teknik raporu görüntüleyebilirsiniz:

- [📄 Teknik Rapor (PDF)](project_documentation.pdf)

## ⚡ Kullanım ve Entegrasyon
Bu sistem, `saitama.png` gibi görselleri giriş olarak alır ve doğrudan robot kontrolcüsüne aktarılabilecek `.mod` dosyaları oluşturur. Python kütüphaneleri (OpenCV, NumPy) ile hızlı veri işleme sağlar.
