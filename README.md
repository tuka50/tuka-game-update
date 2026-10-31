# TUKA Game System OTA

ESP32 tabanlı **TUKA Game System** için OTA firmware güncelleme deposu.

## Güncel Sürüm

**v1.12 — Build 112**

## v1.12 Değişiklikleri

- Güncellemeler ekranı Wi-Fi menüsünden kaldırılıp ana menünün en altına taşındı.
- Dokunmatik ekran okuma sistemi yeniden düzenlendi.
- XPT2046 artık T_IRQ interrupt durumuna bağımlı olmadan polling ile okunuyor.
- Dokunmatik için basınç, çoklu örnek, koordinat dağılımı ve parazit filtreleri korunuyor.
- Encoder okuma sistemi tam fiziksel detent/tık mantığına geçirildi.
- Encoder artık fiziksel tık tamamlanmadan değer değiştirmiyor.
- Oyun başlarken DFPlayer ses durumu sıfırlanıp efekt profili yeniden kuruluyor.
- Ana menüye dönüldüğünde DFPlayer, anons, gong ve müzik durumları sıfırlanıyor.
- Oyun sonrası seslerin kaybolması ve ana menü müziğinin başlamaması sorunları için ses durumu iyileştirildi.
- Güncelleme ekranında encoder hareketi sırasında tam ekran yeniden çizim kaldırıldı.
- Tema ekranında encoder hareketi sırasında ekran titremesi azaltıldı.
- Tema ayarlarına **Yazı Rengi** seçeneği eklendi.
- Tema renk seçeneklerine **Siyah** eklendi.
- Alt menülerde yazılar, alan uygunsa daha büyük gösterilecek şekilde düzenlendi.
- Ayarlar, Ses, Wi-Fi, Oyun Lobby ve Tema ekranlarının okunabilirliği artırıldı.
- Font tipi seçimi, flash alanını gereksiz tüketmemek için bu sürümde eklenmedi.
- Ayar yapısı **Settings Version 8** olarak güncellendi.
- Önceki ayarlar otomatik migration ile korunuyor.

## OTA Dosyaları

Bu repoda OTA sistemi için kullanılan temel dosyalar:

- `version.json` — ESP32'nin kontrol ettiği güncelleme manifesti
- `firmware/TUKA_GameSystem_latest.bin` — güncel application firmware dosyası

## OTA Manifest Adresi

```text
https://raw.githubusercontent.com/tuka50/tuka-game-update/main/version.json
```

## Firmware Adresi

```text
https://raw.githubusercontent.com/tuka50/tuka-game-update/main/firmware/TUKA_GameSystem_latest.bin
```

## Güncelleme Sistemi

ESP32 cihazı `version.json` dosyasını kontrol eder.

Manifestteki `build` değeri cihazdaki yerel build numarasından büyükse yeni sürüm bulunduğu kabul edilir.

Firmware indirilirken:

- dosya boyutu kontrol edilir,
- SHA-256 hesaplanır,
- manifestteki SHA-256 ile karşılaştırılır,
- doğrulama başarılıysa OTA bölümüne yazılır,
- güncelleme tamamlanınca cihaz yeniden başlatılır.

## Mevcut Bulut OTA Bilgisi

- **Firmware:** ESP32 v1.12
- **Build:** 112
- **OTA Repo:** `tuka50/tuka-game-update`
- **Arduino OTA Hostname:** `TUKA-GAME`
- **Arduino OTA Password:** `tuka5050`

---

TUKA Game System geliştirme ve OTA dağıtım deposu.
