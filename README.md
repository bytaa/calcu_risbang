
🧮 Simple Web Calculator
📝 Penjelasan Singkat Proyek
Proyek ini adalah implementasi dasar kalkulator fungsional yang dibuat sebagai demonstrasi kemampuan front-end development dasar. Kalkulator ini mampu menangani operasi aritmatika standar dan menampilkan antarmuka yang sederhana dan user-friendly.


🛠️ Bahasa dan Program yang Digunakan
Komponen	Bahasa/Teknologi	Peran
Struktur	HTML5	Kerangka dasar, mendefinisikan tombol, dan input screen.
Tampilan	CSS3	Menata tampilan (styling), memberikan soft UI (neomorphism) dengan pink color scheme, dan mengatur layout menggunakan Flexbox dan Grid.
Logika	JavaScript (Vanilla JS)	Menangani interaksi tombol, memproses input, dan melakukan perhitungan.


🔄 Penjelasan Alur Program
Alur kerja kalkulator ini berpusat pada pembaruan nilai pada layar input (#outputscreen):

Input Angka/Operator: Saat pengguna mengklik tombol angka atau operator, fungsi display(num) dipanggil. Fungsi ini mengambil nilai dari tombol (num) dan menambahkannya ke nilai yang sudah ada di output screen (outputscreen.value += num;).

Perhitungan: Saat tombol sama dengan (=) diklik, fungsi Calculate() dieksekusi.

Fungsi ini menggunakan eval() JavaScript untuk mengevaluasi string ekspresi matematika yang ada di output screen.

Hasil perhitungan kemudian ditampilkan kembali di output screen.

Terdapat blok try...catch untuk menangani error (misalnya, jika ekspresi tidak valid), yang akan menampilkan alert "Invalid".

Hapus:

Tombol Cl (Clear) memanggil Clear(), yang mengatur nilai output screen menjadi kosong ("").

Tombol DEL (Delete) memanggil del(). Namun, perlu diperhatikan bahwa implementasi saat ini (outputscreen.value.slice(0 - 1);) tidak berfungsi dengan benar; seharusnya menggunakan slice(0, -1) untuk menghapus karakter terakhir.


📜 Cuplikan Kode Utama (JavaScript)
Kode di bawah menunjukkan fungsi kunci untuk logika perhitungan dan interaksi:

JavaScript
// Menargetkan elemen input display
let outputscreen = document.getElementById("outputscreen");

// Fungsi untuk menambahkan angka/operator ke display
function display(num) {
  outputscreen.value += num;
}

// Fungsi untuk melakukan perhitungan
function Calculate() {
  try {
    // Menggunakan eval() untuk mengevaluasi ekspresi matematika
    outputscreen.value = eval(outputscreen.value);
  } catch (err) {
    alert("Invalid"); // Menampilkan pesan error jika terjadi kesalahan
  }
}

// Fungsi untuk menghapus semua input
function Clear() {
  outputscreen.value = "";
}

// Fungsi untuk menghapus karakter terakhir (Perlu Perbaikan: saat ini salah)
function del() {
  // Implementasi yang benar seharusnya: outputscreen.value = outputscreen.value.slice(0, -1);
  outputscreen.value.slice(0 - 1); 
}


⌨️ Contoh Input & Output
Aksi Pengguna	Input Display Awal	Hasil/Output Display Akhir
Tekan 1, +, 2, =	1+2	3
Tekan 5, *, 6, =	5*6	30
Tekan 10, %, 2, =	10%2	0
Tekan 1234, lalu Cl	1234	(Kosong)



