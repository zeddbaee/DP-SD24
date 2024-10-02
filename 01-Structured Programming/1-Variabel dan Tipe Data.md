[<< Materi Sebelumnya (Daftar Materi) <<](../DaftarMateri.md)
# 1.1 - Variabel, Tipe Data, dan Basic I/O)
## Variabel dan Tipe Data C
Pada hampir semua bahasa pemrograman, terdapat sebuah sistem yang bernama variabel. Seperti pada aljabar, variabel adalah sebuah ekspresi yang berfungsi untuk menyimpan sebuah data. Pada aljabar, variabel dapat digambarkan di bawah ini.
```
x + y = 10
2x + 5y = 38
```
Dari contoh di atas, dapat disimpulkan bahwa `x` bernilai 4 dan `y` bernilai 6. Pada bahasa C, terdapat juga variabel yang memiliki fungsi yang mirip seperti di atas, namun dengan berbagai macam jenis, masing-masing memiliki jenis data apa yang dapat disimpan dalam variabel tersebut. Lihat tabel di bawah ini

### Tipe data C
|Tipe Data|Jenis Data|Pendefinisian|
|--|--|--|
|Integer|Bilangan bulat|`char`, `short`, `int`, `long`, dan `long long`|
|Unsigned Integer|Bilangan bulat non-negatif|Sama dengan atas, diberi imbuhan depan `unsigned`|
|Floating Point|Bilangan real|`float` dan `double`|
|Structure|Tipe data buatan pengguna|Buatan pengguna|

Setiap tipe data di atas memiliki rentang (nilai maksimal dan minimal yang dapat disimpan dalam sebuah variabel) masing-masing. Contohnya, `char` hanya dapat menyimpan -128 hingga 127, sedangkan `long` hingga 2 milyar tergantung pada implementasinya. Tipe data `unsigned` tidak dapat merepresentasikan bilangan negatif, namun rentang atasnya dua kali dari bilangan bulat. Floating point dapat menyimpan bilangan real seperti `3.14` atau `12.345`.

### Pendefinisian Variabel C
Variabel di bahasa pemrograman C harus didefinisikan sebelum dipakai pada program. Sebagai contoh, kita akan mendefinisikan sebuah variabel bernama `bejo` dan `dengklek` yang menyimpan nilai `42` dan `68`. Untuk nilai yang berupa angka, kita biasa menggunakan tipe data `int`.
```c
int bejo = 42;
int dengklek 68;
```
Kita coba untuk mendefinisikan variabel di atas dengan gaya yang berbeda.
```c
int bejo = 42, dengklek = 68;
```
Kita coba untuk mendefinisikan variabel di atas, namun tidak memberikan nilai untuknya.
```c
int bejo, dengklek;
```

## Basic I/O
I/O, yang memiliki kepanjangan Input/Output adalah separuh hati dari banyak program. I/O membuat program yang kalian buat dapat berinteraksi dengan dunia luar, baik dengan file, program lain, atau pengguna/manusia. Untuk kali ini, kita hanya akan membahas I/O yang melibatkan pengguna/manusia.
### Basic Output
Salah satu output (keluaran) yang paling mendasar yang dapat dibuat oleh program C adalah perintah *print to console* atau mencetak *console*. Seperti yang telah kita bahas pada sub-subbab sebelumnya mengenai [memahami kode *hello world*](#program-sederhana), kita dapat menggunakan perintah `printf()` untuk mencetak apapun yang kita mau ke konsol. 
```c
printf("Hello, World!");
printf("Hello 1234");
```
Sejauh ini, kita baru mempelajari cara mencetak data yang langsung kita berikan sebagai *string* atau tulisan mentah. Bagaimana jika kita ingin mencetak nilai dari sebuah variabel? Caranya adalah dengan menggunakan format. Perhatikan kode di bawah ini.
```c
#include <stdio.h>  
int main() {
	char name[8] = "Michael";  
	int number = 150;
	
	printf("Your Variables: %s %d \n", name, number);
	// '\n' adalah "newline", sama seperti "enter"
	return  0;  
}
```
*Output* pada *console*:
```
Your Variables: Michael 150
```
Pada contoh program di atas, kita menggunakan format pada fungsi `printf()` kita untuk mencetak variabel `name[]` dan `number`, di mana `name[]` bertipe *char array* atau string, sedangkan `number` bertipe integer. Seperti yang dapat kita lihat, konstanta format (`%s` dan `%d`) merupakan sebuah placeholder atau tempat dari variabel yang kita berikan di sebelah kanan. `%s` berkorespondensi dengan variabel `name`, sedangkan `%d` dengan `number`. Format bagi masing-masing tipe data berbeda-beda. Lihat tabel dan potongan kode di bawah ini.

|Placeholder|Tipe Data|Penjelasan|
|:---------:|---------|----------|
|%s|string / *char array*|Tulisan alfanumerik|
|%d|integer|Angka/bilangan|
|%f|floating point|Bilangan real|

```c
#include <stdio.h>  
int main() {
	char name[9] = "Everglow";  
	int number = 42;
	float real = 3.14;

	printf("Your Variables: %s %d %f \n", name, number, real);
	// Pada compiler modern, return pada main() tidak harus dituliskan
	// Referensikan ke perintah dosen kalian mengenai penulisan return pada main()
}
```
*Output* pada *console*:
```
Your Variables: Everglow 42 3.14
```
> Cara terbaik untuk memahami Basic I/O adalah terus mencoba dan bereksperimen pada IDE kalian!

### Basic Input
Jika kita sudah mengetahui bagaimana cara mencetak variabel yang telah kita definisikan, sekarang kita akan mempelajari cara meminta pengguna program kita untuk mengisi sebuah variabel. Perhatikan contoh kode di bawah.
```c
#include <stdio.h>  
int main() {
	char name[100];  
	int number;
	float real;

    printf("Enter a value: ");
    scanf("%s %d %f", name, &number, &real);
	
	printf("Your Inputs: %s %d %f \n", name, number, real);
}
```
*Output* pada *console*:
```
Enter a value: Halo 12 43.93
Your Inputs: Halo 12 43.93
```
> Note: "Halo 12 43.93" adalah nilai yang dimasukkan oleh pengguna

Dapat kita lihat bahwa fungsi yang "menangkap" masukan/input pengguna dari *console*, yaitu `scanf()`, menggunakan format placeholder yang sama dengan fungsi `printf()`.
```c
scanf("%s %d %f", name, &number, &real);
```
Potongan fungsi di atas akan menangkap masukan pengguna yang dibatasi oleh spasi, dan urut berupa string, integer, dan float, dari kiri ke kanan. Dengan menginput `Halo 12 43.93`, program akan memasukkan "Halo" ke variabel `name`, 12 ke variabel `number`, dan 43.93 ke variabel `real`.  Diperlukan *ampersand* (`&`) di depan variabel berjenis integer/floating point, namun tidak akan dijelaskan alasannya sekarang. *Do as above*
Fungsi `scanf()` yang kita gunakan ini memiliki sebuah kekurangan, yaitu tidak bisa menerima *string* yang ber-spasi. Namun, kita akan tetap menggunakan metode ini untuk sekarang.

Jika kalian ingin memasukkan input dengan banyak kata, kalian bisa menggunakan fgets, berikut syntax dari fgets.

```c
fgets(char *str, int n, FILE *stream)
```

dengan 
- char *str merupakan variabel yang akan diisi;
- int n merupakan jumlah maksmal karakter yang diinputkan;
- FILE *stream untuk saat ini diisi dengan stdin

```c
#include <stdio.h>

int main(){
	char nama[100];
	fgets(nama, 100, stdin);
	printf("%s", nama);
}
```

> Cobalah bereksperimen dengan memberikan masukan ber spasi, atau menghapus ampersand (&) di awal variabel integer dan floating point!

<br />

[>> Materi Berikutnya (Algoritma, Pseudocode, dan Source Code) >>](2-AlgoritmaPseudocodeSourcecode.md)
