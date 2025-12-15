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

📜 Cuplikan Kode Utama (JavaScript)
Kode JavaScript ini menangani seluruh logika interaksi dan perhitungan, mulai dari menampilkan input hingga menjalankan operasi matematika.
<!-- Kalkulator Sederhana -->
<div class="Calculator">
  <!-- Layar output kalkulator -->
  <input type="text" placeholder="0" id="outputscreen" />

  <!-- Tombol-tombol fungsi -->
  <button onclick="Clear()">Cl</button>       <!-- Bersihkan semua input -->
  <button onclick="deleteLast()">DEL</button> <!-- Hapus karakter terakhir -->
  <button onclick="display('%')">%</button>   <!-- Operator persen -->
  <button onclick="display('/')">/</button>   <!-- Operator bagi -->

  <!-- Tombol angka -->
  <button onclick="display('7')">7</button>
  <button onclick="display('8')">8</button>
  <button onclick="display('9')">9</button>
  <button onclick="display('*')">*</button>   <!-- Operator kali -->

  <button onclick="display('4')">4</button>
  <button onclick="display('5')">5</button>
  <button onclick="display('6')">6</button>
  <button onclick="display('-')">-</button>   <!-- Operator kurang -->

  <button onclick="display('1')">1</button>
  <button onclick="display('2')">2</button>
  <button onclick="display('3')">3</button>
  <button onclick="display('+')">+</button>   <!-- Operator tambah -->

  <button onclick="display('.')">.</button>  <!-- Titik desimal -->
  <button onclick="display('0')">0</button>
  <button onclick="Calculate()" class="equal">=</button> <!-- Hitung hasil -->
</div>

<script>
  // Ambil elemen input layar kalkulator
  let outputscreen = document.getElementById("outputscreen");

  // Fungsi untuk menampilkan input di layar
  function display(num) {
    outputscreen.value += num;
  }

  // Fungsi untuk menghitung ekspresi matematika
  function Calculate() {
    try {
      outputscreen.value = eval(outputscreen.value); // eval menghitung string matematika
    } catch {
      alert("Invalid Input"); // Tampilkan pesan jika input salah
    }
  }

  // Fungsi untuk membersihkan layar
  function Clear() {
    outputscreen.value = "";
  }

  // Fungsi untuk menghapus karakter terakhir
  function deleteLast() {
    outputscreen.value = outputscreen.value.slice(0, -1);
  }
</script>


## ⌨️ Contoh Input & Output

| Aksi Pengguna | Input Display Awal | Hasil/Output Display Akhir |
| :--- | :--- | :--- |
| Tekan `1`, `+`, `2`, `=` | `1+2` | `3` |
| Tekan `5`, `*`, `6`, `=` | `5*6` | `30` |
| Tekan `10`, `%`, `2`, `=` | `10%2` | `0` |
| Tekan `1234`, lalu `Cl` | `1234` | (Kosong) |
