# GELİŞMİŞ DISCORD OWO FARM

Lütfen hataları bildirin ve duyurularımızı takip etmeye devam edin!

> Kullanım sırasında herhangi bir sorun/hata/hatayla karşılaşırsanız lütfen bildirin, sorumluluk bilinciyle yardımcı olmak için elimden geleni yapacağım.


## Gereksinim
__Node.js Sürümü:__ v22.11.0 ve üzeri

Dizüstü ve masaüstü bilgisayarlar için: Windows 10/11 veya üzeri, Linux ve MacOS

Android için: [Termux](https://f-droid.org/en/packages/com.termux/) uygulamasını indirin ve yükleyin

iOS için: Henüz desteklenmiyor (destekleyen bir yöntem biliyorsanız lütfen bize bildirin)

__Not:__ Google Play Store'daki Termux desteklenmiyor.


## Kurulum

### Node.js kurulumu

##### Windows/Linux/MacOS:

Lütfen cihazlarınıza [Node.js LTS](https://nodejs.org/en/download) yüklediğinizden emin olun.

![Imgur](https://i.imgur.com/qjaEpiu.png)

##### Telefon içinTermux:

Termux'ta aşağıdaki komutları çalıştırın:
```bash
apt update
apt upgrade
apt install -y nodejs-lts git
```

### Araç kurulumu

[Modülü indirip çıkarın](https://github.com/eren-mlg/wbotss/archive/refs/heads/main.zip) veya [Git](https://git-scm.com/downloads) kullanarak klonlayın/çekin:
```bash
git clone https://github.com/eren-mlg/wbotss.git
```

[Klasörün içindeki terminali açın](https://www.groovypost.com/howto/open-command-window-terminal-window-specific-folder-windows-mac-linux/) gidin ve aracı indirdiğiniz
```bash
cd wbotss
```
ve aşağıdaki komutu çalıştırın:

```bash
npm install
```
Bu, aracın doğru çalışması için gereken tüm gereksinimleri (kütüphaneleri) yükleyecektir.

### Token alma

Yöntem 1: Hesap Tokeninizi almak için [bu talimatı](https://pcstrike.com/how-to-get-discord-token/) izleyin.

Yöntem 2: __Ctrl + Shift + I__ tuşlarına basın ve aşağıdaki Kodu yapıştırın.

```javascript
window.webpackChunkdiscord_app.push([
[Sembol()],
{},
req => {
if (!req.c) return;
for (let m of Object.values(req.c)) {
try {
if (!m.exports || m.exports === window) continue;
if (m.exports?.getToken) return copy(m.exports.getToken());
for (let ex in m.exports) {
if (m.exports?.[ex]?.getToken && m.exports[ex][Sembol.toStringTag] !== 'IntlMessagesProxy') return copy(m.exports[ex].getToken());
}
} catch {}
}
},
]);

window.webpackChunkdiscord_app.pop();
console.log('%cÇalıştı!', 'font-size: 50px');
console.log(`%cToken'ınız artık panoda!`, 'font-size: 16px');
```

## Kullanım

### Normal Kullanım (Etkileşimli Komut Satırı Kullanıcı Arayüzleri)

Aracı çalıştırmak için lütfen aşağıdaki komutu kullanın (araç klasörünün içinde)

```bash
npm start
```

Aşağıdaki uyarıyı görürseniz

![Imgur](https://i.imgur.com/jJudxy5.png)

Tebrikler, `Gelişmiş Discord OwO Farm ` başarıyla yüklediniz.

"Y" yazın, enter tuşuna basın ve keyfini çıkarın! (Araç yalnızca Enter tuşuna basarsanız kapanacaktır)

#### Hesap Girişi

Giriş yapmak için 2 yöntemi destekliyoruz: **token** ve **QR Kodu** ile

![Imgur](https://i.imgur.com/r0BpWjh.png)

##### Token ile:

__- 1. Adım: Discord hesap tokeninizi alın__

[Discord tokeninizi nasıl alırsınız](#Token-alma) bölümüne bakın

__- 2. Adım: Tokeninizi terminale yapıştırın, bu biraz zaman alacaktır__

![Imgur](https://i.imgur.com/6kCDt6r.png)

##### QR Kodu ile
Discord mobil cihazınızın ekranındaki QR Kodunu tarayın ve sabırla bekleyin...

![Imgur](https://i.imgur.com/zqeR2q6.png)

### Komut Satırı Kullanımı (Komut Satırı) Arayüz)

```bash
node . [komut] [seçenekler]
npm start [komut] [seçenekler]
npm start -- -- [seçenekler]

# Örnek
npm start generate config-sample.json # generate config-sample.json
npm start import config.json # Otomatik içe aktarmayı tetikle ve verilen config.json ile çalıştır
```

#### CLI Seçenekleri:
```sh
-s, --skip-check-update # Güncelleme kontrolünü atla
-u, --update # Sormadan güncelle
-v, --verbose # Hata ayıklamayı etkinleştir
```

## Yapılandırma Kılavuzu

### Temel Kurulum
```js
{
"username": "", // İsteğe bağlı: Görünen ad (yoksayılabilir)
"token": "your.discord.token", // Gerekli: Discord hesap token'ınız
"guildID": "123456789", // İsteğe bağlı: Sunucu Kimliği Botun çalıştığı yer
"channelID": [ // Gerekli: Farming için kanal kimlikleri dizisi (en az bir tane)
"channel-id-1",
"channel-id-2",
"channel-id-3"
]
}
```

### Bildirim Ayarları
```js
{
"wayNotify": [ // Bildirim yöntemlerini seçin: "webhook", "dms", "call", "music", "popup"
"webhook",
"dms"
],
"webhookURL": "https://discord.com/api/webhooks/...", // Webhook kullanılıyorsa gereklidir
"adminID": "your-user-id", // Dms/call bildirimleri kullanılıyorsa gereklidir
"musicPath": "./path/to/music.mp3", // Müzik bildirimleri kullanılıyorsa gereklidir
"prefix": "!" // Bot komutları için komut öneki
}
```

### Captcha Çözümü
```js
{
"captchaAPI": "2captcha", // Seçenekler: "2captcha", "yescaptcha"
"apiKey": "api-anahtarınız" // CaptchaAPI ayarlanmışsa gereklidir
}
```

### Huntbot Yapılandırması
```js
{
"autoHuntbot": true, // Huntbot otomasyonunu etkinleştir/devre dışı bırak
"autoTrait": "verimlilik", // Seçenekler: "verimlilik", "süre", "maliyet", "kazanç", "deneyim", "radar"
"useAdotfAPI": true // Gelişmiş Discord OwO Araç Çiftliği API'sini Kullan
}
```

### Otomatik Komutlar
```js
{
"autoPray": [ // Otomatik dua/lanetler komutları
"dua et",
"dua et kullanıcı-kimliği-buraya", // Belirli kullanıcıları hedefleyebilirsiniz
"lanet et kullanıcı-kimliği-buraya"
],
"autoQuote": [ // Otomatik alıntı komutları
"owo", // Owo/uwu'yu rastgele gönder
"quote" // Rastgele alıntılar gönder
],
"autoRPP": [ // Diğer otomatik komutlar
"run",
"pup",
"piku"
]
}
```

### Gem Yönetimi
```js
{
"autoGem": 1, // 0: devre dışı, 1: efsanevi→yaygın yükselt, -1: ortak→masal düşür
"gemTier": [ // Kullanılacak mücevher katmanları (autoGem etkinken)
"yaygın",
"sıra dışı",
"nadir",
"epik",
"efsanevi"
// Mevcut: "efsanevi", "efsanevi"
],
"useSpecialGem": false // Özel mücevherleri kullan
}
```

### Ganimet Kutusu ve Günlük İşlemler
```js
{
"autoLootbox": true, // Normal ganimet kutularını otomatik kullan
"autoFabledLootbox": false, // Efsanevi ganimet kutularını otomatik kullan
"autoDaily": true, // Günlük ödülleri otomatik al
"autoCookie": true, // Çerezleri otomatik kullan
"autoClover": true, // Yoncaları otomatik kullan
"autoSell": true // Nakit bittiğinde hayvanları otomatik sat
}
```

### Sistem Ayarları
```js
{
"autoSleep": true, // Rastgele duraklama aralıkları oluştur (5-20 dakika)
"autoReload": true, // Yapılandırmayı günlük olarak otomatik olarak yeniden yükle
"autoResume": true, // Çözdükten sonra otomatik olarak devam et captcha
"showRPC": true // Discord Zengin Varlığını Göster
}
```
### Tam Örnek
```js
{
"token": "your.discord.token.here",
"guildID": "123456789012345678",
"channelID": ["987654321098765432"],
"wayNotify": ["webhook"],
"webhookURL": "https://discord.com/api/webhooks/your/webhook/url",
"adminID": "your-user-id-here",
"prefix": "!",
"captchaAPI": "2captcha",
"apiKey": "your-2captcha-api-key",
"autoHuntbot": true,
"autoTrait": "verimlilik",
"useAdotfAPI": doğru,
"autoPray": ["dua et"],
"autoGem": 1,
"gemTier": ["yaygın", "nadir", "destansı", "efsanevi"],
"useSpecialGem": yanlış,
"autoLootbox": doğru,
"autoFabledLootbox": yanlış,
"autoQuote": ["owo"],
"autoRPP": ["koş", "yavru"],
"autoDaily": doğru,
"autoCookie": doğru,
"autoClover": doğru,
"autoSell": doğru,
"autoSleep": doğru,
"autoReload": doğru,
"autoResume": doğru,
"showRPC": doğru
}
```

### Yapılandırma İpuçları
- **Gerekli alanlar**: `token`, `channelID` (en az bir tane)
- **Koşullu Gereksinimler**:
- "webhook" bildirimleri kullanılıyorsa `webhookURL` gereklidir
- "dms" veya "call" bildirimleri kullanılıyorsa `adminID` gereklidir
- "music" bildirimleri kullanılıyorsa `musicPath` gereklidir
- `captchaAPI` ayarlanmışsa `apiKey` gereklidir
- **Örnek yapılandırma oluştur**: Şablon oluşturmak için `npm start generate config-sample.json` kullanın

## Sıkça Sorulan Sorular (SSS)

### Genel Sorular

**S: Bu aracı kullanmak güvenli mi?**

C:Ancak, herhangi bir otomasyon aracını kullanmak risk taşır. Her zaman kendi takdirinize göre kullanın ve Discord Hizmet Şartları'na uyun.

**S: Bunu kullandığım için yasaklanır mıyım?**

C: Otomasyon araçlarını kullanırken her zaman bir risk vardır. Rastgele gecikmeler ve captcha çözme gibi güvenlik özellikleri ekledik, ancak hesabınızın güvenliğini garanti edemeyiz.

**S: Bu mobil cihazlarda çalışıyor mu?**

C: Evet! Termux aracılığıyla Android'de kullanabilirsiniz. iOS desteği henüz mevcut değil.

### Kurulum ve Yükleme

**S: "npm tanınmıyor" hatası alıyorum**

C: Önce Node.js'yi yüklemeniz gerekiyor. [nodejs.org](https://nodejs.org/) adresinden indirin ve terminalinizi yeniden başlattığınızdan emin olun.

**S: Araç kurulumdan sonra başlamıyor**

C: Önce `npm install` komutunu çalıştırdığınızdan emin olun. Sorunlar devam ederse şunu deneyin:
```bash
npm cache clean --force
npm install
```

**S: Discord token'ımı nasıl alabilirim?**

C: Yukarıdaki [Token Al](#get-token) bölümümüze bakın. Token'ınızı asla kimseyle paylaşmayın!

**S: Yapılandırma dosyamı nereye koymalıyım?**

C: Araçla aynı klasörde `config.json` adlı bir dosya oluşturun veya `npm st` komutunu kullanın.
