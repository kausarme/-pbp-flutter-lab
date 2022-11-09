# Tugas 7

## Checklist

Pada tugas ini, kamu akan mengimplementasikan beberapa elemen dasar pada Flutter.

_Checklist_ untuk tugas ini adalah sebagai berikut.

- [X] Membuat sebuah program Flutter baru dengan nama `counter_7`.
- [X] Mengubah tampilan program menjadi seperti berikut.
- [X] Mengimplementasikan logika berikut pada program.
    - [X] Tombol + menambahkan angka sebanyak satu satuan.
    - [X] Tombol - mengurangi angka sebanyak satu satuan. Apabila _counter_ bernilai 0, maka tombol - tidak memiliki
      efek apapun pada _counter_.
    - [X] Apabila _counter_ bernilai ganjil, maka teks indikator berubah menjadi "GANJIL" dengan warna biru.
    - [X] Apabila _counter_ bernilai genap, maka teks indikator berubah menjadi "GENAP" dengan warna merah.
    - [X] Angka 0 dianggap sebagai angka genap.
- [X] Menjawab beberapa pertanyaan berikut pada `README.md` pada _root folder_.
    - [X] Jelaskan apa yang dimaksud dengan _stateless widget_ dan _stateful widget_ dan jelaskan perbedaan dari
      keduanya.
    - [X] Sebutkan widget apa saja yang kamu pakai di proyek kali ini dan jelaskan fungsinya.
    - [X] Apa fungsi dari `setState()`? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
    - [X] Jelaskan perbedaan antara `const` dengan `final`.
    - [X] Jelaskan bagaimana cara kamu mengimplementasikan _checklist_ di atas.
- [X] Melakukan `add`-`commit`-`push` ke suatu repositori baru di GitHub. Kamu dapat menamai repositori barumu dengan
  nama `pbp-flutter-lab`.

### Bonus

Kamu akan mendapatkan nilai bonus pada penilaian tugas ini apabila kamu membuat fitur berikut.

- [X] Menyembunyikan/menghilangkan tombol - apabila _counter_ bernilai 0.

---

## Jawaban

### Stateless dan Stateful Widgets

Stateless dan Stateful merupakan terminologi dalam pemrograman platform.

#### Stateful

- Stateful Widgets mengizinkan user-nya untuk menyimpan, merekam, atau mengembalikan data.
- Stateful Widgets itu dinamik, artinya dapat berubah meresponse aksi dari user atau saat menerima data.
- Stateful widgets subclass StatefulWidget. Contohnya:  Checkbox, Radio, Slider, InkWell, Form, and TextField

#### Stateles

- Stateless Widgets adalah widgets yang tidak menyimpan, merekam, ataupun mereferensikan data sebelumnya.
- Stateless Widget tidak berubah.
- Stateless widgets subclass StatelessWidget. Contohnya adalah Icon, IconButton, and Text are examples of stateless
  widgets.

### setState()

State dalam sebuah widget disimpan dalam sebuah State Object. Statenya berisi nilai yang dapat berubah dalam widget
tersebut seperti nilai slider atau apakah checkbox terceklis.

- Saat state widget berubah objek state akan memanggil `setState()`, menuruh framework flutter untuk menggambar ulang
  widgetnya.
- Fungsi setState() adalah untuk melakukan perubahan nilai nilai pada state suatu stateful widget.

### Widgets yang saya gunakan pada Tugas ini

Widgets yang saya gunakan:

- **_Text_**, widget untuk menampilkan text. saya gunakan untuk menampilkan GENAP GANJIL dan counter
- **_FloatingActionButton_**, widget tombol yang melayang saya gunakan sebagai tombol untuk menambahkan dan mengurangi
  counter.
- **_Row dan Column_**, widget untuk menata layout horizontal dan vertikal.
- **_Padding_**, widget yang menambahkan padding pada widget lain agar tidak mempel dengan tepi layar.
- **_Scaffold_**, widget layar putih yang menjadi dasar dari widget-widget lain.
- **_Visibility_**, widget yang berfungsi untuk mengatur visibilitas widget childnya.
- **_Expanded_**, widget untuk menata layout supaya widget menggunakan seluruh bagian layar yang tersedia.

### const dan final

- Const menyatakan sebuah variabel memiliki nilai yang tidak dapat diubah. Const akan dijalankan saat compile. Sehingga,
  jika kita menggunakan const pada suatu object, maka object tersebut harus dapat ditentukan keseluruhan datanya seperti
  attribute ketika dicompile dan seluruh data tersebut akan menjadi immutable dan tidak dapat diubah lagi. Akibatnya
  const hanya dapat digunakan untuk objek yang memiliki nilai yang diketahui saat compile.

- Final menyatakan bahwa ini merupakan assignment terakhir variabel. Akibatnya jika final diterapkan pada variabel yang
  menyimpan suatu objek, variabel tersebut tidak dapat diganti isinya dengan objek tersebut dengan object lain. Walaupun
  begitu, final hanya melarang nilai variabel tersebut diganti dengan reference object lain. Namun kita masih bisa
  mengubah data atau attribute dari object yang disimpan variabel tersebut. Oleh sebab itu, final sering digunakan untuk
  objek yang nilainya tidak dapat ditentukan saat compile seperti HTTP Response yang tidak akan diubah-ubah.

## Implementasi

### 1. Bikin Aplikasi

Jalankan perintah `flutter create counter_7` untuk membuat sebuah aplikasi dasar bernama counter_7 Cek Hasilnya dengan
menjalankna `flutter run`

### 2. Buat Fungsi `_decrementCounter`

```dart
void _decrementCounter() {
  setState(() {
    if (_counter != 0) _counter--;
  });
}
```

panggil setState() dalam fungsi `_decrementCounter` untuk mengubah state. dan tambahkan logika yang diperlukan.

### 3. Tambahkan Tombol decrement
Untuk menambahkan tombol decrement tambahkan FloatingActionButton baru yang akan menggunakan icon.remove dan fungsi 
`_decrementCounter` 
```dart
floatingActionButton: FloatingActionButton(
              onPressed: _incrementCounter,
              tooltip: 'Increment',
              child: const Icon(Icons.add),
            )
```

### 4. Ubah teks counter jadi genap ganjil 
tambahkan logika untuk mengubah teks counter menjadi GENAP atau GANJIL berdasarkan `_counter%2`
```dart
_counter % 2 == 0
    ? const Text(
        'GENAP',
        style: TextStyle(color: Colors.red),
      )
    : const Text(
        'GANJIL',
        style: TextStyle(color: Colors.blue),
      ),
Text(
  '$_counter',
  style: Theme.of(context).textTheme.headline4,
),
```


### 5. Tata Layout 
menggunakan bottomSheet, Row, Colummn, Padding, dll. tata layout widget widget aplikasi.

### 6. Selesaikan README.md
