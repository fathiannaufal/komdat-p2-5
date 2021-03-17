# Aplikasi Web "Known"
![full_logo_blk](https://user-images.githubusercontent.com/60083946/111310174-5c2f9680-868f-11eb-9b66-655f14394381.png)

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:

## Anggota
<table>
    <thead>
        <tr>
            <th></th>
            <th>Nama</th>
            <th>Nim</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>Indra Rizky Gunawan</td>
            <td>G64180010</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Ihsan Firdaus</td>
            <td>G64180054</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Fathi Annaufal Soblia</td>
            <td>G64180094</td>
        </tr>
        <tr>
            <td>4</td>
            <td>Muhammad Dwiki Ramdhani</td>
            <td>G64180032</td>
        </tr>
</tbody>
</table>

## Sekilas Tentang

[`^ kembali ke atas ^`](#)

**Known** merupakan social group platform yang memungkinkan sejumlah pengguna untuk membuat sejumlah postingan, update status, foto dan banyak lagi. Known merupakan open source project yang dapat digunakan untuk membangun situs komunitas yang lengkap, atau blog untuk satu pengguna.

**Known** memiliki fitur antara lain :
- Bookmarklet
- Tags
- Responsive layout
- Email notification
- Multi-author
- HTML & Rich Text Editor
- Static Pages

## Instalasi

[`^ kembali ke atas ^`](#)

#### Kebutuhan sistem:
- A Web Server that supports URL rewriting (Apache + mod_rewrite recommended).
- If you are using Apache, you also need to make sure support for .htaccess is enabled (using the AllowOverride All directive).
- PHP 7.3 or above.
- MySQL 5+ / MariaDB or MongoDB. We recommend MySQL.

#### Proses Instalasi :

1. Login ke dalam vm lokal menggunakan ssh.
```
 $ ssh student@localhost -p 2200
```

2. Install seluruh kebutuhan sistem seperti `Apache`, `PHP`, dan `MySQL`. Pastikan juga sistem kita sudah update dengan versi terbaru.
```
 $ sudo apt-get install apache2
 $ sudo apt-get install mysql-server
 $ sudo apt-get install php
 $ sudo apt-get install php-curl php-xml php-gd php-mbstring php-mysql
 $ sudo apt-get install unzip
```

3. Unduh **Known** ke direktori kita, lalu ekstrak ke folder `/var/www/html` dan jangan lupa ubah otorisasi.
```
 $ wget "https://withknown.marcus-povey.co.uk/known-1.2.2.zip"
 $ sudo unzip known-1.2.2.zip -d /var/www/html/known
 $ sudo chown -R www-data:www-data /var/www/html/known
```

4. Buat database beserta user untuk `Known`.
```
sudo mysql -u root -ve "
  CREATE DATABASE knownsite;
  CREATE USER knownsite IDENTIFIED BY 'knownpass';
  GRANT ALL PRIVILEGES ON knownsite.* TO knownsite;
FLUSH PRIVILEGES;"
```

5. Set `AllowOverride` menjadi `All` pada apache agar `Known` dapat berjalan dengan baik.
```
 $ cd /etc/apache2
 $ sudo nano apache2.conf
```
![edit-apache](https://github.com/ihsanfir/komdat-p2-5/blob/main/image/edit-apache2.png)

6. Restart kembali Apache Web Server.
```
 $ sudo service apache2 restart
```
7. Kunjungi `localhost/8000/known` menggunakan web browser untuk melanjutkan instalasi.
    - Tampilan Awal
![1](https://raw.githubusercontent.com/ihsanfir/komdat-p2-5/main/image/tampilan-awal.png)
    - Halamanan untuk mengecek requirement yang dibutuhkan, pastikan tidak ada yang berwarna merah
![2](https://github.com/ihsanfir/komdat-p2-5/blob/main/image/requirement.png)
    - Setup database dan nama web
![3](https://github.com/ihsanfir/komdat-p2-5/blob/main/image/setting-site.png)
    - Membuat akun untuk admin
![4](https://github.com/ihsanfir/komdat-p2-5/blob/main/image/akun-admin.png)
    - Known berhasil di install
![5](https://github.com/ihsanfir/komdat-p2-5/blob/main/image/get-started.png)

## Cara Pemakaian

[`^ kembali ke atas ^`](#)

Cara menggunakan **Known** cukup mudah, karena tampilannya masih sederhana sehingga mudah dipahami oleh pengguna. Meskipun sederhana tetapi terdapat plugin yang dapat diaktifkan. Berikut cara pemakaiannya :
1. Tampilan awal setelah installasi berhasil, di sini kita sebagai admin.

![halaman-depan](https://raw.githubusercontent.com/ihsanfir/komdat-p2-5/main/image/tampilan-depan.png)

2. Kita bisa mengatur website sesuai dengan kebutuhan pada menu site configuration.

![setting](https://raw.githubusercontent.com/ihsanfir/komdat-p2-5/main/image/konfigurasi.png)

3. Terdapat juga plugin yang bisa diaktifkan sesuai kebutuhan.

![plugin](https://raw.githubusercontent.com/ihsanfir/komdat-p2-5/main/image/mengatur-plugin.png)

4. Kita juga dapat memilih tema, terdapat beberapa pilihan tema yang dapat digunakan.

![tema](https://raw.githubusercontent.com/ihsanfir/komdat-p2-5/main/image/pilih-tema.png)

5. Selain tema bawaan, kita juga bisa melakukan custom sendiri dengan mengupload file css jika plugin css diaktifkan.

![css](https://raw.githubusercontent.com/ihsanfir/komdat-p2-5/main/image/custom-css.png)

6. Pada `Known` terdapat fitur-fitur yang mirip seperti sosial media yang sudah ada, seperti update status, mengupload musik, membagikan video dari web lain bahkan membuat sebuah post yang tentunya dapat dibagikan kepada pengguna terdaftar.

![post](https://raw.githubusercontent.com/ihsanfir/komdat-p2-5/main/image/post.png)

7. Berikut beberapa post dan status yang telah di submit oleh admin.

![halaman-akhir](https://raw.githubusercontent.com/ihsanfir/komdat-p2-5/main/image/halaman%20selesai.png)

## Pembahasan

[`^ kembali ke atas ^`](#)

**Known** menggunakan bahasa `PHP` yang mendukung penggunaan MySQL, meskipun namanya terdengar awam tetapi terdapat beberapa kelebihan, diantaranya :
- Aplikasi merupakan `opensource` sehingga dapat digunakan secara gratis, dan tentunya dapat di kustomisasi sesuai kebutuhan.
- Dapat digunakan sebagai media sosial yang dikhususkan untuk sebuah komunitas.
- Know memiliki fitur multi author.
- Bisa digunakan sebagai blog probadi.
- Dapat kustomisasi tema dengan mengupload css buatan sendiri.

Meskipun memiliki beberapa kelebihan, tetapi terdapat beberapa kekurangan, diantaranya :
- Pilihan tema yang disajikan masih terbilang sedikit dan sederhana
- Plugin yang tersedia masih kurang powerfull
- Kustomisasi tampilan terbilang cukup sulit jika hanya menggunakan upload file css untuk orang awam.

Jika dibandingkan dengan **Wordpress**, **Known** bisa dikatakan masih terbilang cukup jauh. Berikut perbandingan antara keduanya :
- **Wordpress** lebih familiar dikalangan masyarakat sedangkan **Known** masih belum cukup terkenal
- Pada **Wordpress** terdapat banyak plugin yang dapat digunakan dan cukup powerfull sehingga memudahkan pengguna.
- **Wordpress** mempunyai pilihan tema yangn banyak dan lebih modern, serta banyak orang-orang yang sering memperjual belikan temanya sedangkan **Known**, selain pilihan tema yang sedikit, kustomisasi yang digunakan juga hanya sebatas pada mengupload file css.
- **Known** mungkin lebih fleksibel karena dapat digunakan untuk berbagai macam mode, sedangkan **Wordpress** harus menginstall beberapa plugin jika ingin merubah ke mode-mode lainnya.
- Dalam proses instalasi, keduanya sangat mudah dan dapat dikatakan hampir mirip.

## Referensi

[`^ kembali ke atas ^`](#)

1. [About Known](https://withknown.com/) - Known
2. [Known Documentation](http://docs.withknown.com/en/latest/install/requirements/) - Known
3. [Activate AllowOverride](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles) - Help Ubuntu
