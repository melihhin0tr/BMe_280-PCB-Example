# BME_280-PCB-Example

STM32F407VGT6 mikrodenetleyicisi ve BME280 ortam sensörü temel alınarak tasarlanmış, USB Type-C üzerinden programlanabilen açık kaynaklı bir PCB tasarımıdır. Bu kart, ilerleyen sürümlerde motor kontrolü, uçuş sensörleri ve gelişmiş güç dağıtım entegreleri eklenerek tam donanımlı bir uçuş kartına dönüştürülmek üzere geliştirilmektedir.


<img width="862" height="750" alt="image" src="https://github.com/user-attachments/assets/5ab9c743-2e3c-4351-a40d-1194fb99a00d" />
<img width="635" height="555" alt="image" src="https://github.com/user-attachments/assets/dc1018f7-42a0-45ed-ac7f-14e49a9d01e5" />



---

## Özellikler

- **Mikrodenetleyici:** STM32F407VGT6 (ARM Cortex-M4, 168 MHz)
- **Sensör:** BME280 — sıcaklık, nem ve basınç ölçümü (I2C)
- **Güç:** USB Type-C girişi → 5V, LDO regülatör ile 3.3V üretimi
- **Programlama:** USB üzerinden DFU modu veya SWD (Serial Wire Debug)
- **Kristal:** 8 MHz harici osilatör (TAXM8M2QLFCDT1T)
- **Gösterge:** 2 adet kontrol LED'i, 2 adet kullanıcı LED'i
- **Arayüz:** I2C pull-up dirençleri, BOOT0 jumper, harici reset butonu

---

## Dosya Yapısı

```
s__BMe_280-PCB-example__/
│
├── Schematic/          # Şematik dosyaları (.sch / .kicad_sch)
├── Gerber/             # Üretim için Gerber dosyaları
├── BOM/                # Malzeme listesi (Bill of Materials)
└── README.md
```

---

## Nasıl Kullanılır

### 1. Gerber Dosyalarını Üretimye Gönderin
`Gerber/` klasöründeki dosyaları JLCPCB, PCBWay veya benzeri bir PCB üreticisine yükleyin.

### 2. Malzemeleri Temin Edin
`BOM/` klasöründeki malzeme listesini kullanarak bileşenleri temin edin. Bileşenler LCSC ve Mouser üzerinden kolaylıkla bulunabilir.

### 3. Kartı Programlayın
**USB üzerinden (DFU modu):**
1. BOOT0 jumper'ını takın (3.3V'a bağlı konuma getirin)
2. USB Type-C kablosuyla bilgisayara bağlayın
3. STM32CubeProgrammer ile `.hex` veya `.bin` dosyanızı yükleyin
4. BOOT0 jumper'ını çıkarın ve kartı yeniden başlatın

**SWD üzerinden:**
1. ST-Link veya J-Link programlayıcıyı CN1 konnektörüne bağlayın
2. STM32CubeIDE veya OpenOCD üzerinden programlayın

### 4. BME280 Sensörünü Kullanın
Sensör varsayılan olarak **I2C adresi 0x76** ile yapılandırılmıştır. SDO pinini 3.3V'a bağlayarak adresi 0x77 olarak değiştirebilirsiniz.

---

## Geliştirme Planı

Bu kart, tam donanımlı bir uçuş kartına giden yolun ilk adımıdır. Sonraki sürümlerde eklenmesi planlanan özellikler:

- Motor kontrolü (ESC sürücü devresi)
- Uçuş için gerekli ek sensörler (IMU, GPS, barometre)
- Gelişmiş güç dağıtım entegreleri

---

## Lisans

Bu proje açık kaynaklıdır. Ticari olmayan kullanımlar için serbestçe kullanılabilir ve geliştirilebilir.
