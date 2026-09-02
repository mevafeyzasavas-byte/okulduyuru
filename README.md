# Okul Duyuru - APK

Bu klasör, `okulduyuru.html` uygulamasını GitHub Actions üzerinden otomatik olarak
Android APK'sına dönüştürüp, GitHub Releases sayfasına yükleyecek şekilde hazırlanmıştır.
Uygulama simgesi olarak MEB logosu kullanılmıştır (`res/icon/android/*`).

## Kurulum (tek seferlik)

1. GitHub'da **yeni bir repo** oluşturun (örnek: `okulduyuru-apk`), boş olarak.
2. Bu klasördeki tüm dosyaları o reponun içine kopyalayıp push edin:

```bash
cd okulduyuru-apk
git init
git add .
git commit -m "İlk sürüm"
git branch -M main
git remote add origin https://github.com/KULLANICI_ADIN/okulduyuru-apk.git
git push -u origin main
```

3. Push işleminden sonra GitHub, reponuzun **Actions** sekmesinde otomatik olarak
   "Build APK" iş akışını çalıştırır (birkaç dakika sürer).
4. İşlem bitince reponuzun **Releases** sayfasında `latest` etiketiyle bir sürüm
   oluşur ve `okulduyuru.apk` dosyası oraya eklenir.

## Doğrudan indirme linki

İş akışı her tamamlandığında aynı linkte APK güncellenir, yani bu link **sabit**
kalır (paylaşmak için idealdir):

```
https://github.com/KULLANICI_ADIN/okulduyuru-apk/releases/latest/download/okulduyuru.apk
```

`KULLANICI_ADIN` kısmını kendi GitHub kullanıcı adınızla değiştirin.

## HTML dosyasını güncellemek istersen

`www/index.html` dosyasını değiştirip tekrar `git push` yapmanız yeterli;
Actions otomatik olarak yeni bir APK derleyip Releases'e yükler.

## Not

Bu iş akışı `cordova build android --debug` ile derler, yani üretilen APK
Cordova'nın otomatik debug anahtarıyla imzalanır. Kendi cihazınıza kurarken
"bilinmeyen kaynaklardan yükleme" iznini açmanız gerekebilir. Google Play'e
yüklemek isterseniz ayrıca release-key imzalama adımı eklenmesi gerekir.
