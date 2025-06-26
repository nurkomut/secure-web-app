# RWR 

Radar İkaz Alıcısı (RWR), bir platformun (genellikle askeri uçak, gemi veya kara aracı) etrafındaki elektromanyetik spektrumu pasif olarak dinleyerek tehdit oluşturan radar sinyallerini tespit eden, analiz eden, sınıflandıran ve mürettebatı uyaran kritik bir Elektronik Destek (ED) sistemidir. Temel amacı, platformun "hayatta kalma kabiliyetini" (survivability) artırmaktır.

---


## 📡 Teknik Mimarisi ve Bileşenleri

Modern bir Radar İkaz Alıcısı (RWR) sistemi, birbiriyle entegre çalışan birkaç ana bileşenden oluşur:

### 1. Anten Grubu (Antenna Array)
- Platformun etrafına stratejik olarak yerleştirilmiş çoklu antenlerden oluşur.
- Genellikle **360° kapsama alanı** sağlamak için tasarlanmıştır.
- Gelen radar sinyalinin **geliş açısını (*Angle of Arrival - AoA*)** yüksek hassasiyetle tespit etmeyi sağlar.
- Farklı frekans bantlarını (örneğin C, D, E, I, J bantları) kapsayacak şekilde geniş bantlı veya çoklu dar bantlı olabilirler.

### 2. RF Front-End ve Sinyal Alıcısı (Receiver)
- Antenlerden gelen analog sinyalleri güçlendirir, filtreler ve sayısallaştırır.
- **Süperheterodin (*Superheterodyne*)** veya daha modern **doğrudan dijital dönüşüm (*Direct Digital Conversion*)** mimarilerini kullanabilir.
- Sistemin **hassasiyetini (*sensitivity*)** ve **dinamik aralığını (*dynamic range*)** belirleyen en kritik bileşenlerden biridir.

### 3. Sinyal İşlemci ve İşlem Birimi (Signal Processor)
- RWR sisteminin beynidir. Sayısallaştırılmış sinyal verilerini (IQ data) işleyerek radar darbelerinin temel parametrelerini çıkarır.
- Bu işlem, **Darbe Tanımlama Kelimeleri (*Pulse Descriptor Words - PDW*)** oluşturur. Her PDW, tek bir radar darbesinin şu temel özelliklerini içerir:
  - **Geliş Açısı (AoA)**
  - **Darbe Genişliği (Pulse Width - PW)**
  - **Darbe Frekansı (Pulse Repetition Frequency - PRF)** veya **Darbe Tekrarlama Aralığı (Pulse Repetition Interval - PRI)**
  - **Radyo Frekansı (RF)**
  - **Taramalı Desen Analizi (Scan Pattern Analysis)**

### 4. Tehdit Kütüphanesi Veritabanı (Threat Library Database)
- Önceden bilinen tüm dost ve düşman radar sistemlerinin (kara tabanlı, hava tabanlı, füze arayıcı başlıkları) sinyal parametrelerini içeren bir veritabanıdır.
- Bu kütüphane, sistemin başarısı için hayati öneme sahiptir ve sürekli güncel tutulması gerekir.

### 5. Ekran ve Kontrol Ünitesi
- İşlemcinin tanımladığı tehditleri, mürettebata anlaşılır bir formatta sunan arayüzdür.
- Genellikle tehdidin yönünü, türünü ve durumunu (örneğin; arama, takip, fırlatma) gösteren bir **azimut ekranı** kullanılır.

---



## 🔎 Hangi Radarları Tespit Eder?

| Radar Türü                 | Açıklama                                          | Tehdit Seviyesi |
|---------------------------|---------------------------------------------------|-----------------|
| **Arama Radarları**       | Geniş alan tarar, henüz hedef seçmemiştir         | 🟢 Düşük        |
| **Takip Radarları**       | Hedefi izlemeye başlar                            | 🟡 Orta         |
| **Atış Kontrol Radarları**| Füze yönlendirme yapar, hedefe kilitlenmiştir     | 🔴 Yüksek       |
| **Aktif Füze Radarları**  | Füzenin kendisinden yayılan radar sinyalleridir   | 🔴🔴 Çok Yüksek  |

---

## 📊 Hangi Parametreler Analiz Edilir?

- **Frekans (GHz):** Radarın taşıyıcı sinyal frekansı  
- **Puls Genişliği (µs):** Radar sinyalinin süresi  
- **Puls Tekrar Frekansı (PRF):** Saniyedeki pulse sayısı  
- **Modülasyon Türü:** CW, FMCW, Pulsed gibi radar dalga biçimleri  
- **Geliş Açısı (Direction of Arrival – DoA):** Sinyalin geldiği yön  
- **Sinyal Gücü (dBm):** Sinyalin algılanan güç düzeyi  

---

---

## 🧪 Örnek Kullanım Komutları



### 🔹 Radar Sinyali Üretimi























