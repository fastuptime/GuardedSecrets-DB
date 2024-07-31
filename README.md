# 🔒 CryptoJS ile Şifreleme ve Deşifreleme

Bu proje, `crypto-js` kütüphanesini kullanarak veritabanında güvenli bir şekilde şifreleme ve deşifreleme işlemlerini gerçekleştirmenizi sağlar. Özellikle, gizli anahtarlar ve hassas bilgilerin veritabanında düz metin olarak saklanmasının yaratabileceği güvenlik sorunlarını önlemeye yardımcı olur.

## 🎯 Amaç

Gizli anahtarlar ve hassas veriler genellikle veritabanlarında saklanır. Ancak, bu bilgilerin düz metin olarak saklanması güvenlik riskleri oluşturur:

- **Yetkisiz Erişim:** Düz metin veriler, yetkisiz kişilerin veritabanına erişmesi durumunda doğrudan okunabilir ve kullanılabilir.
- **Veri Sızıntısı:** Eğer veritabanınızın güvenliği sağlanamazsa, gizli anahtarlar ve diğer hassas bilgiler sızabilir ve büyük güvenlik açıklarına yol açabilir.

Bu proje, bu tür riskleri en aza indirmek için verilerinizi şifreleyerek ve deşifre ederek saklamanızı sağlar.

## 🚀 Başlarken

### 📦 Gereksinimler

- Node.js
- `crypto-js` kütüphanesi

### 🔧 Kurulum

1. Öncelikle, projenize `crypto-js` kütüphanesini ekleyin:

   ```bash
   npm install crypto-js
   ```

2. Aşağıdaki örnek kodu kullanarak şifreleme ve deşifreleme işlemlerini gerçekleştirin:

### 💻 Kod Örneği

```javascript
const CryptoJS = require('crypto-js');

// Şifreleme fonksiyonu
function encrypt(text, secretKey) {
    return CryptoJS.AES.encrypt(text, secretKey).toString();
}

// Deşifreleme fonksiyonu
function decrypt(encryptedText, secretKey) {
    const bytes = CryptoJS.AES.decrypt(encryptedText, secretKey);
    return bytes.toString(CryptoJS.enc.Utf8);
}

// Örnek kullanım
const secretKey = 'my-secret-key-123'; // Bu anahtar 256 bit olmalıdır
const secretData = 'Bu gizli bir veridir';

// Veriyi şifreleme
const encryptedData = encrypt(secretData, secretKey);
console.log('Şifrelenmiş Veri:', encryptedData);

// Veri Tabanına Kayıt Edin

// Şifrelenmiş veriyi çözme
const decryptedData = decrypt(encryptedData, secretKey);
console.log('Çözülmüş Veri:', decryptedData);
```

### 🔑 Anahtar Yönetimi

- **Anahtar Uzunluğu:** Güçlü ve yeterli uzunlukta bir anahtar kullanın. AES şifrelemesi için genellikle 128-bit, 192-bit veya 256-bit anahtarlar önerilir.
- **Güvenli Depolama:** Şifreleme anahtarlarını ve şifreli verileri güvenli bir şekilde saklamaya dikkat edin. Anahtarların ve şifreli verilerin yetkisiz kişiler tarafından erişilmesini engellemek önemlidir.
