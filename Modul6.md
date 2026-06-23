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

## 6.4 Dasar TCP

## Pertanyaan

1. Berapa nomor urut segmen TCP SYN yang digunakan untuk memulai sambungan TCP antara komputer klien dan gaia.cs.umass.edu? Apa yang dimiliki segmen tersebut sehingga teridentifikasi sebagai segmen SYN? 
2. Berapa nomor urut segmen SYNACK yang dikirim oleh gaia.cs.umass.edu ke komputer klien sebagai balasan dari SYN? Berapa nilai dari field Acknowledgement pada segmen SYNACK? Bagaimana gaia.cs.umass.edu menentukan nilai tersebut? Apa yang dimiliki oleh segmen sehingga teridentifikasi sebagai segmen SYNACK? 
3. Berapa nomor urut segmen TCP yang berisi perintah HTTP POST? Perhatikan bahwa untuk menemukan perintah POST, Anda harus menelusuri content field milik paket di bagian bawah jendela Wireshark, kemudian cari segmen yang berisi "POST" di bagian field DATAnya. 
4. Anggap segmen TCP yang berisi HTTP POST sebagai segmen pertama dalam koneksi TCP. Berapa nomor urut dari enam segmen pertama dalam TCP (termasuk segmen yang berisi HTTP POST)? Pada jam berapa setiap segmen dikirim? Kapan ACK untuk setiap segmen diterima? Dengan adanya perbedaan antara kapan setiap segmen TCP dikirim dan kapan acknowledgement-nya diterima, berapakah nilai RTT untuk keenam segmen tersebut? Berapa nilai EstimatedRTT setelah penerimaan setiap ACK? (Catatan: Wireshark memiliki fitur yang memungkinkan Anda untuk memplot RTT untuk setiap segmen TCP yang dikirim. Pilih segmen TCP yang dikirim dari klien ke server gaia.cs.umass.edu pada jendela "daftaraket yang ditangkap". Kemudian pilih: Statistics->TCP Stream Graph- >Round Trip Time Graph). 
5. Berapa panjang setiap enam segmen TCP pertama? 
6. Berapa jumlah minimum ruang buffer tersedia yang disarankan kepada penerima dan diterima untuk seluruh trace? Apakah kurangnya ruang buffer penerima pernah menghambat pengiriman? 
7. Apakah ada segmen yang ditransmisikan ulang dalam file trace? Apa yang anda periksa (di dalam file trace) untuk menjawab pertanyaan ini? 
8. Berapa banyak data yang biasanya diakui oleh penerima dalam ACK? Dapatkah anda mengidentifikasi kasus-kasus di mana penerima melakukan ACK untuk setiap segmen yang diterima? 
9. Berapa throughput (byte yang ditransfer per satuan waktu) untuk sambungan TCP? Jelaskan bagaimana Anda menghitung nilai ini.

# Jawaban

1. Nomor urut (Sequence Number) pada segmen SYN adalah Seq = 0. Segmen ini dikenali sebagai SYN karena pada kolom info terdapat [SYN], yang berarti flag SYN aktif (1) dan digunakan untuk memulai koneksi TCP.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/96ed1df8-b068-48c1-b496-d9a2cff88926" />

2. Nomor urut (Sequence Number) pada segmen SYN-ACK adalah Seq = 0, sedangkan nilai Acknowledgement Number = 1. Nilai Acknowledgement tersebut diperoleh dari nomor urut segmen SYN milik klien (Seq = 0) yang kemudian ditambah 1, karena dalam TCP, segmen SYN dianggap mengonsumsi satu nomor urut. Segmen ini dapat diidentifikasi sebagai segmen SYN-ACK karena pada bagian Flags terlihat [SYN, ACK], yang berarti kedua flag tersebut aktif (set).
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3304d98f-3264-4c73-88da-978bce24213f" />

3. Nomor urut (Sequence Number) segmen TCP yang berisi perintah HTTP POST adalah Seq = 1. Segmen ini ditemukan pada frame nomor 4, yang dapat diidentifikasi dengan melihat isi payload pada bagian data yang mengandung teks "POST /ethereal-labs/lab3-1-reply.htm HTTP/1.1". Selain itu, segmen ini juga memiliki flag [PSH, ACK] dengan panjang data Len = 565 byte, yang menunjukkan bahwa segmen tersebut membawa data aplikasi (HTTP POST).
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9e4e8664-6896-4751-9002-29c06b03f519" />

4. Berdasarkan grafik Round Trip Time pada Wireshark, enam segmen TCP pertama memiliki nilai RTT yang bervariasi, yaitu sekitar 30 ms hingga 180 ms. Nilai RTT diperoleh dari enam titik pertama pada grafik. Waktu pengiriman segmen dilihat pada sumbu waktu, sedangkan waktu penerimaan ACK didapat dari penjumlahan waktu kirim dengan RTT masing-masing segmen. Perbedaan nilai RTT menunjukkan adanya variasi delay pada jaringan. Estimated RTT dihitung menggunakan metode EWMA dengan α = 0,125, di mana nilai awal diambil dari RTT pertama dan diperbarui untuk setiap segmen berikutnya. Hasilnya, Estimated RTT lebih stabil dibandingkan RTT aktual.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/98c6f57c-c148-4f1a-9d60-61a272ecf9e3" />

5. total panjang dari 6 segmen pertama adalah 7865 byte
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ea304c4e-5270-4fb3-9363-9606bd7c1571" />

6. nilai ruang buffer yang tersedia pada sisi penerima adalah sebesar 17520 byte. Nilai ini menunjukkan bahwa penerima memiliki kapasitas buffer yang cukup untuk menerima data dari pengirim. Selama proses komunikasi, tidak terlihat adanya indikasi bahwa buffer penerima menjadi penuh (tidak terdapat nilai window size = 0), sehingga dapat disimpulkan bahwa kekurangan ruang buffer tidak pernah menghambat proses pengiriman data.
<img width="563" height="147" alt="image" src="https://github.com/user-attachments/assets/874c7dc3-25ce-48c0-bcde-bb3eb21509ad" />

7. tidak ditemukan adanya segmen TCP yang ditransmisikan ulang. Hal ini menunjukkan bahwa selama proses komunikasi tidak terjadi kehilangan paket, sehingga pengiriman data berlangsung dengan lancar tanpa perlu pengiriman ulang.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5d2be88e-f251-40b4-9b6c-47193af52d30" />

8. Jumlah data yang diakui oleh ACK tidak selalu sama dan dapat bervariasi. Penerima dapat mengakui beberapa segmen sekaligus dalam satu ACK, sehingga tidak selalu dilakukan untuk setiap segmen secara individual.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/85a3a43b-f282-4682-9e67-3fb7cb9c57aa" />

9. Throughput sambungan TCP pada grafik tersebut berada pada kisaran sekitar 200–250 kbps atau setara dengan ±25–31 KB per detik. Nilai ini diperoleh dengan melihat garis average throughput (warna cokelat) pada sumbu kanan yang menunjukkan nilai stabil di rentang tersebut, kemudian mengonversinya dari kilobit per detik ke byte per detik dengan membagi 8.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6074a54c-a0aa-4958-a9a2-1fc5473ddba4" />

## 6.5 Congestion Control pada TCP
mekanisme untuk mencegah pengirim data membebani jaringan (network overload), yang bertujuan menghindari congestion collapse dan menjamin keadilan (fairness) penggunaan bandwidth. TCP menggunakan algoritma dinamis, terutama Congestion Window (CWND), untuk menyesuaikan laju pengiriman berdasarkan tingkat kemacetan yang dideteksi melalui packet loss atau timeout. 

## Langkah - Langkah dan Pertanyaan

1. Mengidentifikasi slow start dan congestion avoidance 
- Buka file tcp-ethereal-trace-1 menggunakan wireshark
- setelah terbuka ketik "tcp" pada search bar
- click menu stattistic -> tcp stream graph -> Time-Sequence Graph (Stevens) maka akan muncul seperti gambar
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0142d991-4771-42d1-8495-973e86185866" />

- fase slow start dimulai sejak awal transmisi (sekitar t = 0 detik) dan berlangsung hingga kira-kira 0,5 detik, yang ditandai dengan peningkatan sequence number yang semakin cepat. Setelah itu, TCP memasuki fase congestion avoidance, yang terlihat dari pola kenaikan sequence number yang lebih stabil dan cenderung linear hingga akhir pengamatan. Dibandingkan dengan perilaku TCP ideal, hasil pengukuran menunjukkan bahwa fase slow start tidak sepenuhnya eksponensial dan grafik berbentuk bertingkat (staircase), yang disebabkan oleh kondisi jaringan nyata seperti delay, mekanisme ACK, dan variasi RTT.

2. Mengidentifikasi slow start & songestion svoidance (alice.txt)
- buka wireshark lalu pilih wifi
- buka link "http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html" pada browser anda, lalu upload file alice.txt
- setelah itu kembali ke wireshark dan ketik "tcp" pada search bar
- lalu click menu stattistic -> tcp stream graph -> Time-Sequence Graph (Stevens) maka akan muncul seperti gambar
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d2866094-62c0-462a-9748-23a49d16c6d7" />

- Fase slow start tidak tampak jelas seperti pada kondisi ideal, karena sejak awal peningkatan sequence number sudah terlihat bertahap dan tidak menunjukkan pola eksponensial yang kuat. Grafik lebih banyak memperlihatkan pola kenaikan berbentuk bertahap (staircase) dengan jeda waktu yang cukup panjang. Hal ini menunjukkan bahwa TCP hampir sepanjang waktu berada pada fase congestion avoidance atau dibatasi oleh faktor lain, seperti keterbatasan aplikasi atau kondisi jaringan (misalnya latensi Wi-Fi).
Jika dibandingkan dengan perilaku TCP yang ideal, hasil ini cukup berbeda karena tidak terlihat adanya peningkatan cepat pada awal koneksi serta terdapat interval pengiriman data yang relatif lama. Kondisi ini kemungkinan disebabkan oleh laju pengiriman aplikasi yang rendah, latensi jaringan yang tinggi, atau mekanisme flow control yang membatasi pengiriman data.
