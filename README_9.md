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
