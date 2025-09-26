# Uydu Uplink ve Downlink Simülasyonu 🚀

![Project Banner](https://github.com/yunuseemredogan/screenshots-.gitkeep/blob/main/uplink-downlink.png)

## 📖 Overview
Uydu Uplink ve Downlink Simülasyonu, MATLAB Simulink kullanılarak geliştirilmiş bir iletişim sistemi modelidir. Bu proje, uydu tabanlı uplink (yerden uyduya) ve downlink (uydu'dan yere) süreçlerini simüle eder. Model, QPSK modülasyonu/demodülasyonu, frekans dönüşümleri, güç amplifikatörleri, kanal etkileri (AWGN ve FSPL) ve hata oranı hesaplamalarını kapsar. Özellikle Düşük Dünya Yörüngesi (LEO) uydu sistemleri için tasarlanmıştır.

Bu proje, şu amaçlar için idealdir:
- Uydu iletişim protokollerini test etmek, örneğin IoT tabanlı uzay tabanlı ağlar veya uzaktan algılama sistemleri.
- Gerçek dünya senaryolarını simüle etmek; SNR, RSSI ve BER metriklerini analiz ederek kanal performansı değerlendirmesi.
- Eğitimsel kullanım; modülasyon, kanal kodlama ve RF bileşenlerini öğretmek için pratik bir araç.

Temel fikir, karmaşık uydu iletişim zincirini görselleştirerek ve parametrik olarak analiz etmektir. Model, Bernoulli binary kaynakla başlar, QPSK ile modüle edilir, uplink/downlink zincirleri üzerinden geçer ve demodülasyonla sonuçlanır. Performans metrikleri (örneğin, BER: 0.0015) gerçek zamanlı olarak hesaplanır. Not: Bu bir simülasyon modeli; fiziksel donanım gerektirmez, sadece MATLAB/Simulink lisansı yeterlidir.

## ✨ Key Features
- **Tam Uplink/Downlink Zinciri**: Veri kaynağı'ndan demodülasyona kadar tam simülasyon, frekans dönüşümleri ve amplifikasyon dahil. 🛰️
- **QPSK Modülasyon/Demodülasyon**: Standart QPSK ile 4-bit/s/Hz spektral verimlilik. 🔄
- **Kanal Modelleri**: AWGN gürültüsü ve FSPL (LEO için) ile gerçekçi kanal bozulmaları. 🌌
- **Güç ve Gürültü Bileşenleri**: Yüksek güç amplifikatörü (uplink), düşük gürültü amplifikatörü (downlink) ve bellek polinomu distorsiyonu. 📡
- **Performans Metrikleri**: Gerçek zamanlı BER hesaplama (örneğin, 163/105691 = 0.0015), RSSI (-77.4418 dBm) ve SNR (23.5355 dB) izleme. 📊
- **Parametrik Analiz**: Kolayca SNR, modülasyon veya kanal parametrelerini değiştirerek simülasyonu uyarlama. ⚙️
- **Görsel Tablolar**: Simulink scopes ile sinyal, hata oranı ve metrik görselleştirmeleri. 📈
- **Hata Oranı Hesaplaması**: Tx/Rx karşılaştırması ile bit hata oranı (BER) ve sembol hata oranı (SER) analizi. ❌
- **Modüler Yapı**: Bileşenler (modülatör, kanal, demodülatör) ayrı bloklar halinde, kolay genişletilebilir.

## 📋 Requirements
Bu modeli çalıştırmak için sisteminizin aşağıdaki gereksinimleri karşılaması gerekmektedir. Model, Windows/Linux/macOS'ta çalışır, ancak Simulink lisansı gereklidir.

### Software Dependencies:
- **MATLAB R2018b+**: Simulink toolbox'u ile birlikte. [mathworks.com](https://www.mathworks.com/products/matlab.html) adresinden indirin. 🧮
- **Communications Toolbox**: QPSK mod/demod ve hata oranı blokları için zorunlu. Varsayılan olarak MATLAB ile gelir, yoksa lisanslayın.
- **DSP System Toolbox**: Filtreler ve sinyal işleme için (isteğe bağlı, temel model için yeterli).
- **Diğer**: Standart Simulink blokları (Scope, Bernoulli Generator, AWGN vb.) – ekstra kurulum yok.

### Hardware Requirements:
- **Standart PC**: En az 8 GB RAM ve i5 işlemci önerilir; simülasyon süresi parametrelere göre değişir.
- **Lisans**: Geçerli MATLAB/Simulink lisansı (akademik veya ticari).

**Platform Notes**: Model platform bağımsızdır, ancak Simulink'in yüklü olması şarttır. Linux'ta Wine ile çalıştırılabilir, ancak yerel kurulum önerilir.

## 🛠️ Installation
Projeyi yerel makinenizde çalıştırmak için şu adımları izleyin.

1. **Repository'yi Klonlayın**:
   ```bash
   git clone https://github.com/yunuseemredogan/Satellite-Uplink-Downlink-Modeling.git
   cd Satellite-Uplink-Downlink-Modeling
   ```
   Bu, Simulink model dosyasını (.slx) ve README'yi indirir.

2. **MATLAB'ı Hazırlayın**:
   MATLAB'i açın ve toolbox'ları doğrulayın:
   ```matlab
   ver('Communications Toolbox')
   ```
   Hata verirse, lisansınızı kontrol edin.

3. **Modeli Açın**:
   Klasörde MATLAB terminalinde:
   ```matlab
   open('satellite-uplink-downlink.slx')
   ```
   Model açılacak ve scopes hazır olacak.

4. **İsteğe Bağlı: Ekran Görüntüleri Klasörü Oluşturun**:
   README'ye görseller eklemek için `screenshots` klasörü oluşturun ve model diyagramı gibi yakalamalar yükleyin.

## ▶️ Usage
Modeli çalıştırmak basittir.

1. **Modeli Başlatın**:
   Simulink'te modeli açtıktan sonra "Run" butonuna tıklayın veya Ctrl+R basın.

2. **Parametreleri Yapılandırın**:
   - **SNR Ayarı**: AWGN bloğunda SNR değerini değiştirin (örneğin, 23 dB için).
   - **Veri Uzunluğu**: Bernoulli bloğunda örnek sayısını ayarlayın (örneğin, 105691 bit).
   - **Frekanslar**: Up/Down-converter'larda fc değerlerini güncelleyin.
   - "Run" ile simüle edin.

3. **Sonuçları İzleyin ve Durdurun**:
   - Scopes'ta sinyalleri, RSSI/SNR değerlerini ve BER'i izleyin.
   - Simülasyon bitince "Stop" ile durun; verileri workspace'e kaydedin.

4. **Analiz (Repo'da Dahil Değil)**:
   - MATLAB script'i ile BER vs SNR grafiği çizin: `semilogy(EbNo, ber);`
   - Veya dış araçlar (örneğin, Python ile veri dışa aktarma) kullanın.

**Pro Tip**: İlk test için varsayılan parametreleri kullanın; BER 0.0015 civarında olmalı.

## 🔍 How It Works: The Inner Mechanics
Model, uplink ve downlink zincirlerini paralel olarak simüle eder. İşte detaylı breakdown.

### High-Level Workflow (ASCII Diagram):
```
+-------------------+   Mod   +-------------------+   Channel   +-------------------+
| Bernoulli Binary  | ------> | QPSK Modulator    | ----------> | Up-Converter      |
| (Data Source)     |        | + HPA + Mem Poly  |             | + FSPL(LEO)        |
+-------------------+        +-------------------+             +-------------------+
  |                                         |                          |
  v                                         v                          v
Downlink: LNA + Mem Poly + Down-Conv + AWGN  |  Demod: QPSK + BER Calc (0.0015)
                                             |  
                                     Scopes: RSSI (-77.44), SNR (23.54)
```

1. **Uplink Zinciri**:
   - Veri: Bernoulli binary generator ile rastgele bitler üret (örneğin, 105691 bit).
   - Modülasyon: QPSK ile sembollere dönüştür.
   - RF İşleme: Up-converter (fc), yüksek güç amplifikatörü ve bellek polinomu (distorsiyon).
   - Kanal: FSPL (LEO yol kaybı) uygula.

2. **Downlink Zinciri**:
   - Alım: Düşük gürültü amplifikatörü (LNA) ve bellek polinomu.
   - Frekans Dönüşümü: Down-converter (fc).
   - Gürültü: AWGN kanalı ekle (SNR bazlı).
   - Demodülasyon: QPSK demodülatörü ile bitlere dönüştür.

3. **Metrik Hesaplaması**:
   - BER: Tx/Rx karşılaştırması (163 hata / 105691 bit = 0.0015).
   - RSSI: Alınan sinyal gücü (-77.4418 dBm).
   - SNR: Hesaplanan sinyal-gürültü oranı (23.5355 dB).
   - Scopes: Sinyal in/out, ERC (hata oranı) görselleştirmesi.

Model, sabit parametrelerle çalışır (örneğin, QPSK, 30 dB SNR), ancak blok parametrelerini değiştirerek uyarlanabilir. Simülasyon süresi ~10-30 sn'dir.

## 🧱 Code Structure
Model, tek bir .slx dosyasında modüler bloklarla yapılandırılmıştır.

- **Giriş Bloğu**: Bernoulli Binary Generator (veri kaynağı).
- **Modülasyon Alt Sistemi**: QPSK Modulator ve scopes.
- **Uplink Alt Sistemi**: Up-Conv, HPA, Mem Poly, FSPL.
- **Downlink Alt Sistemi**: LNA, Mem Poly, Down-Conv, AWGN.
- **Demodülasyon Alt Sistemi**: QPSK Demod, BER Calculation.
- **Çıkış Bloğu**: Scopes (Signal, RSSI, SNR, ERC).
- **Konfigürasyon**: Model Properties'te solver ayarları (ode45, fixed-step).

Toplam blok sayısı: ~25, netlik için etiketli (daha fazla ekleyin eğer 필요).

## ⚠️ Troubleshooting
- **Simulink Açılmıyor**: Lisansı kontrol edin; `license checkout Simulink` çalıştırın.
- **Blok Hataları**: Toolbox'ları doğrulayın; eksikse yükleyin.
- **Yavaş Simülasyon**: Örnek sayısını azaltın veya solver'ı değiştirin.
- **BER Yüksek**: SNR'yi artırın veya kanal parametrelerini ayarlayın.
- **Scopes Boş**: Run süresini uzatın (Configuration Parameters > Stop Time).
- **Çökmeler**: MATLAB'i güncelleyin veya debugger kullanın.

## 📉 Limitations
- Simülasyon tabanlı; gerçek RF donanımı yok.
- Sabit modülasyon (sadece QPSK); genişletmek için ekleyin.
- LEO'ya odaklanmış; GEO için FSPL uyarlayın.
- Kodlama yok (ERC bloğu temel); ileri hata düzeltme ekleyin.
- Platform bağımlı (MATLAB lisansı).

## 🤝 Contributing
Repo'yu fork'layın, değişiklik yapın ve PR gönderin! Öneriler: Diğer modülasyonlar (16QAM), Doppler etkisi, veya Python entegrasyonu.

## 📜 License
MIT License - Kullanın, değiştirin ve paylaşın. [LICENSE](LICENSE) dosyasını görün.

*2025'te ❤️ ile yapılmış. Sorular için issue açın!*
