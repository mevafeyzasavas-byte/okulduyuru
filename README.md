# Okul Duyuru - APK

Bu repo iki parçadan oluşur:

1. **`docs/index.html`** — asıl uygulama (haberler/duyurular listesi, tarih filtresi
   dahil). GitHub Pages ile yayınlanır. İçeriği değiştirip push ettiğinizde,
   telefonlardaki uygulama **APK'yı yeniden kurmaya gerek kalmadan** anında
   güncel halini gösterir.
2. **`www/index.html`** — APK'nın içine gömülen, çok küçük bir "yönlendirici"
   sayfa. Açılışta doğrudan `docs/index.html`'in yayınlandığı GitHub Pages
   adresine yönlenir. Bu dosyaya normalde dokunmanıza gerek yok.

Uygulama simgesi olarak MEB logosu kullanılmıştır (`res/icon/android/*`).

## Kurulum (tek seferlik)

### 1) Kodu push edin
Bu klasördeki tüm dosyaları reponuzun köküne push edin (zaten yaptıysanız
atlayabilirsiniz).

### 2) GitHub Pages'i açın
1. Repo **Settings → Pages**
2. **Source**: "Deploy from a branch"
3. **Branch**: `main`, klasör: **`/docs`**
4. **Save**

Birkaç dakika içinde uygulamanız şu adreste yayında olur:
```
https://KULLANICI_ADIN.github.io/REPO_ADIN/
```

> Bu proje için adres: `https://mevafeyzasavas-byte.github.io/okulduyuru/`
> Bu link `www/index.html` içinde `REMOTE_URL` değişkenine zaten yazılı.
> Kullanıcı adınız/repo adınız farklıysa `www/index.html` içindeki
> `REMOTE_URL` satırını güncelleyip **bir kez daha** APK derlemeniz gerekir
> (sonrasında bir daha gerekmez).

### 3) Workflow izinleri
**Settings → Actions → General → Workflow permissions →
"Read and write permissions"** seçip kaydedin (APK'nın Releases'e
yüklenebilmesi için gerekli).

### 4) APK'yı indirin
Push sonrası **Actions** sekmesinde "Build APK" otomatik çalışır. Bitince
repo ana sayfasının sağındaki **Releases** bölümünde sabit bir linkle
`okulduyuru.apk` belirir:

```
https://github.com/mevafeyzasavas-byte/okulduyuru/releases/latest/download/okulduyuru.apk
```

## Bundan sonra nasıl güncelleme yaparım?

- **İçerik/görünüm/filtre değişikliği** (ör. haber filtresi, tasarım, okul
  listesi) → sadece **`docs/index.html`**'i düzenleyip push edin. GitHub
  Pages otomatik günceller, telefonlardaki uygulama açılışta yeni sürümü
  çeker. **APK'yı tekrar indirmeye gerek yok.**
- **Uygulama simgesi, adı veya yönlendirme adresi** gibi APK'nın kendisiyle
  ilgili bir şey değişirse → `www/index.html`, `config.xml` veya `res/`
  içinde değişiklik yapıp push edin; bu durumda Actions yeni bir APK
  derler ve Releases'teki dosya güncellenir, kullanıcıların o zaman
  yeniden indirmesi gerekir.

## Not

Bu iş akışı `cordova build android --debug` ile derler, yani üretilen APK
Cordova'nın otomatik debug anahtarıyla imzalanır. Kendi cihazınıza kurarken
"bilinmeyen kaynaklardan yükleme" iznini açmanız gerekebilir. Google Play'e
yüklemek isterseniz ayrıca release-key imzalama adımı eklenmesi gerekir.
