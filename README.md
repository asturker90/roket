# ROKET

**Sürüm: v2.2** — değişiklik geçmişi için [CHANGELOG.md](CHANGELOG.md).

Yerçekimi tabanlı bir uzay yolculuğu oyunu. Tek HTML dosyası, bağımlılık yok, çevrimdışı çalışır.

Bir gezegenden kalkıp bir sonrakine iniyorsun. İndiğin gezegen, bir sonraki sıçramanın kalkış noktası oluyor — bölümler ayrı sahneler değil, tek bir kesintisiz yolculuk.

## Bölümler ve zorluk eğrisi

Yolculuk 5'erli tematik bloklara ayrılır; her blok yeni bir zorluk ekler, öncekiler azalarak devam eder (katmanlı zorluk). Başlangıç ekranında sıçrama numarasının yanında bloğun adı yazar.

| Bölüm | Tema | Ne çıkar |
|---|---|---|
| **1-5 · TEMELLER** | Temiz iniş öğrenme | Az göktaşı, başka tehlike yok |
| **6-10 · KURTARMA** | İkmal/kurtarma | Sarı kurtarma gezegeni (mahsur mekik) + ara kütleler, daha çok göktaşı |
| **11-15 · USTALIK** | Yoğun seyrüsefer | Ara kütleler sıkça, göktaşı yoğunluğu artar |
| **16-20 · TEHLİKE BÖLGESİ** | Kara delik + UFO | Kara delik çıkar; UFO belirir (16-20: 3 füze) |
| **20+ · SONSUZ** | Her şey birlikte | Tüm tehlikeler; UFO atışı 21-25: 4, 26+: 5'e çıkar |

## Oynanış

- **Yeşil** gezegene yavaş ve dik inmen gerekiyor. Hem hız hem açı tutmalı. Dikkat: "dik" ekrana göre değil, **gezegen yüzeyine** göredir — yani roketin burnu, indiğin noktada gezegenin merkezinden dışa doğru bakmalı. Hedefe yaklaşınca açılan **iniş rehberi** bunu gösterir (aşağıya bak).
- **Mavi** gezegen geldiğin yer. Üzerinde durabilirsin ama hızlı çarparsan ölürsün.
- **Beyaz** gezegenler yolun üstündeki kütleler. Yörüngeni büker; tuzak da olabilir, hızlanma fırsatı da.
- **Mor** girdap bir kara deliktir. Çekimi bir gezegeninkinden çok daha güçlü — yörüngeni sertçe büker. Olay ufkuna (ortadaki koyu disk) girersen seni yutar ve sıçramayı kaybedersin. Etrafındaki **soluk mor halka** tehlike bölgesini önceden gösteren bir uyarı çemberidir. Ustalıkla kullanırsan sapan etkisiyle hızlanmanın da yoludur. 4. sıçramadan sonra çıkmaya başlar ve artık diğer gezegenlerle üst üste binmez.
- **Kapsüller** yol boyunca dağılmış toplanabilir öğelerdir. Yeşil altıgen (**F**) yakıt verir, sarı altıgen (**$**) kredi. Rotandan sapıp risk almana değer katarlar; bazen tam da kara deliğin yanında dururlar.
- Yakıt sınırlı ve sıçramalar arasında taşınıyor. Tersaneden ikmal almak para gerektiriyor.

## Füze

Gezegenin boyutuna göre farklı davranır:

| Gezegen | Sonuç |
|---|---|
| Küçük | Tamamen parçalanır, etrafa kırıntı saçar |
| Orta | İkiye ayrılır, iki parça da hedef sayılır |
| Büyük | Krater açar ve gezegeni iter |

Kırıntılar tehlikeli göktaşına dönüşür — patlatmak bedava değil. Kraterler kalıcıdır ve gezegenle birlikte yolculuğa devam eder.

Hedef gezegeni tamamen yok edersen sıçramayı kaybedersin.

## Kredi ve iniş kalitesi

Başarılı her inişten sabit bir sıçrama ödülü alırsın. Bunun üstüne inişinin kalitesi kadar bonus eklenir:

- **Yumuşak iniş** — hedefe ne kadar yavaş dokunursan (iniş hızı sıfıra ne kadar yakınsa) o kadar çok kredi.
- **Dik iniş** — ne kadar dik (yüzeye ne kadar dik açıyla) inersen o kadar çok kredi.
- **Süre bonusu** — sıçramayı ne kadar hızlı tamamlarsan.

İniş sonrası ekranda her kalemin katkısı ve yüzden ("% yavaş", "% dik") gösterilir. Kusursuz bir iniş, ödülü kabaca iki katına çıkarabilir — yani hem inmek hem de *iyi* inmek para eder.

## İniş rehberi

Hedefe yaklaşınca bir rehber açılır ve düzgün inip inmediğini anında gösterir:

- Yüzeyde bir **kılavuz koni** belirir; ortadaki kesikli çizgi doğru "yukarı" (yüzey normali) yönünü, iki kenar da kabul edilen açı aralığını gösterir. Roketin burnunu bu koninin içine getir.
- Roketin etrafındaki **durum ışığı** renk değiştirir: **kırmızı** = eğiksin, **sarı** = açı düz ama çok hızlısın (yavaşla), **yeşil** = düz ve yeterince yavaş, inebilirsin.
- Sağ üstte **AÇI ✓ DÜZ / ✗ EĞİK** göstergesi aynı bilgiyi metin olarak verir.

## Kurtarma görevi (sarı gezegen)

Bazı sıçramalarda yolun üstünde **sarı bir gezegen** çıkar; üzerinde sana benzeyen, **mahsur kalmış bir uzay mekiği** durur. İstersen uğramadan hedefe gidebilirsin — ama uğrarsan:

1. Sarı gezegene **düzgün in** (yavaş + dik). Sert çarparsan ölürsün; nazikçe ama eğik değersen ölmezsin ama yakıt akmaz.
2. Düzgün konumda beklerken **kendi yakıtından mekiğe akar** — senin yakıtın azalır, onun göstergesi dolar (kendine en az bir miktar yakıt ayrılır, mahsur kalmazsın).
3. Mekik dolunca **kalkıp uzaklaşır** ve kurtulduğu için sana **bol miktarda kredi** bırakır.
4. Sonra oradan kalkıp kendi hedefine devam edersin — yani tek durak değil, çift duraklı bir yolculuk.

Yakıtından verdiğin için bu bir tercih: yolun uzar, yakıtın azalır, ama ödül büyüktür.

## UFO (16. sıçramadan sonra)

16. sıçramadan itibaren (Tehlike Bölgesi) her sıçramada bir **düşman UFO** belirir. Haritaya **rastgele bir kenardan, rastgele bir zamanda** girer — nereden geleceğini bilemezsin. Görünür alanı çaprazlarken sana doğru belli aralıklarla füze atar — **16-20 arası 3, 21-25 arası 4, 26+ için 5** füze (pembe oklar). Füzeye değersen ölürsün; **kalkanın** varsa emer.

Bir uyarı ("UFO YAKLASIYOR") gelir. İki seçeneğin var: **kaç** (füzeleri savuştur), ya da **kendi füzenle UFO'yu vur** — vurursan patlar ve **+150 kredi** verir.

## Tersane

Her inişten sonra açılır. En sık kullanılan **sarf malzemeleri (yakıt/füze/uydu ikmali) listenin en üstündedir**; altında altı kalıcı yükseltme, en altta bir sonraki sıçramaya geçiş vardır. Üst şeritte altın-coin ile kredin ve pil gibi dolan bir **yakıt göstergesi** (sayı + bar) durur.

Yükseltmelerin hepsi 5 seviyeye çıkar; **yakıt tankı ise 10 seviyeye** kadar. **Motor** itkiyi %14 artırır ama yakıt tüketimini %20 artırır — net kazanç değil, bir tercih. **Füze rampası** kapasiteyi 2 artırır ve dolu gelir. **Kalkan** her seviyede bir yük ekler; her sıçrama başında dolar ve bir göktaşı ya da kara delik çarpmasını emerek seni kurtarır (kara delikte acil fırlatma yapar). İniş hatalarını engellemez — beceri hâlâ sende.

## Uydu (kontrol noktası)

Ölünce oyun sıfırlanmaz — o sıçramanın başına dönersin, paran ve yükseltmelerin durur. Uzun sıçramalarda baştan başlamak yorucu olabilir; **uydu** bunun için var.

Tersane'den satın aldığın bir sarf malzemesidir (en fazla 3 taşırsın). Uçarken istediğin anda bir tuşla bırakırsın; o anki durum kaydedilir. **Ölürsen sıçramanın başına değil, uydunun olduğu yerden devam edersin.** Zor bir geçitten hemen önce bırakmak en mantıklısı. Bıraktığın uydu o sıçrama boyunca geçerlidir; başarıyla inince ya da **BAŞTAN** dersen iptal olur.

## Kontroller

| | Kol | Klavye | Dokunmatik |
|---|---|---|---|
| Dönüş | Sol çubuk / D-pad | ← → veya A D | **Sol analog joystick** (sağa/sola çek) |
| İtki | A veya RT | ↑ veya W veya Boşluk | **Sağdaki büyük gaz tuşu** ▲ |
| Füze | B | X | Gazın yanındaki FÜZE |
| Uydu bırak | Y / Üçgen | C | Gazın yanındaki UYDU |
| Onay | A | Enter | Ekrana dokun |
| Yeniden dene | — | R | — |

Dokunmatikte kontroller Mobile Legends tarzıdır: **solda analog joystick** ile dönersin (ne kadar çekersen o kadar hızlı döner), **sağda büyük gaz tuşu** ve etrafında FÜZE / UYDU. Her tuşun altında karşılık gelen klavye tuşu yazılıdır — ▲ (W), FÜZE (X), UYDU (C).

Kol bağlandığında ekran tuşları otomatik kaybolur.

## Çalıştırma

`index.html` dosyasını herhangi bir tarayıcıda aç. Sunucu, kurulum, internet gerekmez.

Telefonda oynayacaksan ekranı yatay çevir.

## Teknik

Saf JavaScript ve Canvas 2D. Çerçeve yok, derleme adımı yok, harici kütüphane yok.

- Yerçekimi ters kare kanunuyla, her gezegenden ayrı ayrı hesaplanıyor
- Kamera roketi, kalkış ve hedef gezegenini çerçeveleyecek şekilde kendini ölçekliyor
- Yıldız alanı dünya koordinatlarında karma fonksiyonuyla üretiliyor, bellekte tutulmuyor
- Bölümler prosedürel üretiliyor; sıçrama sayısı arttıkça mesafe ve göktaşı yoğunluğu artıyor
- Her sıçrama başında dünyanın anlık görüntüsü alınıyor, ölünce oraya dönülüyor

## Lisans

MIT
