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


<div align="justify">Kemudian mencoba menjawab beberapa pertanyaan yang diberikan oleh modul seperti penjelasan dibawah ini.</div>

* **Pertanyaan** 
    * 1. Cari pesan permintaan DNS dan balasannya. Apakah pesan tersebut dikirimkan melalui UDP atau TCP?
    * 2. Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasannya?
    * 3. Pada pesan permintaan DNS, apa alamat IP tujuannya? Apa alamat IP server DNS lokal anda (gunakan ipconfig untuk mencari tahu)? Apakah kedua alamat IP tersebut sama?
    * 4. Periksa pesan permintaan DNS. Apa “jenis” atau ”type” dari pesan tersebut? Apakah pesan permintaan tersebut mengandung ”jawaban” atau ”answers”?
    * 5. Periksa pesan balasan DNS. Berapa banyak ”jawaban” atau ”answers” yang terdapat di dalamnya? Apa saja isi yang terkandung dalam setiap jawaban tersebut?
    * 6. Perhatikan paket TCP SYN yang selanjutnya dikirimkan oleh host Anda. Apakah alamat IP pada paket tersebut sesuai dengan alamat IP yang tertera pada pesan balasan DNS?
    * 7. Halaman web yang sebelumnya diakses www.ietf.org memuat beberapa gambar. Apakah host Anda perlu mengirimkan pesan permintaan DNS baru setiap kali ingin mengakses suatu gambar?

* **Implementasi/Jawaban**
    * 1. Jadi pesan yang dikirimkan oleh server adalah UDP dimana berisikan 30 bytes. seperti ini.

       <img width="445" height="127" alt="image" src="https://github.com/user-attachments/assets/e4401897-02cd-484a-94fc-ce1c0e22e127" />

    * 2. Untuk port tujuan yang diberikan adalah 61566 dengan sumber port yang diberikan yaitu 53.

         <img width="876" height="55" alt="image" src="https://github.com/user-attachments/assets/827d6fb3-f865-421e-8e8f-d67d5a59c6c6" />

    * 3. Jadi setelah melakukan penerapan implementasinya berikut seperti dibawah ini yang bisa dimuat contoh ip lokal yang didapat adalah 10.218.5.217 dimana gatewaynya adalah 10.218.0.253. dan dns milik server tersebut adalah 23.217.163.122. dimana ini merupakan dns yang bisa didapat melalui perantara ISP sedangkan 10.217.7.77 milik lokal.

          <img width="862" height="567" alt="image" src="https://github.com/user-attachments/assets/6c9aea44-09e3-4ae1-935b-d28e1093512d" />

    * 4. Memeriksan DNS dari jenis ataupun type apakah muncul sebuah jawaban. setelah melakukan peneran pada wireshark tidak ditemukannya jawaban atau tampilannya 0 seperti gambar dibawah ini.

         <img width="876" height="248" alt="image" src="https://github.com/user-attachments/assets/755a31d8-7d2d-4b2d-8055-a48597ee778b" />

    * 5. Setelah melakukan implementasi dengan menggunakan beberapa filter terdapat jawaban yang terkandung yaitu name, type, class, ttl, data length, svcpriority, dan terakhir adalah targetname.

          <img width="873" height="215" alt="image" src="https://github.com/user-attachments/assets/7efd8eb5-c872-4b94-a237-f17fd486f7cb" />

    * 6. Iya telah sesuai karena sebelumnya pada saat melakukan pengecekan melalui nslookup alamat 104.16.44.99 adalah salah satu dari Addresses yang diberikan oleh server DNS.

         <img width="871" height="342" alt="image" src="https://github.com/user-attachments/assets/187c0330-3a6c-4c98-b0e5-ce98ff7438ec" />

    * 7.  Tidak karena komputer melakukan lookup pertama kali untuk www.ietf.org, maka hasilnya akan disimpan di dalam DNS Cache lokal. Karena IP-nya diketahui komputer tidak perlu bertanya lagi ke server DNS.
         
        <img width="872" height="195" alt="image" src="https://github.com/user-attachments/assets/dc547d1e-f09e-4438-8482-b1513b2e6570" />

<div align="justify">Selanjutnya adalah menjawab beberapa pertanyaan kembali sesuai dengan arahan modul yaitu mengabaikan  dua pasangan permintaan-balasan pertama karena mereka merupakan paket yang khusus dihasilkan oleh nslookup. kita  cukup fokus pada pesan permintaan dan balasan terakhir. berikut beberapa pertanyaan yang bisa dijawab yaitu.</div>

* **Pertanyaan**
    * 1. Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasan DNS?
    * 2. Ke alamat IP manakah pesan permintaan DNS dikirimkan? Apakah alamat IP tersebut merupakan default alamat IP server DNS lokal Anda?
    * 3. Periksa pesan permintaan DNS. Apa ”jenis” atau ”type” dari pesan tersebut? Apakah pesan tersebut mengandung ”jawaban” atau ”answers”?
    * 4. Periksa pesan balasan DNS. Berapa banyak ”jawaban” atau “answers” yang terdapat di dalamnya. Apa saja isi yang terkandung dalam setiap jawaban tersebut?

* **Jawaban**
    * 1. Iya, keduanya yaitu dari port tujuan dan juga port sumber pada pesan balasan yaitu 53

         <img width="875" height="432" alt="image" src="https://github.com/user-attachments/assets/012bc267-43b2-4677-bcf2-7bccc200ade5" />

    * 2. Alamat IP untuk yang dituju dari permintaan adalah 128.238.29.22 disini alamat IP tidak sama dengan server dns lokal karena harus lewat berbagai dns termasuk ISP sendiri.

        <img width="877" height="271" alt="image" src="https://github.com/user-attachments/assets/cbdd4c1e-cd47-4675-a743-2a6bb55c5fce" />

    * 3. Pesan yang dikirim tersebut hanya menjawab 0 

         <img width="872" height="386" alt="image" src="https://github.com/user-attachments/assets/8491edb3-be1f-4665-bcc3-24bcd4de69ed" />

    * 4. Terdapat beberapa jawaban yang dikirim sesuai dengan gambar seperti name, type dan lain sebagainya.

         <img width="877" height="207" alt="image" src="https://github.com/user-attachments/assets/ddf01c17-4a58-43bc-8d2e-b28c69c73ed3" />


<div align="justify"> Selanjutnya mencoba menjawab pertanyaan kembali sesuai modul yaitu yang pertama adalah Ke alamat IP manakah pesan permintaan DNS dikirimkan? Apakah alamat IP tersebut merupakan default alamat IP server DNS lokal Anda? Alamat IP permintaan DNS dikirimkan di IP 192.168.137.1 yang merupakan alamat IP server DNS lokal</div>
<div align="justify"> - </div>
<div align="justify"> Selanjutnya pertanyaan Periksa pesan permintaan DNS. Apa ”jenis” atau ”type” dari pesan tersebut? Apakah pesan tersebut mengandung ”jawaban” atau ”answers”? Tidak. Pesan permintaan hanya berisi pertanyaan. Bagian "Answers" atau "Answer RRs" pada paket permintaan selalu bernilai 0. Jawaban muncul pada paket balasan</div>
<div align="justify"> - </div>
<div align="justify"> Kemudian pertanyaan terakhir yaitu Periksa pesan balasan DNS. Apa nama server MIT yang diberikan oleh pesan balasan? Apakah pesan balasan ini juga memberikan alamat IP untuk server MIT tersebut? terdapat beberapa nama server yang diberikan seperti dibawah ini.</div>
   <img width="868" height="562" alt="image" src="https://github.com/user-attachments/assets/1c95b3fb-9a05-458a-a3eb-c2d2c2e27be7" />
<div align="justify"> - </div>
<div align="justify"> Ke alamat IP manakah pesan permintaan DNS dikirimkan? Apakah alamat IP tersebut
merupakan default alamat IP server DNS lokal Anda? Sama seperti sebelumnya yaitu 192.168.137.1 </div>
<div align="justify"> - </div>
<div align="justify">  Periksa pesan permintaan DNS. Apa ”jenis” atau ”type” dari pesan tersebut? Apakah pesan
tersebut mengandung ”jawaban” atau ”answers”? tidak ada jawaban yang diberikan pada permintaan DNS </div>
<div align="justify"> - </div>
<div align="justify"> Periksa pesan balasan DNS. Berapa banyak ”jawaban” atau “answers” yang terdapat di
dalamnya. Apa saja isi yang terkandung dalam setiap jawaban tersebut? Hasil tidak dapat ditemukan karena setelah melakukan pengecekan balasan DNS yang diberikan adalah RTO atau biasa disebut Request Time Out. </div>
     <img width="871" height="305" alt="image" src="https://github.com/user-attachments/assets/ad5d6ce4-a03e-46ab-97af-98a4e3b70369" />
