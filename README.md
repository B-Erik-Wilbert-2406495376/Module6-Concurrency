# Commit 1 Reflection notes
Pada bagian handle_connection, saya mencoba untuk memahami bagaimana Rust membaca request HTTP secara bertahap dan terstruktur. Penggunaan BufReader membantu proses pembacaan menjadi lebih efisien karena data tidak langsung diambil mentah dari stream, melainkan melalui buffer. Method .lines() memungkinkan setiap baris dibaca satu per satu, lalu dihentikan saat menemui baris kosong dengan .take_while, yang menandakan akhir dari header HTTP. Bagian ini membuat saya melihat bahwa Rust mampu menyederhanakan proses pembacaan data tanpa menghilangkan kendali di tangan programmer, sehingga alurnya tetap jelas dan mudah diikuti.

# Commit 2 Reflection notes
Pada bagian ini, saya melihat bagaimana response HTTP mulai dibangun secara langsung dari file yang dibaca. Prosesnya terasa lebih jelas: server menerima request, mengambil isi file, lalu mengirimkannya kembali sebagai response. Hal kecil yang cukup penting adalah bagaimana struktur response seperti status line dan Content-Length harus disusun dengan benar agar bisa dipahami oleh client.

