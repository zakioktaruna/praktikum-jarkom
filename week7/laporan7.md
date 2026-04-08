# Laporan Praktikum Jaringan Komputer

## Modul 6 – TCP

**Nama:** MUHAMMAD ZAKI OKTARUNA  
**NIM:** 103072400001 

## Tujuan
memahami atau mengetahui cara kerja dan membuat program berbasis socket UDP dan TCP

## Percobaan Praktikum

### 7.2

#### 7.2.1 UDP Client

1. Membuat soket UDP
2. Membaca baris input dari pengguna
3. Melampirkan alamat server (IP dan Port) ke pesan
4. Mengirimkan pesan melalui soket ke server 
5. Menggangu dan menerima pesan balasan dari server
6. Menutup soket
![Gambar UDP Client](../assets/week7/Gambar%20UDP%20Client.png)

#### 7.2.2 UDP Server

1. Membuat soket UDP
2. Mengikat (bind) nomor port ke soket tersebut
3. Masuk ke while loop untuk menunggu paket dari klien 
4. Menerima pesan dan alamat klien
5. Memproses pesan (misal mengubah ke huruf kapital)
6. Mengirimkan pesan yang sudah diproses kembali ke alamat klien
![Gambar UDP Server](../assets/week7/Gambar%20UDP%20Server.png)

Hasil Output UDP: 
![Gambar Output UDP](../assets/week7/Gambar%20Output%20UDP.png)

### 7.3

#### 7.3.1 TCP Client

1. Membuat Socket: Sama seperti server, klien membuat soket TCP
2. Connect: Klien harus melakukan connect() ke alamat IP dan nomor port server yang dituju. Di balik layar, ini proses 3-way handshake TCP 
3. Kirim Data: Koneksi sudah terbentuk, klien cukup menggunakan fungsi send() untuk mengirimkan pesan tanpa perlu melampirkan alamat tujuan di setiap paket (berbeda dengan UDP)
4. Terima Balasan: Klien menunggu dan membaca data dari server menggunakan recv()
5. Close: Menutup soket setelah pertukaran data selesai
![Gambar TCP Client](../assets/week7/Gambar%20TCP%20Client.png)

#### 7.3.2 TCP Server

1. Membuat Socket: Server membuat soket TCP menggunakan AF_INET (untuk IPv4) dan SOCK_STREAM (untuk TCP)
2. Bind: Mengaitkan nomor port tertentu ke soket server agar klien tahu ke mana harus menghubungi
3. Listen: Server mulai mendengarkan (listening) permintaan koneksi masuk
4. Accept: Ketika klien mencoba terhubung, server menjalankan fungsi accept(). Ini akan menghasilkan soket baru (connectionSocket) khusus digunakan berkomunikasi dengan klien tersebut, sementara soket utama tetap mendengarkan koneksi baru lainnya
5. Komunikasi: Menerima data menggunakan recv() dan mengirim balasan menggunakan send()
6. Close: Menutup koneksi setelah selesai
![Gambar TCP Server](../assets/week7/Gambar%20TCP%20Server.png)

Hasil Output TCP: 
![Gambar Output TCP](../assets/week7/Gambar%20Output%20TCP.png)