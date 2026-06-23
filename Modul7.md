# Modul 7 SOCKET PROGRAMMING

Socket programming adalah metode pemrograman yang memungkinkan dua aplikasi atau lebih berkomunikasi melalui jaringan dengan menggunakan socket sebagai media penghubung. Komunikasi ini memanfaatkan alamat IP dan nomor port untuk mengidentifikasi perangkat dan layanan yang terlibat. Umumnya, socket programming menerapkan arsitektur client-server, di mana client mengirimkan permintaan dan server memberikan respons. Dalam implementasinya, komunikasi dapat menggunakan protokol TCP yang menjamin keandalan pengiriman data atau UDP yang menawarkan kecepatan lebih tinggi tetapi tanpa jaminan pengiriman data yang sempurna.
# TCP

TCP (Transmission Control Protocol) adalah protokol komunikasi pada jaringan yang bersifat connection-oriented, artinya koneksi harus dibangun terlebih dahulu sebelum data dikirim. TCP memastikan data sampai dengan aman, lengkap, dan dalam urutan yang benar, sehingga banyak digunakan pada aplikasi seperti web, email, dan transfer file.

## TCP Client

```
from socket import *

serverName = "localhost"
serverPort = 12000

clientSocket = socket(AF_INET, SOCK_STREAM)

clientSocket.connect(
    (serverName, serverPort)
)

print("[SYSTEM] Masukan pesan")

running = True
while running:

    message = input("> ")

    clientSocket.send(message.encode())

    if message.lower() == "exit" :
        print("[SYSTEM] Keluar dari program")
        running = False
        break

    modifiedMessage = clientSocket.recv(2048)

    print("[SERVER] pesan: ", modifiedMessage.decode())

clientSocket.close()
print("[SYSTEM] socket ditutup")
```

## TCP Server
```
from socket import *

serverPort = 12000
serverSocket = socket(AF_INET, SOCK_STREAM)

serverSocket.bind(
    ('', serverPort)
)

serverSocket.listen(1)
print("[SYSTEM] server TCP siap digunakan")

running = True
while running: 
    
    connectionSocket, addr = serverSocket.accept()

    while True:
        message = connectionSocket.recv(2448).decode()

        if not message:
            break

        if message.lower() == "exit":
            print("[SYSTEM] client ingin keluar")
            running = False
            break

        modifiedMessage = message.upper()
        print("[SERVER] diterima: ",modifiedMessage)

        connectionSocket.send(
            modifiedMessage.encode()
        )
        
    connectionSocket.close()

serverSocket.close()
```
## Langkah - Langkah

<img width="1302" height="212" alt="image" src="https://github.com/user-attachments/assets/67f82f65-e142-4a97-99f8-8fc86e115126" />


1. Run server melalui terminal
2. Lalu run client melalui terminal juga
3. setelah client di run maka server menerima koneksi dari client
4. lalu client mengirim pesan dan pesan tersebut masuk ke server
5. server menampilkan hasil pesan dari client
6. jika client mengirim pesan "exit" maka koneksi server dan client otomatis terhenti

# UDP

UDP (User Datagram Protocol) adalah protokol komunikasi jaringan yang bersifat connectionless, artinya data dapat dikirim tanpa harus membangun koneksi terlebih dahulu. UDP lebih cepat dibanding TCP, tetapi tidak menjamin data sampai, tidak urut, dan bisa hilang di tengah jalan. Karena itu, UDP biasanya digunakan pada aplikasi yang membutuhkan kecepatan tinggi seperti streaming, game online, dan video call.

## UDP Client
```
from socket import *

serverName = "localhost"
serverPort = 12000

clientSocket = socket(AF_INET, SOCK_STREAM)
clientSocket.connect((serverName, serverPort))

print("[SYSTEM] Masukkan pesan")

while True:
    message = input("> ")

    if not message:
        continue

    clientSocket.send(message.encode())

    if message.lower() == "exit":
        print("Perintah exit dikirim. Menutup koneksi...")
        break
    elif message.lower() == "keluar":
        print("Menutup klien...")
        break

    try:
        modifiedMessage = clientSocket.recv(2048)
        print(f"[SERVER] {modifiedMessage.decode()}\n")
    except timeout:
        print("Kesalahan: Server tidak merespons (Timeout)\n")

clientSocket.close()
print("[SYSTEM] socket ditutup")
```

## UDP Server
```
from socket import *

serverPort = 12000
serverSocket = socket(AF_INET, SOCK_STREAM)

serverSocket.bind(('', serverPort))
serverSocket.listen(1)

print("[SYSTEM] Server siap digunakan")

running = True
while running:
    connectionSocket, clientAddress = serverSocket.accept()
    print(f"[SYSTEM] Terhubung dengan {clientAddress[0]}:{clientAddress[1]}")

    while True:
        message = connectionSocket.recv(2048)

        if not message:
            break

        original_message = message.decode().strip()

        if original_message.lower() == 'exit':
            print("[SYSTEM] Mematikan server...")
            running = False
            break

        modifiedMessage = original_message.upper()

        print(f"Diterima dari {clientAddress[0]}:{clientAddress[1]}: {original_message}")
        print(f"Mengirim balik: {modifiedMessage}")

        connectionSocket.send(modifiedMessage.encode())

    connectionSocket.close()

serverSocket.close()
print("[SYSTEM] Server ditutup")
```

## Langkah - Langkah

<img width="497" height="131" alt="image" src="https://github.com/user-attachments/assets/63abc4ff-e20a-41e5-acba-a4f15b40db24" />
<img width="300" height="178" alt="image" src="https://github.com/user-attachments/assets/964f9afc-dc8f-4d6c-84e8-da7e6abe6a35" />


1. Run server
2. lalu run client nya
3. client mengirim pesan ke server
4. server akan mengirim pesan ke client dan di ubah menjadi huruf besar semua
5. jika ingin keluar maka ketik "exit"

# Perbedaan TCP dan UDP

Perbedaan utama TCP dan UDP terletak pada cara pengiriman datanya.

TCP (Transmission Control Protocol) bersifat connection-oriented, artinya harus membangun koneksi terlebih dahulu sebelum mengirim data. TCP menjamin data sampai dengan lengkap, urut, dan tanpa duplikasi, tetapi kecepatannya lebih lambat karena ada proses pengecekan.

Sedangkan UDP (User Datagram Protocol) bersifat connectionless, sehingga data bisa langsung dikirim tanpa koneksi. UDP lebih cepat, tetapi tidak menjamin data sampai, tidak urut, dan bisa hilang.

Singkatnya, TCP digunakan ketika keamanan dan keakuratan data penting (seperti web dan email), sedangkan UDP digunakan ketika kecepatan lebih diutamakan (seperti game online dan streaming).
