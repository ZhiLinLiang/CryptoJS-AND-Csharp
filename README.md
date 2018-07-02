# CryptoJS-AND-Csharp
CryptoJS 前端加解密与Csharp后端加解密

#### CryptoJS 的 ASE与DES 加解密
1. DES加密(ECB模式)
```javascript
/* javascript */
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
/* javascript */
  function decryptByDES(message,key) {
    var keyHex = CryptoJS.enc.Utf8.parse(key);
    var decrypted = CryptoJS.DES.decrypt(message, keyHex, {
      mode: CryptoJS.mode.ECB,
      padding: CryptoJS.pad.Pkcs7
    });
    return decrypted.toString(CryptoJS.enc.Utf8);
}
```
```C#
/* C# */
public static string CryptoJS_DES_Decrypt(string decryptString, string decryptKey)
{
      if (string.IsNullOrEmpty(decryptString))
        return decryptString;
      var DES = new DESCryptoServiceProvider();
      DES.Key = Encoding.UTF8.GetBytes(decryptKey);
      DES.Mode = CipherMode.ECB;
      DES.Padding = System.Security.Cryptography.PaddingMode.PKCS7;
      ICryptoTransform DESDecrypt = DES.CreateDecryptor();
      byte[] Buffer = Convert.FromBase64String(decryptString);
      return Encoding.UTF8.GetString(DESDecrypt.TransformFinalBlock(Buffer, 0, Buffer.Length));
}
```
3. AES加密(ECB模式)
```javascript
/* javascript */
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
/* javascript */
  function decryptByAES(message, key) {
    var keyHex = CryptoJS.enc.Utf8.parse(key);
    var encrypted = CryptoJS.AES.decrypt(message, keyHex, {
      mode: CryptoJS.mode.ECB,
      padding: CryptoJS.pad.Pkcs7
    });
      return encrypted.toString(CryptoJS.enc.Utf8);
}
```
```C#
/* C# */
public static string CryptoJS_AES_Decrypt(string decryptString, string decryptKey)
{
  if (string.IsNullOrEmpty(decryptString))
    return decryptString;
    
  byte[] keyArray = UTF8Encoding.UTF8.GetBytes(decryptKey);
  byte[] toEncryptArray = Convert.FromBase64String(decryptString);
  RijndaelManaged rDel = new RijndaelManaged();
  rDel.Key = keyArray;
  rDel.Mode = CipherMode.ECB;
  rDel.Padding = PaddingMode.PKCS7;
  ICryptoTransform cTransform = rDel.CreateDecryptor();
  byte[] resultArray = cTransform.TransformFinalBlock(toEncryptArray, 0, toEncryptArray.Length);
  return UTF8Encoding.UTF8.GetString(resultArray);
}
```
