# Modul 12

<div align="justify"> Sebelum melakukan implementasi pada ICMP terlebih dahulu mengetahui apa sebenarnya ICMP itu? jadi icmp itu singkatan dari internet control message protocol dimana ini adalah protokol jaringan yang digunakan perangkat dan router untuk mengirimkan pesan kesalahan dan informasi operasional. Protokol ini bekerja di balik layar agar paket data mencapai tujuan dan mendiagnosis masalah koneksi.</div>
<br>

1. **Fungsi ICMP**
   - Digunakan untuk mendeteksi adanya masalah dalam jaringan.
   - Membantu melakukan pelacakan atau monitoring alur koneksi di setiap titik jaringan.
   - Memberikan notifikasi apabila paket data terlalu lama berada di dalam jaringan sebelum mencapai tujuan.

2. **Bagaimana cara kerja ICMP**
<div align="justify">ICMP merupakan protokol tanpa koneksi karena ia tidak terkait dengan protokol lapisan transport seperti TCP dan UDP. jadi satu perangkat tidak perlu membuka koneksi dengan perangkat lain sebelum mengirim pesan ICMP. Lalu lintas IP normal dikirim menggunakan TCP, yang berarti setiap dua perangkat yang bertukar data pertama akan melakukan hand shake TCP untuk memastikan kedua perangkat siap menerima data. ICMP tidak membuka koneksi dengan cara itu.</div>

# A. Pesan ICMP yang dihasilkan oleh program Ping.

<div align="justify"> Langkah pertama untuk mengimplementasikan pesan ICMP yang dihasilkan program ping adalah membuka command terminal windows. kemudian mengetikkan syntax yait ping 8.8.8.8 atau jika ingin melihat hanya beberapa baris berarti syntax yang digunakan harus lebih spesifik. contohnya adalah ping -n 10 8.8.8.8 dimana -n itu adalah merupakan batas maksimal yang dapat dijalankan oleh terminal sedangkan 10 adalah nilai atau jumlah x yang ingin ditentukan seberapa banyak baris untuk ngetrack pesan pingnya. seperti pada contoh gambar dibawah ini terdapat beberapa pesan yang sempurna atau jaringan sedang berjalan dengan normal tanpa terjadi request time out yang berarti beberapa data hilang.</div>
</br>
<div align="justify">untuk ICMP sendiri ia dibagi menjadi dua tugas yaitu ICMP Echo Request tipe 8 yang dimana pesan yang dikirim oleh komputer ke perangkat tujuan untuk mengecek apakah perangkat tersebut aktif dan terhubung. dan yang kedua adalah ICMP Echo Reply tipe 0 dimana ini merupakan pesan balasan yang dikirim balik oleh perangkat tujuan ke komputer, yang menandakan bahwa perangkat itu menerima permintaan.</div>
    <img width="937" height="386" alt="image" src="https://github.com/user-attachments/assets/c4846633-8158-41da-b5cc-0ef72c37145b" />
    <img width="936" height="313" alt="image" src="https://github.com/user-attachments/assets/10720a77-1bf7-4699-8b7a-111692530cdd" />

<div align="justify"> Selanjutnya jika dilihat melalui wireshark maka akan terdapat beberapa track dimana masing - masing track tersebut menerangkan reply dan request jika misal melihat koneksi sebanyak 10 maka total baris yang akan keluar adalah 20 dimana 10 milik request dan 10 lagi milik reply.</div>
    <img width="936" height="317" alt="image" src="https://github.com/user-attachments/assets/37ec86f3-1f79-477d-9d28-233e016d013b" />

# B. Pesan ICMP yang dihasilkan oleh program Traceroute.

<div align="justify"> Selanjutnya dilakukan implementasi tracert (traceroute) menggunakan Command Prompt (CMD) dan juga Wireshark untuk melihat proses perjalanan paket dalam jaringan.
Pada proses pengecekan rute jaringan, traceroute menghasilkan dan menerima dua jenis pesan utama dari protokol ICMP (Internet Control Message Protocol), yaitu Time Exceeded dan Destination Unreachable.
Pesan Time Exceeded dikirim oleh setiap router yang dilewati ketika nilai Time To Live (TTL) pada paket telah habis (mencapai 0). Router kemudian menghapus paket tersebut dan mengirimkan pesan kembali ke pengirim untuk menunjukkan posisi router dalam jalur pengiriman.
Sementara itu, Destination Unreachable muncul ketika paket sudah mencapai host tujuan akhir atau ketika tujuan tidak dapat dijangkau oleh jaringan. Dalam kondisi ini, sistem akan memberikan notifikasi bahwa alamat tujuan tidak bisa diakses.
Dengan demikian, setiap kali paket kehabisan TTL di sepanjang jalur, router akan membuang paket tersebut dan mengirimkan respons berupa ICMP Time-to-Live Exceeded kembali ke pengirim.</div>
    <img width="938" height="307" alt="image" src="https://github.com/user-attachments/assets/0663f9a0-6331-420f-bd06-b0501a8db41c" />

# C. format dan isi pesan ICMP.

<div align="justify"></div>

| Type               | Panjang | Deskripsi                                                                                                                                        |
| ------------------ | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Type               | 8 bit   | Menentukan jenis atau kategori utama dari pesan ICMP yang dikirimkan.                                                                            |
| Code               | 8 Bit   | Memberikan informasi atau sub-kategori yang lebih spesifik mengenai Type. kalau Type adalah gambaran umumnya, maka Code adalah alasan detailnya. |
| CheckSum           | 16 bit  | Digunakan untuk mendeteksi apakah terjadi kerusakan paket selama proses transmisi.                                                               |
| Rest of the header | 32 bit  | Bagian header tambahan yang isinya bervariasi tergantung pada nilai Type dan Code yang digunakan.                                                |
| Data Section       | Dynamic | Tempat diletakkannya muatan utama yaitu payload atau informasi tambahan dari pesan ICMP.                                                         |
