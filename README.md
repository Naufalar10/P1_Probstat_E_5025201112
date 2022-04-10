# P1_Probstat_E_5025201112
NRP | NAMA
-------------- | ------------------------
5025201112     | Naufal Ariq Putra Yosyam

# SOAL 1
Seorang penyurvei secara acak memilih orang-orang di jalan sampai dia bertemu dengan
seseorang yang menghadiri acara vaksinasi sebelumnya.
a. Berapa peluang penyurvei bertemu x = 3 orang yang tidak menghadiri acara vaksinasi
sebelum keberhasilan pertama ketika p = 0,20 dari populasi menghadiri acara vaksinasi ?
(distribusi Geometrik)
b. mean Distribusi Geometrik dengan 10000 data random , prob = 0,20 dimana distribusi
geometrik acak tersebut X = 3 ( distribusi geometrik acak () == 3 )
c. Bandingkan Hasil poin a dan b , apa kesimpulan yang bisa didapatkan?
d. Histogram Distribusi Geometrik , Peluang X = 3 gagal Sebelum Sukses Pertama
e. Nilai Rataan (μ) dan Varian (σ²) dari Distribusi Geometrik.

## 1a
Poin ini dapat diselesaikan dengan bantuan fungsi dgeom(). fungsi tersebut berisi x(jumlah orang yang tidak hadir vaksin) dan p(jumlah orang yang hadir vaksin).
```
p=0.20
x=3
a<- dgeom(x,p)
print(a)
```
![alt text](https://github.com/Naufalar10/P1_Probstat_E_5025201112/probstat_1/main/1a.PNG)
