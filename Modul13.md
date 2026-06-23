# MODUL 13 

**ARP (Address Resolution Protocol)** 
adalah protokol jaringan yang berfungsi untuk menerjemahkan atau mencocokkan alamat **IP Address** menjadi **MAC Address** pada jaringan lokal (LAN).

ARP bekerja ketika sebuah perangkat ingin mengirim data ke perangkat lain dalam satu jaringan, tetapi hanya mengetahui alamat IP tujuan. Melalui proses ARP, perangkat akan mencari dan memperoleh MAC Address yang sesuai dengan IP tersebut, sehingga data dapat dikirim ke perangkat yang tepat pada jaringan.

Dengan demikian, ARP memiliki peran penting dalam komunikasi jaringan karena setiap pengiriman data pada **data link layer** membutuhkan MAC Address sebagai tujuan akhir pengiriman.

## Cara Kerja ARP

1. Perangkat sumber mengetahui alamat IP tujuan, tetapi belum mengetahui MAC Address tujuan.
2. Perangkat sumber memeriksa ARP Cache untuk melihat apakah MAC Address tujuan sudah tersimpan.
3. Jika tidak ditemukan, perangkat mengirim ARP Request secara broadcast ke seluruh perangkat dalam jaringan lokal.
4. ARP Request berisi pertanyaan mengenai siapa pemilik alamat IP yang dituju.
5. Perangkat yang memiliki alamat IP tersebut akan mengirim ARP Reply yang berisi MAC Address miliknya.
6. Perangkat sumber menerima ARP Reply dan menyimpan pasangan IP Address – MAC Address ke dalam ARP Cache.
7. Setelah MAC Address tujuan diketahui, perangkat sumber dapat mengirimkan data ke perangkat tujuan melalui jaringan.
8. Untuk komunikasi berikutnya, perangkat dapat menggunakan informasi yang tersimpan di ARP Cache tanpa perlu mengirim ARP Request lagi selama data tersebut masih valid.

## Langkah-Langkah

1. Buka cmd lalu run as administrator, setekah itu jalankan perintah arp -d * pada cmd untuk menghapus semua dapat yang tersimpan pada ARP Cache
<img width="270" height="52" alt="image" src="https://github.com/user-attachments/assets/79e52d84-8056-49de-9c3b-6450b58cbf1e" />

2. Buka wireshark lalu pilih Analyze → Enabled Protocols → IPv4
<img width="1257" height="651" alt="image" src="https://github.com/user-attachments/assets/6e6b364a-e02d-4840-937e-b1c9f079d108" />

3. Start capture wireshark
4. Setelah start capture buka website "http://gaia.cs.umass.edu/wireshark-labs/HTTP-ethereal-lab-file3.html"
5. Setelah membuka website tersbeut stop capture pada wireshark
6. Ketik "arp" pada seach bar
<img width="1918" height="468" alt="image" src="https://github.com/user-attachments/assets/a06e364f-9258-4138-8224-4c18b36f0cda" />

7. Pilih salah satu packet untuk di analisis
<img width="1326" height="702" alt="image" src="https://github.com/user-attachments/assets/eb26bfa5-96c8-4573-b25d-cc8ba618fd7a" />

Berdasarkan hasil capture pada Wireshark, paket yang diamati merupakan **ARP Request (Opcode = request/1)**. Perangkat dengan IP Address **10.144.53.2** dan MAC Address **f6:54:f7:de:c3:69** mengirimkan permintaan untuk mencari MAC Address dari perangkat dengan IP Address **10.144.53.204**.

Karena MAC Address tujuan belum diketahui, maka nilai **Target MAC Address** masih bernilai **00:00:00:00:00:00**. Pada bagian informasi terlihat pesan *“Who has 10.144.53.204? Tell 10.144.53.2”*, yang menunjukkan bahwa perangkat **10.144.53.2** sedang meminta identitas pemilik IP tersebut.

Setelah itu, perangkat dengan IP **10.144.53.204** memberikan balasan berupa **ARP Reply** dengan informasi *“10.144.53.204 is at b8:1e:a4:96:65:57”*, yang berarti IP tersebut telah berhasil dipetakan ke MAC Address yang sesuai.

Dari hasil ini dapat disimpulkan bahwa protokol ARP berfungsi untuk menerjemahkan atau mencocokkan alamat IP Address ke MAC Address, sehingga komunikasi antar perangkat dalam jaringan lokal dapat berjalan dengan benar.
