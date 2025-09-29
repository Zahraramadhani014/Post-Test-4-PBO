### $_$ - Post Test 4 PBO - $_$
--------------------------------------------------------------------------------------------

#### Disusun oleh:

Nama: Zahraturramadhani

NIM: 2409116014

Kelas: Sistem Informasi A'2024

--------------------------------------------------------------------------------------------

<h2 align="center">💵💸💹 Manajemen Catatan Keuangan Harian (Budget Tracker) 💰🪙💴 </h2> 

<h2 align="center">=================================================</h2> 
<h1 align="center">🛡️ POCKET GUARD 🛡️</h1>
<h2 align="center">=================================================</h2> 

### ~ 📗 Deskripsi Singkat 📒  ~

Program ini dibuat untuk membantu mencatat dan mengelola catatan keuangan harian. Aplikasinya bernama Pocket Guard, aplikasi Java sederhana berbasis console.

Di dalam program, setiap catatan keuangan dapat diisi lengkap dengan tanggal, keterangan singkat, jenis catatan (pemasukan atau pengeluaran), kategori (gaji, makan, transportasi, hiburan, belanja, tabungan,tagihan), metode pembayaran (cash, e-wallet, atau transfer), serta jumlah uang yang dikeluarkan atau diterima.

Aplikasi ini bisa menambah catatan baru, melihat seluruh daftar catatan, mengubah jika ada kekeliruan, atau menghapus catatan yang tidak diperlukan. Program juga dapat menampilkan ringkasan saldo (total pemasukan, total pengeluaran, dan selisihnya) sehingga kondisi keuangan mudah dipantau.

Tersedia pula fitur filter catatan berdasarkan jenis, kategori, dan metode pembayaran, serta fitur search berdasarkan keterangan catatan. Selain itu, batas pengeluaran bulanan dapat ditetapkan, bila pengeluaran melewati batas, program akan menampilkan peringatan agar pengelolaan uang lebih terkendali.

Secara keseluruhan, Pocket Guard membantu melacak arus kas harian, menjaga keseimbangan keuangan, dan membiasakan pencatatan keuangan secara teratur.

### ~ Penjelasan Program  ~

1. Penjelasan class yang ada di program "Pocket Guard"
   
   a. Class App.Java yang terdapat di Packages Main
   
      <img width="331" height="44" alt="image" src="https://github.com/user-attachments/assets/9c8671df-aa36-41fe-9192-2b3d77087926" />

      > Kelas App berfungsi sebagai titik masuk utama program dan berada pada package main. Di dalam kelas ini terdapat method main yang menampilkan menu aplikasi Pocket Guard dengan antarmuka berbasis console. Kelas App mengatur perulangan menu menggunakan struktur do..while serta switch case untuk mengeksekusi pilihan pengguna, seperti menambah, melihat, mengubah, menghapus catatan, hingga menampilkan ringkasan saldo atau mengatur batas pengeluaran. Semua logika yang lebih kompleks didelegasikan kepada kelas TransaksiService. Selain itu, di file ini juga terdapat kelas kecil bernama SafeInput yang bertugas menangani input angka agar lebih aman, sehingga program tidak error ketika pengguna salah memasukkan data. Dengan demikian, App berperan sebagai penghubung antara pengguna dengan logika bisnis yang ada di service.

   b. Class Transaksi.Java yang terdapat di Packages Model

      <img width="332" height="115" alt="image" src="https://github.com/user-attachments/assets/19888393-0825-4799-b009-dc5324e0b25a" />

      > Kelas Transaksi terletak pada package model dan berperan sebagai superclass atau kelas induk dari data transaksi. Kelas ini berisi atribut yang umum dimiliki setiap transaksi, yaitu id, tanggal, keterangan, jenis, kategori, metodePembayaran, dan jumlah. Semua atribut dibuat private untuk menerapkan konsep encapsulation, sedangkan aksesnya diberikan melalui method getter dan setter yang bersifat public. Konstruktor kelas Transaksi digunakan untuk menginisialisasi seluruh atribut ketika sebuah objek transaksi baru dibuat. Dengan adanya kelas ini, struktur data transaksi menjadi konsisten dan dapat diwariskan ke subclass lain. Kelas Transaksi juga menjadi kontrak dasar yang memungkinkan penggunaan polimorfisme pada list transaksi di kelas service.

   c. Class Pemasukan.Java yang terdapat di Packages Model

      <img width="332" height="115" alt="image" src="https://github.com/user-attachments/assets/0b43dcb2-197d-444c-b043-c153776644bd" />

      > Kelas Pemasukan juga berada pada package model dan merupakan subclass dari Transaksi. Kelas ini merepresentasikan transaksi yang berjenis pemasukan. Konstruktor di dalamnya akan otomatis mengatur jenis transaksi menjadi “Pemasukan” tanpa harus diinput ulang oleh pengguna. Selain itu, kelas ini melakukan overriding terhadap method getJenis() sehingga setiap kali dipanggil akan selalu mengembalikan nilai “Pemasukan”. Method setJenis() juga dioverride dan dikosongkan agar nilai jenis tidak dapat diubah secara sembarangan. Dengan cara ini, objek Pemasukan tetap konsisten menyimpan identitasnya sebagai pemasukan, sekalipun pengguna mencoba melakukan perubahan pada menu ubah data.

   d. Class Pengeluaran.Java yang terdapat di Packages Model

      <img width="332" height="115" alt="image" src="https://github.com/user-attachments/assets/a878740f-0cc3-4502-85d2-96bcd4401439" />

      > Kelas Pengeluaran merupakan subclass lain dari Transaksi yang juga berada di package model. Fungsinya adalah merepresentasikan transaksi yang berjenis pengeluaran. Sama seperti Pemasukan, konstruktor Pengeluaran secara otomatis menetapkan jenis transaksi sebagai “Pengeluaran”. Method getJenis() dioverride agar selalu mengembalikan “Pengeluaran”, sedangkan method setJenis() juga dioverride untuk mencegah perubahan jenis. Hal ini membuat setiap objek Pengeluaran tetap terjaga konsistensinya sebagai transaksi pengeluaran. Dengan adanya subclass Pemasukan dan Pengeluaran, struktur data lebih terpisah dengan jelas sekaligus lebih aman dari kesalahan input.

   e. Class SaldoEffect.Java yang terdapat di Packages Model
   
      <img width="332" height="115" alt="image" src="https://github.com/user-attachments/assets/fe6201ce-ca29-45c5-a7d6-980559ea4936" />

      >
      
   f. Class TransaksiService.Java yang terdapat di Packages Service

      <img width="343" height="52" alt="image" src="https://github.com/user-attachments/assets/137a271d-7e35-4e0e-b586-ce8c51ef3573" />

      > Kelas TransaksiService terletak pada package service dan bertanggung jawab mengelola seluruh logika bisnis aplikasi. Di dalamnya terdapat sebuah list bertipe Transaksi yang dapat menyimpan objek Pemasukan maupun Pengeluaran. Di sinilah konsep polimorfisme dijalankan, karena meskipun list bertipe Transaksi, saat method getJenis() dipanggil, hasilnya akan menyesuaikan perilaku override dari masing-masing subclass. TransaksiService menyediakan berbagai fitur seperti menambah data baru dengan memilih subclass sesuai jenis transaksi, menampilkan seluruh catatan dalam bentuk tabel, mengubah data, menghapus data, menghitung ringkasan saldo, serta mengatur batas pengeluaran bulanan. Selain itu, TransaksiService juga memiliki fitur filter berdasarkan kategori, metode pembayaran, dan jenis transaksi, serta pencarian berdasarkan keterangan. Untuk mendukung hal itu, disediakan berbagai helper method privat seperti validasi input, pencarian ID, pemformatan rupiah, dan tampilan tabel. Dengan demikian, TransaksiService berfungsi sebagai penghubung utama antara antarmuka di kelas App dan data model pada kelas Transaksi beserta turunannya.

1. Penjelasan packages yang ada di program "Pocket Guard"
   
   - Packages Main
      
    <img width="315" height="25" alt="image" src="https://github.com/user-attachments/assets/43507736-f43d-471e-a16c-bafc7755910c" />

      > Package com.mycompany.posttest3pbo.main berisi kelas utama yang menjadi titik masuk program, yaitu App.java. Di dalamnya terdapat method main yang bertugas menampilkan menu aplikasi Pocket Guard, menerima input pengguna, dan memanggil metode-metode yang ada di service. Dengan kata lain, package ini menangani sisi antarmuka console yang berinteraksi langsung dengan user. Selain itu, di dalam file yang sama terdapat kelas SafeInput yang digunakan untuk memastikan input angka selalu valid agar program berjalan tanpa error. Package ini fokus pada bagian view dan entry point aplikasi.

    - Packages Model 

      <img width="335" height="27" alt="image" src="https://github.com/user-attachments/assets/12b5e9c2-8d4e-4ff8-a3b6-40c13c8e86eb" />

      > Package com.mycompany.posttest3pbo.model berfungsi menyimpan struktur data transaksi. Di dalamnya terdapat kelas Transaksi sebagai superclass yang berisi atribut dan method dasar untuk sebuah catatan keuangan. Kemudian ada dua subclass, yaitu Pemasukan dan Pengeluaran, yang mewarisi struktur dari Transaksi namun melakukan overriding pada method getJenis() dan setJenis() agar setiap objek memiliki jenis transaksi yang konsisten. Dengan adanya package ini, data transaksi terkelola dengan baik, mendukung konsep encapsulation untuk keamanan atribut, sekaligus menerapkan inheritance dan polimorfisme sesuai prinsip OOP.

    - Packages Service
      
        <img width="325" height="24" alt="image" src="https://github.com/user-attachments/assets/3c91dc17-f660-4ca6-a227-b79b1e16f29b" />

        > Package com.mycompany.posttest3pbo.service berisi logika bisnis yang mengatur jalannya aplikasi, diwakili oleh kelas TransaksiService. Kelas ini bertugas menyimpan daftar transaksi, menambahkan data baru, mengedit, menghapus, hingga menampilkan ringkasan saldo. Selain itu, package ini juga mengelola fitur tambahan seperti pengaturan batas pengeluaran, filter berdasarkan kategori, metode pembayaran, maupun pencarian keterangan. Package Service inilah yang menjadi penghubung antara antarmuka pengguna di kelas App dengan struktur data pada package Model, sehingga tanggung jawab program terpisah dengan jelas dan program lebih mudah dikelola.

2. Penjelasan encapsulation (getter dan setter)
   
   <img width="1077" height="341" alt="image" src="https://github.com/user-attachments/assets/85f7d6c2-6608-4782-8b76-593537d4647a" />

   > Pada program Pocket Guard, konsep encapsulation diterapkan dengan cara menjadikan seluruh atribut di kelas Transaksi bersifat private. Dengan begitu, data seperti id, tanggal, keterangan, jenis, kategori, metode pembayaran, dan jumlah tidak dapat diakses maupun diubah secara langsung dari luar kelas. Untuk memberikan akses yang aman, setiap atribut memiliki getter dan setter yang bersifat public. Getter digunakan untuk membaca nilai atribut, sedangkan setter dipakai untuk memperbarui nilai atribut. Pola ini memastikan bahwa perubahan data selalu melalui metode resmi yang sudah disediakan, sehingga integritas data tetap terjaga dan program lebih terkontrol.
   >
   > Selain itu, encapsulation juga memudahkan pengembangan di masa depan. Jika diperlukan logika tambahan, misalnya validasi nilai sebelum disimpan, hal tersebut dapat ditambahkan langsung di dalam setter tanpa perlu mengubah kode di bagian lain. Dengan demikian, encapsulation tidak hanya berfungsi melindungi data, tetapi juga membuat program lebih rapi, terstruktur, serta sejalan dengan prinsip dasar Object-Oriented Programming (OOP).

3. Penjelasan inheritance (minimal memiliki 1 superclass dengan 2 subclass)

   Pada program ini, konsep inheritance diterapkan dengan menjadikan kelas Transaksi.java sebagai superclass, sedangkan kelas Pemasukan.java dan Pengeluaran.java sebagai subclass.
   
   a. Transaksi.Java (Super Class)

      <img width="165" height="28" alt="image" src="https://github.com/user-attachments/assets/65a8e0d8-7772-4bda-9d2f-a5c31a38b24e" />

      > Kelas Transaksi.java berfungsi sebagai induk yang menyimpan seluruh atribut dasar dari sebuah catatan keuangan, seperti id, tanggal, keterangan, jenis, kategori, metode pembayaran, dan jumlah. Semua atribut ini dilengkapi dengan konstruktor serta method getter dan setter untuk menjaga enkapsulasi. Dengan adanya superclass ini, struktur data transaksi menjadi seragam dan siap diwarisi oleh kelas lain.

   b. Pemasukan.Java (Sub Class)

      <img width="163" height="25" alt="image" src="https://github.com/user-attachments/assets/aef230ae-91aa-4fb0-b9ea-d50d1e10bda1" />

   > Kelas Pemasukan.java merupakan subclass yang mewarisi seluruh atribut dan method dari Transaksi, tetapi secara khusus digunakan untuk transaksi berjenis pemasukan. Di dalamnya terdapat konstruktor yang secara otomatis menetapkan jenis transaksi sebagai “Pemasukan”. Selain itu, kelas ini juga melakukan overriding terhadap method getJenis() agar selalu mengembalikan nilai “Pemasukan” dan overriding pada method setJenis() untuk mencegah perubahan nilai jenis secara sembarangan. Hal ini menjamin bahwa setiap objek Pemasukan akan tetap konsisten dengan identitasnya.

   c. Pengeluaran.Java (Sub Class)

      <img width="173" height="23" alt="image" src="https://github.com/user-attachments/assets/ae5e320b-b41b-43a5-beef-a50a880da778" />

      > Kelas Pengeluaran.java juga menjadi subclass dari Transaksi, namun dikhususkan untuk transaksi dengan jenis pengeluaran. Sama seperti Pemasukan, konstruktor kelas ini otomatis memberikan nilai “Pengeluaran” pada jenis transaksi. Method getJenis() dioverride untuk selalu mengembalikan “Pengeluaran”, sedangkan method setJenis() dioverride agar tidak dapat mengubah nilai jenis. Dengan demikian, setiap objek Pengeluaran terjaga konsistensinya sebagai transaksi keluar.

   Melalui penerapan inheritance ini, program dapat memanfaatkan satu struktur induk yang umum (Transaksi) sekaligus mengelompokkan transaksi ke dalam subclass khusus (Pemasukan dan Pengeluaran).

4. Penjelasan Overriding

   Pada program Pocket Guard, konsep overriding diterapkan di dalam subclass Pemasukan.java dan Pengeluaran.java. Overriding berarti sebuah subclass mendefinisikan ulang method yang sudah ada di superclass dengan perilaku yang lebih spesifik sesuai kebutuhan.

   a. Class Pemasukan.Java

      <img width="405" height="233" alt="image" src="https://github.com/user-attachments/assets/a0aedc93-9373-46d3-b114-9cc94d765e18" />

      >Pada kelas Pemasukan.java, method getJenis() dioverride agar selalu mengembalikan nilai string “Pemasukan”. Dengan demikian, setiap kali objek Pemasukan dipanggil untuk mengetahui jenis transaksinya, hasilnya akan konsisten dan tidak dapat berubah. Selain itu, method setJenis(String jenis) juga dioverride namun dibuat kosong, sehingga meskipun pengguna mencoba mengubah jenis transaksi, nilainya tidak akan berubah. Hal ini memastikan bahwa objek Pemasukan akan selalu beridentitas sebagai pemasukan.

   b. Class Pengeluaran.Java

      <img width="392" height="232" alt="image" src="https://github.com/user-attachments/assets/50a4cb6d-7c14-4c84-9e7e-dc92f2c2ce50" />

   >Hal serupa juga dilakukan pada kelas Pengeluaran.java. Method getJenis() dioverride agar setiap kali dipanggil akan mengembalikan nilai string “Pengeluaran”. Sedangkan method setJenis(String jenis) dioverride tanpa isi sehingga upaya untuk mengubah jenis transaksi tidak akan berdampak. Dengan pola ini, semua objek Pengeluaran akan tetap konsisten sebagai transaksi pengeluaran.

   Penerapan overriding ini sangat penting karena menjaga konsistensi data antara jenis transaksi dengan subclass yang menaunginya. Selain itu, hal ini juga memperlihatkan penggunaan prinsip polimorfisme dalam OOP, di mana pemanggilan method getJenis() akan menghasilkan perilaku yang berbeda tergantung pada objek sebenarnya, apakah itu Pemasukan atau Pengeluaran, meskipun keduanya ditampung dalam list bertipe Transaksi.

#### Penerapan Abstraction
1) **Interface `SaldoEffect`**: mendefinisikan kontrak `efekSaldo()` untuk menghitung pengaruh transaksi terhadap saldo.

   <img width="568" height="155" alt="image" src="https://github.com/user-attachments/assets/243d563b-af09-473a-bc07-9513a49c7921" />

   <img width="578" height="27" alt="image" src="https://github.com/user-attachments/assets/5cf9f219-4e05-4c4e-8e2c-af236a323bdf" />

   <img width="499" height="120" alt="image" src="https://github.com/user-attachments/assets/f2de32cc-27ea-4fe1-a62d-8ac0227ed5dd" />

   
1) **Abstract Class `Transaksi`**: menjadi template bagi semua transaksi. Menyediakan field umum (id, tanggal, dll) dan *abstract method* `tandaSaldo()` yang harus diimplementasi subclass

   <img width="898" height="641" alt="image" src="https://github.com/user-attachments/assets/e6e6876b-a1a6-426f-a9f2-a41c67c201c6" />

#### Penerapan Polymorphism
- **Overriding**
  - `Pemasukan.getJenis()` & `Pengeluaran.getJenis()` mengunci jenis masing-masing
  - `Pemasukan.tandaSaldo()` mengembalikan `+1`, `Pengeluaran.tandaSaldo()` `-1`

   <img width="959" height="400" alt="image" src="https://github.com/user-attachments/assets/3feedb55-f839-49e0-817c-81d8f8a98b07" />
   
   <img width="966" height="413" alt="image" src="https://github.com/user-attachments/assets/3563bf29-b6de-4701-a765-d1992048cdf0" />


- **Overloading**
  - `TransaksiService.tampilkanTabel()` di-*overload*: ada versi tanpa parameter dan versi dengan parameter `List<Transaksi>`

    <img width="1562" height="773" alt="image" src="https://github.com/user-attachments/assets/e8909b0f-64cc-42d7-b981-84a80cd47008" />


#### Kombinasi abstract class + interface
- `Transaksi` (abstract class) **mengimplementasikan** interface `SaldoEffect`. Perhitungan saldo global menggunakan pemanggilan polimorfik `efekSaldo()`
  
  <img width="633" height="27" alt="image" src="https://github.com/user-attachments/assets/e0f25372-1e28-4c90-b92c-f2ae9915bcfb" />
  <img width="543" height="141" alt="image" src="https://github.com/user-attachments/assets/b17f7d2f-90d3-440a-a05c-047423f4d125" />

  <img width="1152" height="378" alt="image" src="https://github.com/user-attachments/assets/817a76e6-31d4-4ad0-a296-384085e6be06" />



#### Letak Kode Utama
- Abstraction (interface & abstract class): `model/SaldoEffect.java`, `model/Transaksi.java`
- Polymorphism (Overriding): `model/Pemasukan.java`, `model/Pengeluaran.java`
- Polymorphism (Overloading): `service/TransaksiService.java` → `tampilkanTabel()` overload.
- Perhitungan saldo via interface: `TransaksiService.ringkasanSaldo()`.

    
### ~ Penjelasan Alur Program (Output Program)  ~

<h1 align="center"><img width="369" height="306" alt="image" src="https://github.com/user-attachments/assets/9aaa0cd6-68b4-4dd0-903c-988aa4aedf47" /></h1>

> Saat program dijalankan, muncul pesan pembuka “SELAMAT DATANG DI POCKET GUARD – Aplikasi Catatan Keuangan Harian Anda”. Setelah itu tampil Menu Utama berisi pilihan untuk menambah catatan, melihat daftar catatan, mengubah atau menghapus catatan, menampilkan ringkasan saldo, memfilter catatan (berdasarkan jenis, kategori, atau metode pembayaran) dan searching berdasarkan keterangan, menetapkan batas pengeluaran bulanan, serta opsi keluar untuk mengakhiri program.
>
> ### ✨ Penjelasan Masing-Masing Menu ✨
> 
> 1. Tambah Catatan Keuangan
>    
>    Menu ini digunakan untuk menambahkan catatan keuangan baru. Data yang dimasukkan meliputi tanggal, keterangan, jenis (pemasukan/pengeluaran), kategori, metode pembayaran, dan jumlah. Setelah disimpan, catatan langsung masuk ke daftar utama.
>    
> 2. Lihat Semua Catatan Keuangan
>    
>    Menampilkan seluruh daftar catatan keuangan dalam bentuk tabel yang rapi. Pengguna bisa melihat detail lengkap seperti ID, tanggal, jenis, kategori, metode pembayaran, jumlah, dan keterangan.
>    
> 3. Ubah Catatan Keuangan
>    
>    Menu ini berfungsi untuk memperbarui data catatan keuangan yang sudah ada. Cukup masukkan ID catatan, lalu ganti data yang ingin diperbarui seperti tanggal, keterangan, jenis, kategori, metode pembayaran, maupun jumlah.
>    
> 4. Hapus Catatan Keuangan
>    
>    Digunakan untuk menghapus catatan keuangan yang sudah tidak diperlukan. Cukup masukkan ID catatan, lalu data akan dihapus permanen dari daftar.
>    
> 5. Ringkasan Saldo
>    
>    Menampilkan ringkasan keuangan berupa total pemasukan, total pengeluaran, dan saldo akhir (selisih antara pemasukan dan pengeluaran). Dengan menu ini kondisi keuangan bisa dipantau secara cepat.
>    
> 6. Filter dan Search
>    
>    Menu ini menampilkan sub-menu filter dan search (berdasarkan keterangan) yang bisa digunakan untuk menyaring catatan keuangan berdasarkan:
>    
>    a. Jenis (pemasukan/pengeluaran)
>    
>    b. Kategori (makan, transportasi, hiburan, belanja, tabungan, dll.)
>    
>    c. Metode pembayaran (cash, e-wallet, transfer)
>
>    d. Search (cari berdasarkan keterangan)
>
>    Fitur ini mempermudah pencarian data tertentu agar lebih spesifik.
>    
> 7. Set Batas Pengeluaran
>    
>    Menu ini digunakan untuk menetapkan batas pengeluaran bulanan. Jika total pengeluaran melewati batas yang ditetapkan, sistem akan memberikan peringatan agar pengelolaan keuangan lebih terkendali.
>    
> 8. Keluar
>    
>    Menu ini digunakan untuk keluar dari aplikasi. Setelah memilih opsi ini, sistem akan menampilkan pesan penutup sebelum program dihentikan.

### 1. Menu Tambah Catatan Keuangan

<img width="688" height="407" alt="image" src="https://github.com/user-attachments/assets/feae8186-3ee4-44f1-9104-c23d6dc6ec5b" />

> Ketika menginputkan angka 1 pada menu utama maka akan diarahkan ke menu "Tambah Catatan Keuangan" seperti yang tertera pada gambar di atas

<img width="905" height="217" alt="image" src="https://github.com/user-attachments/assets/cb715ebe-5e17-4511-ae2b-66bccd306636" />

> Setelah itu bakal diminta untuk menginputkan "Tanggal", "Keterangan", "Jenis Transaksi", "Kategori Transaksi", "Metode Pembayaran", serta "Nominal Transaksi". Ketika berhasil menambahkan data baru akan muncul pesan "Data Berhasil Ditambahkan"

<img width="1025" height="408" alt="image" src="https://github.com/user-attachments/assets/df4b47e0-b4bd-4266-8b85-14f4d19fd624" />

> Setelah data baru berhasil ditambahkan, program akan langsung menampilkan ulang seluruh daftar catatan keuangan dalam bentuk tabel. Tabel ini memuat informasi lengkap seperti ID, Tanggal, Jenis (pemasukan/pengeluaran), Kategori, Metode Pembayaran, Jumlah, serta Keterangan.

> Di bagian bawah tabel, program juga memberikan pilihan "Apakah Ingin Menambah Catatan Lagi? (Y/T):".
> 
>  a. Jika menginputkan "Y", maka akan diarahkan untuk menginputkan catatan baru mulai dari menginputkan tanggal sampai nominal transaksinya. Ketika berhasil menambahkan data maka akan muncul pesan bahwa "Data Berhasil Ditambahkan".
> 
> <img width="957" height="219" alt="image" src="https://github.com/user-attachments/assets/ec4aabe8-aede-4d4a-8296-e7e4c56c4584" />
>
> Dan setelah berhasil menambahkan data baru, program akan langsung menampilkan ulang seluruh daftar catatan keuangan dalam bentuk tabel dan diarahkan kembali ke pertanyaan "Apakah Ingin Menambah Catatan Lagi? (Y/T):", seperti yang tertera pada gambar di bawah ini.
> 
> <img width="1016" height="389" alt="image" src="https://github.com/user-attachments/assets/93414b8b-46ec-4601-8c40-3704b477d5a5" />
>
>  b. Jika  menginputkan "T" maka akan di arahkan ke menu utama program ini.
> 
> <img width="386" height="348" alt="image" src="https://github.com/user-attachments/assets/c1a16e7a-c0f0-4a95-b777-fffb111a0ec5" />

#### Validasi Input Pada Menu "Tambah Catatan Keuangan"

- Pada menu "Tambah Catatan Keuangan", ketika nominal transaksi diinputkan menggunakan huruf alih-alih angka, sistem akan menampilkan peringatan berupa pesan "Harus angka! Silakan input ulang". Pesan ini memastikan agar data yang dimasukkan valid sesuai format angka, sehingga perhitungan transaksi dapat berjalan dengan benar, seperti terlihat pada gambar di bawah ini.
  
  <img width="936" height="202" alt="image" src="https://github.com/user-attachments/assets/0aa64c3f-7944-46ad-b028-b2f69707e823" />

- Selain validasi input angka, pada menu "Tambah Catatan Keuangan", setiap kali catatan pengeluaran baru ditambahkan, sistem akan otomatis menghitung ulang total seluruh pengeluaran. Jika total pengeluaran tersebut melebihi batas bulanan yang sudah ditentukan sebelumnya, maka aplikasi akan langsung menampilkan peringatan agar anggaran tetap terkontrol, seperti yang terlihat pada gambar di bawah ini.
  
  <img width="1061" height="586" alt="image" src="https://github.com/user-attachments/assets/26b2b15c-c5ed-4aae-a019-1fb9122c2e78" />

- Selain validasi input angka, pada menu "Tambah Catatan Keuangan", setiap kali mengosongkan inputan "misal mengosongkan input tanggal", maka sistem akan menampilkan peringatan berupa pesan "Tidak boleh kosong. Coba lagi".

  <img width="670" height="128" alt="image" src="https://github.com/user-attachments/assets/677956e8-ef34-4d7d-bc29-62b201ee3dc0" />

- Jika menginputkan tanggal tidak sesuai format yang diminta yaitu "yyyy-mm-dd", maka akan muncul pesan "Format tanggal harus yyyy-mm-dd" dan sistem akan meminta untuk menginputkan kembali tanggal sesuai dengan format "yyyy-mm-dd".

  <img width="662" height="110" alt="image" src="https://github.com/user-attachments/assets/70540860-6f9a-4e13-abad-1d96ea4ba85d" />

- Jika menginputkan jenis transaksi selain "Pemasukan/Pengeluaran", maka akan muncul pesan "Pilihan tidak valid. Pilihan yang valid: Pemasukan/Pengeluaran" dan sistem akan meminta ulang untuk menginputkan jenis transaksi yang sesuai dengan jenis transaksi yang tersedia yaitu "Pemasukan/Pengeluaran".

  <img width="685" height="192" alt="image" src="https://github.com/user-attachments/assets/5d9be1b6-9710-477e-b8f4-eef87a7d0bba" />

- Jika menginputkan kategori selain "Gaji, Makan, Transportasi, Hiburan, Belanja, Tabungan, Tagihan", maka akan muncul pesan "Pilihan tidak valid. Pilihan yang valid: Gaji/Makan/Transportasi/Hiburan/Belanja/Tabungan/Tagihan" dan sistem akan meminta ulang untuk menginputkan kategori yang sesuai dengan kategori yang tersedia yaitu "Gaji, Makan, Transportasi, Hiburan, Belanja, Tabungan, Tagihan".

  <img width="820" height="251" alt="image" src="https://github.com/user-attachments/assets/27663a6a-582b-4f7a-92f5-2056450bf5b2" />

- Jika menginputkan metode pembayaran selain "Cash, E-Wallet, Transfer", maka akan muncul pesan "Pilihan tidak valid. Pilihan yang valid: Cash/E-Wallet/Transfer" dan sistem akan meminta ulang untuk menginputkan metode pembayaran yang sesuai dengan meode pembayaran yang tersedia yaitu "Cash, E-Wallet, Transfer".

  <img width="802" height="302" alt="image" src="https://github.com/user-attachments/assets/4dc6401a-76e1-4eb4-99f6-9a1fc1449452" />


### 2. Menu Lihat Semua Catatan Keuangan 

<img width="1032" height="684" alt="image" src="https://github.com/user-attachments/assets/f9e507f9-4769-4189-bfe8-c6ad65a0efad" />

> Ketika menginputkan angka 2 pada menu utama maka akan diarahkan ke menu "Lihat Semua Catatan Keuangan" seperti yang tertera pada gambar di atas.
>
> Pada menu ini, seluruh catatan keuangan yang sudah dimasukkan akan ditampilkan dalam bentuk tabel yang rapi, berisi informasi ID, Tanggal, Jenis (Pemasukan/Pengeluaran), Kategori, Metode, Jumlah, dan Keterangan.
>
> Selain itu, pada bagian bawah tabel akan muncul perintah "Ketik 0 untuk kembali" yang berfungsi untuk kembali ke menu utama.

### 3. Menu Ubah Catatan Keuangan

<img width="1018" height="717" alt="image" src="https://github.com/user-attachments/assets/207e61d0-10be-427f-bc5f-da01b1fbb83c" />

> Ketika menginputkan angka 3 pada menu utama maka akan diarahkan ke menu "Ubah Catatan Keuangan" seperti yang tertera pada gambar di atas.
>
>  Pada menu ini, seluruh daftar transaksi ditampilkan lengkap dengan ID, tanggal, jenis, kategori, metode pembayaran, jumlah, dan keterangan, sehingga catatan yang ingin diperbarui dapat dipilih dengan mudah.

<img width="1036" height="602" alt="image" src="https://github.com/user-attachments/assets/23f136c0-7b04-4160-be1e-0c0c8d68a6a6" />

<img width="1016" height="331" alt="image" src="https://github.com/user-attachments/assets/33144f74-7c63-402f-8659-55d029c3a935" />

> Setelah itu sistem akan meminta ID dari transaksi yang ingin diubah. Setelah ID dimasukkan, tersedia opsi untuk mengganti setiap field transaksi, mulai dari tanggal, keterangan, jenis, kategori, metode pembayaran, hingga nominal. Jika pada salah satu field tidak diberikan input baru dan langsung menekan Enter, maka nilai lama akan tetap dipertahankan. Dengan mekanisme ini, perubahan data dapat dilakukan secara fleksibel tanpa perlu menghapus atau menambahkan ulang catatan transaksi.
>
> Sebagai contoh, pada gambar ditunjukkan transaksi dengan ID 11 yang sebelumnya berisi data pemasukan dengan kategori gaji. Beberapa field kemudian diganti, seperti tanggal, keterangan, jenis, kategori, metode pembayaran, dan nominal transaksi. Setelah proses selesai, sistem akan menampilkan pesan “Data berhasil diubah” serta menampilkan kembali tabel catatan keuangan yang sudah diperbarui.

- ID sebelum diubah catatan keuangan nya
  <img width="981" height="25" alt="image" src="https://github.com/user-attachments/assets/57381df9-080b-4e93-a6d5-9150a7dc04fa" />
  
- ID sesudah diubah catatan keuangan nya
  <img width="982" height="28" alt="image" src="https://github.com/user-attachments/assets/1ee1b467-dc9e-4597-8483-5d6e32354b6e" />

Setelah proses Ubah Catatan Keuangan selesai dilakukan, sistem akan menampilkan daftar catatan terbaru yang sudah diperbarui. Selanjutnya, akan diberikan pilihan seperti yang terlihat pada gambar di bawah ini:

<img width="1028" height="395" alt="image" src="https://github.com/user-attachments/assets/9b6c060f-669d-451d-b795-be444910a6db" />

> a. Jika menginputkan "Y"
> 
>  <img width="1038" height="673" alt="image" src="https://github.com/user-attachments/assets/688421af-a675-4f78-8fb7-3b94081e9652" />
>  <img width="1009" height="339" alt="image" src="https://github.com/user-attachments/assets/e6e7773f-d2e4-4fcb-9dba-dca93c0be3c8" />
>
>  Program akan kembali menampilkan menu Ubah Catatan Keuangan. Pada tahap ini dapat dimasukkan ID lain untuk diperbarui. Dengan begitu, proses ubah catatan bisa dilakukan berulang kali sesuai kebutuhan tanpa harus kembali ke menu utama terlebih dahulu.
>
> b. Jika  menginputkan "T"
> 
>  <img width="385" height="349" alt="image" src="https://github.com/user-attachments/assets/bb046725-13d4-4df0-890a-25350b46a088" />
>
>
>  Program akan langsung keluar dari menu ubah catatan dan kembali ke Menu Utama. Hal ini memudahkan jika tidak ingin lagi melakukan perubahan pada catatan yang ada.

#### Validasi Input Pada Menu "Ubah Catatan Keuangan"

- Pada saat menginputkan ID yang tidak tersedia di dalam tabel, sistem akan memberikan peringatan "ID tidak ditemukan" seperti gambar di bawah ini.
  
  <img width="1199" height="815" alt="image" src="https://github.com/user-attachments/assets/7b99194b-783e-4dd7-a122-0a5cb58b09fe" />

  Hal ini menunjukkan bahwa ID yang dimasukkan tidak sesuai dengan daftar transaksi yang ada. Setelah itu, sistem tetap menampilkan ulang tabel catatan keuangan terbaru agar bisa memastikan ID mana yang valid. Dengan cara ini, tidak akan terjadi kesalahan dalam mengubah data transaksi karena hanya ID yang tersedia dalam tabel yang dapat diproses.
  
- Pada saat mencoba menginputkan ID dengan huruf (contoh: "sebelas") alih-alih angka (11), sistem akan otomatis menolak input tersebut. Program akan menampilkan pesan error "Harus angka! Silakan input ulang:".
  
  <img width="994" height="474" alt="image" src="https://github.com/user-attachments/assets/c6004323-fdf3-4281-bf23-ab5368a095b0" />

  Pesan ini memastikan bahwa input yang diterima hanya berupa angka valid sesuai ID transaksi.

- Pada saat mengosongkan inputan ID yang ingin diubah, maka sistem akan memberikan peringatan "Harus angka! Silakan input ulang:" seperti gambar di bawah ini.

  <img width="1009" height="477" alt="image" src="https://github.com/user-attachments/assets/1d1b1b34-876c-4b94-bd76-6101caea9f0f" />

- Apabila nominal transaksi diinputkan dengan huruf (contoh: "tiga juta") alih-alih angka (3000000), sistem akan langsung menolak input tersebut dan menampilkan pesan error "Harus angka! Silakan input ulang:" seperti pada gambar di bawah ini.
  
  <img width="497" height="211" alt="image" src="https://github.com/user-attachments/assets/115dfe19-20a1-409c-85be-36bf89500fcc" />
  <img width="1266" height="462" alt="image" src="https://github.com/user-attachments/assets/cffebac3-341f-4648-94b3-ab0c20ce469b" />

  Setelah itu, sistem akan meminta untuk memasukkan ulang nilai nominal dengan format angka yang benar. Begitu input diperbaiki, data transaksi akan berhasil diperbarui dan ditampilkan kembali pada tabel catatan keuangan.

- Pada menu "Ubah Catatan Keuangan", jika mengosongkan inputan yang ingin di update "misal mengosongkan inputan input tanggal baru, keterangan baru, jenis baru, kategori baru, metode pembayaran baru, dan nominal transaksi baru" maka nilai lama yang akan dipertahankan.

  <img width="1001" height="518" alt="image" src="https://github.com/user-attachments/assets/6668a812-564b-472c-8717-4abb92e583d6" />


### 4. Menu Hapus Catatan Keuangan  

<img width="998" height="724" alt="image" src="https://github.com/user-attachments/assets/2f9ce51e-330b-4a68-978a-a1401913bc5e" />

<img width="1045" height="438" alt="image" src="https://github.com/user-attachments/assets/3ccec24b-50e3-4458-8b6f-3104ed8a5a7a" />

>  Ketika  menginputkan angka 4 pada menu utama, sistem akan mengarahkan ke menu Hapus Catatan Keuangan. Pada tahap ini, tabel catatan keuangan akan ditampilkan terlebih dahulu agar tidak terjadi kebingungan mengenai data mana yang ingin dihapus. Setelah tabel ditampilkan, sistem kemudian meminta untuk menginputkan ID catatan yang ingin dihapus atau klik enter untuk membatalkan penghapusan catatan.
>
> Jika kita berubah pikiran, tidak jadi ingin menghapus catatan keuangan maka bisa klik enter saja untuk membatalkan penghapusan dan akan muncul pesan "Penghapusan dibatalkan" dan akan diarahkan lagi ke menu utama program ini, seperti gambar yang tertera di bawah ini.
> 
> <img width="560" height="372" alt="image" src="https://github.com/user-attachments/assets/940b3ef7-ec5c-43a8-a1bd-489427a24b51" />

> Jika ID yang diinputkan sesuai dengan data yang ada, maka sistem akan menampilkan pertanyaan konfirmasi "Apakah Anda yakin ingin menghapus data dengan ID ... (Y/T)?".
> 
> a. Jika  menginputkan "Y"
> 
>  <img width="531" height="108" alt="image" src="https://github.com/user-attachments/assets/765e9670-676f-4baa-9cb1-a1aec2497058" />
>
>   Maka catatan akan dihapus dari daftar, dan sistem menampilkan pesan "Data berhasil dihapus".
>
>   - Tampilan tabel sebelum dihapus datanya
>     <img width="987" height="308" alt="image" src="https://github.com/user-attachments/assets/6141a705-e19c-4652-b2f7-ef0abdd308b0" />
>    
>   - Tampilan tabel setelah di hapus datanya
>     <img width="1000" height="289" alt="image" src="https://github.com/user-attachments/assets/e3e67acc-690e-4c74-9fa3-3895c3bdfa05" />
>
> b. Jika menginputkan "T"
> 
>   <img width="550" height="105" alt="image" src="https://github.com/user-attachments/assets/cecccff0-205f-4406-bb0f-483ed10689ac" />
>
>   Maka proses penghapusan dibatalkan, dan sistem menampilkan pesan "Penghapusan dibatalkan".

Setelah berhasil menghapus data, sistem akan menampilkan pertanyaan "Apakah Ingin Menghapus Catatan Lagi? (Y/T):" seperti terlihat pada gambar di bawah.

  <img width="1006" height="448" alt="image" src="https://github.com/user-attachments/assets/9f3618d5-4345-4936-892d-d81015957710" />

> a. Jika menginputkan "Y"
> 
>   <img width="1009" height="551" alt="image" src="https://github.com/user-attachments/assets/66af7810-6277-41dc-98e3-cb2ad9d5e119" />
>
>  Program akan kembali menampilkan tabel catatan keuangan terbaru, kemudian meminta untuk  menginputkan ID catatan lain yang ingin dihapus. Proses ini dapat dilakukan berulang kali sampai dipilih untuk berhenti. Dengan cara ini, lebih dari satu catatan dapat dihapus dalam satu kali sesi tanpa harus kembali ke menu utama terlebih dahulu.
>
> b. Jika menginputkan "T"
> 
>  <img width="394" height="352" alt="image" src="https://github.com/user-attachments/assets/08b57eb1-5e35-477b-971d-9116a3f91602" />
>
>
>  Program akan langsung kembali ke Menu Utama tanpa menghapus catatan tambahan.

#### Validasi Input Pada Menu "Hapus Catatan Keuangan"

<img width="1024" height="485" alt="image" src="https://github.com/user-attachments/assets/72867780-f83f-4f8e-9a36-7014f33cd9dd" />

> Jika ID yang diinputkan tidak sesuai atau tidak ada dalam daftar catatan keuangan, maka sistem akan menampilkan pesan "ID tidak ditemukan".
>
> Hal ini bertujuan agar tidak terjadi kesalahan dalam menghapus catatan yang tidak ada pada tabel. Setelah itu, sistem tetap memberikan pilihan "Apakah Ingin Menghapus Catatan Lagi? (Y/T):" sehingga dapat dicoba kembali dengan memasukkan ID yang benar, atau keluar dari proses penghapusan dengan menginputkan "T".


<img width="1038" height="422" alt="image" src="https://github.com/user-attachments/assets/5f670a08-9cab-4713-8535-fb659566e937" />

> Jika ID diinputkan dalam bentuk huruf (contoh: mengetik "satu" alih-alih angka 1), maka sistem tidak akan menerima input tersebut dan akan menampilkan pesan "Harus angka! Silakan input ulang:".
>
> Pesan ini berfungsi sebagai validasi agar ID hanya bisa diinputkan dalam bentuk angka sesuai dengan tabel catatan yang tersedia.

### 5. Menu Ringkasan Saldo

<img width="686" height="474" alt="image" src="https://github.com/user-attachments/assets/2e60355e-8fe5-4cf1-b81b-7f5106fc4a0c" />

> Ketika menginputkan angka 5 pada menu utama, sistem akan menampilkan menu Ringkasan Saldo. Pada menu ini ditampilkan rekapitulasi keuangan yang berisi total pemasukan, total pengeluaran, serta saldo akhir yang merupakan selisih dari keduanya. Informasi ini membantu menampilkan kondisi keuangan terkini secara lebih jelas dan ringkas. Setelah ringkasan saldo ditampilkan, sistem akan meminta untuk mengetik angka 0 agar dapat kembali ke menu utama.

<img width="701" height="225" alt="image" src="https://github.com/user-attachments/assets/1080d1c1-cb4b-46b8-a54b-c792eded2da2" />

> Ketika menambahkan catatan pengeluaran dengan jumlah yang melebihi pemasukan, lalu membuka menu Ringkasan Saldo, sistem akan tetap menampilkan total pemasukan, total pengeluaran, dan saldo akhir. Karena nilai pengeluaran lebih besar dibandingkan pemasukan, saldo ditampilkan dalam kondisi negatif. Selain itu, sistem juga memberikan catatan berupa peringatan: “Pengeluaran lebih besar dari pemasukan. Harap bijak mengatur keuangan.” Setelah itu, sistem meminta untuk mengetik angka 0 agar dapat kembali ke menu utama.

### 6. Menu Filter dan Search Catatan

<img width="628" height="514" alt="image" src="https://github.com/user-attachments/assets/655b7415-3cac-417f-8ba4-846db2ef18c7" />

> Ketika menginputkan angka 6 pada menu utama, sistem akan menampilkan menu filter/search. Pada menu ini tersedia beberapa pilihan filter dan search (berdasarkan keterangan), untuk pilihan filter yaitu ada filter per jenis transaksi (pemasukan atau pengeluaran), filter per kategori, dan filter per metode pembayaran. Selain itu, juga tersedia opsi untuk kembali ke menu sebelumnya. Melalui menu ini, catatan keuangan dapat disaring sesuai kriteria tertentu agar informasi yang ditampilkan lebih fokus dan mudah dipahami.

a. Filter per Jenis (Pemasukan/Pengeluaran) 

  <img width="685" height="294" alt="image" src="https://github.com/user-attachments/assets/0a5138b5-f668-47ae-9423-3923062de9c9" />

  > Setelah memilih opsi 1. Filter per Jenis (Pemasukan/Pengeluaran) pada menu filter/search, sistem akan menampilkan tampilan baru bertuliskan Filter berdasarkan Jenis. Pada tahap ini, sistem meminta input jenis transaksi yang ingin difilter, apakah termasuk pemasukan atau pengeluaran. Input tersebut akan digunakan untuk menampilkan daftar catatan keuangan sesuai jenis yang dipilih sehingga data lebih terfokus.

- Pemasukan
  
  <img width="1013" height="255" alt="image" src="https://github.com/user-attachments/assets/24f57eb7-3956-43ff-90e5-759c3ebb0ca7" />
  
  > Setelah memilih jenis transaksi Pemasukan, sistem akan menampilkan daftar catatan keuangan yang hanya berisi transaksi dengan jenis tersebut. Tabel yang ditampilkan memuat detail berupa ID, tanggal, jenis, kategori, metode, jumlah, serta keterangan dari setiap transaksi pemasukan. Dari hasil filter terlihat bahwa hanya transaksi dengan kategori gaji maupun tabungan yang masuk dalam daftar. Setelah selesai melihat data, dapat diketik angka 0 untuk kembali ke menu sebelumnya.

- Pengeluaran
  
  <img width="1024" height="308" alt="image" src="https://github.com/user-attachments/assets/4175bc72-9c95-4eec-944e-321486b2d114" />

  > Setelah memilih jenis transaksi Pengeluaran, sistem menampilkan daftar catatan keuangan yang hanya berisi transaksi dengan jenis pengeluaran. Tabel yang ditampilkan berisi detail ID, tanggal, jenis, kategori, metode, jumlah, serta keterangan dari setiap transaksi. Dari hasil filter terlihat bahwa data pengeluaran meliputi kebutuhan sehari-hari seperti makan, transportasi, hiburan, belanja, serta tagihan. Dengan tampilan ini, semua transaksi pengeluaran dapat diamati secara lebih jelas tanpa bercampur dengan pemasukan. Setelah selesai, cukup mengetik angka 0 untuk kembali ke menu sebelumnya.

- Selain pilihan pemasukan dan pengeluaran
  
  <img width="673" height="118" alt="image" src="https://github.com/user-attachments/assets/acb5f4f7-8f5a-42ed-bffe-0fa9d19d8970" />

  > Jika pada filter jenis transaksi dimasukkan selain pilihan Pemasukan atau Pengeluaran, misalnya kata pendapatan, maka sistem akan menampilkan pesan“ Pilihan tidak valid. Pilihan yang valid: Pemasukan/Pengeluaran”. Setelah itu, sistem secara otomatis akan meminta input ulang yang benar yaitu "Pemasukan/Pengeluaran".

- Pada filter berdasarkan jenis, jika mengosongkan inputan "Masukan Jenis (Pemasukan/Pengeluaran). Maka akan muncul pesan peringatan yaitu "Tidak boleh kosong. Coba lagi", dan akan diminta untuk menginputkan ulang jenis yang ingin di filter.

  <img width="681" height="127" alt="image" src="https://github.com/user-attachments/assets/b52560ec-c886-46aa-932d-445b791e5251" />


b. Filter per Kategori  

  <img width="716" height="288" alt="image" src="https://github.com/user-attachments/assets/f9e842f5-eea3-434f-9940-27be111e86d7" />


  > Ketika memilih opsi Filter per Kategori pada menu filter/search, sistem akan menampilkan pilihan untuk memasukkan kategori transaksi. Kategori yang tersedia antara lain gaji, makan, transportasi, hiburan, belanja, tabungan, dan tagihan. Setelah kategori dimasukkan, sistem akan menampilkan catatan transaksi yang sesuai dengan kategori tersebut dalam bentuk tabel, sehingga lebih mudah untuk melihat pengeluaran atau pemasukan berdasarkan kategori tertentu.

- Kategori gaji
  
  <img width="1019" height="210" alt="image" src="https://github.com/user-attachments/assets/4dc47c9e-072a-41cd-92a9-4240bb77cce5" />

  > Ketika memilih kategori gaji, sistem akan menampilkan daftar transaksi yang termasuk dalam kategori tersebut. Pada tampilan terlihat catatan pemasukan pada tanggal 1 September 2025 dengan metode transfer sebesar Rp 3.000.000 yang tercatat sebagai Gaji Bulan September. Setelah data ditampilkan, tersedia perintah untuk mengetik angka 0 agar bisa kembali ke menu sebelumnya.

- Kategori makan
  
  <img width="1008" height="214" alt="image" src="https://github.com/user-attachments/assets/7dae145d-325a-4fab-a905-65ef1f65300b" />

  > Ketika memilih kategori makan, sistem akan menampilkan data transaksi yang sesuai dengan kategori tersebut. Pada hasil filter terlihat satu catatan pengeluaran pada tanggal 2 September 2025 dengan metode pembayaran cash sebesar Rp 25.000, yang tercatat sebagai Beli Makan Siang. Setelah data ditampilkan, sistem memberikan opsi untuk mengetik angka 0 agar dapat kembali ke menu sebelumnya.
  
- Kategori transportasi
  
  <img width="1003" height="215" alt="image" src="https://github.com/user-attachments/assets/e1533edb-284f-426f-a00b-fb69bce4c928" />
  
  > Ketika memilih kategori transportasi, sistem akan menampilkan data transaksi yang sesuai dengan kategori tersebut. Pada hasil filter terlihat satu catatan pengeluaran pada tanggal 3 September 2025 dengan metode pembayaran cash sebesar Rp 10.000, yang tercatat sebagai Ongkos Transportasi. Setelah data ditampilkan, sistem akan meminta untuk mengetik angka 0 agar dapat kembali ke menu sebelumnya.

- Kategori hiburan
  
  <img width="1009" height="214" alt="image" src="https://github.com/user-attachments/assets/03ce37e8-0027-421b-9be9-3e5c7dbab591" />

  > Ketika memilih kategori hiburan, sistem akan menampilkan transaksi yang tercatat dalam kategori tersebut. Pada hasil filter terlihat satu catatan pengeluaran pada tanggal 4 September 2025 dengan metode pembayaran E-Wallet sebesar Rp 50.000, yang digunakan untuk kegiatan nonton bioskop. Setelah informasi ditampilkan, sistem memberikan opsi untuk mengetik angka 0 agar dapat kembali ke menu sebelumnya.

- Kategori belanja
  
  <img width="1005" height="216" alt="image" src="https://github.com/user-attachments/assets/4fa0a197-ffb1-4d67-a579-6d45e3353329" />

  > Ketika memilih kategori belanja, sistem akan menampilkan catatan transaksi yang termasuk dalam kategori tersebut. Pada hasil filter terlihat satu transaksi pengeluaran yang terjadi pada tanggal 5 September 2025 dengan metode pembayaran transfer sebesar Rp 200.000, yang digunakan untuk membeli pakaian. Setelah data ini ditampilkan, sistem memberikan opsi untuk mengetik angka 0 agar dapat kembali ke menu sebelumnya.

- Kategori tabungan
  
  <img width="1029" height="238" alt="image" src="https://github.com/user-attachments/assets/c7e691ba-19bb-48f4-b4f5-e80d056e9a96" />

  > Ketika memilih kategori tabungan, sistem akan menampilkan daftar transaksi yang berkaitan dengan tabungan. Dari hasil filter terlihat ada dua transaksi pemasukan. Transaksi pertama terjadi pada tanggal 6 September 2025 sebesar Rp 500.000 dengan metode transfer, yang dicatat sebagai kegiatan menabung rutin. Transaksi kedua terjadi pada tanggal 9 September 2025 sebesar Rp 300.000 dengan metode transfer, yang dicatat sebagai isi saldo tabungan. Setelah data ditampilkan, sistem menunggu input angka 0 untuk kembali ke menu sebelumnya.

- Kategori tagihan
  
  <img width="1006" height="238" alt="image" src="https://github.com/user-attachments/assets/69386296-20ab-436e-bf40-626b39e72146" />

  > Ketika memilih kategori tagihan, sistem menampilkan dua transaksi pengeluaran. Transaksi pertama tercatat pada tanggal 7 September 2025 sebesar Rp 150.000 dengan metode E-Wallet, digunakan untuk membayar listrik. Transaksi kedua terjadi pada tanggal 8 September 2025 sebesar Rp 100.000 dengan metode transfer, digunakan untuk membayar air. Setelah daftar transaksi tagihan ditampilkan, sistem menunggu input angka 0 untuk kembali ke menu sebelumnya.

- Selain yang ada di pilihan kategori
  
  <img width="806" height="128" alt="image" src="https://github.com/user-attachments/assets/e1f5e12e-96f9-4907-a163-0068a9c9cc50" />

   > Ketika memasukkan kategori yang tidak tersedia dalam daftar pilihan, misalnya sedekah, sistem akan menampilkan pesan "Pilihan tidak valid. Pilihan yang valid: Gaji/Makan/Transportasi/Hiburan/Belanja/Tabungan/Tagihan". Dengan begitu, hanya kategori yang memang tercatat dalam sistem seperti gaji, makan, transportasi, hiburan, belanja, tabungan, atau tagihan yang dapat difilter. Setelah itu, tampilan akan kembali meminta untuk menginputkan kategori sesuai kategori yang ada.

- Pada filter kategori, jika mengosongkan inputan "Masukkan Kategori (gaji, makan, transportasi, hiburan, belanja, tabungan, tagihan):", maka akan muncul pesan peringatan yaitu "Tidak boleh kosong. Coba lagi", dan akan diminta untuk menginputkan ulang kategori yang ingin di filter.

  <img width="728" height="121" alt="image" src="https://github.com/user-attachments/assets/16f8cb25-9561-4952-8fc5-41fe7bfa542d" />

c. Filter per Metode Pembayaran 

   <img width="678" height="293" alt="image" src="https://github.com/user-attachments/assets/62430ead-a506-4378-a6c2-53ff27f83d65" />


  > Ketika memilih menu Filter per Metode Pembayaran pada menu filter/search, sistem akan menampilkan opsi untuk memasukkan metode pembayaran, yaitu Cash, E-Wallet, atau Transfer.

- Cash
  
  <img width="1025" height="233" alt="image" src="https://github.com/user-attachments/assets/3f97f153-3452-4f0a-bb29-b3541e66cb98" />

  > Ketika memilih metode pembayaran Cash, sistem akan menampilkan daftar transaksi yang menggunakan metode pembayaran tersebut. Pada tampilan terlihat dua catatan pengeluaran, yaitu transaksi makan dengan nominal Rp 25.000 dan transaksi transportasi dengan nominal Rp 10.000. Setelah data ditampilkan, tersedia perintah untuk mengetik angka 0 agar bisa kembali ke menu sebelumnya.

- Transfer
  
  <img width="1037" height="295" alt="image" src="https://github.com/user-attachments/assets/444926c9-c446-4f7b-9cb1-efbca08994ae" />

  > Ketika memilih metode pembayaran Transfer, sistem akan menampilkan daftar transaksi yang menggunakan metode tersebut. Pada tampilan terlihat beberapa catatan, di antaranya pemasukan gaji sebesar Rp 3.000.000, pengeluaran belanja sebesar Rp 200.000, pemasukan tabungan sebesar Rp 500.000, pembayaran tagihan air sebesar Rp 100.000, serta pemasukan tabungan sebesar Rp 300.000. Seluruh transaksi ditampilkan dalam bentuk tabel agar lebih jelas, dan setelah itu tersedia perintah untuk mengetik angka 0 agar bisa kembali ke menu sebelumnya.

- E-Wallet
  
  <img width="1015" height="242" alt="image" src="https://github.com/user-attachments/assets/4ab75684-8f54-4050-be4d-5fc08afee3d3" />

  > Ketika memilih metode pembayaran E-Wallet, sistem akan menampilkan daftar transaksi yang dilakukan menggunakan dompet digital. Pada tabel terlihat dua catatan pengeluaran, yaitu sebesar Rp 50.000 untuk hiburan menonton bioskop dan Rp 150.000 untuk pembayaran tagihan listrik. Seluruh data ditampilkan dengan format tabel agar mudah dibaca, dan setelah selesai tersedia instruksi untuk mengetik angka 0 agar kembali ke menu sebelumnya.

- Selain yang ada di pilihan metode pembayaran
  
  <img width="675" height="114" alt="image" src="https://github.com/user-attachments/assets/02fbf1c0-e75e-452b-8695-04aa5240e6e7" />

   > Ketika pada menu filter dimasukkan metode pembayaran yang tidak tersedia, misalnya “Kartu debit”, sistem akan langsung menampilkan pesan bahwa "Pilihan tidak valid. Pilihan yang valid: Cash/E-Wallet/Transfer". Setelah itu, sistem akan menampilkan untuk meminta ulang input metode pembayaran yang tersedia.

- Pada filter metode pembayaran, jika mengosongkan inputan "Masukkan Metode (Cash/E-Wallet/Transfer):", maka akan muncul pesan peringatan yaitu "Tidak boleh kosong. Coba lagi", dan akan diminta untuk menginputkan ulang metode pembayaran yang ingin di filter.

  <img width="682" height="121" alt="image" src="https://github.com/user-attachments/assets/eb0676d8-a796-44a0-b25a-4f152e42dfbe" />

d. Search (cari di keterangan)  

<img width="682" height="292" alt="image" src="https://github.com/user-attachments/assets/7d890f9c-d9b7-4afd-99ff-ff973ff32bd4" />

> Pada menu Filter/Search dipilih opsi 4. Search (cari di keterangan). Sistem menampilkan header SEARCH KETERANGAN dan meminta input “Kata kunci:” untuk memulai pencarian pada kolom keterangan transaksi.

<img width="999" height="230" alt="image" src="https://github.com/user-attachments/assets/fe6fb5a0-4fcf-4811-89cb-5510f59989a6" />

> Input kata kunci: “makan”. Sistem melakukan pencarian case-insensitive pada kolom keterangan, lalu menampilkan tabel hasil yang cocok (ID, Tanggal, Jenis, Kategori, Metode, Jumlah, Keterangan). Tampil dua catatan transaksi yang mengandung kata “makan”. Di bagian bawah tabel terdapat prompt “-> Ketik 0 untuk kembali” untuk kembali ke menu.

<img width="689" height="148" alt="image" src="https://github.com/user-attachments/assets/68f52940-d063-447c-9886-387cbf9902d4" />

> Input kata kunci: “bayar utang”. Sistem tidak menemukan catatan transaksi dengan keterangan yang memuat frasa tersebut, sehingga muncul pesan “Tidak ada data dengan hasil pencarian.” dan tetap menampilkan opsi “-> Ketik 0 untuk kembali” ke menu sebelumnya.

<img width="685" height="127" alt="image" src="https://github.com/user-attachments/assets/e826ca27-510f-4694-9c69-1bee409eb77e" />

> Saat masuk ke menu SEARCH KETERANGAN, tombol Enter ditekan tanpa mengisi kata kunci. Sistem mendeteksi input kosong lalu menampilkan pesan “Tidak boleh kosong. Coba lagi”. Setelah itu, sistem kembali meminta input “-> Kata kunci:” hingga nilai yang dimasukkan valid.

e. Kembali

  <img width="642" height="522" alt="image" src="https://github.com/user-attachments/assets/92fa30e3-292b-49f6-8ac1-c01bf6863bed" />

  > Ketika pada menu filter dipilih opsi nomor 5, sistem akan mengembalikan tampilan ke menu utama. Dengan begitu, proses penyaringan catatan dapat dihentikan sementara dan navigasi diarahkan kembali ke pilihan utama aplikasi, seperti menambah catatan keuangan, melihat daftar catatan, mengubah, menghapus, hingga ringkasan saldo. Fitur ini berfungsi sebagai jalan pintas agar tidak perlu menutup aplikasi saat ingin berpindah dari menu filter dan search ke menu utama.

f. Jika menginputkan selain menu 1-5

  <img width="629" height="450" alt="image" src="https://github.com/user-attachments/assets/516b43f7-3075-4e1d-93b8-e86c7f80a4c4" />

  > Apabila pada menu filter dimasukkan angka di luar pilihan 1 sampai 5, sistem akan langsung menampilkan pesan “Pilihan tidak valid”. Setelah itu, menu filter catatan ditampilkan kembali sehingga dapat memilih opsi yang benar sesuai dengan daftar yang tersedia. Hal ini memastikan agar hanya input yang sesuai dengan menu yang bisa diproses oleh sistem.

g. Jika menginputkan menu pakai huruf bukan angka

  <img width="627" height="223" alt="image" src="https://github.com/user-attachments/assets/0da41826-f2a1-4983-b749-a9f45bef5db1" />

  > Apabila pada menu filter dimasukkan huruf alih-alih angka, sistem akan langsung menolak input tersebut dengan menampilkan pesan “Harus angka! Silakan input ulang”. Dengan begitu, hanya input berupa angka yang valid sesuai pilihan menu 1 sampai 4 yang bisa diterima. Mekanisme ini dibuat untuk memastikan agar sistem tetap berjalan sesuai alur yang benar dan menghindari kesalahan input.

h. Jika mengosongkan input pada menu

<img width="642" height="221" alt="image" src="https://github.com/user-attachments/assets/cd658bc2-873a-428e-8b33-469f9fa152e4" />

Maka akan muncul pesan "Harus angka! Silakan input ulang:".


### 7. Menu Set Batas Pengeluaran

<img width="697" height="420" alt="image" src="https://github.com/user-attachments/assets/9c7eaf12-58ae-4787-91b2-1298c2fa5819" />

> Ketika menginputkan angka 7 pada menu utama, sistem akan menampilkan menu Set Batas Pengeluaran Bulanan. Pada menu ini, ditunjukkan terlebih dahulu batas pengeluaran saat ini. Jika batas belum pernah ditentukan, maka statusnya akan ditampilkan sebagai “tidak diaktifkan”. Selanjutnya, diminta untuk memasukkan batas baru sesuai kebutuhan, atau mengetik angka 0 apabila ingin menonaktifkan fitur batas pengeluaran.

<img width="715" height="195" alt="image" src="https://github.com/user-attachments/assets/529ef75f-34ed-42e2-8f88-1a625e7e4991" />

> Setelah memasukkan batas pengeluaran baru, sistem akan menampilkan informasi yang lebih detail. Batas pengeluaran ditetapkan sesuai angka yang dimasukkan, misalnya Rp 1.000.000. Kemudian, sistem menampilkan total pengeluaran saat ini, yaitu Rp 535.000. Dari data tersebut, dihitung sisa ruang anggaran sebesar Rp 465.000. Informasi ini membantu dalam memantau sejauh mana pengeluaran mendekati batas yang sudah ditentukan. Setelah itu, dapat mengetik angka 0 untuk kembali ke menu utama.

<img width="733" height="218" alt="image" src="https://github.com/user-attachments/assets/5cc2fd79-04b4-4ba8-bd90-8cb28cff1bc8" />

> Ketika batas pengeluaran baru ditetapkan sebesar Rp 1.000.000, sistem langsung membandingkannya dengan total pengeluaran yang sudah tercatat. Dari hasil perhitungan, total pengeluaran mencapai Rp 4.035.000, yang berarti jauh melebihi batas yang telah ditentukan. Akibatnya, sisa ruang anggaran menjadi negatif, yaitu Rp -3.035.000. Sistem kemudian memberikan peringatan dengan jelas berupa pesan: “Pengeluaran sudah melebihi batas !!!”. Hal ini berfungsi sebagai pengingat agar lebih berhati-hati dalam mengatur keuangan. Setelah informasi ini ditampilkan, dapat mengetik angka 0 untuk kembali ke menu utama.

<img width="706" height="162" alt="image" src="https://github.com/user-attachments/assets/f7adb9fd-b96a-4b6f-8d75-068e41b4ae9e" />

> Ketika batas pengeluaran diatur dengan nilai 0, sistem akan secara otomatis menonaktifkan fitur pembatasan pengeluaran bulanan. Setelah itu, ditampilkan pesan konfirmasi berupa “Batas pengeluaran bulanan dinonaktifkan” sebagai tanda bahwa pengaturan sebelumnya tidak lagi berlaku. Untuk kembali ke menu utama, cukup mengetik angka 0 sesuai instruksi yang diberikan sistem.

<img width="688" height="150" alt="image" src="https://github.com/user-attachments/assets/04b689b2-6cb4-4ff9-be2d-d9f1fe62f9a1" />

> Ketika mengosongkan input "Masukkan batas baru (ketik 0 untuk menonaktifkan):", makan akan muncul pesan "Tidak boleh kosong. Coba lagi", sehingga hanya boleh mengisi batas pengeluaran terbaru atau ketik 0 untuk menonaktifkan.

<img width="675" height="133" alt="image" src="https://github.com/user-attachments/assets/e65fd4c4-af86-4bf2-a6fe-5db1148ab43c" />

> Ketika menginputkan batas pengeluaran dengan angka negatif, maka akan muncul pesan "Tidak boleh negatif. Coba lagi" dan sistem akan meminta menginputkan ulang batas pengeluaran atau input 0 untuk menonaktifkan.


### 8. Menu Keluar

<img width="454" height="401" alt="image" src="https://github.com/user-attachments/assets/d0652801-2e8f-47f5-9db6-a739c1f7b7ce" />

> Ketika menginputkan angka 8 pada menu utama, sistem akan langsung menutup aplikasi Pocket Guard. Sebelum keluar, ditampilkan pesan ucapan terima kasih berupa “Terima kasih telah menggunakan POCKET GUARD” serta doa agar keuangan selalu aman dan terjaga. Dengan begitu, aplikasi benar-benar mengakhiri jalannya program setelah perintah keluar dipilih.

### 9. Jika Menginputkan Menu Selain Menu 1-8, Menginputkan Menu Pakai Huruf Bukan Angka, dan Mengosongkan inputan pada saat input menu 1-8

<img width="430" height="702" alt="image" src="https://github.com/user-attachments/assets/640fee0c-2940-4da6-8931-8cde3526e169" />

> Ketika menginputkan angka di luar rentang 1 sampai 8 pada menu utama, sistem akan menampilkan pesan “Pilihan tidak valid. Silakan coba lagi!!!” lalu mengembalikan tampilan ke menu utama agar dapat memilih ulang menu yang benar.


<img width="431" height="326" alt="image" src="https://github.com/user-attachments/assets/5e558d4d-c4b3-4581-b535-eaf94c632bc6" />

> Selain itu, jika input yang dimasukkan berupa huruf atau teks alih-alih angka, sistem akan menolak dengan menampilkan pesan “Harus angka! Silakan input ulang:” kemudian meminta masukan baru sampai format yang dimasukkan benar berupa angka dalam rentang 1–8.


<img width="404" height="325" alt="image" src="https://github.com/user-attachments/assets/325cdbbe-ea57-43c5-a232-41ac93870e5a" />

> Jika input yang dimasukkan kosong atau bukan angka, sistem akan menolak dengan menampilkan pesan “Harus angka! Silakan input ulang:”, lalu meminta pengguna untuk memasukkan kembali pilihan menu dalam bentuk angka 1–8.


