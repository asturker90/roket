# ROKET

**Sürüm: v1.3** — değişiklik geçmişi için [CHANGELOG.md](CHANGELOG.md).

Yerçekimi tabanlı bir uzay yolculuğu oyunu. Tek HTML dosyası, bağımlılık yok, çevrimdışı çalışır.

Bir gezegenden kalkıp bir sonrakine iniyorsun. İndiğin gezegen, bir sonraki sıçramanın kalkış noktası oluyor — bölümler ayrı sahneler değil, tek bir kesintisiz yolculuk.

## Oynanış

- **Yeşil** gezegene yavaş ve dik inmen gerekiyor. Hem hız hem açı tutmalı.
- **Mavi** gezegen geldiğin yer. Üzerinde durabilirsin ama hızlı çarparsan ölürsün.
- **Beyaz** gezegenler yolun üstündeki kütleler. Yörüngeni büker; tuzak da olabilir, hızlanma fırsatı da.
- **Mor** girdap bir kara deliktir. Çekimi bir gezegeninkinden çok daha güçlü — yörüngeni sertçe büker. Olay ufkuna girersen seni yutar ve sıçramayı kaybedersin. Ustalıkla kullanırsan sapan etkisiyle hızlanmanın da yoludur. 4. sıçramadan sonra çıkmaya başlar.
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

## Tersane

Her inişten sonra açılır. Altı yükseltme ve iki sarf malzemesi var.

**Motor** itkiyi %14 artırır ama yakıt tüketimini %20 artırır — net kazanç değil, bir tercih. **Füze rampası** kapasiteyi 2 artırır ve dolu gelir. **Kalkan** her seviyede bir yük ekler; her sıçrama başında dolar ve bir göktaşı ya da kara delik çarpmasını emerek seni kurtarır (kara delikte acil fırlatma yapar). İniş hatalarını engellemez — beceri hâlâ sende.

## Kontroller

| | Kol | Klavye | Dokunmatik |
|---|---|---|---|
| Dönüş | Sol çubuk / D-pad | ← → veya A D | Sol alttaki tuşlar |
| İtki | A veya RT | ↑ veya W veya Boşluk | Sağ alttaki ▲ |
| Füze | B | X | Sağ alttaki FÜZE |
| Onay | A | Enter | Ekrana dokun |
| Yeniden dene | — | R | — |

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
