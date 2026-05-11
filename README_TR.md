# Raspberry Pi 4G Kamera Yayın Sistemi

🇬🇧 English documentation: [README.md](README.md)

LTE/4G bağlantısı kullanan, Raspberry Pi tabanlı deneysel uzaktan kamera yayın sistemi.

Bu proje; Raspberry Pi, LTE modem, Cloudflare Tunnel ve Flask/OpenCV kullanılarak düşük maliyetli uzaktan görüntü aktarım sisteminin nasıl geliştirilebileceğini araştırmak amacıyla hazırlanmıştır.

---

# Proje Durumu

Prototype / Research Project

Bu proje halen geliştirme ve araştırma aşamasındadır.

Orijinal kaynak kodlarının bir kısmı zaman içerisinde kaybolmuştur. Ancak sistem mimarisi, donanım kurulumu, ağ yapısı ve geliştirme süreci teknik raporlar halinde korunmuştur.

---

# Projenin Amacı

Bu projedeki temel hedefler:

- Raspberry Pi üzerinde 4G/LTE internet bağlantısı kurmak
- Uzak kamera yayını gerçekleştirmek
- Düşük maliyetli uzaktan izleme sistemi oluşturmak
- Static IP gerektirmeyen alternatif haberleşme yöntemleri geliştirmek
- Cloudflare Tunnel kullanarak güvenli bağlantı sağlamak

---

# Kullanılan Donanımlar

- Raspberry Pi 4
- Sixfab 3G/4G LTE Base HAT
- Quectel EC25-EUX mini PCIe LTE modem
- SIM kart
- LTE antenleri
- USB kamera
- SMA bağlantı kabloları

---

# Kullanılan Yazılımlar

- Raspberry Pi OS (32-bit Legacy)
- PPP bağlantı scriptleri
- Motion
- Flask
- OpenCV
- Cloudflare Tunnel

---

# LTE / 4G Bağlantısı

Projede Raspberry Pi’ye mobil internet bağlantısı kazandırmak için Sixfab LTE Base HAT ve Quectel EC25 LTE modem kullanılmıştır.

Kurulum süreci:

1. LTE modülünün HAT üzerine takılması
2. Anten bağlantılarının yapılması
3. HAT’in Raspberry Pi’ye bağlanması
4. PPP scriptlerinin kurulması
5. APN ayarlarının yapılması
6. LTE bağlantısının başlatılması

Bağlantı komutu:

```bash
sudo pon
```

Yapılan testlerde güncel 64-bit sürümlerde uyumsuzluklar gözlemlendiği için Raspberry Pi OS 32-bit legacy sürümü tercih edilmiştir.

---

# Kamera Yayın Sistemi

Projede iki farklı yöntem test edilmiştir.

## 1. Motion Tabanlı Yayın

Motion uygulaması kullanılarak hafif yapılı bir kamera yayın sistemi kurulmuştur.

Yapılan ayarlar:

- daemon modu
- uzaktan erişim
- yayın erişimi
- çözünürlük ayarları
- fps optimizasyonları

---

## 2. Flask + OpenCV Tabanlı Yayın

Alternatif olarak Flask ve OpenCV kullanılarak MJPEG yayın sistemi test edilmiştir.

Sistem çalışma mantığı:

Kamera → Raspberry Pi → Flask Sunucusu → İnternet → Uzak Kullanıcı

Raspberry Pi kameradan aldığı görüntüleri HTTP üzerinden yayınlamaktadır.

---

# Cloudflare Tunnel Kullanımı

Yerel ağdaki Flask yayınını internet üzerinden güvenli şekilde erişilebilir hale getirmek için Cloudflare Tunnel kullanılmıştır.

Avantajları:

- Güvenli bağlantı
- Port açma gereksinimini azaltması
- Static IP gerektirmemesi
- Kolay erişim sağlaması

Kullanılan yönlendirme:

```text
http://localhost:5000
```

---

# Alternatif Sistem Mimarisi

Projede ayrıca static IP sahibi SIM kart gereksinimini azaltmaya yönelik alternatif bir mimari fikri üzerinde düşünülmüştür.

Bu yapıda:

- Kamera cihazı merkezi bir sunucuya bağlanır
- Kumanda veya görüntüleme cihazı aynı sunucuya bağlanır
- Sunucu cihazları eşleştirir
- IP değişimlerinde yeniden bağlantı kurulabilir

Bu yaklaşım sayesinde iki mobil cihazın doğrudan static IP olmadan haberleşebilmesi hedeflenmiştir.

Ara sunucu olarak kullanılabilecek sistemler:

- Raspberry Pi Zero
- Küçük VPS sunucuları
- Cloudflare Tunnel destekli sistemler

Bu mimari halen deneysel durumdadır ve daha fazla geliştirme gerektirmektedir.

---

# Karşılaşılan Problemler

Testler sırasında gözlemlenen bazı problemler:

- FPS düşüşleri
- Görüntü kalitesinde dalgalanmalar
- LTE gecikmesi
- Yeniden bağlantı problemleri
- İnternet kalitesine bağımlılık
- Donanım limitleri

Sistem henüz üretim seviyesinde değildir.

---

# Gelecekte Yapılabilecek Geliştirmeler

- WebRTC desteği
- Daha iyi sıkıştırma yöntemleri
- GPU hızlandırması
- OpenCV tabanlı görüntü işleme
- Otomatik yeniden bağlantı sistemi
- VPN/Tailscale entegrasyonu
- Daha düşük gecikmeli yayın
- Adaptif bitrate sistemi
- Güç optimizasyonları

---

# Klasör Yapısı

```text
project/
│
├── README.md
├── README_TR.md
├── docs/
├── images/
├── architecture/
└── future-work.md
```

---

# Dokümantasyon

`docs/` klasörü içerisinde:

- LTE bağlantı kurulumu
- APN ayarları
- Motion yapılandırması
- Cloudflare Tunnel kurulumu
- Flask/OpenCV kamera yayını
- Ağ mimarisi fikirleri

gibi detaylı teknik raporlar bulunmaktadır.

---

# Not

Bu repository daha çok:

- araştırma
- deneysel geliştirme
- sistem tasarımı
- prototipleme

amacıyla paylaşılmıştır.

Tamamlanmış ticari bir ürün değildir.

---

# Hazırlayan

Hasan Aksoy

2024
