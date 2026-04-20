# Commit 1 Reflection notes
Pada bagian handle_connection, saya mencoba untuk memahami bagaimana Rust membaca request HTTP secara bertahap dan terstruktur. Penggunaan BufReader membantu proses pembacaan menjadi lebih efisien karena data tidak langsung diambil mentah dari stream, melainkan melalui buffer. Method .lines() memungkinkan setiap baris dibaca satu per satu, lalu dihentikan saat menemui baris kosong dengan .take_while, yang menandakan akhir dari header HTTP. Bagian ini membuat saya melihat bahwa Rust mampu menyederhanakan proses pembacaan data tanpa menghilangkan kendali di tangan programmer, sehingga alurnya tetap jelas dan mudah diikuti.

# Commit 2 Reflection notes
Pada bagian ini, saya melihat bagaimana response HTTP mulai dibangun secara langsung dari file yang dibaca. Prosesnya terasa lebih jelas: server menerima request, mengambil isi file, lalu mengirimkannya kembali sebagai response. Hal kecil yang cukup penting adalah bagaimana struktur response seperti status line dan Content-Length harus disusun dengan benar agar bisa dipahami oleh client.

# Commit 3 Reflection notes
Pemisahan response dilakukan dengan menentukan status_line dan filename terlebih dahulu berdasarkan request, lalu pembacaan file dan penyusunan HTTP response dikerjakan di satu tempat. Bagian yang berubah (jenis response) dipisahkan dari bagian yang tetap (format response), sehingga alurnya lebih jelas. Refactoring ini diperlukan agar tidak terjadi duplikasi kode di setiap kondisi if-else, sekaligus membuat kode lebih mudah dibaca dan dikembangkan ketika nanti ingin menambah route atau variasi response lain.

# Commit 4 Reflection notes
Match membuat penanganan request jadi lebih rapi karena setiap route langsung dipasangkan dengan response-nya. Penambahan /sleep juga menunjukkan bahwa satu request bisa menahan proses lain, sehingga terlihat bagaimana server bekerja secara berurutan.