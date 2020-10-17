# Jarkom Modul1 Lapres B11

## Soal
Terdapat tiga buah file *.pcapng yang mendukung soal-soal display filter, yaitu:
- File pertama untuk menjawab soal nomor 1-5 dan nomor 10.
- File kedua untuk menjawab soal nomor 6, 7, dan 9.
- File ketiga untuk menjawab soal nomor 8.

#### A. Display Filter
1. Sebutkan webserver yang digunakan pada "testing.mekanis.me"!
2. Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"!
3. Cari username dan password ketika login di "ppid.dpr.go.id"!
4. Temukan paket dari web-web yang menggunakan basic authentication method!
5. Ikuti perintah di aku.pengen.pw! Username dan password bisa didapatkan dari file .pcapng!
6. Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file zipkey.txt (passwordnya adalah isi dari file txt tersebut).
7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 1.zip, 2.zip, ..., 500.zip. Salah satunya berisi pdf yang berisi puisi. Simpan dan Buka file pdf tersebut. Your Super Mega Ultra Rare Hint = nama pdf-nya "Yes.pdf"
8. Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service!
9. Cari username dan password ketika login FTP pada localhost!
10. Cari file .pdf di wireshark lalu download dan buka file tersebut! clue: "25 50 44 46"

#### B. Capture Filter
11. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
12. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
14. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
15. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke monta.if.its.ac.id!


## Jawaban

2. Masukan kode `http.request.method =="GET"` ke filter di wireshark
![Gambar 2.1](img/2_1.png)
lalu di export http pada paket tersebut di .
![Gambar 2.2](img/2_2.png)
setelah di export save dan buka filenya. hasil =
![DPR](img/2_dpr.jpg)

3. Unutk tahu username dan password ketika logind apat dicari dengan memasukkan `http.request.methid == POST`
![Gambar 3.1](img/3_1.png)

4. Masukkan `http.authbasic` di filter wireshark. hasil :
![Gambar 4.1](img/4_1.png)

5. untuk mencari username dan password aku.pengen.pw dapat dicari dengan memasukkan `http.host.contains "aku.pengen.pw"`
![gambar 5.1](img/5_1.png)


6. Gunakan `ftp-data` lalu menggunakan ctrl+f untuk mencari file .zip nya
![gambar](img/6_1.png)
untuk menemukna pass nya tinggal cari juga dengan ctrl+f lalu ketik .txt
![gambar](img/6_2.png)
Hasil export :
![gambar](img/6_3.png)

7. Untuk mencari file tersebut yang dilakukan pertama yaitu input `ftp-data containes "yes.pdf"`
hasil :
![gambar 7.1](img/7_1.png)
lalu klik kanan dan follow akan keluar seperti ini = 
![gambar 7.2](img/7_2.png)

llau ke tcp stream -> raw dan save as saja, lalu buka file akan keluar hasil seperti berikut =
![gambar 7.3](img/7_3.png)



11. tinggal input `src port 21`
hasil sebagai berikut =
![gambar 11](img/11_1.png)

13. tinggal input `dst port 443`
hasil sebagai berikut =
![gambar 13](img/13_1.png)

15. tinggal input `dst host monta.if.its.ac.id`
hasil sebagai berikut =
![gambar 15](img/15_1.png)
