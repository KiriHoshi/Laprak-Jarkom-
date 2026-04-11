Nama : Gevin Shinarsa Pratama

NIM : 103072400080

Kelas : IF - 04 -05

# Modul 5 UDP
UDP (User Datagram Protocol) adalah salah satu protokol komunikasi dalam jaringan komputer yang digunakan untuk mengirim data antar perangkat dengan cara yang cepat dan sederhana. Berbeda dengan protokol lain seperti TCP, UDP tidak melakukan pengecekan apakah data yang dikirim berhasil sampai atau tidak, sehingga tidak ada proses konfirmasi, pengurutan, atau perbaikan data yang hilang.

## Langkah - Langkah

1. Download file dari link berikut http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip
2. extrack file yang sudah di download dari link tersebut
<img width="758" height="93" alt="image" src="https://github.com/user-attachments/assets/ef0dbe1d-d226-4bb3-892a-56bddf5787db" />

3. Setelah di extract pilih file bernama "http-ethereal-trace-5" dan buka menggunakan wireshark
<img width="750" height="39" alt="image" src="https://github.com/user-attachments/assets/8a689ce5-c6b6-4d8b-a52f-0e01dbcb970d" />

4. Setelah membuka file nya menggunakan wireshark ketik udp pada kolom filter agar terfilter.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c85daad8-6744-47a0-92ee-6d961c1bd0d6" />

## Pertanyaan

1. Pilih satu paket UDP yang terdapat pada trace Anda. Dari paket tersebut, berapa banyak “field” yang terdapat pada header UDP? Sebutkan nama-nama field yang Anda temukan!
2. Perhatikan informasi “content field” pada paket yang Anda pilih di pertanyaan 1. Berapa panjang (dalam satuan byte) masing-masing “field” yang terdapat pada header UDP?
3. Nilai yang tertera pada ”Length” menyatakan nilai apa? Verfikasi jawaban Anda melalui paket UDP pada trace.
4. Berapa jumlah maksimum byte yang dapat disertakan dalam payload UDP? (Petunjuk: jawaban untuk pertanyaan ini dapat ditentukan dari jawaban Anda untuk pertanyaan 2)
5. Berapa nomor port terbesar yang dapat menjadi port sumber? (Petunjuk: lihat petunjuk pada pertanyaan 4)
6. Berapa nomor protokol untuk UDP? Berikan jawaban Anda dalam notasi heksadesimal dan desimal. Untuk menjawab pertanyaan ini, Anda harus melihat ke bagian ”Protocol” pada datagram IP yang mengandung segmen UDP.
7. Periksa pasangan paket UDP di mana host Anda mengirimkan paket UDP pertama dan paket UDP kedua merupakan balasan dari paket UDP yang pertama. (Petunjuk: agar paket kedua merupakan balasan dari paket pertama, pengirim paket pertama harus menjadi tujuan dari paket kedua). Jelaskan hubungan antara nomor port pada kedua paket tersebut!

## Jawaban

1.Pada paket UDP yang dipilih dari hasil trace, terdapat empat bagian utama pada header UDP, yaitu Source Port, Destination Port, Length, dan Checksum.

Source Port menunjukkan port asal pengirim data
Destination Port menunjukkan port tujuan penerima
Length berisi ukuran total paket UDP
Checksum digunakan untuk memastikan data tidak mengalami kerusakan selama pengiriman

Keempat field ini berfungsi untuk mengatur proses pengiriman data agar sampai ke tujuan dengan benar
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e7741b0a-a2af-4f4c-a464-ec9f544334b5" />

2. Pada header UDP, setiap field memiliki ukuran yang sudah tetap. Source Port berukuran 2 byte, Destination Port juga 2 byte, Length sebesar 2 byte, dan Checksum sebesar 2 byte. Dengan demikian, jika dijumlahkan, total ukuran header UDP adalah 8 byte.

3. Nilai yang terdapat pada field Length di header UDP menunjukkan total ukuran paket UDP dalam satuan byte, yaitu hasil penjumlahan antara header UDP dan data (payload).

Berdasarkan hasil verifikasi dari paket pada trace, diperoleh nilai Length = 58 byte. Dari jumlah tersebut, 8 byte merupakan ukuran header UDP, sedangkan 50 byte sisanya adalah data (payload). Hal ini sesuai dengan informasi yang ditampilkan, yaitu UDP payload (50 bytes).
<img width="961" height="340" alt="Screenshot 2026-04-10 235624" src="https://github.com/user-attachments/assets/ca9f976e-62be-4d4b-989d-cc3b6d691825" />

4. Ukuran maksimum payload UDP dapat ditentukan dari batas nilai pada field Length. Karena field ini memiliki ukuran 2 byte (16 bit), maka nilai maksimal yang bisa direpresentasikan adalah 65.535 byte.

Namun, nilai tersebut sudah mencakup keseluruhan paket UDP, termasuk header yang berukuran 8 byte. Oleh karena itu, untuk mendapatkan ukuran maksimum payload, perlu dikurangi dengan ukuran header:

65.535 − 8 = 65.527 byte

Dengan demikian, jumlah maksimum data (payload) yang dapat dikirim dalam satu paket UDP adalah 65.527 byte.

5. Nomor port terbesar yang dapat menjadi port sumber pada UDP adalah 65.535, karena field Source Port memiliki ukuran 2 byte (16 bit), sehingga nilai maksimum yang dapat direpresentasikan adalah 2¹⁶ − 1 = 65.535.

6. Nomor protokol UDP yang terlihat pada bagian Protocol di IP adalah 17 (desimal), yang jika ditulis dalam bentuk heksadesimal menjadi 0x11.
<img width="629" height="306" alt="image" src="https://github.com/user-attachments/assets/c06380a8-9445-4d21-9071-e39ba1e84a9f" />

7. Pada pasangan paket UDP, bahwa nomor port pada paket balasan merupakan kebalikan dari paket pertama. Paket pertama dikirim dari port 4337 ke port 161, sedangkan pada paket balasannya berubah menjadi dari port 161 ke port 4337. Port sumber dan port tujuan saling bertukar antara paket pertama dan paket balasan agar komunikasi antar kedua host bisa berlangsung dengan benar.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/82974289-eea8-4d93-8faf-6613ea23f2e3" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e93ae0b2-bab9-48fa-b8a9-5f9c954ae5e9" />
