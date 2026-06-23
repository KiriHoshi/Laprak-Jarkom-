# Modul 9 Web Server

Web server merupakan perangkat lunak yang berfungsi melayani permintaan dari pengguna melalui jaringan atau internet, lalu memberikan respons berupa halaman web maupun data yang diminta. Sistem ini menggunakan protokol HTTP atau HTTPS untuk memastikan proses pertukaran informasi antara browser dan website dapat berlangsung dengan lancar. Beberapa web server yang banyak digunakan antara lain Apache HTTP Server, Nginx, dan Microsoft IIS. Tugas utama web server adalah menyimpan, mengelola, serta mendistribusikan berbagai jenis konten website, seperti dokumen HTML, gambar, video, dan data aplikasi web kepada pengguna yang mengaksesnya.

## Langkah-Langkah membuat web sederhana

1. Membuat file python di vscode
2. lalu masukkan code berikut
```
from socket import *
import threading

def handle_client(connectionSocket):
    try:
        message = connectionSocket.recv(1024).decode()
        message = message[4:16]
        print(message)
        f = open(message[1:])
        outputData = f.read()
        connectionSocket.send(
            "HTTP/1.1 200 OK\r\n\r\n".encode()
        )

        connectionSocket.sendall(outputData.encode())

        connectionSocket.close()
    
    except IOError:
        connectionSocket.send(
            "HTTP/1.1 404 Not Found\r\n\r\n".encode()
        )

        connectionSocket.send(
            "<h1>404 Not found</h1>".encode()
        )

        connectionSocket.close()

serverSocket = socket(AF_INET, SOCK_STREAM)
serverSocket.bind(('', 6789))
serverSocket.listen(5)
print("[SYSTEM] server is running...")

while True:
    connectionSocket, addr = serverSocket.accept()

    thread = threading.Thread(
        target = handle_client,
        args = (connectionSocket,)
)
    thread.start()
```
3. buat file html di folder yang sama
4. isi code berikut pada file html
```
<html>
<head>
    <title>tes</title>
</head>
<body>
    <h1>Ya berhasil</h1>
</body>
</html>
```
5. lalu jalankan file python nya terlebih dahulu
6. buka browser lalu ketik http://localhost:6789/index.html untuk menampilkan output dari file html

<img width="1251" height="897" alt="image" src="https://github.com/user-attachments/assets/426f148d-23d9-4847-946d-2c5b1a06a53a" />
