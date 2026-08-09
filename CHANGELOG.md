# Değişiklik Geçmişi

Bu projedeki tüm önemli değişiklikler bu dosyada tutulur.
Sürümleme kabaca [SemVer](https://semver.org/lang/tr/) mantığını izler.

## [v2.7] — 2026-08-09

### Eklendi (2 kişilik derinlik)
- **Füze ikmali (2P)**: sarı (para) kapsüller artık +1 füze verir (maks 6); yeşil kapsül yakıt.
  Böylece füzeler bitince friendly fire ölmez, düello sürebilir.
- **Uydu (2P)**: her oyuncuya bölüm başına 1 kontrol noktası. P1 `.` / P2 `Q` ile bırakılır;
  ölünce uydunun olduğu yerden dirilir (o kullanımda tükenir). Bırakılmış uydu haritada
  oyuncu renginde baklava simgesiyle gösterilir.
- Panellerde füze/uydu sayısı ve uydu tuşu da yazıyor.

## [v2.6] — 2026-08-09

### Eklendi
- **GitHub Pages yayını**: `.github/workflows/pages.yml` ile her `main` güncellemesinde
  otomatik dağıtım. Oyun: https://asturker90.github.io/roket/

### Değiştirildi (2 kişilik mod)
- **Bir sonraki bölüme geçmek için ikisinin de hedefe inmesi gerekir.** Önce inen roket
  hedefte park edip (halka + "INDI ▸ BEKLIYOR") diğerini bekler; ikisi de inince birlikte
  ilerlenir. Biri elenmişse tek kalan inince ilerler.
- **Tuşlar ekranda**: her oyuncunun kontrol tuşları kendi panelinde yazıyor
  (P1: ← → ↑ + Sağ Shift · P2: A D W + Sol Shift) — "türk milleti okumaz" :)

## [v2.5] — 2026-08-09

### Eklendi (İki kişilik yerel mod — co-opetition)
- Başlangıç ekranında **2** tuşu ile aynı ekranda 2 kişilik mod. 1P'ye dokunulmadan ayrı bir
  modül olarak eklendi (`guncelleIkili`/`ikiliCiz` ve yardımcıları).
- İki roket (mavi P1, turuncu P2) aynı dünyada; **ortak ilerleme**: ilk hedefe inen bölümü açar,
  ikisi de bir sonraki bölüme geçer. "Gidebildiğin kadar git."
- Her oyuncunun **kendi yakıtı ve 3 kalbi**; kalp bitince elenir, diğeri tek başına devam eder.
  Kalp varken bölüm başından kısa dokunulmazlıkla dirilir. Yakıt kapsüllerden dolar.
- **Friendly fire açık**: füzen rakibi vurursa ona kalp kaybettirir (kendi füzen sana zarar vermez);
  füzeler sahibinin rengiyle çizilir.
- İkisi de elenince **en uzağa giden (son elenen) kazanır**; kazanan ekranı (2 = tekrar, 1 = tek kişilik).
- Kontroller: P1 = oklar + Sağ Shift, P2 = WASD + Sol Shift; 2 gamepad de desteklenir (pad0→P1, pad1→P2).
- HUD: sol/sağ köşede oyuncu panelleri (kalpler + yakıt pili + füze); kamera iki roketi de çerçeveler.
- `roketCiz()` artık renk parametresi alır; `kameraGuncelle` 2P'de iki roketi çerçeveler.
- Not: 2P arcade'dir (tersane/yükseltme yok). Online sürüm ileride planlanıyor.

## [v2.4] — 2026-08-09

### Eklendi (can / kalp sistemi)
- **3 kalple başlanır**; her ölüm bir kalp götürür ve sıçrama tekrarlanır (uydu varsa uydudan).
  **Üç kalp de biterse** oyun tamamen sıfırlanır (1. bölüm, sıfır para/yükseltme).
- Kalp Tersane'den **pahalıya (500)** satın alınabilir; en fazla 5 taşınır.
- HUD sol üstte ve Tersane üst şeridinde **kalp göstergesi** (dolu/boş); CAN satırında da mevcut kalpler.
- Kalp çizimi için `kalpCiz()` yardımcısı eklendi.

### Değiştirildi
- **Uydu artık aynı anda 1 taşınır** (önce 5); fiyatı 130 → **260**. Kullanınca yeniden alınır.
- Ölüm artık doğrudan "en baştan" değil, **kalp bitince** en baştan (v2.3'teki sert kural yumuşatıldı,
  kullanıcı isteğiyle can sistemine bağlandı).
- Ölüm ekranı mesajı kalp durumuna göre güncellendi ("N can kaldi" / "TUM CANLAR BITTI — EN BASTAN").
- Tersane 11 satıra göre yeniden aralıklandı (CAN satırı eklendiği için).

## [v2.3] — 2026-08-09

### Değiştirildi (ölüm artık kalıcı — dikkat & strateji)
- **Ölünce oyun tamamen sıfırlanır**: 1. bölüm, sıfır kredi, sıfır yükseltme.
  Önceden sadece o sıçramanın başına dönülüyordu; artık her hata tüm ilerlemeyi siler.
- **Tek istisna uydu**: Bırakılmış bir uydu (kontrol noktası) varsa ölünce baştan değil,
  uydudan devam edilir (para/yükseltme korunur). Uydu böylece tek "can simidi" oldu.
- Ekrandaki **BAŞTAN** tuşu artık oyunu gerçekten en baştan başlatır (sıçrama tekrarı değil);
  bedavaya sıçrama tekrarlama açığı kapatıldı.
- Ölüm ekranı mesajı güncellendi ("UYDU yok — EN BASTAN basliyorsun" / "Birakilan uyduya donuluyor").
- Toplam deneme (ölüm) sayacı baştan başlarken de korunur.

## [v2.2] — 2026-08-07

### Değiştirildi (Tersane elden geçirildi)
- **Sarf malzemeleri (yakıt/füze/uydu ikmali) listenin en üstüne** taşındı; artık her
  seferinde en alta inmeye gerek yok. Sıra: ikmaller → yükseltmeler → devam.
- **Yükseltme seviyeleri artırıldı**: hepsi 5'e (motor/jiroskop/iniş takımı/füze/kalkan);
  **yakıt tankı 10'a**. Uydu taşıma kapasitesi 5. Seviye göstergesi (pip) 10'a kadar sığar.
- **Yakıt göstergesi pil stiline** çevrildi (yatay dolan bar + uç). Tersanede üst şeritte
  ve YAKIT IKMALI satırında bar + sayı birlikte; HUD'da da pil barı.
- **Kredi yanına altın-coin** simgesi eklendi (tersane şeridi ve HUD).

### İç yapı
- Tersane satırları birleşik model (`dukkanSatirlari()`/`dukkanY()`) ile yeniden yazıldı;
  sıralama ve yerleşim tek yerden yönetiliyor.

## [v2.1] — 2026-08-07

### Değiştirildi (bölüm/zorluk yapısı — Aşama 1)
- Mekanikler 5'erli tematik bloklara oturtuldu, zorluk eğrisi katmanlı yükseliyor:
  - **1-5 Temeller**: sadece iniş + az göktaşı (kurtarma/ara kütle/kara delik yok).
  - **6-10 Kurtarma**: sarı kurtarma gezegeni ve ara kütleler bu bloktan başlar.
  - **11-15 Ustalık**: ara kütle sıklaşır, göktaşı yoğunlaşır.
  - **16-20 Tehlike Bölgesi**: kara delik artık buradan (önce 4'ten) başlar; UFO buradan (önce 20'den) belirir.
  - **20+ Sonsuz**: her şey birlikte.
- **UFO atışı kademeli**: 16-20 → 3, 21-25 → 4, 26+ → 5 füze (`ufoAtisSayisi()`).
- Göktaşı sayısı daha yumuşak eğriyle artar (1-2 → 4-5).
- Başlangıç ekranında sıçrama başlığına blok adı eklendi (ör. "8. SICRAMA — KURTARMA").

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
