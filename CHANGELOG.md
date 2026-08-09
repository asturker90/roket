# Değişiklik Geçmişi

Bu projedeki tüm önemli değişiklikler bu dosyada tutulur.
Sürümleme kabaca [SemVer](https://semver.org/lang/tr/) mantığını izler.

## [v2.0] — 2026-08-07

### Değiştirildi (dokunmatik kontrol elden geçirildi)
- **Sol analog joystick**: Ayrı sol/sağ butonları kaldırıldı; yerine Mobile Legends
  tarzı çember-içi-topuz joystick geldi. Yatay çekme miktarı dönüşü **analog** kontrol
  eder (ne kadar çekersen o kadar hızlı döner). Klavye ve kol dönüşü de aynı birleşik
  `girdi.don` değerine bağlandı.
- **Sağ küme (MOBA düzeni)**: Gaz (itki) tuşu büyütüldü ve sağ alta alındı; FÜZE ve
  UYDU tuşları onun etrafına yerleştirildi.
- Çoklu dokunma korunur: bir parmakla dönerken diğeriyle gaz/füze verilebilir.

## [v1.9] — 2026-08-07

### Eklendi
- **Düşman UFO (20. sıçrama sonrası)**: 20. sıçramayı geçince her sıçramada bir UFO
  belirir. Haritaya rastgele bir kenardan, rastgele bir zamanda girer (nereden
  geleceği belli olmaz), görünür alanı çaprazlar ve rokete doğru **toplam 3 füze**
  atar (pembe, ölümcül; kalkan emer). "UFO YAKLASIYOR" uyarısı gelir.
  - Oyuncu kendi füzesiyle UFO'yu vurabilir → patlar, +150 kredi.
  - İlk atış UFO görünür alana girene kadar geciktirilir; yörünge oyun alanından
    geçecek şekilde ayarlandı (füzeler ekran dışından sürpriz gelmez).
  - Düşman UFO ve füzeleri anlık görüntüye dahil değil; ölünce/dirilince UFO
    yeniden gelir.

## [v1.8] — 2026-08-07

### Düzeltildi
- **Nesne çakışması önlendi**: Yol üstündeki büyük cisimler (beyaz ara kütle,
  kurtarma gezegeni, kara delik) artık birbirinin ve mevcut gezegenlerin üstüne
  binmiyor. Yeni `yerAra()` yardımcısı her cisim için, mevcut gezegen/kara
  deliklerden yeterince uzak bir konum bulana kadar (en çok 12 deneme) yer arar;
  bulamazsa o cisim o sıçramada atlanır. Kara delik en son ve en geniş boşlukla
  yerleştirilir. 600 sıçramalık testte 0 çakışma.

## [v1.7] — 2026-08-07

### Eklendi
- **Kurtarma görevi (çift duraklı yolculuk)**: Bazı sıçramalarda yolun üstünde sarı
  bir gezegen çıkar; üzerinde mahsur kalmış, oyuncuya benzeyen bir uzay mekiği durur.
  - Gezegene düzgün inince (yavaş + dik) oyuncunun yakıtı mekiğe akar; oyuncu en az
    15 birim rezerv tutar (mahsur kalmaz). Sert çarpma ölüm, nazik-ama-eğik temas
    güvenli ama yakıt akmaz.
  - Mekik dolunca kalkıp uzaklaşır (itki izli animasyon) ve büyük bir kredi ödülü
    bırakır (320 + etap·45). Ortada "MEKIK KURTARILDI" bildirimi görünür.
  - Opsiyonel bir durak: uğramadan da hedefe gidilebilir. İniş rehberi ve "AÇI"
    göstergesi artık yaklaşılan en yakın inilebilir gezegene (hedef ya da kurtarma)
    göre çalışır.
  - Sarı gezegen + yakıt göstergeli mekik çizimi; anlık görüntü sistemine mekik ve
    `para` alanı eklendi (ölünce ödül tekrar tekrar alınamaz; uydu bırakırsan kilitlenir).

## [v1.6] — 2026-08-07

### İyileştirildi
- **Dokunmatik butonlarda klavye tuşu**: Her ekran tuşunun altına karşılık gelen
  klavye tuşu yazıldı — ◀ (A), ▶ (D), ▲ (W), FÜZE (X), UYDU (C). Oyuncular yönerge
  okumadan hangi tuşun ne işe yaradığını görebiliyor. Etiket biraz yukarı alınıp
  altına küçük, soluk tuş ipucu eklendi.

## [v1.5] — 2026-08-07

### Eklendi
- **Uydu (kontrol noktası)**: Tersane'den alınan sarf malzemesi (en fazla 3).
  Uçarken bir tuşla (C / ekran tuşu / kol Y) bırakılır; o anki dünya + roket durumu
  kaydedilir. Ölünce oyuncu sıçramanın başına değil, uydunun bırakıldığı yerden
  (durgun, kontrol hemen elde) devam eder. Uydu o sıçrama boyunca geçerlidir;
  başarılı iniş veya "BAŞTAN" ile iptal olur.
  - Bırakılan uydu dünyada mavi bir işaretle görünür; HUD "UYDU n · NOKTA AKTIF"
    gösterir; ekran tuşu ve kol (Y/üçgen) desteği eklendi.
  - Anlık görüntü sistemi ortak `anlikGoruntu()` / `anlikGeriYukle()` fonksiyonlarına
    çıkarıldı; hem etap-başı hem uydu diriliş bu ortak yolu kullanır.

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
