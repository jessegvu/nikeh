# Football News App

## Widget Tree dan Parent-Child Relationship
Widget tree dalam Flutter adalah struktur hierarkis yang menggambarkan bagaimana widget tersusun dalam aplikasi. Setiap widget dapat menjadi parent yang memiliki satu atau lebih child widgets, membentuk struktur pohon. Parent widget bertanggung jawab untuk mengatur layout, styling, dan behavior dari child widgets-nya.

Contoh hubungan parent-child dalam proyek ini:
```
MaterialApp (parent)
└── Scaffold (child dari MaterialApp, parent untuk widget di bawahnya)
    ├── AppBar (child dari Scaffold)
    └── Body/Padding (child dari Scaffold, parent untuk widget di bawahnya)
        └── Column (child dari Padding, parent untuk Row dan Center)
```

## Widget yang Digunakan
1. `MaterialApp`: Widget root yang menyediakan konfigurasi tema dan routing
2. `Scaffold`: Menyediakan struktur dasar layout material design
3. `AppBar`: Menampilkan bar di bagian atas aplikasi
4. `Column`: Menyusun widget secara vertikal
5. `Row`: Menyusun widget secara horizontal
6. `Text`: Menampilkan teks
7. `Card`: Menampilkan panel dengan efek elevasi
8. `Container`: Membungkus widget lain dengan padding dan dekorasi
9. `GridView`: Menampilkan widget dalam format grid
10. `Icon`: Menampilkan ikon
11. `InkWell`: Memberikan efek sentuhan dan handling event tap
12. `Center`: Menempatkan widget di tengah
13. `Padding`: Memberikan padding pada widget
14. `SizedBox`: Memberikan jarak antar widget

## MaterialApp Widget
MaterialApp adalah widget yang mengonfigurasi navigasi level-teratas dan tema untuk aplikasi yang menggunakan Material Design. Widget ini sering digunakan sebagai root widget karena:
- Menyediakan konfigurasi tema default
- Mengatur navigasi dan routing
- Menginisialisasi design system Material
- Mengatur orientasi aplikasi
- Menyediakan title untuk aplikasi

## StatelessWidget vs StatefulWidget
**StatelessWidget**:
- Widget yang tidak memiliki state internal
- Tidak dapat berubah setelah dibuat
- Lebih efisien untuk UI yang statis
- Contoh: Icon, Text

**StatefulWidget**:
- Widget yang memiliki state yang dapat berubah
- Dapat diperbarui selama lifetime widget
- Cocok untuk UI yang dinamis
- Contoh: Checkbox, Form

Pilih StatelessWidget jika UI bersifat statis dan tidak perlu update, pilih StatefulWidget jika UI perlu berubah berdasarkan interaksi user atau data yang berubah.

## BuildContext
BuildContext adalah handle ke lokasi widget dalam widget tree. Penting karena:
- Memberikan akses ke tema dan media queries
- Digunakan untuk navigasi
- Memungkinkan akses ke widget ancestor
- Diperlukan untuk menampilkan dialog/snackbar

Dalam metode build, BuildContext digunakan sebagai parameter yang memberikan informasi tentang posisi widget dalam tree, contoh:
```dart
@override
Widget build(BuildContext context) {
    return Scaffold(
        // Menggunakan context untuk mengakses tema
        backgroundColor: Theme.of(context).backgroundColor,
    );
}
```

## Hot Reload vs Hot Restart
**Hot Reload**:
- Memperbarui UI dengan cepat tanpa kehilangan state
- Hanya mengompilasi widget yang berubah
- State tetap dipertahankan
- Berguna untuk iterasi cepat dalam pengembangan UI

**Hot Restart**:
- Memulai ulang aplikasi dari awal
- Mengompilasi ulang seluruh aplikasi
- Menghapus semua state
- Digunakan ketika perubahan mempengaruhi state atau inisialisasi aplikasi

Perbedaan utama adalah hot reload mempertahankan state sedangkan hot restart menghapus semua state dan memulai ulang aplikasi.