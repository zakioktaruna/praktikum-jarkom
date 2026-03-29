# Laporan Praktikum Jaringan Komputer

## Modul 4 – DNS

**Nama:** MUHAMMAD ZAKI OKTARUNA  
**NIM:** 103072400001 

## Tujuan
memahami cara kerja DNS menggunakan Wireshark dan CMD

## Percobaan Praktikum

### 4.2 Nslookup

#### Langkah Praktikum
1.  Menjalankan nslookup untuk mendapatkan alamat ip Universitas Tokyo dari server web di Asia. Dan alamat ip nya adalah 210.152.243.234

#### Hasil Pengujian 
Berdasarkan pengujian yang dilakukan terhadap server web Universitas Tokyo (Jepang) sebagai perwakilan server di Asia, hasilnya:
* Domain: `www.u-tokyo.ac.jp`
* Alamat IP (IPv4): `210.152.243.234`
* Server DNS yang Menjawab: `192.168.1.1`
![Alamat Ip dari Universitas Tokyo](../assets/week4/Gambar1.png)
2. Menjalankan nslookup agar mengetahui server DNS otoratif dari University of Cambridge. Untuk pengujian server di Eropa, dilakukan pengecekan terhadap domain University of Cambridge (Inggris) menggunakan opsi -type=NS

##### Hasil Pengamatan
terdapat beberapa Name Server otoritatif yang mengelola domain cam.ac.uk, di antaranya:
* auth0.dns.cam.ac.uk dengan alamat IP: 131.111.8.37
* auth1.dns.cam.ac.uk dengan alamat IP: 131.111.12.37
* dns0.cl.cam.ac.uk
* ns1.mythic-beasts.com

##### Analisis 
Daftar tersebut menunjukkan server-server yang memiliki otoritas penuh atas informasi DNS di lingkungan University of Cambridge. Alamat IP 131.111.8.37 (auth0) akan digunakan sebagai referensi untuk melakukan query pada langkah selanjutnya
![Alamat server DNS otoratif dari University of Cambridge](../assets/week4/Gambar2.png)
3. Menjalankan nslookuip mencari tahu informasi mengenai server email dari Yahoo!. Alamat ip nya adalah 131.111.8.37

Pada tahap ini, dilakukan percobaan untuk mencari informasi alamat IP www.u-tokyo.ac.jp (Jepang) dengan menggunakan server DNS milik University of Cambridge (131.111.8.37) sebagai perantara (resolver)

##### Hasil Pengamatan 
* Perintah: nslookup www.u-tokyo.ac.jp 131.111.8.37
* Respon: *** auth0.dns.cam.ac.uk can't find www.u-tokyo.ac.jp: Query refused

#### Analisis 
* Munculnya pesan "Query refused" (Permintaan ditolak) terjadi karena server auth0.dns.cam.ac.uk merupakan Authoritative Name Server
* Server ini didesain hanya untuk menjawab permintaan yang berkaitan dengan domain internal mereka sendiri (cam.ac.uk)
* Server tersebut menolak melakukan recursive query (mencari informasi domain luar seperti u-tokyo.ac.jp) untuk pengguna umum dari internet guna mencegah penyalahgunaan server 
![Server email dari Yahoo!](../assets/week4/Gambar3.png)

### 4.3 Ipconfig

#### Langkah 
1. Ketikan ipconfig saja, maka akan muncul menampilkan informasi mengenai TCP/IP termasuk
alamat IP Anda, alamat server DNS, jenis adaptor, dan sebagainya
![Gambar Ipconfig](../assets/week4/Gambar4.png)
2. Lanjutkan dengan ipconfig /all maka akan muncul dari nama device atau host name, di bagian wifi dapat melihat ip4v address, subnet mask, dns server tidak hanya satu juga ada lebih untuk cadangan, dll
![Gambar Ipconfig /all](../assets/week4/Gambar5.png)
3. Lalu ketikan ipconfig /displaydns akan memunculkan informasi DNS yang tersimpan dalam host. Hasil yang didapatkan akan menampilkan record dan sisa Time To Live (TTL) dalam satuan detik
![Gambar Ipconfig /displaydns](..//assets/week4/Gambar6.png)
4. Terakhir untuk menghapus catatan ketik ipconfig /flushdns. Akan Mengosongkan catatan DNS berarti menghapus semua record dan memuat ulang record dari file host
![Gambar Ipconfig /flushdns](../assets/week4/Gambar7.png)

### 4.4 Tracing DNS dengan Wireshark

#### Langkah
1. Gunakan ipconfig untuk mengosongkan catatan DNS di host
2. Buka browser Anda dan kosongkan cache-nya
3. Buka Wireshark dan masukkan "ip.addr == 192.168.1.5" ke dalam filter
4. Mulai pengambilan paket di Wireshark
5. Dengan browser Anda, kunjungi halaman web `http://www.ietf.org`
6. Hentikan pengambilan paket

#### Analisis dan Jawab Soal
1. Sudah tertemukan permintaan dns dan balasannya. Pesan dikirim melalui UDP
![Gambar UDP](../assets/week4/Gambar8.png)
2. Port tujuan pada permintaan dns yaitu 53. Port sumber pada pesan balasannya yaitu 59065
![Gambar permintaan dan sumber dns](../assets/week4/Gambar9.png)
3. Sesuaikan pesan permintaan DNS dari alamat IP dan alamat IP server DNS lokal 
![Gambar permintaan DNS dari alamat IP dan alamat IP server DNS lokal](../assets/week4/Gambar10.png)
4. Pada pesan permintaan jenis atau typenya adalah AAAA. Tidak mengandung jawaban atau answer
![Gambar pesan permintaan jenis atau typenya](../assets/week4/Gambar11.png)
5. Ada 2 jawaban atau answer. Isinya sesuai di gambar dibawah
![Gambar jawaban atau answer](../assets/week4/Gambar12.png)
6. Lalu cocokkan destination TCP SYN dengan DNS bagian answer 
![Gambar TCP SYN](../assets/week4/Gambar13.png)
7. Host tidak selalu mengirimkan dns baru untuk setiap objek di suatu web karena browser sudah menyimpan hasil resolusi dns dalam page
![Gambar pesan permintaan DNS](../assets/week4/Gambar14.png)

### Bagian 2 dari 4.4

#### Jawab Soal (Download dari file dns-ethereal-trace-2)
1. Port tujuannya itu 53 dan sumbernya itu 3742
![Port Tujuan](../assets/week4/Gambar15.png)
2. Ke alamat ip 128.238.29.22, bukan alamat default ip server DNS lokal yaitu 128.238.38.160
![Alamat Ip](../assets/week4/Gambar16.png)
3. Termasuk jenis atau type A, tidak ada jawaban atau answer 
![Jenis A](../assets/week4/Gambar17.png)
4. Hanya ada satu jawaban atau answer 
![Satu Jawaban](..//assets/week4/Gambar18.png)

### Bagian 3 dari 4.4

#### Jawab Soal 
1. Port tujuannya itu 53 dan sumbernya 57219
![Port Tujuan 2](../assets/week4/Gambar19.png)
2. Jenis atau tipe AAAA, dan ada dua jawaban
![Jenis AAAA](../assets/week4/Gambar20.png)
3. server DNS tidak menyertakan Additional Records yang berisi daftar Name Server otoritatif untuk domain mit.edu. Namun, pesan tersebut memberikan jawaban atas query AAAA (tipe IPv6) dengan memberikan dua alamat IPv6 untuk mit.edu, yaitu:
* 2a02:26f0:9100:1591::255e
* 2a02:26f0:9100:159d::255e
![Server MIT](../assets/week4/Gambar21.png)

### Bagian 4 dari 4.4

#### Jawab Soal
1. Ke alamat ip 18.0.72.3 bukan default alamat IP server DNS lokal karena defaultnya 192.168.1.5
![Alamat Ip](../assets/week4/Gambar22.png)
2. Berjenis atau tipe AAAA, dan ya mengandung jawaban
![Jenis AAAA](../assets/week4/Gambar23.png)
3. ada dua jawaban dan isinya sesuai di screenshot 
![Jawaban](../assets/week4/Gambar23.png)