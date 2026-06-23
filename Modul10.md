# Laporan Jaringan Komputer Informatika Week 10

# A. Apa itu IP Address
<div align="justify">IP address adalah alamat unik yang digunakan oleh setiap perangkat agar dapat saling terhubung dalam sebuah jaringan, sehingga memungkinkan terjadinya komunikasi antar perangkat.Sebagai contoh implementasi, kita dapat memeriksa alamat IP melalui terminal dengan menggunakan perintah “ipconfig”. Hasil yang ditampilkan menunjukkan bahwa perangkat saat ini mendapatkan IP secara otomatis dari access point atau DHCP yang berasal dari ONT. Contohnya adalah alamat IP 192.168.1.13.</div>
    <img width="752" height="402" alt="image" src="https://github.com/user-attachments/assets/ee842988-892f-45b1-88ee-b12a3b7507c2" />


# B. Traceroute dari suatu website
<div align="justify">Selanjutnya adalah mencoba untuk traceroute suatu website. disini sebagai salah satu contoh yang dimuat adalah website dari gaia.cs.umass.edu. traceroute sendiri itu merupakan  melacak jalur atau rute paket data dari komputer ke tujuan. dengan menunjukan setiap hop yang dilewati. seperti pada gambar dibawah ini titik yang terhubung adalah dari resources.indosat selain itu juga ada atlas.cogentco. agar lebih faham mengenai route beberapa implementasi website yang bisa dipaparkan seperti dibawah ini. dan satu lagi traceroute juga dapat digunakan untuk mengukur waktu respons di setiap titiknya.</div>
    <img width="752" height="371" alt="image" src="https://github.com/user-attachments/assets/74f3f1bd-4ed8-4a91-967a-89f8f5be4d9b" />
    <img width="742" height="163" alt="image" src="https://github.com/user-attachments/assets/a888e32d-4d68-451e-87b5-f4f4f641378d" />

# C. apa itu ICMP, MTU, dan TTL
<div align="justify">Selanjutnya adalah selain mempelajari IP terdapat beberapa istilah lainnya seperti ICMP yang merupakan protokol lapisan jaringan yang digunakan oleh perangkat jaringan untuk mengirim pesan kesalahan. contoh yang biasa diterapkan biasanya adalah ping atau seperti sebelumnya yaitu traceroute.</div>
<br>
<div align="justify">lalu ada MTU atau kepanjangannya adalah maximum transmission unit. dimana ini merupaka ukuran terbesar dari frame atau paket data yang dapat dikirimkan melalui koneksi jaringan. biasanya fungsinya adalah mengatur ukuran paket agar sesuai dengan kapasitas perangkat keras yang dimiliki.</div>
<br>
<div align="justify"> Dan terakhir ada Time to Live ini merupakan paket data yang menentukan berapa lama atau berapa banyak hop paket itu diizinkan di jaringan. biasanya ini digunakan untuk mencegah paket data berputar tanpa akhir di jaringan jika terjadi kesalahan rute. berikut dibawah ini contoh implementasi untuk melihat ICMP dari file yang sudah disediakan sebelumnya. seperti pada gambar dibawah didapat salah satu paket dengan ttl dengan bernilai 3 yang berarti bahwa paket Echo atau ping request tersebut dikirim dengan batasan 3 hop.</div>
    <img width="748" height="402" alt="image" src="https://github.com/user-attachments/assets/368231a0-c988-4dd6-9a2e-408baba2de79" />


# D. Mencari Contoh Fragmentasi di Wireshark
<div align="justify"> Selanjutnya adalah memuat contoh untuk fragmentasi dalam wireshark dengan menggunakan fitur filter. berikut dibawah ini implementasi yang bisa dibuat.</div>
    <img width="752" height="258" alt="image" src="https://github.com/user-attachments/assets/d8a9cc98-d87b-499c-be51-8ada64e3fcb1" />
<div align="justify"> Untuk mengetahui fragmentasi pada wireshark yang bisa dilakukan adalah memuat ping pada cmd dengan besar byte yang dikirim diatas 1500, sebagai contoh yang dibuat disini saya set 1600 pada google. dan muncul seperti pada dibawah ini.</div>
    <img width="748" height="122" alt="image" src="https://github.com/user-attachments/assets/f1e95d05-4f65-44f2-a99e-5b530517b18c" />
    
# E. Mencari IPv6 di Wireshark
<div align="justify">Selanjutnya adalah mencoba mencari IPv6 di wireshark setelah melakukan penerapannya dengan menggunakan filter "ipv6". dengan menggunakan file sample yang diberikan. terdapat beberapa source dan destination yang terbaca setelah melakukan filter tersebut.</div>
    <img width="751" height="377" alt="image" src="https://github.com/user-attachments/assets/655f7c11-262c-4d42-9526-c48e1edbcbfd" />
