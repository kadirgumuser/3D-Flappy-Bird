# 3D Flappy Bird - Modular Edition 🎮

El hareketleriyle kontrol edilen 3D Flappy Bird oyunu. MediaPipe el takibi ve Three.js ile yapılmıştır.

## ✨ Özellikler

- 🎯 **El Takibi Kontrolü**: MediaPipe ile gerçek zamanlı el hareketi algılama
- 🚀 **Fizik Tabanlı Oyun**: Delta-time bazlı yumuşak fizik
- 💎 **Power-Up Sistemi**: Shield ve Wall Breaker güçlendirmeleri
- 📊 **Max Skor Sistemi**: LocalStorage ile kalıcı en yüksek skor kaydı
- 🎨 **3D Grafik**: Three.js ile profesyonel görsellik
- 📦 **Modüler Yapı**: Bakımı kolay, ayrı dosyalar

## 🗂️ Dosya Yapısı

```
3D-Flappy-Bird-main/
├── index.html              # Ana HTML yapısı
├── css/
│   └── style.css          # Tüm CSS stilleri
├── js/
│   ├── constants.js       # Oyun sabitleri
│   ├── game.js           # Ana oyun mantığı
│   ├── mediapipe-handler.js  # El takibi
│   └── model-loader.js   # 3D model yükleme (opsiyonel)
└── README.md             # Bu dosya
```

## 🎮 Nasıl Oynanır?

1. **Kamera İzni**: Tarayıcıda kamera erişimine izin verin
2. **El Kontrolü**: Elinizi kameranın önüne tutun
   - **Sağa/Sola**: El pozisyonunu sağa/sola hareket ettir
   - **Zıplama**: Başparmak ve işaret parmağını birleştir (pinch/çimdik hareketi)
3. **Amaç**: Borulardan geçerek puan topla, yere veya borulara çarpma!

## 🚀 Kurulum ve Çalıştırma

### Yöntem 1: Live Server (Önerilen)

VS Code Live Server uzantısı kullanın:
```bash
# VS Code'da sağ tık > Open with Live Server
```

### Yöntem 2: Python HTTP Server

```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

Tarayıcıda `http://localhost:8000` adresine gidin.

### Yöntem 3: NPM Serve

```bash
npx serve .
```

## 🔧 Değişiklikler (v2.0)

### ✅ Modüler Yapı
- Tek HTML dosyasından ayrı CSS ve JS dosyalarına geçiş
- Daha kolay bakım ve geliştirme
- Kod organizasyonu iyileştirildi

### 🐛 Bug Düzeltmeleri
- **Power-Up Spawn Bug**: Power-up alındıktan sonra boruların kaybolması sorunu çözüldü
  - `lastPipeZ` artık power-up spawn'ında değiştirilmiyor
  - Ayrı `lastPowerUpZ` değişkeni eklendi
  - Spawn mantığı yeniden yazıldı

### 🎯 Yeni Özellikler
- **Max Skor Sistemi**: 
  - LocalStorage ile kalıcı en yüksek skor kaydı
  - UI'da max skor gösterimi (🏆 ikonu ile)
  - Yeni rekor kırıldığında özel mesaj (🎉 YENİ REKOR!)
  
### 🎨 3D Model Desteği
- GLTFLoader entegrasyonu hazırlandı
- `model-loader.js` modülü eklendi
- Poly.pizza veya diğer kaynaklardan model yükleme altyapısı

## 📝 Özelleştirme

### Oyun Sabitleri

`js/constants.js` dosyasında oyun parametrelerini değiştirebilirsiniz:

```javascript
const GRAVITY = 18.5;          // Yerçekimi hızı
const JUMP_STRENGTH = 12.0;    // Zıplama gücü
const GAME_SPEED = 6.0;        // Oyun hızı
const PIPE_DISTANCE = 50;      // Borular arası mesafe
const SHIELD_DURATION = 5.0;   // Shield süresi (saniye)
```

### 3D Model Yükleme

`js/model-loader.js` dosyasını kullanarak kendi modellerinizi yükleyebilirsiniz:

```javascript
// model-loader.js içinde MODEL_URLS'i değiştirin
const MODEL_URLS = {
    bird: 'https://your-model-url.com/bird.glb',
};
```

Veya oyun başlatırken:

```javascript
// game.js içinde createBird() yerine:
loadBirdModel(scene, bird).then(newBird => {
    bird = newBird;
}).catch(() => {
    // Varsayılan kuş mesh'i kullan
    createBird();
});
```

## 🎯 Power-Up'lar

### 🛡️ Shield (Mavi Küre)
- Süre: 5 saniye
- Etki: Borulara çarpmayı engeller
- Görsel: Kuşun etrafında mavi glow efekti

### 🔨 Wall Breaker (Kırmızı Küp)
- Süre: 4 saniye  
- Etki: Duvarları geçebilirsin
- Görsel: Duvarlar kaybolur, "NO WALLS" mesajı

## 🐛 Bilinen Sorunlar

- MediaPipe bazı mobil tarayıcılarda çalışmayabilir
- HTTPS gerekliliği: Bazı tarayıcılarda kamera erişimi için HTTPS gerekir

## 📊 Teknik Detaylar

- **Three.js**: r128
- **MediaPipe Hands**: Google MediaPipe el takibi modeli
- **Fizik**: Delta-time bazlı frame-independent fizik
- **Depolama**: LocalStorage (max skor için)

## 🤝 Katkıda Bulunma

Katkılarınızı bekliyoruz! PR göndermekten çekinmeyin.

## 📜 Lisans

Bu proje açık kaynaklıdır ve özgürce kullanılabilir.

---

**İyi Oyunlar! 🎮**