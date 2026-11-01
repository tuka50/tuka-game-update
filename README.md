# TUKA Game System OTA

ESP32 tabanlı **TUKA Game System** firmware ve OTA güncelleme deposu.

## Güncel Sürüm

**v1.16 — Build 116**

## v1.16 Detaylı Değişiklikler

- LED Tenis **MOD** seçimi artık oyun ayarlarının içinde değil, oyuna girince açılan ana oyun menüsünde.
- Yardım ve Hakkında ekranları dört dile bağlandı; dil değişince bu bölümler de anında değişiyor.
- Yardım/Hakkında yazıları büyütüldü ve kelimeler ortadan bölünmeden otomatik satır sarılıyor.
- Genel Ayarlara **Maks LED Parlaklık** eklendi. Varsayılan **%50**.
- Pil **%15 altına** düşerse global LED parlaklığı en fazla **%20** oluyor.
- Pil tekrar **%50 veya üzerine** çıkınca kullanıcının ayarladığı parlaklık geri geliyor.
- LED sayısı düşürüldüğünde ana menü LED animasyonu da orantılı olarak daralıyor.
- DFPlayer için non-blocking ses seviyesi koruması eklendi; oyun sırasında beklenmedik ses yükselmesi azaltıldı.
- TFT backlight şu an doğrudan 3.3 V bağlı olduğu için yazılımdan gerçek ekran parlaklık kontrolü eklenmedi.

## OTA Adresleri

Manifest:
```text
https://raw.githubusercontent.com/tuka50/tuka-game-update/main/version.json
```

Firmware:
```text
https://raw.githubusercontent.com/tuka50/tuka-game-update/main/firmware/TUKA_GameSystem_latest.bin
```

## İlk Sürümden İtibaren Tüm Geliştirme Geçmişi

```text
TUKA GAME SYSTEM - KUMULATIF CHANGELOG
=======================================
Bu dosya v1.10'dan itibaren her kod ZIP paketinde bulunacak ve sonraki
surumlerde guncellenecek.

PROTOTIP DONEMI - ESP8266 / NODEMCU (v1.0 ONCESI)
--------------------------------------------------
- 144 WS2812B LED serit uzerinde LED Tenis prototipi.
- Iki oyuncu butonu, TFT, encoder ve DFPlayer Mini.
- Kirmizi/sari/yesil vurus bolgeleri.
- CPU modu, top izi, parlaklik, top rengi, skor ve ses ayarlari.
- TFT flicker, encoder yonu ve buton gecikmeleri ilk prototipte ele alindi.
- Oyun icinde topa vuruldugunda beklemeden karsi yone donme ana hedef oldu.

v1.0 - ESP32 YENIDEN YAZIM
---------------------------
- ESP32-WROOM-32 DevKit mimarisine gecildi.
- P1 GPIO32, P2 GPIO33 interrupt.
- WS2812 GPIO13.
- Encoder GPIO21/22, SW GPIO27.
- ILI9341 + XPT2046 ortak SPI.
- DFPlayer UART2 GPIO16/17.
- Delay'siz oyun dongusu ve yavaslatilmis TFT HUD.
- Ilk oyunlar: LED Tenis, Refleks Duellosu, Halat Cekme, Hedef Vurusu,
  Hafiza 2-Tus.
- Preferences tabanli ayar saklama.

v1.1
----
- Gercek Arduino IDE'de derlenen ilk ESP32 surumu.
- Encoder yonu duzeltildi.
- Menu secim cercevesi izi duzeltildi.
- Touch ayar/ses menu kontrolu ve sayfa ok tuslari.
- Splash yaklasik 4 saniye.
- Oyun sonu encoder kisa bas = tekrar.
- Oyun lobby'leri.
- HIZ YARISI ve REFLEKS AVI eklendi.
- Buton debounce ~7 ms.
- LED Tenis vurus toleransi iyilestirildi.

v1.2
----
- Ana menu touch oklar.
- Mavi/kirmizi taraf degistirme (side swap).
- Oyuncu isimleri ve ikonlari.
- Touch isim klavyesi: ABC/abc/123/sembol/ikon.
- HUD'da oyuncu isimleri.

v1.3
----
- Wi-Fi ayarlari ve ag tarama.
- SSID secimi ve Wi-Fi parola klavyesi.
- Wi-Fi bilgileri ayri Preferences alaninda.
- OTA guncelleme.
- Hostname: TUKA-GAME.
- Ilk OTA sifresi: tukaota.
- TFT OTA ilerleme ekrani.
- DFPlayer profil/komut zamanlamasi iyilestirmeleri.

v1.4
----
- Wi-Fi parolasi varsayilan gorunur + goster/gizle.
- Klavyeye geri/sil/space/baglan.
- Touch 5 ornek ortalama.
- Oyun adlari Turkce varsayilan.
- Dil: TR / EN / AZ / RU.
- Ekran yonu 0/180.
- Touch kalibrasyon/rotasyon uyumu.

v1.5
----
- Gercek Kiril Rusca.
- Hafif 5x7 Kiril fontu.
- Rusca oyuncu adi klavyesi.
- UTF-8 icin oyuncu isim buffer'i genisletildi.
- Her reboot/reset/acilista dil TURKCE'ye doner.

v1.5.1
------
- Arduino auto-prototype kaynakli ButtonEvents/GameId/HitZone/SfxCategory
  derleme hatalari duzeltildi.
- Enum/struct ve Kiril katmani yeniden siralandi.
- Acik fonksiyon prototype'lari eklendi.

v1.6
----
- Wi-Fi encoder kontrolu ana loop'a alindi.
- Wi-Fi GERI tuslari.
- Ses menusu SIRADAKI SARKI.
- Temalar: Modern, Windows 98, Atari, Neon Cyber, Midnight,
  Retro Amber, Matrix, Arcade 80s.
- Tema vurgu/baslik renkleri.
- GPIO35 ile 1S 18650 pil yuzdesi.
- Ust baslikta pil ikonu/yuzdesi.

v1.7
----
- Oyun sonu HAZIR/tekrar sistemi.
- Oyun alanina dokun = direkt tekrar.
- 2P: kendi butonuna cift bas = HAZIR; iki taraf hazir = tekrar.
- 1P modlarda tek oyuncunun cift basisi yeterli.
- Dusuk pil gongu /mp3/0041.
- %9-%2 her yeni yuzdede bir gong; %1 altinda 10 saniyede bir.
- HIZ YARISI / HALAT CEKME kontrollu oyun sesleri.
- REFLEKS AVI cue sesi.

v1.8
----
- XPT2046 T_IRQ -> GPIO34.
- Hayalet touch icin IRQ + Z basinc + coklu ornek + koordinat dagilim filtresi.
- Press stable / release guard.
- Touch kalibrasyonu IRQ kontrollu.
- OTA sifresi tuka5050.

v1.9
----
- Suno kadin spiker anonslari 0042-0092 entegre edildi.
- Oyuna BASLAT deyince oyun hemen hareket etmez; oyuncularin hazir olmasini bekler.
- 2P: P1/P2 birer kez basar; 1P/CPU: yalniz insan oyuncu.
- Baslangic anonsu bittikten sonra oyun fiziksel olarak baslar.
- DFPlayer anons state-machine + timeout fallback.
- Pil 15-ornek median + IIR filtre.
- Buton basisi sonrasi ADC olcumu kisa sure ertelendi.
- Uygun alt menulerde sag-alt GERI.

v1.9.1
------
- AnnouncerAction ve AudioProfile enum sirasi nedeniyle olusan derleme hatasi
  duzeltildi.
- Tipler fonksiyonlardan onceye alindi ve acik prototype eklendi.

v1.10
-----
- Oyundan cikinca menu muzigi bazen susuyordu:
  DFPlayer/bayrak durumu sifirlanip menu muzigi zorla yeniden baslatiliyor.
- Pil sarjdayken 100% / -- dalgalanmasi:
  4.20-6.10V yuksek ADC sicrama araligi dolu pil olarak clamp edilir;
  tek gecersiz olcum son gecerli yuzdeyi silmez.
- Tum menu encoder navigasyonu wrap yerine clamp:
  en altta asagi cevirince en altta, en ustte yukari cevirince en ustte.
- Ses Ayarlari:
  SPIKER ANONSU ACIK/KAPALI
  SPIKER SESI 0-30
- Spiker volume normal efekt volume'dan ayrildi.
- Wi-Fi encoder hareketinde tam ekran redraw yerine satir bazli redraw;
  flicker/titreme azaltildi.
- Hedef Vurusu hareketli top/cursor aktif takim renginde.
- Side Swap renk hesabina dahil.
- Settings version 7; v1.9.1 ayarlari SettingsV6 migrasyonuyla korunur.

SES DOSYA HARITASI
------------------
/mp3/0001-0040 : 4 stil x 10 oyun/SFX
/mp3/0041      : dusuk pil gongu
/mp3/0042-0092 : Suno spiker anonslari
/05/001...     : menu/background muzikleri

DONANIM OZETI
-------------
P1 GPIO32
P2 GPIO33
WS2812 DATA GPIO13
Encoder A/B GPIO21/22
Encoder SW GPIO27
TFT SCK/MOSI/MISO GPIO18/23/19
TFT CS/DC GPIO25/26
Touch CS GPIO14
Touch IRQ GPIO34
DFPlayer RX/TX GPIO16/17
Pil ADC GPIO35, 100K/100K bolucu


v1.11
-----
- Cloudflare Pages tabanli "Buluttan OTA" guncelleme sistemi eklendi.
- Wi-Fi Ayarlari menusune GUNCELLEME KONTROL eklendi.
- Cihaz version.json manifestini HTTPS ile kontrol eder.
- Manifest build numarasi cihazdaki CLOUD_LOCAL_BUILD degerinden buyukse
  yeni surum olarak gosterilir.
- Guncelleme ekrani mevcut/yeni surum ve kisa degisiklik notlarini gosterir.
- Firmware .bin dosyasi cihaz tarafindan indirilip aktif olmayan OTA
  uygulama bolumune yazilir.
- Firmware SHA-256 hash'i cihazda hesaplanir ve manifestteki degerle
  karsilastirilir; uyusmazsa Update.end yapilmaz.
- Firmware boyutu OTA alanindan buyukse indirme/yazma reddedilir.
- Indirme/yazma yuzdesi TFT'de progress bar ile gosterilir.
- Basarili guncellemeden sonra ESP32 otomatik yeniden baslar.
- Mevcut Arduino IDE Wi-Fi OTA sistemi de korunur.
- Cloudflare adresi bir kez CLOUD_MANIFEST_URL sabitine yazilir.
- Windows icin HAZIRLA_GUNCELLEME.ps1 araci eklendi:
  .bin'i kopyalar, SHA-256 ve boyutu hesaplar, version.json hazirlar.

v1.11 - GITHUB RAW GECISI
-------------------------
- Turkiye'de pages.dev erisim problemi nedeniyle Cloudflare Pages terk edildi.
- OTA manifest adresi GitHub Raw olarak sabitlendi:
  https://raw.githubusercontent.com/tuka50/tuka-game-update/main/version.json
- Firmware URL:
  https://raw.githubusercontent.com/tuka50/tuka-game-update/main/firmware/TUKA_GameSystem_latest.bin
- GitHub'a ozel Windows firmware/manifest hazirlama araci eklendi.


v1.11.1
-------
- Arduino derleme hatasi duzeltildi:
  mbedtls_sha256_starts_ret / update_ret / finish_ret kullanimi,
  kullanicinin kurulu ESP32-mbedTLS surumunde mevcut olmadigi icin
  mbedtls_sha256_starts / update / finish fonksiyonlarina gecildi.
- GitHub Raw bulut OTA mantigi degismedi.
- CLOUD_LOCAL_BUILD bilincli olarak 111 birakildi; GitHub'daki mevcut
  build 111 manifesti bu surumde de "SISTEM GUNCEL" olarak gorunur.
- SHA-256 firmware dogrulamasi korunur.


v1.12
-----
- Bulut guncelleme menusu Wi-Fi Ayarlari'ndan kaldirildi ve ANA MENU'nun
  en altina GUNCELLEMELER olarak tasindi.
- CLOUD_LOCAL_BUILD 112 oldu. v1.11.1 build111 cihaz, GitHub'a v1.12
  manifest+firmware yuklendiginde bu surumu buluttan gorebilir.
- XPT2046 touch, T_IRQ FALLING interrupt/isrWake durumuna bagimli olmaktan
  cikarildi. T_IRQ kablosu fiziksel olarak kalabilir; okuma normal polling.
- Touch'ta Z basinc, coklu ornek, raw dagilim, stable press ve release guard
  filtreleri korunarak hayalet tiklamaya karsi koruma devam eder.
- Encoder EC11 okuma tam quadrature/detent sistemine gecirildi.
  Deger fiziksel tik tamamlanmadan degismez.
- Yeni oyun baslangicinda DFPlayer hard audio reset + efekt profili.
- Ana menuye donuste DFPlayer/anons/gong/muzik durumlari hard reset edilip
  menu muzigi fiziksel olarak yeniden baslatilir.
- GUNCELLEMELER ekraninda encoder secimi tam ekran redraw yapmaz;
  sadece iki buton yeniden cizilir, flicker azaltildi.
- TEMALAR ekraninda normal encoder gezintisi tam ekran redraw yapmaz;
  eski/yeni satir yeniden cizilir.
- Tema ayarlarina YAZI RENGI eklendi.
- Tema renk listesine SIYAH/BLACK eklendi.
- Alt menu satirlarinda label yazilari uygun alan varsa textSize 2;
  uzun satirlarda otomatik textSize 1 fallback.
- Ayarlar, Ses, Wi-Fi, Oyun Lobby ve Tema satirlari daha okunur hale geldi.
- Ek font dosyalari eklenmedi. Program flash kullanimi zaten yuksek oldugu icin
  font tipi secimi kaynak/flash tasarrufu amaciyla bu surumde bilerek atlandi.
- Settings version 8; v1.11.1 SettingsV7 ayarlari korunarak migrate edilir.


v1.13
-----
- Touch kalibrasyonu ayri tukatouch Preferences namespace'ine tasindi.
- Touch kaydi magic/version/checksum ile korunur; Settings migration ve fabrika ayari silmez.
- DFPlayer RX checksum ve track-finished parca numarasi eslestirmesi eklendi.
- Eski SFX finish mesajinin yeni anonsu kapatmasi engellendi; anons oncesi RX flush.
- DFPlayer profil komut araliklari artirildi; asiri yakin hit SFX 70ms ile sinirlandi.
- LED Tenis ISR timestamp + onceki gorunen LED icin 90ms temporal grace.
- Tennis hit grace 2 LED -> 3 LED.
- Alt menu sag deger yazilari alan uygunsa textSize 2.
- 0042-0092 spiker sesleri icin temiz referans TXT/CSV eklendi.


v1.14
-----
- Ana menu sadeleştirildi: 7 oyun + grafik disli ikonlu AYARLAR klasoru.
- Wi-Fi, Ses, Genel Ayarlar, Temalar, Istatistik ve Guncellemeler AYARLAR klasorune tasindi.
- Ana menudeki her oyunun basina oyuna uygun hafif vektor ikon eklendi.
- Her oyun lobby'sine OYUN AYARLARI klasoru eklendi.
- Oyuna ozel skor, sure, hiz, zorluk ve oyun parametreleri kendi oyun klasorune tasindi.
- LED Tenis oyun ayarlarina mod, CPU zorlugu, hedef skor, baslangic/min hiz,
  kirmizi/sari/yesil bolgeler, bolge/top parlakligi, top rengi ve golge boyu toplandi.
- Genel Ayarlar artik donanim/arayuz odakli: toplam LED, dil, ekran yonu,
  touch kalibrasyonu ve fabrika ayari.
- Kalici ayar sistemi tukacfg Preferences namespace'i ile eklendi.
- Oyun, ses, tema, oyuncu profili, ekran ve LED ayarlari key-value olarak ayri
  NVS alaninda saklanir; Settings struct degisse bile firmware guncellemesinde geri yuklenir.
- LED Tenis 1P CPU / 2P modu da kalici ayara dahil edildi.
- Wi-Fi mevcut ayri Preferences alaninda, touch kalibrasyonu tukatouch alaninda kalir.
- Guncelleme ekranindaki CIHAZI KAPATMAYIN uyarisi buyutuldu ve kirmizi yapildi.
- Acilis ekraninda GAME SYSTEMS yazisi en uste ve buyuk olarak tasindi.
- Acilis progress bar her adimda komple silinmek yerine yalniz yeni dolan bolumu
  ciziyor; yukleme barindaki yanip-sonme/flicker azaltildi.
- Oyun HUD'unda oyuncu isimleri alan uygunsa daha buyuk gosteriliyor.
- Oyun bitisinde kazanan oyuncunun isim + puan paneli animasyonlu hale getirildi.
- Kazanan panelinin altinda P1 KAZANDI / P2 KAZANDI; CPU modunda CPU KAZANDI yazilir.
- AYARLAR alt ekranlarindaki GERI tuslari AYARLAR klasorune doner.
- OYUN AYARLARI geri tusu ilgili oyunun lobby ekranina doner.
- GitHub README artik guncel surum detayinin yaninda ilk prototipten itibaren
  tum kumulatif surum gecmisini de tasir.
- GitHub OTA hazirlama BAT/PowerShell artik kullanicidan yol istemez.
  Masaustunde TUKA_GameSystem_ESP32_v1_14_GITHUB.ino.bin dosyasini otomatik arar.


v1.15
-----
- ISTATISTIK AYARLAR klasorunden cikarildi ve ana menuye tasindi.
- Ana menu sirasi: 7 oyun, AYARLAR, ISTATISTIK, YARDIM, HAKKINDA.
- Ana menu oyun ve sistem ikonlari sabit renkli hale getirildi.
- ISTATISTIK ekrani 3 sayfali, daha buyuk ve anlasilir kart tasarimina gecirildi.
- LED Tenis 1P CPU modunda artik insan tarafi sabit P1 degil.
  Baslangic hazir ekraninda ilk hangi fiziksel P1/P2 butonuna basilirsa
  o taraf oyuncu olur, karsi taraf CPU olur.
- CPU sol/P1 veya sag/P2 fiziksel tarafta oynayabilecek sekilde tenis CPU
  hedef, vurus, skor ve istatistik mantigi genellestirildi.
- Oyun lobby satirlari P1 ISIM ve P2 ISIM olarak sadelestirildi.
  Isim klavyesindeki ICON sekmesi korunur; ikon hala bagimsiz secilebilir.
- Ana menuye detayli YARDIM klasoru eklendi:
  7 oyunun her biri, kontroller, menu kullanimi, Wi-Fi/guncelleme ve ses/pil.
- Ana menuye HAKKINDA ekrani eklendi.
  Tunahan Kara iletisim/sosyal medya bilgileri ve Adil Ozkan tesekkur bolumu eklendi.
- YARDIM ve HAKKINDA menulerine grafik ikonlar eklendi.


v1.16
-----
- LED Tenis MOD secimi OYUN AYARLARI'ndan cikarildi; LED Tenis oyun lobby'sine tasindi.
- LED Tenis oyun ayarlari 11 satira dusuruldu; CPU zorlugu ve diger teknik ayarlar kendi klasorunde kalir.
- YARDIM ve HAKKINDA metinleri Turkce, Ingilizce, Azerbaycan ve Rusca secili dile gore degisir.
- YARDIM ve HAKKINDA yazi boyutu textSize 2 yapildi.
- Uzun metinler kelime ortasindan bolunmeden otomatik satir sarma ile gosterilir.
- YARDIM ve HAKKINDA ekranlarinda encoder/touch ile satir kaydirma eklendi.
- Genel Ayarlar'a MAKS LED PARLAKLIK eklendi; varsayilan %50.
- Maksimum LED parlakligi tukacfg kalici ayar alaninda saklanir ve firmware guncellemesinde korunur.
- Pil %15 altina indiginde global LED parlakligi en fazla %20'ye sinirlanir.
- Dusuk pil LED modu, pil %50 veya ustune cikana kadar aktif kalir; sonra kullanici parlaklik ayari geri gelir.
- Ana menu LED animasyon genisligi aktif LED sayisiyla orantili hale getirildi.
  LED sayisi azalinca animasyon fiziksel olarak daralir.
- DFPlayer icin non-blocking volume guard eklendi.
  Her track/anons/muzik baslangicindan sonra hedef profil ses seviyesi yeniden uygulanir;
  oyun sirasinda sesin kendiliginden yukselmesi hedeflenerek bastirildi.
- Mevcut TFT backlight LED pini dogrudan 3.3V'a bagli oldugu icin sahte bir ekran parlaklik ayari eklenmedi.
  Yazilimla ekran parlakligi ayari icin backlight'in PWM kontrollu transistor/MOSFET uzerinden surulmesi gerekir.

```
