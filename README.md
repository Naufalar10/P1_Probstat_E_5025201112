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

## 1b
Poin ini diselesaikan dengan menggunakan rumus rerata dengan parameter berupa angka acak dari distribusi Geometri yang telah dilakukan dengan bantuan fungsi rgeom().
Fungsi berisi banyaknya data acak dan probabilitasnya
```
mean(rgeom(n = 10000, prob = p) == 3)
```

## 1c
Kesimpulan yang dapat untuk poin A nilai sudah tetap di satu nilai. sedangkan poin B nilai masih bertukar terus karena random. poin B lebih digunakan untuk keperluan sampling.

## 1d
gunakan fungsi hist() dengan parameter fungsi rgeom().

```
hist(rgeom(n = 10000,prob = p))
```

## 1e
varians dan rataan dapat didapatkan dengan rumus dibawah ini.
```
rataangeometrik <- function(p){
    hasil = 1/p
    return(hasil)
}

rataangeometrik(p)

variansgeometrik <- function(p){
    hasil = (1-p)/p^2
    return (hasil)
}

variansgeometrik(p)
```

# SOAL 2
Terdapat 20 pasien menderita Covid19 dengan peluang sembuh sebesar 0.2. Tentukan :
a. Peluang terdapat 4 pasien yang sembuh.
b. Gambarkan grafik histogram berdasarkan kasus tersebut.
c. Nilai Rataan (μ) dan Varian (σ²) dari DistribusiBinomial

## 2a
dapat diselesaikan dengan cara berikut
```
n = 20
p = 0.20
x = 4

probability = dbinom(x,n,prob = p, log = FALSE)
```

## 2b
histogram digambarkan dengan cara berikut
```
hist(rbinom(x,n,prob=p), xlab = "x", ylab = "frekuensi", main = "Histogram of Binomial")
```

## 2c
varians dan rataan dengan cara berikut
```
rataanbinomial <- function(n,p){
  hasil = n*p
  return(hasil)
}

variansbinomial <- function(n,p,q){
  hasil = n*p*q
  return(hasil)
}
rataanbinomial(20, 0.2)
variansbinomial(20, 0.2,0.8)
```

# SOAL 3
Diketahui data dari sebuah tempat bersalin di rumah sakit tertentu menunjukkan rata-rata historis
4,5 bayi lahir di rumah sakit ini setiap hari. (gunakan Distribusi Poisson)
a. Berapa peluang bahwa 6 bayi akan lahir di rumah sakit ini besok?
b. simulasikan dan buatlah histogram kelahiran 6 bayi akan lahir di rumah sakit ini selama
setahun (n = 365)
c. dan bandingkan hasil poin a dan b , Apa kesimpulan yang bisa didapatkan
d. Nilai Rataan (μ) dan Varian (σ²) dari Distribusi Poisson.

## 3a
dapat diselesaikan dengan cara berikut
```
dpois(6,4.5)
```

## 3b
histogram dapat dibuat dengan cara berikut
```
library(dplyr)
library(ggplot2)

set.seed(1)
  data.frame('data'= rpois(365,4.5))%>%
  ggplot() +
  geom_histogram(aes(x=data,
                     y=stat(count/sum(count)),
                     fill = data == 6),
                    binwidth = 1,
                    color ='black',) +
    scale_x_continuous(breaks = 0:10) +
    labs(x = 'Jumlah bayi yang lahir per periode',
         y = 'Proporsi',
         title ='simulasi kelahiran bayi pada 365 hari dengan Pois(lamda=4.5)' )+
    theme_bw()
``` 
## 3c
Poin A dan B cenderung sama, karena nilai dari poin A sendiri didapat dari range nilai poin B. Range dari B dapat dilihat pada plot yang telah terbentuk. Dari sana, nilai dari A berada di dalam range B.

Oleh karena itu, dalam estimasi selama 365 hari akan memberikan nilai hasil yang hampir sama dengan estimasi jumlah bayi yang akan dilahirkan di waktu selanjutnya (esok hari)

## 3d
varians dan rataan dapat dicari dengan cara sebagai berikut
```
rataanpoisson <- function(lamda){
    hasil = lamda
    return(hasil)
} 

varianspoisson <- function(lamda){
    hasil = lamda
    return(hasil)
}

rataanpoisson(3.5)
varianspoisson(3.5)
```

# SOAL 4
Diketahui nilai x = 2 dan v = 10. Tentukan:
a. Fungsi Probabilitas dari Distribusi Chi-Square.
b. Histogram dari Distribusi Chi-Square dengan 100 data random.
c. Nilai Rataan (μ) dan Varian (σ²) dari DistribusiChi-Square.

## 4a
Penyelesaian dapat dilakukan sebagai berikut
```
x=2
v=10
dchisq(x,v)
```

## 4b
histogram dapat digambarkan sebagai berikut
```
y <- rchisq(100, df=10)

hist(y, 
     freq = FALSE, 
     xlim = c(0,25), 
     ylim = c(0,0.2))
curve(dchisq(x, df = 10), from = 0, to = 25, 
      n = 100, col= 'red', lwd=2, add = T)
```

## 4c
nilai varians dan rataan dapat dicari dengan cara
```
rataanchisq <- function(v){
  hasil = v
  return(hasil)
}

varianschisq <- function(v){
  hasil = 2*v
  return(hasil)
}

rataanchisq(v)
varianschisq(v)
```

# SOAL 5
Diketahui bilangan acak (random variable) berdistribusi exponential (λ = 3). Tentukan
a. Fungsi Probabilitas dari Distribusi Exponensial
b. Histogram dari Distribusi Exponensial untuk 10, 100, 1000 dan 10000 bilangan random
c. Nilai Rataan (μ) dan Varian (σ²) dari Distribusi Exponensial untuk n = 100 dan λ = 3
Petunjuk:
● Gunakan set.seed(1)
● Gunakan fungsi bawaan R

## 5a
dapat diselesaikan dengan cara berikut
```
probability = dexp(1, rate = 3)
```

## 5b
histogram dibuat dengan cara berikut
```
set.seed(1)
par(mfrow=c(2,2))
hist(rexp(10,3))
hist(rexp(100,3))
hist(rexp(1000,3))
hist(rexp(10000,3))
```

## 5c
varians dan rataan dapat dicari dengan cara berikut
```

n = 100   # number of exponentials
lambda =3      #rate parameter chosen for the simulations
simnum <- 100

simdata <- matrix(rexp(simnum * n, rate=lambda), simnum)
sim_rowmean <- apply(simdata,1,mean)
simdata_mean <- mean(sim_rowmean)
sim_var <- var(sim_rowmean)
```

# SOAL 6
Diketahui generate random nilai sebanyak 100 data, mean = 50, sd = 8. Tentukan
a. Fungsi Probabilitas dari Distribusi Normal P(X1 ≤ x ≤ X2), hitung Z-Score Nya dan plot
data generate randomnya dalam bentuk grafik. Petunjuk(gunakan fungsi plot()).
Keterangan :
X1 = Dibawah rata-rata
X2 = Diatas rata-rata
1,2,4,2,6,3,10,11,5,3,6,8
rata-rata = 5.083333
X1 = 5
X2 = 6
b. Generate Histogram dari Distribusi Normal dengan breaks 50 dan format penamaan:
NRP_Nama_Probstat_{Nama Kelas}_DNhistogram
Contoh :
312312312_Rola_Probstat_A_DNhistogram
c. Nilai Varian (σ²) dari hasil generate random nilai Distribusi Normal.

## 6a
dapat diselesaikan dengan cara berikut
```
n = 100
mean = 50
sd = 8

set.seed(1)
data <- rnorm(n, mean, sd)
data
summary(data)

x1 = runif(1, min = min(data), max = mean)
x2 = runif(1, min = mean, max = max(data))
x1
x2

probability1 <- pnorm(x1, mean, sd)
probability2 <- pnorm(x2, mean, sd)
probability1
probability2

probability <- probability2 - probability1
plot(data)
```

## 6b 
diselesaikan dengan cara berikut
```
breaks = 50
hist(data, breaks, main = "5025201112_Naufal Ariq Putra Yosyam_Probstat_E_DNhistogram")
```

## 6c
varians diselesaikan dengan cara
```
variance = (sd(data)) ^ 2
variance
```
