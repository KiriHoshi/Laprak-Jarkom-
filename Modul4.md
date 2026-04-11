Nama : Gevin Shinarsa Pratama
NIM : 103072400080
Kelas : IF-04-05

# Modul 4

## 4.2 NsLookup
nslookup adalah sebuah perintah atau alat yang digunakan untuk mencari dan menampilkan informasi DNS, seperti mengetahui alamat IP dari suatu nama domain atau sebaliknya, sehingga sering dipakai untuk mengecek dan menganalisis koneksi jaringan.

## Langkah - Langkah
1. Buka cmd lalu ketik "nslookup www.mit.edu" lalu enter, command tersebut untuk melihat IP domain
<img width="477" height="359" alt="image" src="https://github.com/user-attachments/assets/7673e919-6802-4367-b5c6-35e108b0f931" />

2. ketik "nslookup –type=NS mit.edu" pada cmd lalu enter, command tersebut untuk menampilkan daftar name server yang terhubung
<img width="505" height="325" alt="image" src="https://github.com/user-attachments/assets/97064b2e-43ce-4860-831b-acef5146090b" />

3. ketik "nslookup www.aiit.or.kr bitsy.mit.edu" pada cmd lalu enter, command tersebut untuk meminta informasi tentang IP address dari domain www.aiit.or.kr ke server DNS bitsy.mit.edu
<img width="672" height="353" alt="image" src="https://github.com/user-attachments/assets/8e69baaf-6ae1-43cf-a9f8-8375b1874832" />

# Pertanyaan
**1. Jalankan nslookup untuk mendapatkan alamat IP dari server web di Asia. Berapa alamat IP server tersebut?**

IP yang di dapat dari web www.nus.edu.sg adalah 45.60.35.225

<img width="516" height="234" alt="image" src="https://github.com/user-attachments/assets/45b9c202-c215-4ac1-9628-b30964063af1" />


**2. Jalankan nslookup agar dapat mengetahui server DNS otoritatif untuk universitas di Eropa.**

salah satu kampus yang saya pakai untuk mengetahui server DNS adalah Technical University Of Munich, Untuk mencari nya menggunakan command "nslookup -type=ns tum.de"

<img width="524" height="206" alt="image" src="https://github.com/user-attachments/assets/a93520a0-ac5b-49ad-87a4-b12fd284cbac" />

**3. Jalankan nslookup untuk mencari tahu informasi mengenai server email dari Yahoo! Mail melalui salah satu server yang didapatkan di pertanyaan nomor 2. Apa alamat IP-nya ?**

Saya mencoba menggunakan server DNS dari domain tum.de, yaitu:

dns1.lrz.de
dns2.lrz.bayern
dns3.lrz.eu

Saat menjalankan perintah nslookup untuk mencari record MX (mail server) dari yahoo.com melalui salah satu DNS tersebut, muncul hasil “Query refused”.

Hal ini terjadi karena server DNS tersebut bersifat terbatas (hanya untuk jaringan internal), sehingga tidak menerima permintaan query dari luar. Akibatnya, informasi mengenai alamat IP server email Yahoo tidak bisa didapatkan melalui DNS tersebut.

<img width="718" height="459" alt="image" src="https://github.com/user-attachments/assets/9cf21ab7-33c1-4c36-ab1d-2ba2f69c4632" />

## 4.3 IP Config

IP Config adalah sebuah perintah yang digunakan untuk menampilkan informasi konfigurasi jaringan pada komputer, seperti alamat IP, subnet mask, dan default gateway.

## Langkah - Langkah
1. Buka cmd lalu ketik "ipconfig /all" lalu enter, command tersebut untuk menampilkan IP dan DNS pada laptop
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/a0c2e680-26ae-4525-9348-418bac7b5a45" />

2. Ketik "ipconfig /all > networkinfo.txt" pada cmd lalu enter, command tersebut untuk menyimpan IP dan DNS yang sudah di tampilkan namun di simpan berupa file txt.
<img width="563" height="46" alt="image" src="https://github.com/user-attachments/assets/db35959a-ced9-490d-9972-05804d1e4a5b" />

Contoh file 

<img width="746" height="29" alt="image" src="https://github.com/user-attachments/assets/4c0bc74b-6480-487a-a4fd-388e1fbbb0e6" />

lokasi file C:\Users\USER

3. Ketik "ipconfig /displaydns" pada cmd lalu enter, command tersebut untuk menampilkan DNS
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/2ccb838b-c048-4624-af08-74132d3a8cbc" />

4. Ketik "ipconfig /flushdns" pada cmd lalu enter, command tersebut untuk menghapus DNS yang di telah buka pada device
<img width="555" height="170" alt="image" src="https://github.com/user-attachments/assets/309c914e-8e60-4e48-bde2-be98d95e21c6" />

## 4.3 Tracking DNS dengan WireShark
Tracking DNS menggunakan Wireshark adalah kegiatan untuk mengamati dan menganalisis lalu lintas DNS dalam jaringan guna memahami bagaimana sebuah nama domain diubah menjadi alamat IP.

Dengan Wireshark, kita dapat menangkap paket DNS yang dikirim dari perangkat ke server DNS, kemudian melihat detail permintaan (query) serta balasan (response). Di dalam response tersebut biasanya terdapat alamat IP dari domain yang dicari.

Proses ini sangat membantu dalam melakukan troubleshooting jaringan maupun analisis keamanan, karena kita bisa mengetahui apakah proses resolusi DNS berjalan dengan benar atau tidak.
