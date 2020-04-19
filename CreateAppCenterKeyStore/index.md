# Create AppCenter Keystore Using Keytool

![](https://raw.githubusercontent.com/jaysonragasa/jaraimages/master/CreateAppCenterKeyStore/clearddvslookupmove_atios.gif)  
  
To be able to run the distributed application in any Android device. AppCenter requires you to upload your KeyStore to be able to sign the apk file.

To do this, you must generate your personal `.keystore` file.  
  
Note that you can also use the Archive Manager in Visual Studio but if you want to use the command line. _Continue reading ..._

Head over to `keytool.exe` directory by using PowerShell in **Administrative mode** or you'll get Access Denied when keyool generates your keystore file.
    
* And enter `cmd` then ↲ - The reason why we do this is to just simplify our navigation to Java folder in `Profile Files (x86)` or directly in JDK folder. 
  
* Next `cd %java_home%\bin` ↲ - if that failed, then you can try this `cd %programfiles(x86)%\Java` ↲ then `dir` ↲ and it should list the folder contents  
  
```
C:\Program Files (x86)\Java>dir
 Volume in drive C is SIDE A
 Volume Serial Number is 5851-D4A3

 Directory of C:\Program Files (x86)\Java

03/29/2020  05:18 AM    <DIR>          .
03/29/2020  05:18 AM    <DIR>          ..
09/19/2018  12:55 PM    <DIR>          jdk1.8.0_181
03/29/2020  05:17 AM    <DIR>          jre1.8.0_241
               0 File(s)              0 bytes
               4 Dir(s)  17,503,277,056 bytes free

C:\Program Files (x86)\Java>
```  
  
* _(cont).._ `cd jdk` + then current version. i.e `cd jdk1.8.0_181` ↲ then finaly `cd bin`  
    
* Next `keytool -genkeypair -v -keystore WhateverFilenameYouWant.keystore -alias AndWhateverKeystoreAliasYouWant -keyalg RSA -keysize 2048 -validity 10000 -deststoretype PKCS12` ↲  
    
    i.e `keytool -genkeypair -v -keystore AppCenter.keystore -alias AppCenterKeyStore -keyalg RSA -keysize 2048 -validity 10000 -deststoretype PKCS12` ↲  
  
* Then just answer the questions like the first screenshot above.  
  
* Your keystore file will be saved in the same folder so copy that somewhere meaningful to you.  
  
* You can validate your keystore by typing `keytool -list -v -keystore WhateverFilenameYouWant.keystore -alias AndWhateverKeystoreAliasYouWant -storepass THEPASSWORDYOUSET -keypass THEPASSWORDYOUSET`  
  
    i.e `keytool -list -v -keystore AppCenter.keystore -alias AppCenterKeyStore -storepass secretpass -keypass secretpass`

    and should get something like this

```
Alias name: AndWhateverKeystoreAliasYouWant
Creation date: Apr 19, 2020
Entry type: PrivateKeyEntry
Certificate chain length: 1
Certificate[1]:
Owner: CN=jayson ragasa, OU=dev, O=jaraio, L=manila, ST=metro manila, C=ph
Issuer: CN=jayson ragasa, OU=dev, O=jaraio, L=manila, ST=metro manila, C=ph
Serial number: 48624cd
Valid from: Sun Apr 19 15:22:36 SGT 2020 until: Thu Sep 05 15:22:36 SGT 2047
Certificate fingerprints:
         MD5:  E8:19:1C:D5:58:9F:51:62:0F:70:57:B5:A5:A4:03:04
         SHA1: EF:84:7A:01:22:41:34:AC:27:97:56:B0:47:80:AF:3C:F5:64:D7:9A
         SHA256: E1:5D:DC:A3:91:EC:76:26:79:FC:9F:DB:91:77:AE:E4:5C:C1:AD:6C:DA:08:CB:99:77:D9:C8:33:D7:14:FD:22
Signature algorithm name: SHA256withRSA
Subject Public Key Algorithm: 2048-bit RSA key
Version: 3

Extensions:

#1: ObjectId: 2.5.29.14 Criticality=false
SubjectKeyIdentifier [
KeyIdentifier [
0000: AF 37 11 14 F4 26 E5 C4   8A B7 B2 09 E1 53 83 8F  .7...&.......S..
0010: 29 2E CC 0B                                        )...
]
]
```
* _(cont..)_ next step is to heave over to your build configuration in your AppCenter, upload this keystore then enter password, alias, and password again

# To put this simply
Watch the YouTube video
[![YouTube](https://raw.githubusercontent.com/jaysonragasa/jaraimages/master/CreateAppCenterKeyStore/2020-04-19_1618.png)](https://youtu.be/cRJNeFqrvig)