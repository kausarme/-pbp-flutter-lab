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


---
# Tugas 8

Nama : Kausar Meutuwah
NPM: 2106630100

## Checklist

Pada tugas ini, kamu akan mengimplementasikan beberapa elemen dasar pada Flutter.

_Checklist_ untuk tugas ini adalah sebagai berikut.

- [X] Menambahkan drawer/hamburger menu pada app yang telah dibuat sebeumnya.
- [X] Menambahkan tiga tombol navigasi pada drawer/hamburger.
  - [X] Navigasi pertama untuk ke halaman counter.
  - [X] Navigasi kedua untuk ke halaman form.
  - [X] Navigasi ketiga untuk ke halaman yang menampilkan data _budget_ yang telah di-_input_ melalui form.
- [X] Menambahkan halaman form
  - [X] Menambahkan elemen input dengan tipe data String berupa judul _budget_.
  - [X] Menambahkan elemen input dengan tipe data int berupa nominal _budget_.
  - [X] Menambahkan elemen dropdown yang berisi tipe _budget_ dengan pilihan pemasukan dan pengeluaran.
  - [X] Menambahkan button untuk menyimpan _budget_.
- [X] Menambahkan halaman data _budget_
  - [X] Menampilkan semua judul, nominal, dan tipe _budget_ yang telah ditambahkan pada form.
- [X] Menjawab beberapa pertanyaan berikut pada `README.md` pada _root folder_ (silakan modifikasi `README.md` yang
  telah kamu buat sebelumnya; tambahkan subjudul untuk setiap tugas).
  - [X] Jelaskan perbedaan `Navigator.push` dan `Navigator.pushReplacement`.
  - [X] Sebutkan widget apa saja yang kamu pakai di proyek kali ini dan jelaskan fungsinya.
  - [X] Sebutkan jenis-jenis _event_ yang ada pada Flutter (contoh: `onPressed`).
  - [X] Jelaskan bagaimana cara kerja `Navigator` dalam "mengganti" halaman dari aplikasi Flutter.
  - [X] Jelaskan bagaimana cara kamu mengimplementasikan _checklist_ di atas.
- [X] Melakukan `add`-`commit`-`push` ke GitHub.

### Bonus

Kamu akan mendapatkan nilai bonus pada penilaian tugas ini apabila kamu membuat fitur berikut.

- [X] Menambahkan elemen date picker pada halaman form.
- [X] Menampilkan elemen date (format bebas) pada setiap elemen _budget_ yang ada pada halaman data _budget_.
- [X] _Refactor_ widget Drawer ke sebuah file terpisah.

---

## Jawaban

### Widgets yang saya gunakan pada Tugas ini

Widgets yang saya gunakan (dari Tugas 7):

- `Text` widget untuk menampilkan text. saya gunakan untuk menampilkan GENAP GANJIL dan counter
- `FloatingActionButton` widget tombol yang melayang saya gunakan sebagai tombol untuk menambahkan dan mengurangi
  counter.
- `Row` dan `Column`, widget untuk menata layout horizontal dan vertikal.
- `Padding`, widget yang menambahkan padding pada widget lain agar tidak mempel dengan tepi layar.
- `Scaffold`, widget layar putih yang menjadi dasar dari widget-widget lain.
- `Visibility`, widget yang berfungsi untuk mengatur visibilitas widget childnya.
- `Expanded`, widget untuk menata layout supaya widget menggunakan seluruh bagian layar yang tersedia.

Widgets yang saya gunakan (dari Tugas 8):

- `Card`, widget untuk menampilkan panel berbentuk seperti kartu dengan tepi tumpul dan bayangan. digunakan untuk
  menampung info terkait title, subtitle, dan leading.
- `Drawer`, widget yang berada pada ujung sebelah kanan Scaffold untuk menunjukkan link navigasi.
- `DropdownButton`, widget untuk menampilkan pemilihan opsi dalam bentuk dropdown
- `Dialog`, widget untuk memunculkan pop-up window.
- `Form`, widget untuk mengelompokkan FormField seperti Dropdown, TextFormField.
- `ListView`, widget list yang dapat di _scroll_ ditampilkan secara linear.
- `SizedBox`, widget kotak dengan ukuran tertentu.
- `TextButton`,widget tombol yang memiliki text. digunakan untuk date picker.
- `TextFormField`, widget untuk input form yang memiliki format text. berupa textfield.

### perbedaan `Navigator.push` dan `Navigator.pushReplacement`

#### Definisi

- Navigator.push menambah rute halaman tambahan ke dalam stack Navigasi yang sudah ada.
- Navigator.pushReplacement mengubah rute ke halaman baru lalu membuang rute yang lama dari stack Navigasi.

#### Kembali ke halaman sebelumnya

- Navigator.push bisa kembali ke halaman sebelumnya.
- Navigator.pushReplacement tidak bisa kembali ke halaman sebelumnya.

### jenis-jenis _event_ yang ada pada Flutter.

Sebagian Jenis Event dalam flutter adalah sebagai berikut:

- `onTap`: event saat terjadi tap.
- `onFocusChange`: event saat fokus properti berubah.
- `onPressed`: event saat elemen/widget ditekan.
- `onSaved`: event saat elemen/widget disimpan.
- `onChanged`: event saat terjadi perubahan pada elemen/widget.

### cara kerja `Navigator` dalam "mengganti" halaman dari aplikasi Flutter.

Navigator adalah widget untuk menavigasi layar mana yang perlu ditampilkan. Navigator di Flutter memanfaatkan struktur
data _stack_ untuk mengingat layar yang ditampilkan. Struktur data ini diperlukan karena saat kita memencet tombol _
back_ pada device kita navigator perlu mengetahui layar mana saja yang sudah kita buka.

Ada beberapa metode utama pada objek Navigator yaitu:

- metode `push` untuk menimpa halaman sebelumnya dengan halamn baru.
- metode `pop` untuk menghapus halaman sekarang lalu kembali ke halaman sebelumnya.
- metode `pushReplacement` untuk menghapus halaman sekarang lalu menukarnya dengan halaman baru.

Dengan menggunakan metode push, pop, dan pushReplacement pada Halaman kita dapat memberitahu flutter, layar mana yang
perlu ditampilkan.

## Implementasi

### 1. Buat file dart yang diperlukan

- bikin file
  - `budget.dart`untuk menyimpan data budget.
  - `drawer.dart` untuk menampilkan drawer pada halaman lain.
  - `budget_page.dart` untuk menampilkan halaman berisi data dari budget.
  - `form.dart` untuk menampilkan halaman form untuk tambah budget.
- bikin dan extend class pada setiap file sesuai keperluan.

### 2. Buat tombol navigasi pada drawer

- Mengingat bonus meminta untuk merefactor file pada drawer ke file baru. kita akan membuat drawer dari awal di
  drawer.dart.
- drawer akan meng-extend `StatelessWidget`.
- Implementasikan fungsi build untuk
- Implementasikan buildMenuItems dan tambahkan widget untuk navigasi ke halaman lain.

```dart
Widget buildMenuItems(BuildContext context) =>
    Container(
        padding: const EdgeInsets.all(24),
        child: Wrap(
          runSpacing: 12,
          children: [
            ListTile(
              title: const Text('counter_7'),
              onTap: () {
                // Route menu ke halaman utama
                Navigator.of(context).pushReplacement(
                    MaterialPageRoute(builder: (context) => const MyHomePage()));
              },
            ),
            ListTile(
              title: const Text('Tambah Budget'),
              onTap: () {
                // close navigation drawer before
                Navigator.pop(context);
                // Route menu ke halaman form
                Navigator.of(context).push(
                  MaterialPageRoute(builder: (context) => const MyFormPage()),
                );
              },
            ),
            ListTile(
              title: const Text('Data Budget'),
              onTap: () {
                // close navigation drawer before
                Navigator.pop(context);
                // Route menu ke halaman data budget
                Navigator.of(context).push(
                  MaterialPageRoute(builder: (context) => const MyDataPage()),
                );
              },
            ),
          ],
        ));
```

### 3. Tambahkan drawer ke semua halaman lainnya

```dart
drawer: const NavigationDrawer()
```

### 4. Buat class Budget pada budget.dart untuk menyimpan data budget

```
// Model Budget
class Budget {
  static List<Budget> budgets = [];
  String name;
  int amount;
  String type;
  DateTime date;

  Budget({
    required this.name,
    required this.amount,
    required this.type,
    required this.date,
  });

  static void addBudget({
    required name,
    required amount,
    required type,
    required date,
  }) {
    budgets.add(Budget(
      name: name,
      amount: amount,
      type: type,
      date: date,
    ));
  }
}

```

### 5. Buat Form pada form.dart

- Implementasikan build dan
- Menambahkan TextFormField dengan tipe data String berupa judul _budget_.
- Menambahkan TextFormField dengan tipe data int berupa nominal _budget_.
- Menambahkan DropdownButton yang berisi
  - DropdownMenuItem untuk tipe _budget_ dengan pilihan pemasukan
  - DropdownMenuItem untuk tipe _budget_ dengan pilihan pengeluaran.
- Menambahkan button untuk menyimpan _budget_.

### 6. Buat Date picker pada form.dart (BONUS)

- Menambahkan widget date picker pada halaman form.

```dart
    TextButton
(
onPressed: (() {
showDatePicker(
context: context,
initialDate: DateTime.now(),
firstDate: DateTime(2000),
lastDate: DateTime(2100),
).then((value) {
setState(() {
_date = value;
});
});
})
,
```

### 7. Menampilkan elemen budget pada sebuah halaman.

- Menampilkan semua judul, nominal, dan tipe _budget_ yang telah ditambahkan pada form dalam bentuk kartu.

### 8. Menampilkan elemen date pada setiap elemen budget yang ada pada halaman data budget. (BONUS)

```
  child: ListTile(
      title: Text("${budget.name}\n${budget.amount}"),
      subtitle: Text(budget.date.toString().split(' ')[0]),
      trailing: Text(budget.type)),
);
}).toList(),
```

### 9. Bikin README_8.md

---


# Tugas 9

Nama : Kausar Meutuwah NPM: 2106630100

## Checklist

Pada tugas ini, kamu akan mengintegrasikan *mywatchlist* yang sudah kamu buat pada tugas 3 sebelumnya ke Flutter.
Pengerjaan tugas ini akan menggunakan app yang sama dengan tugas Flutter sebelumnya.

*Checklist* untuk tugas ini adalah sebagai berikut.

- [X] Menambahkan tombol navigasi pada drawer/hamburger untuk ke halaman *mywatchlist*.
- [X] Membuat satu file dart yang berisi model *mywatchlist*.
- [X] Menambahkan halaman *mywatchlist* yang berisi semua *watch list* yang ada pada endpoint JSON di Django yang telah
  kamu *deploy* ke Heroku sebelumnya. Pada bagian ini, kamu cukup menampilkan judul dari setiap *mywatchlist* yang ada.
  - [X] Membuat navigasi dari setiap judul *watch list* ke halaman detail
- [X] Menambahkan halaman detail untuk setiap *mywatchlist* yang ada pada daftar tersebut. Halaman ini menampilkan
  judul, release date, rating, *review*, dan status (sudah ditonton/belum).
- [X] Menambahkan tombol untuk kembali ke daftar *mywatchlist*
- [X] Menjawab beberapa pertanyaan berikut pada `README.md` pada *root folder* (silakan modifikasi `README.md` yang
  telah kamu buat sebelumnya; tambahkan subjudul untuk setiap tugas).
  - [X] Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal
    tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?
  - [X] Sebutkan widget apa saja yang kamu pakai di proyek kali ini dan jelaskan fungsinya.
  - [X] Jelaskan mekanisme pengambilan data dari json hingga dapat ditampilkan pada Flutter.
  - [X] Jelaskan bagaimana cara kamu mengimplementasikan *checklist* di atas.
- [x] Melakukan `add`-`commit`-`push` ke GitHub.

### Bonus

Kamu akan mendapatkan nilai bonus pada penilaian tugas ini apabila kamu membuat fitur berikut.

- [X] Menambahkan *checkbox* pada setiap *watchlist* pada halaman *mywatchlist*. Dimana *checkbox* akan tercentang jika
  status ditonton bernilai `true` dan tidak jika bernilai `false`.
  - [X] Jika *checkbox* ditekan, maka status ditonton akan berubah (perubahan akan terjadi di lokal secara sementara
    saja, status pada endpoint tidak perlu diubah)
- [X] Menambahkan warna untuk *outline* pada setiap *mywatchlist* pada halaman *mywatchlist* berdasarkan status
  ditonton (Dua warna yang dipilih bebas).
- [X] *Refactor* function fetch data dari web service ke sebuah file terpisah.

---

## Jawaban

### Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?

Ya, bisa. Namun, ada beberapa kerugian yaitu dalam hal type safety dan struktur yang berantakan, serta kemungkinan error
yang lebih tinggi.

### Jelaskan mekanisme pengambilan data dari json hingga dapat ditampilkan pada Flutter.

1. data difetch dari API endpoint dalam bentuk json
2. data json di konversi menjadi instance dari model

### Widgets yang saya gunakan pada Tugas ini

Widgets yang saya gunakan (dari Tugas 7):

- `Text` widget untuk menampilkan text. saya gunakan untuk menampilkan GENAP GANJIL dan counter
- `FloatingActionButton` widget tombol yang melayang saya gunakan sebagai tombol untuk menambahkan dan mengurangi
  counter.
- `Row` dan `Column`, widget untuk menata layout horizontal dan vertikal.
- `Padding`, widget yang menambahkan padding pada widget lain agar tidak mempel dengan tepi layar.
- `Scaffold`, widget layar putih yang menjadi dasar dari widget-widget lain.
- `Visibility`, widget yang berfungsi untuk mengatur visibilitas widget childnya.
- `Expanded`, widget untuk menata layout supaya widget menggunakan seluruh bagian layar yang tersedia.

Widgets yang saya gunakan (dari Tugas 8):

- `Card`, widget untuk menampilkan panel berbentuk seperti kartu dengan tepi tumpul dan bayangan. digunakan untuk
  menampung info terkait title, subtitle, dan leading.
- `Drawer`, widget yang berada pada ujung sebelah kanan Scaffold untuk menunjukkan link navigasi.
- `DropdownButton`, widget untuk menampilkan pemilihan opsi dalam bentuk dropdown
- `Dialog`, widget untuk memunculkan pop-up window.
- `Form`, widget untuk mengelompokkan FormField seperti Dropdown, TextFormField.
- `ListView`, widget list yang dapat di _scroll_ ditampilkan secara linear.
- `SizedBox`, widget kotak dengan ukuran tertentu.
- `TextButton`,widget tombol yang memiliki text. digunakan untuk date picker.
- `TextFormField`, widget untuk input form yang memiliki format text. berupa textfield.

Widgets yang saya gunakan (dari Tugas 9):

- `RichText`, widget untuk menampilkan teks namun dengan format tambahan.
- `FutureBuilder`, widget yang membangun dirinya dengan _snapshot_ terakhir dari sebuah fungsi asinkronus.
- `ElevatedButton`, widget yang menampilkan sebuah tombol yang terlihat seakan melayang.

## Impelementasi Checklist

### Refactor File ke bentuk folder model dan page
### Buat model MyWatchList di mywatchlist.dart
Untuk membuat model mywatchlist gunakan https://app.quicktype.io/ dan copy file dari json yang ada.

### Buat Tombol Navigasi menuju MyWatchlist
Tambahkan List Tile di drawer.dart
```dart
ListTile(
            title: const Text('Watchlist'),
            onTap: () {
              Navigator.pop(context);
              Navigator.of(context).push(
                MaterialPageRoute(
                    builder: (context) => const MyWatchListPage()),
              );
            },
          ),
```

### Buat Fungsi Asinkronus untuk mengambil data dari JSON tugas 3
```dart
Future<List<MyWatchList>> fetchMyWatchList() async {
  var url =
      Uri.parse('https://kausarme-tugas2pbp.herokuapp.com/mywatchlist/json');
  var response = await http.get(
    url,
    headers: {
      "Access-Control-Allow-Origin": "*",
      "Content-Type": "application/json",
    },
  );

  // melakukan decode response menjadi bentuk json
  var data = jsonDecode(utf8.decode(response.bodyBytes));

  // melakukan konversi data json menjadi object ToDo
  List<MyWatchList> listMyWatchList = [];
  for (var d in data) {
    if (d != null) {
      listMyWatchList.add(MyWatchList.fromJson(d));
    }
  }

  return listMyWatchList;
}
```


### Buat page MyWatchListPage di mywatchlist_page.dart
MyWatchlistPage akan menggunakan Widget FutureBuilder untuk mengambil data dari fungsi asinkronus.
```dart
body: FutureBuilder(
            future: fetchMyWatchList(),
            builder: (context, AsyncSnapshot snapshot) {
              ...
            }
```
Pastikan untuk mempush halaman detail page yang bersangkutan ke navigator untuk setiap data yang ada pafa halaman.

### Buat page MyWatchListDetailPage di mywatchlist_detail.dart

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.start,
  crossAxisAlignment: CrossAxisAlignment.stretch,
  children: [
    const Text(''),
    Text(
      widget.watchlistItem.fields.title,
      textAlign: TextAlign.center,
      overflow: TextOverflow.fade,
      style: const TextStyle(
        fontWeight: FontWeight.bold,
        fontSize: 25,
      ),
    ),
    const Text(''),
    RichText(...),
    RichText(...),
    RichText(...),
    RichText(...),
    RichText(...),
    Expanded(child: Container()),
```

### tambahkan package intl
jalankan di cmd `flutter pub add intl`
dan import di halaman agar bisa menggunakan DateFormat

### Menambahkan tombol untuk kembali ke daftar *mywatchlist*
```dart
ElevatedButton(
      onPressed: () {
        Navigator.pop(context);
      },
      child: const Text("Back"),
    ),
  ])
```

### Refactor Fungsi asinkronus fecthMyWatchList ke file baru bernama mywatchlist.dart (BONUS)

### Menambahkan *checkbox* pada setiap *watchlist* pada halaman *mywatchlist*.
- *checkbox* akan tercentang jika status ditonton bernilai `true` dan tidak jika bernilai `false`.
- Jika *checkbox* ditekan, maka status ditonton akan berubah (perubahan akan terjadi di lokal secara sementara
  saja, status pada endpoint tidak perlu diubah)


```dart
      Checkbox(
        checkColor: Colors.white,
        fillColor:
            MaterialStateProperty.resolveWith<
                Color>((Set<MaterialState> states) {
          if (snapshot
              .data![index].fields.watched) {
            return Colors.green;
          }
          return Colors.red;
        }),
```

###Menambahkan warna untuk *outline* pada setiap *mywatchlist* pada halaman *mywatchlist* berdasarkan status ditonton
```dart
boxShadow:  [
  BoxShadow(
    color:snapshot.data![index].fields.watched ? Colors.blue : Colors.red, 
    blurRadius: 2.0
  )
]
```

---