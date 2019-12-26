# Praktikum Sembilan: Remote Login, File Transfer, Remote Desktop

![](img/ssh.png)

## Outline

- [Remote Login](#remote-login)
- [File Transfer](#file-transfer)
- [Remote Desktop](#remote-desktop)
- [Challenge](#challenge)

## Remote Login

#### Teori

Kita terkadang perlu mengakses komputer server yang berada jauh lokasinya.

Linux menyediakan fasilitas remote login dan remote desktop untuk melakukan akses ke komputer lain yang lokasinya jauh.

Untuk melakukan remote login (mengakses kompoter lain) di linux dapat menggunakan SSH (Secure Shell).

**Sintaks**:

- `ssh user@ip command`

**Keterangan**:

- `ssh`: melakukan remote login
- `user`: nama user
- `ip`: ip address
- `command`: perintah yang ingin dijalankan setelah login

**Istilah**:

- Komputer local: Komputer sendiri.
- Komputer remote: Komputer orang lain.

#### Praktikum

Cek koneksi dan update Linux:

- `ping google.com`
- `sudo apt update`

Install openssh-server:

- `sudo apt install openssh-server`

Buat user guest dengan password guest:

- `sudo useradd -m guest`
- `sudo passwd guest`

Cek ip address:

- `ifconfig`

Persiapan SSH:

- Catat user dan ip sendiri.
- Cari teman di sebelahnya.
- Catat user dan ip teman sebelahnya.

Melakukan Remote Login - SSH:

- `ssh user@ip`

**Melakukan Remote Command**

Mengecek user yang sedang login di komputer remote:

- `ssh user@ip who`

Membuat file di komputer remote:

- `ssh user@ip touch file_remote`

Membuat folder di komputer remote

- `ssh user@ip mkdir folder_remote`

Mengecek direktori di komputer remote

- `ssh user@ip ls -l`

## File Transfer

#### Teori

Selain melakukan remote login, kita dapat melakukan file transfer melalui ssh.

Perintah `scp` digunakan untuk menyalin file komputer.

Perintah `sftp` dapat digunakan untuk file transfer

#### Praktikum

**SCP**: Menyalin file antar Komputer

Membuat file dan folder di komputer local:

- `touch file_local`
- `mkdir folder_local`

Menyalin file dari komputer local ke komputer remote:

- `scp file_local user@ip:`

Menyalin folder dari komputer local ke komputer remote:

- `scp -r folder_local user@ip:`

Mengecek direktori komputer remote:

- `ssh user@ip ls -l`

Menyalin file dari komputer remote ke komputer local:

- `scp user@ip:file_remote .`

Menyalin folder dari komputer remote ke komputer local:

- `scp user@ip:folder_remote .`

Cek direktori saat ini:

- `ls -l`

**SFTP**: File Transfer

Melakukan koneksi SFTP dengan SSH:

- `sftp user@ip`

Keyword:

- keyword l: mengakses local.
- tanpa keyword l: mengakses remote.

Melakukan perintah di local:

- `lpwd`
- `lls`
- `lcd folder_local`

Melakukan operasi di remote:

- `pwd`
- `ls`
- `cd folder_remote`

Menyalin file dari komputer remote ke komputer local:

- `ls -l`
- `get file_remote`
- `lls -l`

Menyalin file dari komputer local ke komputer remote:

- `lls -l`
- `put file_local`
- `ls -l`

## Remote Desktop

Menjalankan Desktop Sharing:

- Buka **Desktop Sharing** di Pencarian.
- Centang pada **Allow other users to view your desktop**.
- Centang pada **You must confirm each access to this machine**.
- Centang **Require the user to enter this password** dan masukan password.

Menjalankan Remina Remote Desktop:

- Buka **Remina Remote Desktop** di Pencarian
- Klik **New**.
- Pada bagian **Name** masukan nama koneksi.
- Pada bagian **Protocol** pilih: VNC - **Virtual Network Computing**.
- Pada bagian **Server** masukan ip, pada bagian **Username** masukan username, pada bagian **Password** masukan password.
- Klik **Connect**.

## Challenge

**Ketentuan Challenge:**

- Challenge no 1, 3, dan 4 harus menggunakan Screenshot.
- Challenge dikumpulkan di Elen.

**Challenge**:

Terdapat 2 buah laptop dengan skenario sebagai berikut:

1. Laptop local
   1. user: maria
   2. ip: 192.168.1.50
   3. file: index.html
2. Laptop remote
   1. user: john
   2. ip: 192.168.1.70
   3. file: style.css


------

1. Tuliskan perintah SSH untuk mengakses laptop remote (john) dari laptop local (maria).
2. Tuliskan perintah menyalin file index.html ke laptop remote (john) menggunakan ftp.
3. Tuliskan perintah menyalin file style.css ke laptop local (maria) menggunakan sftp.
4. Apa perbedaan scp dan sftp? Jelaskan.
5. Apa evaluasi praktikum kesembilan? apa masukan dan saran?