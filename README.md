# Deskripsi Project

Selamat datang di Proyek Akhir Jaringan Komputer Lanjutan. Anggota kelompok dari proyek ini terdiri dari:
1. Rayhan Egar Sadtya Nugraha (225150201111014)
2. I Gusti Ngurah Ryo Adi Tarta (225150200111011)
3. Maritza Aliyya Devy (225150200111026)

Repository ini adalah sebuah dokumentasi proyek akhir kelompok kami pada mata kuliah Jaringan Komputer Lanjut. Proyek ini adalah implementasi topologi jaringan dengan menggunakan perangkat lunak Mininet. Beberapa percobaan yang dilakukan seperti melakukan subnetting, routing dengan ospf, ibgp, ebgp, dsb. Ilustrasi topologi jaringan yang diimplementasikan pada proyek akhir ini dapat dilihat pada link di bawah ini:
https://www.canva.com/design/DAGUq-uG7EI/YVNsLlUBBAb5kzN2_-aX6Q/edit?utm_content=DAGUq-uG7EI&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton  
Berikut adalah langkah-langkah yang diperlukan untuk dapat menjalankan program. 

Catatan: Sebelum melanjutkan demonstrasi, pastikan Mininet dapat dijalankan. Instalasi Mininet dapat dilihat pada referensi berikut:
https://github.com/mininet/mininet

Untuk melihat contoh konfigurasi yang Kami lakukan, silakan menuju Wiki Jarkomlan101 melalui tautan https://github.com/rayhanegar/jarkomlan101/wiki

### Melakukan Clone Repository
Untuk menyimpan konfigurasi di perangkat, diperlukan clone repository github. Berikut adalah langkah-langkah untuk melakukan clone repository:
1. Salin link github https://github.com/rayhanegar/jarkomlan101.git
2. Buka terminal yang tersedia di perangkat anda.
3. Masuk ke direktori yang diinginkan untuk menyimpan proyek konfigurasi, misal jika ingin disimpan di direktori Download maka masukkan command `cd Downloads`.
4. Masukkan command `git clone https://github.com/rayhanegar/jarkomlan101.git`

### Komponen Project
Masukklah ke direktori dengan menggunakan perintah `cd jarkomlan 101`. Dengan bantuan perintah `ls`, isi direktori dapat dilihat pada cuplikan layar berikut:
Folder config_ospf_lab fungsinya untuk menyimpan konfigurasi yang terdapat pada seluruh node router. Script python routing-lab.py adalah script yang berfungsi untuk menginisialisasi topologi awal dari simulasi internet. Program ini akan menginisiasi interface dan mendefinisikan hubungan antar komponen seperti host, router dan switch. Program ini juga akan menjalankan Mininet ketika dijalankan dengan disertai perizinan sudo. Terakhir, program connect.sh berfungsi untuk membuka virtual terminal dari router. Dengan membuka virtual terminal, suatu router dapat dikonfigurasi.

### Menjalankan Mininet
Setelah melakukan clone terhadap repository, hal yang harus dilakukan berikutnya adalah menjalankan program Mininet. Program ini akan menjalankan Frrouting yang membuat konfigurasi antar node dapat dijalankan. Berikut adalah langkah-langkah yang perlu dilakukan untuk menjalankan Mininet:
1. Pastikan untuk memasuki direktori jarkomlan101 dengan bantuan perintah `cd jarkomlan101`.
2. Masukkan perintah `sudo python3 routing-lab.py`.
3. Pastikan Mininet berhasil dijalankan dengan munculnya mininet CLI dengan prompt `mininet>`. Pada tahap ini, topologi berhasil dibuat dan demonstrasi dapat dilakukan.


### Melihat Konfigurasi Router
Konfigurasi dasar seperti pengaturan interface dan alamat IP dapat dilakukan pada script routing-lab.py. Untuk melakukan konfigurasi lanjut mengenai routing ospf dan bgp, dapat dilakukan dengan memasuki virtual terminal dari router itu sendiri. Langkah-langkahnya adalah sebagai berikut: 
1. Pastikan Mininet sudah berjalan dengan menggunakan perintah `sudo python3 routing-lab.py`. 
2. Bukalah terminal pada tab lainnya dengan direktori yang sama.
3. Jalankan perintah `./connect.sh R11 vtysh`. Perintah ini digunakan untuk memasuki virtual terminal dari router R11. 
4. Setelah memasuki virtual terminal R11, ringkasan konfigurasi dapat dilihat dengan menggunakan perintah `sh run`. 

## PERCOBAAN DEMONSTRASI

### Melakukan Traceroute Antar Node
Sebelum melakukan traceroute, tentukan dua node yang ingin ditelusuri jalur komunikasinya. Proses ini dapat dilakukan dengan memanfaatkan perintah `traceroute`. Sebagai contoh, instruksi ini akan melakukan traceroute antar host dari C11 ke C33. Berikut langkah-langkah untuk melakukan traceroute:
1. Pada window yang sama dengan menjalankan mininet, masukkan command `[node_awal] traceroute [node_tujuan]`. Karena di sini melakukan traceroute dari C11 ke C33, maka contoh command line yang dimasukkan adalah `C11 traceroute C33`.
2. Jika traceroute berhasil, maka output yang keluar adalah sebagai berikut:
- `traceroute to 172.18.1.2 (172.18.1.2), 30 hops max, 60 byte packets`
- `1  172.16.1.1 (172.16.1.1)  0.535 ms  0.440 ms  0.424 ms`
- `2  10.100.2.2 (10.100.2.2)  0.404 ms  0.377 ms  0.360 ms`
- `3  10.10.30.2 (10.10.30.2)  0.344 ms  0.316 ms  0.296 ms`
- `4  10.30.4.1 (10.30.4.1)  0.276 ms  0.246 ms  0.224 ms`
- `5  172.18.1.2 (172.18.1.2)  0.199 ms  0.144 ms  0.117 ms`

### Melakukan Ping Ke Salah Satu Node
Sebelum melakukan ping, tentukan dua node yang ingin ditelusuri jalur komunikasinya. Proses ini dapat dilakukan dengan memanfaatkan perintah `ping`. Sebagai contoh, instruksi ini akan melakukan ping antar host dari C11 ke C33. Berikut langkah-langkah untuk melakukan ping:
1. Pada window yang sama dengan menjalankan mininet, masukkan command `[node_awal] ping [node_tujuan]`. Karena di sini melakukan traceroute dari C11 ke C33, maka contoh command line yang dimasukkan adalah `C11 ping C33`.
2. Jika traceroute berhasil, maka output yang keluar adalah sebagai berikut:
- `PING 172.18.1.2 (172.18.1.2) 56(84) bytes of data.`
- `64 bytes from 172.18.1.2: icmp_seq=1 ttl=60 time=0.078 ms`
- `64 bytes from 172.18.1.2: icmp_seq=2 ttl=60 time=0.117 ms`
- `64 bytes from 172.18.1.2: icmp_seq=3 ttl=60 time=0.099 ms`
- `64 bytes from 172.18.1.2: icmp_seq=4 ttl=60 time=0.142 ms`
3. Untuk menghentikan ping, tekan CTRL + C.
