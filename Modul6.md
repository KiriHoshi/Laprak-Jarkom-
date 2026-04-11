# Modul 6 TCP

TCP (Transmission Control Protocol) adalah protokol komunikasi dalam jaringan komputer yang digunakan untuk mengirim data secara andal dan teratur antar perangkat. Berbeda dengan UDP, TCP memastikan bahwa data yang dikirim sampai ke tujuan dengan lengkap dan dalam urutan yang benar melalui proses pengecekan, pengiriman ulang jika terjadi kesalahan, serta adanya koneksi antara pengirim dan penerima.

## 6.2 Menangkap Tansfer TCP dalam Jumlah Besar dari Komputer Pribadi ke Remote Server

Menangkap transfer TCP dalam jumlah besar dari komputer ke server jarak jauh merupakan proses mengamati dan merekam lalu lintas data yang dikirim melalui protokol TCP dari perangkat lokal ke server tujuan dengan bantuan tools seperti Wireshark.

Dalam proses ini, Wireshark berfungsi untuk menangkap paket-paket TCP yang melintas di jaringan, lalu menampilkannya secara rinci, seperti alamat IP pengirim dan penerima, nomor port, hingga isi data yang ditransmisikan.

Dengan melakukan capture dalam jumlah besar, kita bisa melakukan analisis terhadap kinerja jaringan, menemukan gangguan seperti packet loss atau keterlambatan (delay), serta mendeteksi adanya aktivitas yang tidak wajar atau mencurigakan pada koneksi antara komputer dan server.

1. buka link " http://gaia.cs.umass.edu/wireshark-labs/alice.txt" pada browser, lalu save dengan cara click kanan lalu pilih save as
<img width="1814" height="920" alt="image" src="https://github.com/user-attachments/assets/4da23074-7503-4a86-aed9-bc88e296f90a" />

2. Seetelahnya buka link "http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html"
<img width="1139" height="577" alt="image" src="https://github.com/user-attachments/assets/9d0a09c0-c0fc-4c3f-9f08-58b6046c9c93" />

3. Setelah itu pilih file yang sudah di save tadi dan upload, Setelah upload maka akan muncul seperti di gambar
<img width="1900" height="989" alt="image" src="https://github.com/user-attachments/assets/21693580-60f0-4b32-9fb7-277d476350d3" />


4. hentikan proses capture di Wireshark terlebih dahulu. Setelah itu, ketik tcp pada kolom pencarian (search bar) supaya yang ditampilkan hanya paket dengan protokol TCP.
<img width="1235" height="44" alt="image" src="https://github.com/user-attachments/assets/7c5f31d1-43ba-43b9-81ac-cf7c7c4e73d7" />

Paket SYN digunakan untuk memulai koneksi TCP antara client dan server melalui proses three-way handshake, bukan untuk mengirim file. Tujuannya adalah memastikan bahwa koneksi sudah siap sebelum data benar-benar dikirim.

Setelah koneksi berhasil terbentuk, barulah file dikirim dalam bentuk beberapa segmen kecil melalui TCP. Hal ini dilakukan karena TCP membagi data menjadi bagian-bagian yang lebih kecil agar proses pengiriman menjadi lebih efisien dan lebih mudah dikontrol.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5688f682-6030-4dbd-9546-3596bb4cb04a" />
Setelah proses upload selesai, server akan memberikan respon HTTP/1.1 200 OK. Respon ini menunjukkan bahwa file telah berhasil diterima dan diproses oleh server.

## 6.3 Tampilan Awal pada Captured Trace

## Pertanyaan
1. Berapa alamat IP dan nomor port TCP yang digunakan oleh komputer klien (sumber) untuk mentransfer file ke gaia.cs.umass.edu? Cara paling mudah menjawab pertanyaan ini adalah dengan memilih sebuah pesan HTTP dan meneliti detail paket TCP yang digunakan untuk membawa pesan HTTP tersebut.
2. Apa alamat IP dari gaia.cs.umass.edu? Pada nomor port berapa ia mengirim dan menerima segmen TCP untuk koneksi ini?
3. Berapa alamat IP dan nomor port TCP yang digunakan oleh komputer klien Anda (sumber) untuk mentransfer ke gaia.cs.umass.edu?

## Jawaban

1. Alamat IP komputer klien yang digunakan untuk mentransfer file ke gaia.cs.umass.edu adalah 10.225.197.205 dengan nomor port TCP 56333.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9844423e-09f6-4349-9a9b-83026f1db04a" />

2. Alamat IP dari gaia.cs.umass.edu adalah 128.119.245.12 dan server tersebut menggunakan port TCP 80 untuk mengirim dan menerima segmen TCP pada koneksi ini.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ae2ad143-7b28-40f5-8408-22d74462ef6f" />

3. Alamat IP komputer klien saya adalah 10.225.197.205 dan menggunakan nomor port TCP 56333 untuk mentransfer data ke gaia.cs.umass.edu.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5dc361e1-012f-4c9b-9447-413927b912ec" />
