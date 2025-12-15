# 🧮 Simple Web Calculator

## 📝 Penjelasan Singkat Proyek

Proyek ini adalah implementasi dasar kalkulator fungsional yang dibuat sebagai demonstrasi kemampuan *front-end development* dasar. Kalkulator ini mampu menangani operasi aritmatika standar dan menampilkan antarmuka yang sederhana dan *user-friendly*.

## 🛠️ Bahasa dan Program yang Digunakan

| Komponen | Bahasa/Teknologi | Peran |
| :--- | :--- | :--- |
| **Struktur** | HTML5 | Kerangka dasar, mendefinisikan tombol, dan *input screen*. |
| **Tampilan** | CSS3 | Menata tampilan (styling), memberikan *soft UI* (neomorphism) dengan *pink color scheme*, dan mengatur *layout* menggunakan Flexbox dan Grid. |
| **Logika** | JavaScript (Vanilla JS) | Menangani interaksi tombol, memproses input, dan melakukan perhitungan. |

## 🔄 Penjelasan Alur Program

Alur kerja kalkulator ini berpusat pada pembaruan nilai pada layar *input* (`#outputscreen`):

1.  **Input Angka/Operator:** Saat pengguna mengklik tombol angka atau operator, fungsi `display(num)` dipanggil. Fungsi ini mengambil nilai dari tombol (`num`) dan menambahkannya ke nilai yang sudah ada di *output screen* (`outputscreen.value += num;`).
2.  **Perhitungan:** Saat tombol sama dengan (`=`) diklik, fungsi `Calculate()` dieksekusi.
      * Fungsi ini menggunakan `eval()` JavaScript untuk mengevaluasi *string* ekspresi matematika yang ada di *output screen*.
      * Hasil perhitungan kemudian ditampilkan kembali di *output screen*.
      * Terdapat blok `try...catch` untuk menangani *error* (misalnya, jika ekspresi tidak valid), yang akan menampilkan *alert* "Invalid".
3.  **Hapus:**
      * Tombol **`Cl`** (Clear) memanggil `Clear()`, yang mengatur nilai *output screen* menjadi kosong (`""`).
      * Tombol **`DEL`** (Delete) memanggil `del()`. *Namun, **perlu diperhatikan** bahwa implementasi saat ini (`outputscreen.value.slice(0 - 1);`) **tidak berfungsi dengan benar**; seharusnya menggunakan `slice(0, -1)` untuk menghapus karakter terakhir.*

## 📜 Cuplikan Kode Utama (JavaScript)

Kode di bawah menunjukkan fungsi kunci untuk logika perhitungan dan interaksi:
let outputscreen = document.getElementById("outputscreen");

// 1. Menampilkan angka/operator yang diklik
function display(num) {
  outputscreen.value += num;
}

// 2. Melakukan perhitungan ekspresi
function Calculate() {
  try {
    // Menggunakan eval() untuk mengevaluasi ekspresi
    outputscreen.value = eval(outputscreen.value);
  } catch (err) {
    alert("Invalid"); // Menangani input yang tidak valid
  }
}

// 3. Menghapus seluruh konten display
function Clear() {
  outputscreen.value = "";
}

// 4. Menghapus karakter terakhir
function deleteLast() {
  // Menggunakan slice(0, -1) untuk menghilangkan karakter terakhir
  outputscreen.value = outputscreen.value.slice(0, -1);
}

## ⌨️ Contoh Input & Output

| Aksi Pengguna | Input Display Awal | Hasil/Output Display Akhir |
| :--- | :--- | :--- |
| Tekan `1`, `+`, `2`, `=` | `1+2` | `3` |
| Tekan `5`, `*`, `6`, `=` | `5*6` | `30` |
| Tekan `10`, `%`, `2`, `=` | `10%2` | `0` |
| Tekan `1234`, lalu `Cl` | `1234` | (Kosong) |
