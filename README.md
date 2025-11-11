# Visual Studio Code'da C Dili Nasıl Çalıştırılır?

Bu rehberde, **Visual Studio Code** üzerinde **C dili** programlarını çalıştırmak için gerekli tüm adımları bulacaksınız.

---

## Adım 1: MSYS2 İndirip Kurun

**MSYS2**, Windows üzerinde Linux/Unix benzeri bir terminal ortamı sunar ve `pacman` paket yöneticisi sayesinde C/C++ gibi diller için gerekli **MinGW-w64** araçlarını kolayca yüklemenizi sağlar.

> ⚠️ Kurulum sırasında **programın kurulum yolunu değiştirmeyin**.

![MSYS2 web sitesi](/images/msyssite.png)  
![MSYS2 kurulum ekranı](/images/dosyayolu.png)

---

## Adım 2: Gerekli Araçları Terminalden Yükleyin

Kurulum tamamlandığında bir **MSYS2 terminali** açılacaktır.  
Aşağıdaki komutu bu terminale yapıştırın:

> (Not: `Ctrl+C / Ctrl+V` yerine sağ tık → **Paste** ile yapıştırın.)

```bash
pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain
```

### Bu Komut Ne Yapar?

- `pacman -S` → Paketleri indirip kurar.
- `--needed` → Zaten kurulu olanları atlar.
- `base-devel` → Derleme için temel araçları yükler.
- `mingw-w64-ucrt-x86_64-toolchain` → GCC (C derleyicisi) ve yardımcı araçları yükler.

Kurulum sırasında sadece **Enter** tuşuna basarak varsayılan ayarlarla devam edin, ardından **Y** tuşuna basarak onay verin.

> Hata alırsanız, terminali kapatıp yeniden deneyin.

![MSYS2 terminal komutu](/images/gccindirme.png)

---

## Adım 3: Program Dizinini PATH Değişkenine Ekleyin

MSYS2'nin yüklü olduğu dizini bulmamız gerekiyor.  
Kurulum sırasında yolu değiştirmediyseniz genellikle şu dizindedir:

```
C:\msys64\ucrt64\bin
```

1. `C` sürücüsünden `msys64 → ucrt64 → bin` klasörüne gidin.
2. Üstteki adres çubuğundan yolu kopyalayın.

![Dizin bulma](/images/binyol.png)

3. **Sistem Ortam Değişkenleri** ayarına girin.
4. **Path** kısmını açın → **Yeni (New)** seçeneğine tıklayın.
5. Kopyaladığınız yolu buraya yapıştırın ve **Tamam** diyerek çıkın.

![Ortam değişkeni ayarları](/images/path.png)
![Ortam değişkeni ayarları](/images/pathekleme.png)

---

## Adım 4: Kurulumu Kontrol Edin

Kurulumun başarılı olup olmadığını test etmek için **CMD** (Komut İstemi) açın ve şu komutu girin:

```bash
gcc --version
```

Eğer her şey doğruysa aşağıdakine benzer bir çıktı görmelisiniz 👇  
![GCC versiyon kontrolü](/images/cmd.png)

---

## Adım 5: Visual Studio Code Ayarları

1. VS Code’u açın (açıksa kapatıp yeniden başlatın).
2. **Eklentiler (Extensions)** sekmesinden aşağıdakileri kurun:
   - `C/C++` (Microsoft)
   - _(İsteğe bağlı)_ `Error Lens` → Yazım hatalarını anında görmenizi sağlar.

![VS Code eklentileri](/images/ceklentisi.png)
![VS Code eklentileri](/images/errorlens.png)

---

## Adım 6: İlk Kodunuzu Çalıştırın

Artık hazırız!
Yeni bir dosya açın ve örnek kodunuzu yazın:
![VS Code eklentileri](/images/ilkkod.png)
Üst kısımda bulunan çalıştırma tuşundan çalıştırın
VS Code’un alt kısmındaki **Run / Debug** menüsünden **Terminal** kısımına gelerek program çıktısını görebilirsiniz.

> Terminal ekranı karışırsa `clear` komutu ile temizleyebilirsiniz.

---

## Sonuç

Tebrikler! Artık **Visual Studio Code** üzerinde **C programlarını** yazıp çalıştırabiliyorsun.
Kaynak: Code Bear https://www.youtube.com/watch?v=1PBD5qFWdq8
