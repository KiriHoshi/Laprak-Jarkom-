# Modul 11

# A. Apa itu DHCP ?

<div align="justify">Sebelum memahami DHCP, penting untuk mengetahui kepanjangannya terlebih dahulu, yaitu Dynamic Host Configuration Protocol. DHCP banyak digunakan pada jaringan LAN untuk memberikan alamat IP secara otomatis melalui router atau server DHCP, sehingga dapat mengurangi risiko terjadinya konflik IP antar perangkat klien.

Berikut contoh implementasinya, yaitu dengan melihat IP yang diberikan oleh router pada jaringan LAN. Caranya adalah dengan membuka Network Connection dan memilih jaringan yang sedang terhubung. Dari hasil tersebut, perangkat akan mendapatkan alamat IP, misalnya 10.218.6.166, dengan DNS server 10.217.7.77.</div>
    <img width="937" height="308" alt="image" src="https://github.com/user-attachments/assets/10db30c6-be8b-4362-b3ab-9a6b69aa898e" />
    <img width="936" height="312" alt="image" src="https://github.com/user-attachments/assets/e3cf8b38-3985-4121-9760-d4f4dbaa6a03" />

# B. Kelebihan dan Kekurangan DHCP ?

<div align="justify"> Terdapat beberapa kelebihan dan kekurangan DHCP sendiri yaitu, kelebihannya adalah ia bisa memanajemen IP sehingga client dapat IP mereka masing - masing tanpa harus mengkhatirkan terjadinya tabrakan IP, dapat meningkatkan efisiensi jaringan karena dapat mengatur prefixnya sehingga tidak boros, Otomatisasi Konfigurasi Jaringan jadi setiap client tidak perlu lagi repot - repot untuk memasukkan IP secara manual, dan terakhir adalah pengelolaannya secara terpusat.</div>
<br>
<div align="justify"> ada juga kekurangan yang dimiliki oleh fitur DHCP sendiri ini adalah terkadang penanganannya sangat kompleks jika topologi yang dikerjakan sangat besar, kemudian ketergantungan pada server jika server saat itu sedang down maka client yang menginginkan IP tidak dapat terhubung, dan terakhir adalah alamat IP dapat berubah - ubah / dinamis pada setiap kali reconnect ini sangat tidak cocok apabika berhubungan dengan IoT yang memerlukan IP secara static.</div>

# C. DORA ?

<div align="justify"> Tahap terakhir dalam proses DORA adalah DHCP (Dynamic Host Configuration Protocol), yaitu mekanisme komunikasi antara client dan server dalam memberikan alamat IP secara otomatis.

Proses pertama dimulai dari Discover, yaitu ketika client mencari DHCP server dengan mengirimkan pesan broadcast. Pada tahap ini, destination address yang digunakan adalah 0.0.0.0, sedangkan broadcast address adalah 255.255.255.255.

Selanjutnya adalah tahap Offer, di mana server merespons dengan memberikan penawaran alamat IP kepada client. Setelah itu masuk ke tahap Request, yaitu ketika client mengajukan permintaan atau menyetujui IP yang ditawarkan oleh server.

Tahap terakhir adalah ACK (Acknowledgment), yaitu server mengirimkan konfirmasi bahwa alamat IP tersebut telah resmi dialokasikan dan disewakan kepada client. </div>
    <img width="937" height="307" alt="image" src="https://github.com/user-attachments/assets/2468b7a7-d031-4363-b514-ad7e4c547989" />
