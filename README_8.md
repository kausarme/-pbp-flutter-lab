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