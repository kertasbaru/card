# Card Dump Parser (Termux Guide)

Panduan singkat ini menjelaskan cara mengambil repository target lalu melakukan proses build dan run di **Termux** (Android).

## 1) Persiapan di Termux

Jalankan perintah berikut:

```bash
pkg update && pkg upgrade -y
pkg install -y git openjdk-17
```

> Catatan:
> - Jika project membutuhkan Gradle wrapper (`./gradlew`), Java 17 umumnya sudah cukup untuk build Android modern.
> - Pastikan ruang penyimpanan cukup karena proses build Android bisa besar.

## 2) Clone Repository

```bash
git clone https://github.com/hamsazzad/Card-dump-parser.git
cd Card-dump-parser
```

## 3) Build APK di Termux

Jika file `gradlew` ada di root project:

```bash
chmod +x gradlew
./gradlew assembleDebug
```

APK debug biasanya akan berada di:

```text
app/build/outputs/apk/debug/app-debug.apk
```

## 4) Install & Run di Android

Dari Termux, buka file APK agar bisa di-install melalui installer Android:

```bash
termux-open app/build/outputs/apk/debug/app-debug.apk
```

Setelah terpasang, jalankan aplikasinya dari launcher Android seperti aplikasi biasa.

## 5) Troubleshooting Singkat

- **Permission denied saat menjalankan `gradlew`**  
  Jalankan kembali: `chmod +x gradlew`
- **Build gagal karena dependency**  
  Coba ulang: `./gradlew --refresh-dependencies assembleDebug`
- **Storage penuh**  
  Bersihkan cache build: `./gradlew clean`
