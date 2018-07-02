# CryptoJS-AND-Csharp
CryptoJS 前端加解密与Csharp后端加解密

#### CryptoJS 的 ASE与DES 加解密
1. DES加密
```javascript
       function encryptByDES(message, key) {
               var keyHex = CryptoJS.enc.Utf8.parse(key);
               var encrypted = CryptoJS.DES.encrypt(message, keyHex, {
                           mode: CryptoJS.mode.ECB,
                           padding: CryptoJS.pad.Pkcs7
                });
                return encrypted.toString();
        }
```
2. AES加密
```javascript
        function encryptByAES(message, key) {
            var keyHex = CryptoJS.enc.Utf8.parse(key);
            var encrypted = CryptoJS.AES.encrypt(message, keyHex, {
                mode: CryptoJS.mode.ECB,
                padding: CryptoJS.pad.Pkcs7
            });
            return encrypted.toString();
        }
```
