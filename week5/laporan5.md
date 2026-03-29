# Laporan Praktikum Jaringan Komputer

## Modul 5 – UDP

**Nama:** MUHAMMAD ZAKI OKTARUNA  
**NIM:** 103072400001 

## Tujuan
memahami atau mengetahui cara kerja protokol UDP dengan Wireshark

## Percobaan Praktikum

### 5.2

##### Jawab Pertanyaan
1. Sudah memilih salah satu paket UDP di trace, lalu ditemukan ada 4 field yang terdapat pada header UDP yaitu:
* Source Port
* Destination Port
* Length 
* Checksum
![Gambar UDP](../assets/week5/Gambar%20UDP.png)
2. Header UDP terdiri dari empat field utama yaitu Source Port, Destination Port, Length, dan Checksum. Masing-masing field memiliki panjang sebesar 2 byte, sehingga total panjang seluruh header UDP adalah 8 byte."
![Gambar UDP](../assets/week5/Gambar%20UDP.png)
3. Nilai Length sebesar 59 byte menyatakan total panjang datagram yang terdiri dari 8 byte header UDP dan 51 byte payload data. Dapat diverifikasi dengan menjumlahkan panjang header (8 byte) dengan panjang payload (51 byte) tertera pada detail informasi paket di Wireshark
![Gambar UDP](../assets/week5/Gambar%20UDP.png)
4. Pada field Length di header UDP, nilai tersebut disimpan dalam 16 bit (karena memiliki panjang 2 byte).Nilai maksimum dinyatakan oleh 16 bit adalah $2^{16}$=65. Jadi, nilai maksimum yang dapat tertulis pada field "Length" adalah 65 byte
![Field Length Udp](../assets/week5/Gambar%20Maks%20Byte.png)
5. batasan field 16-bit pada header UDP, nilai maksimum yang dapat merepresentasikan nomor port adalah 65.535. Oleh karena itu, nomor port terbesar yang dapat digunakan sebagai port sumber (maupun port tujuan) adalah 65
![Batasan Field](../assets/week5/Gambar%20Maks%20Byte.png)
6. Analisis pada IP Datagram Header paket nomor 2, nomor protokol untuk UDP adalah 17 dalam notasi desimal dan 0x11 dalam notasi heksadesimal
![Notasi Heksadesimal](../assets/week5/Gambar%20Notasi.png)
7. Hubungan antara nomor port pada kedua paket tersebut bersifat saling berkebalikan (inverse). Polanya:
* Source Port pada paket permintaan menjadi Destination Port pada paket balasan
* Destination Port pada paket permintaan menjadi Source Port pada paket balasan
Paket Pertama (Request/Permintaan):
* Source Port (Port Asal): 4334
* Destination Port (Port Tujuan): 161
 Paket Kedua (Response/Balasan):
* Source Port (Port Asal): 161
* Destination Port (Port Tujuan): 4334
Nomor port berfungsi sebagai "alamat aplikasi" di dalam sebuah komputer. Ketika komputer mengirimkan permintaan ke server, server harus mengetahui ke mana jawaban tersebut harus dikirimkan kembali agar sampai ke aplikasi yang benar (dalam hal ini, aplikasi yang membuka port 4334)
![Gambar Nomor Port](../assets/week5/Gambar%20Notasi.png)
