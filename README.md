# CryptoJS-AND-Csharp
CryptoJS 前端加解密与Csharp后端加解密

#### CryptoJS 的 ASE与DES 加解密
1. DES加密(ECB模式)
```javascript
  function encryptByDES(message, key) {
    var keyHex = CryptoJS.enc.Utf8.parse(key);
    var encrypted = CryptoJS.DES.encrypt(message, keyHex, {
      mode: CryptoJS.mode.ECB,
      padding: CryptoJS.pad.Pkcs7
    });
    return encrypted.toString(CryptoJS.enc.Utf8);
}
```
1. DES解密(ECB模式)
```javascript
  function decryptByDES(message,key) {
    var keyHex = CryptoJS.enc.Utf8.parse(key);
    var decrypted = CryptoJS.DES.decrypt(message, keyHex, {
      mode: CryptoJS.mode.ECB,
      padding: CryptoJS.pad.Pkcs7
    });
    return decrypted.toString(CryptoJS.enc.Utf8);
}
```
3. AES加密(ECB模式)
```javascript
  function encryptByAES(message, key) {
    var keyHex = CryptoJS.enc.Utf8.parse(key);
    var encrypted = CryptoJS.AES.encrypt(message, keyHex, {
      mode: CryptoJS.mode.ECB,
      padding: CryptoJS.pad.Pkcs7
    });
      return encrypted.toString(CryptoJS.enc.Utf8);
}
```
4. AES解密(ECB模式)
```javascript
  function decryptByAES(message, key) {
    var keyHex = CryptoJS.enc.Utf8.parse(key);
    var encrypted = CryptoJS.AES.decrypt(message, keyHex, {
      mode: CryptoJS.mode.ECB,
      padding: CryptoJS.pad.Pkcs7
    });
      return encrypted.toString(CryptoJS.enc.Utf8);
}
```
