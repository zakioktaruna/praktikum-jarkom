# Laporan Praktikum Jaringan Komputer

## Modul 10 – IP

**Nama:** MUHAMMAD ZAKI OKTARUNA  
**NIM:** 103072400001 

## Tujuan
memahami atau mengetahui cara kerja protokol IP menggunakan Wireshark

## Percobaan Praktikum

### 10.2.1 

#### 10.2.1 Bagian 1: IPv4 Dasar
1. Download terlebih dahulu file "wireshark-traces" yang sudah disediakan di modul
2. Setelah didownload lalu belakang nama file ditambahkan ".pcap" akan jadi seperti ini "wireshark-traces.pcap". Kenapa diberi ".pcap" agar bisa dibuka di Wiresharknya
3. Setelah dibuka di Wireshark untuk filenya lalu bagian filter masukkan seperti ini "ip.src==192.168.1.102 && udp" maka akan muncul seperti gambar dibawah yang sudah sesuai yang diminta
![Gambar IP Source](../assets/week10/Gambar%20IP%20Source.png)

### 10.2.3

#### 10.2.3 Bagian 3: Ipv6
1. Untuk Ipv6 bedanya dengan IPv4 hanya di bagian destination jika IPv4 akan berisi full angka dan jika IPv6 akan campur dengan huruf 