# RWR 

Radar İkaz Alıcısı (RWR), bir platformun (genellikle askeri uçak, gemi veya kara aracı) etrafındaki elektromanyetik spektrumu pasif olarak dinleyerek tehdit oluşturan radar sinyallerini tespit eden, analiz eden, sınıflandıran ve mürettebatı uyaran kritik bir Elektronik Destek (ED) sistemidir. Temel amacı, platformun "hayatta kalma kabiliyetini" (survivability) artırmaktır.

---

## 🔐   Elektronik Harp (EW) ile Entegrasyon

RWR sistemleri, diğer elektronik harp (EW) bileşenleriyle entegre çalışarak tehditlere karşı çok katmanlı savunma sağlar:

- **ECM (Electronic Countermeasure):**  
  RWR tespiti sonrası jamming, deception gibi karşı tedbirler uygulanır.

- **ESM (Electronic Support Measures):**  
  RWR verileri üzerinden geniş spektrum analizleri gerçekleştirilir.

- **DIRCM, Chaff / Flare Sistemleri:**  
  Füze tehdidi algılandığında otomatik savunma sistemleri devreye girer.

> 📌 **Örnek:** Füze radar sinyali algılandığında, sistem otomatik olarak flare fırlatımı yapar.


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

 
## 🛰️   Algılama ve Yön Tayini

RWR sistemlerinin temel yeteneklerinden biri, radar sinyallerinin geldiği yönü belirlemektir:

- **Amplitude Comparison:** Farklı yönlerdeki anten sinyal seviyeleri karşılaştırılır.
- **Time Difference of Arrival (TDOA):** Sinyalin antenlere ulaşım süresindeki farklar analiz edilir.
- **Interferometry:** Faz farklarına dayalı yüksek hassasiyetli yön tayini sağlar.

> 📌 **Örnek:** RWR, gelen radar sinyalinin saat 3 yönünden geldiğini belirleyebilir.

---

## 📊  Parametre Çözümleme (Pulse Analysis)

RWR sistemleri, sinyalleri aşağıdaki parametreler üzerinden analiz eder:

- **Frekans (RF)**
- **Pulse Genişliği (PW)**
- **Pulse Tekrarlama Frekansı (PRF)**
- **Pulse Amplitüdü**
- **Modülasyon tipi (e.g. FMCW, pulsed)**

> 📌 **Not:** Bu parametreler, sinyalin hangi radar türüne ait olduğunu belirlemek için kullanılır.

---

## 🗂️  Tehdit Kütüphanesi (Emitter Library)

Tehdit kütüphanesi, önceden bilinen radar sistemlerinin karakteristik verilerini içerir:

- **Veri Yapısı:** PDW (Pulse Descriptor Word) temelli veri kayıtları
- **Kapsam:** Arama radarları, takip radarları, atış kontrol radarları, füze radarları vb.
- **Güncelleme:** Yeni tehdit türleri keşfedildikçe kütüphane güncellenir.

> 📌 **Örnek:** Bir radar sinyali PRF ve PW değerleriyle birlikte tehdit kütüphanesindeki S-300 sistemiyle eşleşebilir.

---

## 🛠️  Çalışma Modları (Operating Modes)

RWR sistemleri, farklı tehdit ortamlarında farklı modlarda çalışarak etkin tehdit algılama ve yanıt imkânı sunar:

- **Wideband Scan Mode:**  
  Geniş frekans aralığında hızlı tarama yapılır, ancak hassasiyet düşüktür.

- **Narrowband Tracking Mode:**  
  Belirli bir frekans bölgesine odaklanılarak yüksek hassasiyetli izleme sağlanır.

- **Priority Mode:**  
  Sadece yüksek tehdit seviyesine sahip radarlar izlenir ve kullanıcıya bildirilir.

> 📌 **Örnek:** Savaş jeti düşman SAM (Surface-to-Air Missile) bölgesine girdiğinde, RWR yalnızca atış kontrol radarlarına öncelik vererek pilotun dikkatini kritik tehditlere yoğunlaştırır.

---

## 🧠  Tehdit Tanıma ve Sınıflandırma Algoritmaları

Modern RWR sistemleri, radar sinyallerini doğru şekilde tanıyabilmek için gelişmiş analiz teknikleri kullanır:

- **Emitter Deinterleaving:**  
  Farklı radar kaynaklarından gelen sinyallerin ayrıştırılması.

- **Pattern Matching:**  
  PDW (Pulse Descriptor Word) verilerinin tehdit kütüphanesiyle karşılaştırılarak eşleştirilmesi.

- **Makine Öğrenimi (ML) Tabanlı Tanıma:**  
  Yeni, bilinmeyen veya hibrit radar türlerinin öğrenilmesi ve sınıflandırılması.

> 📌 **Örnek:** Bilinmeyen PRF varyasyonlarına sahip bir sinyal, eğitilmiş bir ML modeli aracılığıyla mevcut tehdit türleriyle benzerliği tespit edilerek sınıflandırılabilir.

---

## 🧪  Test ve Simülasyon Ortamları

RWR sistemleri sahaya çıkmadan önce kapsamlı test süreçlerinden geçirilir:

- **RF Sinyal Simülatörleri:**  
  Gerçek radar sinyallerine benzer yapay sinyaller üretir.

- **Hardware-in-the-Loop (HIL):**  
  Gerçek donanım ile simülasyon ortamı entegre edilerek canlı testler yapılır.

- **CARLA / RWR-Sim gibi simülatörler:**  
  Eğitim, analiz ve doğrulama için kullanılır.

> 📌 **Örnek:** Sistem, aynı anda 3 farklı yönden gelen radar sinyallerini tanıyıp doğru sınıflandırabiliyor mu?

---



## ⚙️  Donanım Mimarisi Varyasyonları

RWR sistemlerinin donanım mimarisi, kullanıldıkları platformlara göre farklılık gösterir:

| Platform | Donanım Özellikleri             | Açıklama                                 |
|----------|----------------------------------|-------------------------------------------|
| Uçak     | Düşük hacimli, yüksek işlem gücü | Gövde içine gömülü, modüler yapı          |
| Gemi     | Yüksek güçlü, çok antenli         | Geniş kapsama alanı                       |
| İHA      | Düşük ağırlık ve düşük güç tüketimi | Mini-RWR versiyonları kullanılır         |

---

## 📄  Dokümantasyon ve Standartlar

RWR sistemlerinin geliştirme ve entegrasyon süreçlerinde aşağıdaki standartlar sıkça kullanılır:

- **MIL-STD-461:** Elektromanyetik girişim ve uyumluluk gereklilikleri
- **STANAG 4622:** NATO elektronik harp veri formatı standardı
- **RTCA DO-160:** Havacılık elektroniği çevresel koşul test standartları

> 📌 **Not:** Bu standartlar, sistemin farklı operasyonel ve elektromanyetik ortamlarda güvenilir şekilde çalışmasını garanti altına alır.

























