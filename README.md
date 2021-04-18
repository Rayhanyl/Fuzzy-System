# Fuzzy-System
Untuk pemecahan masalah pada data hasil penerimaan pegawai berdasarkan hasil tes kompetensi dan kepribadiannya. Dibutuhkan system penentuan diterima atau tidaknya dari 10 data pelamar menggunakan konsep Fuzzy Logic System dengan menggunakan metode Mamdani. Proses pengambilan keputusan dengan menggunakan Metode Fuzzy Mamdani untuk memperoleh keputusan data pelamar yang akan diterima, dilakukan dengan melalui beberapa tahapan yang secara garis besar terdiri dari input skala parameter dan himpunan fuzzy, proses rules fuzzy dan output yang berupa grafik parameter. 
Dari data pelamar tersebut ada dua parameter yang dijadikan pengujian untuk diterimanya seorang pelamar kerja. dibuat 3 Himpunan Fuzzy untuk setiap parameter beserta input sebagai berikut : 

Tes Kompetensi : Skala(100)
-	Rendah [0,60]
-	Sedang [50,70]
-	Tinggi [80,100]
Kepribadian : Skala(100)
-	Buruk [0,65]
-	Cukup [55,75]
-	Baik [85,100]

Berikut adalah tahapan pada prosedur fussy system mamdani yaitu:
1.	Memanggil Method Fuzzy List, Memasukan Data (Test/Train), lalu diproses sesuai skala dan Himpunan fuzzy yang di input di awal.
2.	Ouput berupa list kompetensi dan kepribadian
3.	Masuk ke Method Fuzzy Rules, menampung list kompetensi dan kepribadian lalu diproses berdasarkan Fuzzy Rules yang sudah dibuat 
for x in range(len(data)) :
      tidak = []
      ya = []
      tidak.append(np.minimum(kompetensi[x]["Rendah"], kepribadian[x]["Buruk"]))
      tidak.append(np.minimum(kompetensi[x]["Sedang"], kepribadian[x]["Buruk"]))
      tidak.append(np.minimum(kompetensi[x]["Tinggi"], kepribadian[x]["Buruk"]))
      
      tidak.append(np.minimum(kompetensi[x]["Rendah"], kepribadian[x]["Cukup"]))
      ya.append(np.minimum(kompetensi[x]["Sedang"], kepribadian[x]["Cukup"]))
      ya.append(np.minimum(kompetensi[x]["Tinggi"], kepribadian[x]["Cukup"]))
      
      tidak.append(np.minimum(kompetensi[x]["Rendah"], kepribadian[x]["Baik"]))
      ya.append(np.minimum(kompetensi[x]["Sedang"], kepribadian[x]["Baik"]))
      ya.append(np.minimum(kompetensi[x]["Tinggi"], kepribadian[x]["Baik"]))
      listK = {"Tidak" : np.max(tidak),"Ya" : np.max(ya)}
      kelayakan.append(listK)
    return kelayakan

4.	Ouput berupa list kelayakan pelamar kerja
5.	Memanggil Method defuzzification, menampung list kelayakan lalu di proses di Method Mamdani yang mengoutputkan nilai Kelayakan
6.	Apabila Nilai Kelayakan > 60 maka pelamar diterima, dan apabila < 60 maka tidak diterima.

Skala Kompetensi (0-n) : 100
Rendah < Rendah-Sedang < Sedang-Tinggi < Tinggi
Parameter Rendah : 60
Parameter Rendah-Sedang : 70
Parameter Sedang-Tinggi : 80
Parameter Tinggi : 90

Skala Kepribadian (0-n) : 100
Parameter < Skala
Buruk < Buruk-Cukup < Cukup-Baik < Baik
Parameter Buruk : 55
Parameter Buruk-Cukup : 65
Parameter Cukup-Baik : 75
Parameter Baik : 85


Tahap terakhir dari prosedur Metode Fuzzy Mamdani adalah proses defuzzifikasi. Proses defuzzifikasi dipergunakan untuk menafsirkan nilai keanggotaan fuzzy menjadi keputusan tertentu atau bilangan real. Untuk mengambil keputusan dari data pegawai tersebut berdasarkan parameter dan himpunan yang dibuat. Ouputnya berupa list prediksi akurasi data untuk data train untuk hasil akurasi optimum sampai saat ini adalah 75.0%. Dari data tersebut dapat dihasilkan akurasi data yang dapat diterima sebagai berikut :

ID	Tes Kompetensi	Kepribadian	Diterima
0	P21	61.5	52.5	Tidak
1	P22	66.5	58.3	Tidak
2	P23	71.0	45.8	Tidak
3	P24	64.5	55.0	Tidak
4	P25	57.5	79.2	Tidak
5	P26	80.0	45.8	Tidak
6	P27	81.5	53.3	Tidak
7	P28	61.0	64.2	Tidak
8	P29	46.0	65.8	Tidak
9	P30	78.0	49.2	Tidak



Link Colab : https://colab.research.google.com/drive/1EuMiij-8X3PhLWHnm0oYv3a3Bb8GVvlw
