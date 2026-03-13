MUHAMMAD ZAKI OKTARUNA
103072400001

# Laporan Praktikum Jarkom IF 

# Tujuan Percobaan 
Mempelajari step pertama Wireshark

## Langkah Percobaan  
1. Installasi Wireshark dan Python yang sudah disediakan di modul atau bisa mencari di website 
2. Membuka aplikasi Wireshark dan memillih interface Wifi karena koneksi yang dipakai berasal dari jaringan Wifi. Interface ini kita gunakan juga untuk menangkap lalu lintas paket data pada jaringan 
3. Terdapat fitur fitur seperti stop capturing packet fungsinya untuk menghentikan proses pencarian atau penangkapan paket, dan ada juga start capturing packet fungsinya untuk melanjutkan proses setelah diberhentikan 
4. Lanjutkan pada kanan atas ada tempat untuk filter beberapa sinyal kategori contoh html, udp, ssdp, tcp, dll. Karena kita akan memfilter menggunakan tcp kali ini jadi diisi tcp di bagian filternya 
5. Setelah itu klik link yang ada di modul yaitu untuk menghasilkan lalu lintas jaringan yang dapat ditangkap oleh Wireshark
6. Setelah link di klik akan muncul seperti di contoh gambar untuk no 6 
7. Kembali ke Wireshark, tekan stop capturing packet dulu kemudian cari "http"
8. Pilih salah satu "http" yang memiliki informasi "GET Request', kemudian lihat source addressnya dan buka cmd ketikkan "ipconfig" kemudian bandingkan source di Wireshark dengan IPv4 Adress di CMD sama yaitu 192.168.1.4 menandakan bahwa paket HTTP GET berasal dari device yang sama kita gunakan

## Lampiran 
Gambar untuk no 3: ![Gambar No 3](../assets/image/week2/Stop%20Capturing%20Packet%20n%20Start%20Capturing%20Packet.png)


Gambar untuk no 4: ![Gambar No 4](../assets/image/week2/Filter%20TCP.png)


Gambar untuk no 5: ![Gambar No 5](../assets/image/week2/Link%20Test%20TCP.png)


Gambar untuk no 6: ![Gambar No 6](../assets/image/week2/Berhasil%20Test%20TCP.png)


Gambar untuk no 7 dan 8: ![Gambar No 7 n 8](../assets/image/week2/Filter%20HTTP.png)




