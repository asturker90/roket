# Değişiklik Geçmişi

Bu projedeki tüm önemli değişiklikler bu dosyada tutulur.
Sürümleme kabaca [SemVer](https://semver.org/lang/tr/) mantığını izler.

## [v1.4] — 2026-08-07

### Eklendi
- **İniş rehberi**: Hedefe yaklaşınca (yüzeye ~300 m kala) açılan görsel kılavuz.
  Oyuncuların "ekranda dik" ile "yüzeye dik"i karıştırmasından kaynaklanan haksız
  "EĞİK İNİŞ" sorununu giderir.
  - Hedef yüzeyinde kabul açısı konisi + ideal yön (yüzey normali) kesikli çizgisi.
  - Roket etrafında durum ışığı: kırmızı (eğik) → sarı (düz ama hızlı) → yeşil
    (düz + yavaş, inişe hazır).
  - HUD'da "ACI ✓ DUZ / ✗ EGIK" göstergesi.
  - `hedefHizalama()` yardımcı fonksiyonu hem rehberi hem HUD'u besler; iniş kabul
    mantığıyla (açı + hız eşikleri) birebir aynı hesabı kullanır.

## [v1.3] — 2026-08-07

### Eklendi
- **İniş kalitesi kredi bonusu**: Başarılı inişte, sabit sıçrama ödülüne ek olarak
  iki yeni bonus verilir — **yumuşak iniş** (iniş hızı sıfıra ne kadar yakınsa o kadar
  çok) ve **dik iniş** (yüzeye ne kadar dik inersen o kadar çok). İniş sonrası ekranda
  her kalem ve yüzdesi ("% yavaş", "% dik") ayrı ayrı gösterilir. Kusursuz iniş ödülü
  kabaca ikiye katlar. Eski "hız bonusu" (süre) "süre bonusu" olarak yeniden adlandırıldı.

### Düzeltildi / İyileştirildi
- **Sürüm bilgisi görünürlüğü (tekrar)**: Sürüm artık dört yerde birden görünüyor —
  tarayıcı sekme başlığı, tüm modal ekranlar (başlangıç/iniş/patlama köşesi), tersane
  başlığı ve her ekranın alt köşesi. Hepsi tek `SURUM` sabitinden beslenir.

## [v1.2] — 2026-08-07

### Eklendi
- **Kalkan yükseltmesi** (Tersane): Her seviye bir kalkan yükü verir (en fazla 3),
  yükler her sıçrama başında dolar. Bir göktaşı çarpmasını ya da kara delik olay
  ufkunu emerek roketi kurtarır — kara delikte roketi etki alanının dışına
  fırlatır. İniş hatalarını (sert/eğik iniş) engellemez. Roket etrafında mavi
  koruyucu halka ve HUD göstergesiyle gösterilir.

### Düzeltildi / İyileştirildi
- **Sürüm bilgisi görünürlüğü**: Sürüm artık tek kaynaktan (`SURUM` sabiti)
  tarayıcı sekme başlığına ve her ekranın (uçuş + tersane) köşesine yansıyor;
  köşe etiketi daha okunur hale getirildi.

## [v1.1] — 2026-08-07

Yeni oynanış içeriği eklendi.

### Eklendi
- **Kara delik**: Gezegenlerden çok daha güçlü çekim uygulayan yerçekimi
  tuzağı. Olay ufkuna giren roketi (ve füzeleri) yutar, sıçramayı kaybettirir;
  ustaca kullanılırsa sapan etkisiyle hızlanma fırsatı da sunar. 4. sıçramadan
  sonra rota kenarında belirir, dönen yutucu disk ve soluk çekim halkasıyla
  önceden görünür.
- **Toplanabilir kapsüller**: Yol boyunca dağılan yakıt (**F**, +25) ve kredi
  (**$**, +40) öğeleri. Rotadan sapıp risk almayı ödüllendirir.
- Oyun içi sürüm etiketi ve başlangıç ekranı ipuçları.

### Teknik
- Yeni öğeler fizik, anlık kayıt/yükleme, sahne temizleme, çizim ve sıfırlama
  akışlarına entegre edildi.

## [v1.0] — Başlangıç sürümü

İlk yayınlanan hali.

### Mevcut
- Yerçekimi tabanlı iniş/kalkış oynanışı (ters kare kanunu, çoklu gezegen).
- Füze sistemi (gezegen boyutuna göre yıkım/bölünme/krater), göktaşları.
- Tersane: 5 yükseltme + 2 sarf malzemesi, kredi ekonomisi.
- Kol / klavye / dokunmatik desteği, prosedürel bölüm üretimi, kamera.
