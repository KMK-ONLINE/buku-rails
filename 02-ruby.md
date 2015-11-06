# Pemrograman Ruby #

## Apa itu Ruby ##

Ruby adalah bahasa pemrograman open source yang dinamis. Fokus Ruby adalah kesederhanaan dan produktivitas. Ruby bersifat multiparadigma yang berorientasi objek, imperatif, reflektif, dan fungsional.

Menurut [Andrew Burgess](http://andrewburgess.ca/), seorang Developer berkebangsaan Kanada, koding di Ruby sangatlah menyenangkan. Beberapa keunggulan Ruby menurutnya yaitu:

1. Ruby bersifat fleksibel.
2. Ruby mudah dipelajari.
3. Ruby memiliki banyak framework yang hebat.
4. Ruby terlihat sederhana di permukaan namun sangat komplek di bawahnya.

## Instalasi Ruby ##

Saat buku ini ditulis, versi stabil terbaru Ruby adalah versi 2.2.3. Ruby tersedia dan dapat dijalankan pada berbagai platform sistem operasi.

### Windows ###

Cara termudah menjalankan Ruby di Windows adalah dengan mengunduh dan kemudian menginstall [RubyInstaller](http://rubyinstaller.org/).

### Ubuntu ###

Buka terminal dan tulis

`sudo apt-get install ruby`

### Mac OSX ###

Mac OS X biasanya sudah memiliki ruby sendiri. Jika ingin install versi lain, bisa gunakan homebrew.

Buka terminal dan install homebrew
`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

kemudian install ruby
`brew install ruby`

## Menggunakan Ruby di Terminal ##

Setelah Ruby terinstall, maka kita dapat menjalankannya langsung dari terminal. Gunakan *Ruby Interactive Shell* (irb) sehingga kita dapat langsung mencoba kode ruby dan langsung melihatnya hasilnya.

Tulis `irb` di terminal, setelah itu akan muncul seperti ini:

    irb(main):001:0>

Tulis: `"Hello World"`

    irb(main):001:0> "Hello World"
    => "Hello World"

Cara lain adalah menulis kode Ruby di editor teks kemudian disimpan dan diberi ekstensi titik rb (.rb)

``` ruby
# isi file halo.rb
puts "Halo, mari belajar Ruby dengan semangat!"
```
    
Jalankan halo.rb di terminal

    $ ruby halo.rb

Berikut outputnya

    Halo, mari belajar Ruby dengan semangat!

## Pemrograman Ruby ##

### Statement dan Comment ###

titik koma (;) dan baris baru adalah tanda dari akhir statemen di Ruby. Namun, apabila Ruby menemukan karakter operator seperti +, -, atau *backslash* di akhir baris, maka karakter tersebut meneruskan statemen yang ada.

Sebagaimana pada bahasa pemrograman pada umumnya, komentar pada ruby akan mencegah Ruby menginterpretasikan sebagian dari baris, sebuah baris, atau beberapa baris yang didahului karakter tagar (#).

``` ruby
# Cuekin aku Kak!

nama = "Abidin" # cuekin aku lagi Kak!

# Cuekin aku Kak!
# Iya cuekin aku
# Gpp kok cuekin aku!
# Iya Kak, cuekin aja.
```

Jika terdapat banyak baris, dapat menggunakan =begin/=end

```ruby
=begin
Cuekin aku Kak!
Iya cuekin aku
Gpp kok cuekin aku!
Iya Kak, cuekin aja.
=end
```

### Variabel dan Tipe Data ###

Variabel adalah lokasi memory menyimpan berbagai data.

#### Konstanta ####

Konstanta ditulis dengan huruf kapital semua.

``` ruby
# nama file pi.rb
PI = 3.14159265359

puts PI
```

output:

    $ ruby pi.rb
    3.14159265359

#### Variabel Global dan Variabel Lokal ####

Variabel global didahului dengan tanda dolar ($).

Variabel lokal didahului dengan huruf kecil atau tanda *under_score* (_). Skup variabel lokal meliputi class, module, def, atau do yang berada di dalam suatu blok.

```ruby
# nama file glokal.rb
$tahun = 2015
umur = 20

puts "sekarang tahun #{$tahun}"
puts "umur saya sekarang #{umur}"
```

output:

    $ ruby glokal.rb
    sekarang tahun 2015
    umur saya sekarang 20

#### Tipe Data ####

Semua tipe data di Ruby merupakan Object, termasuk tipe data primitif seperti Integer, Float, dan Boolean. Bahkan, nil dan Class pun merupakan Object.

    irb(main):002:0> suhu = 2.98 # float
    => 2.98
    irb(main):003:0> umur = 20 # integer
    => 20
    irb(main):004:0> muda = true # boolean
    => true
    irb(main):005:0> remaja = umur <= 20 && umur > 12 # boolean
    => true
    irb(main):006:0> puts umur
    20
    => nil
    irb(main):007:0> puts suhu
    2.98
    => nil
    irb(main):008:0> puts remaja
    true
    => nil

##### Integer #####

Integer atau bilangan bulat di Ruby mulai dari -2^30^ hingga 2^30-1^ atau dari -2^62^ hingga 2^62-1^. Bilangan bulat yang berada pada range terebut disebut *Fixnum* sedangkan yang berada di luar disebut *Bignum*

Gunakan indikator base 0 untuk oktal, 0x untuk hex, atau 0b untuk binari. Kita juga bisa mendapatkan nilai bilangan bulat dari suatu karakter [ASCII](https://id.wikipedia.org/wiki/ASCII) dengan didahului tanda tanya (?).

```ruby
123                  # Fixnum decimal
1_000_000            # Fixnum decimal dengan garis bawah -> satu juta
-500                 # Negative Fixnum
0377                 # octal
0xff                 # hexadecimal
0b1011               # binary
?a                   # kode karakter 'a'
?\n                  # kode baris baru (0x0a)
12345678901234567890 # Bignum
```

##### Floats #####

Floats atau bilangan real. Adalah bilangan yang memiliki desimal. Di Ruby menggunakan tanda titik (.) untuk menampilkan bilangan real.

```ruby
# contoh bilangan real
123.4                # nilai floating point
1.0e6                # notasi scientific
4E20                 # dot not required
4e+20                # sign sebelum exponential
```

##### Strings #####

Strings adalah rangkaian karakter.

```ruby
puts 'escape using "\\"';
puts 'That\'s right';
puts "Hasil perkalian : #{24*60*60}";
```

Output:

    escape using "\"
    That's right
    Hasil perkalian : 86400

Ekspresi Subtitusi

```ruby
x, y, z = 12, 36, 72
puts "Nilai x adalah #{ x }."
puts "Jumlah x dan y adalah #{ x + y }."
puts "Rata-ratanya adalah #{ (x + y + z)/3 }."
```

Output:

    Nilai x adalah 12.
    Jumlah x dan y adalah 48.
    Rata-ratanya adalah 40.

Lihat [Dokumentasi String](http://ruby-doc.org/core-2.2.0/String.html) untuk lebih jelas dan detil.

> **Catatan**
>
> Pada dasarnya, variabel pada Ruby adalah objek sehingga bisa
> variabel yang kita definisikan dan telah kita berikan
> dapat diberikan method atau fungsi untuk mendapatkan suatu output
> sesuai yang diinginkan.
>
> **Contoh**
> Kita dapat konversi tipe data ke tipe data lain.
> 
> `a = 10`
> `b = 1.2`
> `c = [3, 4, 5]`
> 
> `puts a.to_f # Integer ke float`
> `puts b.to_s # Float ke string`
> `puts c.to_a.inspect # array ke string`
> `a.class` # untuk mengetahui tipe data variabel `a`. Hasilnya adalah fixnum

### Operator Logika dan Matematika ###

| Operator | Arti                         |
|----------|------------------------------|
| `+`      | tambah                       |
| `-`      | kurang                       |
| `*`      | kali                         |
| `/`      | bagi                         |
| `%`      | modulus                      |
| `**`     | pangkat                      |
| `&`      | dan (bilangan berbasis 2)    |
| `|`      | atau (bilangan berbasis 2)   |
| `^`      | XOR (bilangan berbasis 2)    |
| `~`      | invert bit (berbasis 2)      |
| `<<`     | shift kiri (berbasis 2)      |
| `>>`     | shift kanan (berbasis 2)     |
| `&&`     | dan (Boolean)                |
| `and`    | dan (Boolean)                |
| `||`     | atau (Boolean)               |
| `or`     | atau (Boolean)               |
| `!`      | bukan (Boolean)              |
| `not`    | bukan (Boolean)              |
| `==`     | sama dengan                  |
| `>`      | lebih dari                   |
| `<`      | kurang dari                  |
| `>=`     | lebih dari sama dengan       |
| `>=`     | lebih dari atau sama dengan  |
| `<=`     | kurang dari atau sama dengan |


#### Array ####

Array adalah koleksi dari berbagai objek yang terurut dan memiliki indeks.

Membuat array kosong:

    arrayku = Array.new
    arrayku_yang_lain = []

contoh penggunaan Array di Ruby:

```ruby
nilai_ujian = [80, 90, 78, 95]
nilai_ujian << 80 # tambah nilai 80 ke dalam array nilai_ujian

nama_sd = %w{Sendy Windy Nani}
nama_smp = ["Fauzi", "Masruchan", "Putri"]

halo_nama_sd = nama_sd.map { |nama| "Halo #{nama}!" }

puts "#{nilai_ujian}"
puts "#{nama_sd}"
puts "#{nama_smp}"
puts "#{halo_nama_sd}"
```

Output:

    [80, 90, 78, 95, 80]
    ["Sendy", "Windy", "Nani"]
    ["Fauzi", "Masruchan", "Putri"]
    ["Halo Sendy!", "Halo Windy!", "Halo Nani!"]

#### Hashes ####

Hash di Ruby mirip dengan *assosiative array* di PHP atau *object literal* di JavaScript. Hash mirip dengan Array.

```ruby
hash_ku = Hash.new
hash_ku_yang_lain = {}

# Untuk memberi nilai ke dalam hash gunakan notasi kurung siku. Bisa gunakan berbagai macam tipe data.

hash_ku["Nama"] = "Andy"
hash_ku[:umur] = 20

puts hash_ku
```

Output:

    {"Nama"=>"Andy", :umur=>20}

Guna menempatkan objek ke dalam Hash, notasi yang digunakan hampir identik dengan *object literal* yang ada pada JavaScript. Perbedaannya di Ruby adalah menggunakan panah (`=>`) antara keys dan values.

```ruby
person = { "name" => "Joe", "age" => 35, "job" => "plumber" }

puts person
```

Output:

    {"name"=>"Joe", "age"=>35, "job"=>"plumber"}

#### Symbols ####

Symbols mirip dengan string. Mereka ditempatkan sebagai identifier. Symbols digunakan menggantikan string karena menggunakan memory yang lebih sedikit. Untuk membuat symbol, cukup berikan titik dua (:) seperti pada contoh bagian Hash sebelumnya.

```ruby
konfigurasi = :username #username adalah symbol
puts konfigurasi

puts :password
puts "password"
```

Output:

    username
    password
    password

### Statement Controls ###

#### Conditional ####

Disini kita belajar mengenai suatu kondisi. Di Ruby terdapat 4 macam statemen yaitu:

1. Statemen if
2. Statemen elseif
3. Statemen unless
4. Statemen case/when

##### Statemen if #####

Jika syarat dipenuhi atau bernilai *true* maka statemen yang berada di dalam blok akan dijalankan.

```ruby
nama = "Desty"

if nama == "Desty"
  puts "Halo #{nama}"
end
```

Output:

    Halo Desty

Kita dapat menggunakan keyword `then` jika hanya membutuhkan satu baris dalam statemen `if`. Kode di atas dapat diubah menjadi:

```ruby
if nama == "Desty" then puts "Halo #{nama}"; end
```

Jangan lupa untuk menambahkan titik koma (;) jika dalam satu baris terdapat lebih dari satu statemen. Maka, setelah statemen `puts "Halo #{nama}"` diakhiri dengan titik koma (;) karena setelahnya ada penutup `end`

##### Statemen elseif #####

Jika syarat tidak dipenuhi maka blok statemen yang berada di blok else yang akan dijalankan.

```ruby
order = { :size => "medium" }

if order[:size] == "small"
    puts "Buat kopi ukuran kecil"
elsif order[:size] == "medium"
    puts "Buat kopi ukuran sedang"
elsif order[:size] == "large"
    puts "Buat kopi ukuran besar"
else
    puts "Belum memutuskan untuk membuat kopi"
end
```

Output:

    Buat kopi ukuran sedang

##### Statemen unless #####

Seperti pada kebanyakan bahasa pemrograman, Ruby memiliki negasi berupa (!). 

```ruby
mesin_nyala = false

if !mesin_nyala
  puts "Mesin sedang diservis"
end
```

output:

    Mesin sedang diservis

Ruby memiliki operator `unless` sehingga kita tidak perlu memberikan negasi terhadap suatu kondisi. Kode di atas dapat diubah menjadi berikut

```ruby
mesin_nyala = false

unless mesin_nyala
  puts "Mesin sedang diservis"
end
```

`unless` dapat digunakan sebagai *modifier* sehingga kode di atas dapat lebih disingkat menjadi

```ruby
puts "Mesin sedang diservis" unless mesin_nyala
```

Output:

    Mesin sedang diservis

##### Statemen case/when #####

Statemen `case/when` di Ruby mirip dengan statemen `switch/case` di C/JavaScript/PHP.

```ruby
jam = 12

case
when jam < 10
  puts "Selamat pagi"
when jam >= 10 && jam < 14
  puts "Selamat siang"
when jam >= 14 && jam < 17
  puts "Selamat sore"
else
  puts "Selamat malam"
end
```

Output:

    Selamat siang

#### Looping ####

##### While #####

Blok statemen yang berada di dalam looping while akan terus dikerjakan hingga kondisi yang dinyatakan bernilai salah.

```ruby
arr = ["Ida", "Benyamin", "Slamet", "Safi'i"]
i = 0 # counter awal

while arr[i]
  puts arr[i]
  i += 1  # artinya sama seperti i = i + 1
end
```

Output:

    Ida
    Benyamin
    Slamet
    Safi'i

##### Until #####

Sama sebagaimana `unless` yang merupakan lawan dari `if`, `until` adalah lawan dari `while`. Blok yang ada di dalam looping `until` akan terus dikerjakan sampai suatu kondisi yang dinyatakan bernilai benar.

```ruby
sisa_waktu = 7

until sisa_waktu == 0
  puts "masih ada #{sisa_waktu} hari untuk kamu selesaikan tugasnya"
  sisa_waktu -= 1 # artinya sama seperti sisa_waktu = sisa_waktu - 1
end
```

Output:

    masih ada 7 hari untuk kamu selesaikan tugasnya
    masih ada 6 hari untuk kamu selesaikan tugasnya
    masih ada 5 hari untuk kamu selesaikan tugasnya
    masih ada 4 hari untuk kamu selesaikan tugasnya
    masih ada 3 hari untuk kamu selesaikan tugasnya
    masih ada 2 hari untuk kamu selesaikan tugasnya
    masih ada 1 hari untuk kamu selesaikan tugasnya

Kita dapat menggunakan modifier untuk kode di atas sehingga menjadi

```ruby
sisa_waktu = 8
puts "masih ada #{sisa_waktu -= 1} hari untuk kamu selesaikan tugasnya" until sisa_waktu == 1
```

output:

    masih ada 7 hari untuk kamu selesaikan tugasnya
    masih ada 6 hari untuk kamu selesaikan tugasnya
    masih ada 5 hari untuk kamu selesaikan tugasnya
    masih ada 4 hari untuk kamu selesaikan tugasnya
    masih ada 3 hari untuk kamu selesaikan tugasnya
    masih ada 2 hari untuk kamu selesaikan tugasnya
    masih ada 1 hari untuk kamu selesaikan tugasnya


##### For #####

Looping for di Ruby mirip dengan for each di PHP

```ruby
arr = ["Ida", "Benyamin", "Slamet", "Safi'i"]

for orang in arr
  puts orang
end
```

Output:

    Ida
    Benyamin
    Slamet
    Safi'i

Gunakan dua variabel ketika menggunakan for pada hash

```ruby
seniman = {"Ida" => "Penyanyi", "Benyamin" => "Pelawak", "Slamet" => "Pelukis", "Safi'i" => "Penyair"}

for nama, karir in seniman
  puts "#{nama} adalah seorang #{karir}"
end
```

Output:

    Ida adalah seorang Penyanyi
    Benyamin adalah seorang Pelawak
    Slamet adalah seorang Pelukis
    Safi'i adalah seorang Penyair

### Methods ###

Methods adalah serangkaian statemen yang melakukan pekerjaan untuk tujuan tertentu. Methods harus memiliki nama. Methods di Ruby diawali dengan keyword `def` dan diakhir dengan `end`.

```ruby
# halo adalah nama methods.
def halo
  puts "Halo! Selamat belajar Ruby"
end

halo  # memanggil methods yang telah didefinisikan sebelumnya.
```

Output:

    Halo! Selamat belajar Ruby

Apabila methods membutuhkan masukan untuk mendapatkan suatu hasil, maka kita dapat memberikan suatu variabel ke dalam methods. Variabel tersebut dinamakan argumen. Sebuah methods dapat memiliki satu atau lebih argumen. Berikut contoh sebuah method yang memiliki dua buah argumen.

```ruby
# method untuk menghitung luas segiempat
# masukan panjang dan lebar
def luas(panjang, lebar)
  puts "Luas segiempat dengan panjang #{panjang} dan lebar #{lebar} adalah #{panjang*lebar}"
end

# ketika memanggil method luas, kita berikan nilai 5 sebagai panjang
# dan 4 sebagai lebar
luas(5, 4)
# dan menggunakan methods yang sama dengan nilai panjang dan lebar yang lain
luas(6,2)
luas(6,3)
```

Output:

    Luas segiempat dengan panjang 5 dan lebar 4 adalah 20
    Luas segiempat dengan panjang 6 dan lebar 2 adalah 12
    Luas segiempat dengan panjang 6 dan lebar 3 adalah 18

Selain dapat kita dapat memberikan argumen, methods juga dapat mengembalikan data atau nilai. Kita gunakan keyword `return` di dalam def methods untuk mengembalikan data atau nilai.

```ruby
# method untuk menghitung luas segiempat
# masukan panjang dan lebar
def luas(panjang, lebar)
  puts "Segiempat ini memiliki panjang #{panjang} dan lebar #{lebar}"
  return panjang * lebar
end

# ketika memanggil method luas, maka method tersebut mengembalikan nilai luas.
# Nilai tersebut bisa diberikan ke dalam variabel dan ditampilkan dengan `puts`
l_segiempat = luas(4,5)

puts "Luas Segiempat adalah #{l_segiempat}"
```

Output:

    Segiempat ini memiliki panjang 4 dan lebar 5
    Luas Segiempat adalah 20

### Block, Proc, Lambda, dan Method Object ###

Cara kita mengelompokkan kode yang akan kita jalankan dinamakan *closure*. Berikut adalah *closure* di Ruby:

1. Blocks
2. Procedures atau Procs
3. Lambdas

#### Block ####

Block adalah serangkaian kode yang dapat dieksekusi. Block bisa digunakan sebagai input ke dalam method. Block kadang-kadang disebut sebagai fungsi anonim karena tidak memiliki nama namun tingkahnya mirip dengan fungsi.

Ada dua cara menulis sintaks block, yaitu dengan diawali `do` dan diakhiri `end` atau dengan menggunakan kurung kurawal `{}` jika hanya satu baris statemen.

```ruby
[1,2,3].each { |n| puts n }
```

Output:

    1
    2
    3

```ruby
[1,2,3].each do |n|
  puts n ** 2 # n pangkat 2
end
```

    1
    4
    9

Terdapat method `collect` yang menerapkan ekspresi di dalam block pada setiap elemen di dalam array.

```ruby
angka_ku = [1, 2, 3]
angka_ku.collect { |n| puts n ** 2 }
puts
puts angka_ku
```

Output:

     1
     4
     9

     1
     2
     3

Ketika block dijalankan nilai yang berada di dalam angka_ku tidak berubah. Namun apabila kita ingin merubahnya, kita dapat menggunakan tanda (!) menjadi `collect!` agar angka_ku ikut berubah nilainya.

```ruby
angka_ku = [1, 2, 3]
angka_ku.collect! { |n| puts n ** 2 }
puts
puts angka_ku
```

Output:

     1
     4
     9

     1
     4
     9

#### Proc ####

Procedure atau Proc adalah adalah block yang kita simpan ke dalam variabel. Contoh menggunakan IRB:

    irb(main):001:0> proc_ku = Proc.new { |arg1| print "#{arg1}!" }
    => #<Proc:0x00000001d39d88@(irb):1>
    irb(main):002:0> [1, 2, 3].each(&proc_ku)
    1!2!3!=> [1, 2, 3]
    irb(main):003:0> [1, 2, 3].each &proc_ku
    1!2!3!=> [1, 2, 3]

Proc adalah objek, sedangkan blok bukan

```ruby
p = Proc.new { puts "Halo dunia!" }

p.call
puts p.class

a = p
p
```

Output:

    Halo dunia!
    Proc
    #<Proc:0x0000000101fc38@proc02.rb:1>
    #<Proc:0x0000000101fc38@proc02.rb:1>

Kita dapat memasukkan banyak proc sebagai daftar list ke dalam method

```ruby
def multiple_procs(proc1, proc2)
  proc1.call
  proc2.call
end

a = Proc.new { puts "Proc pertama" }
b = Proc.new { puts "Proc kedua" }

multiple_procs(a,b)
```

Output:

    Proc pertama
    Proc kedua

#### Lambda ####

Proc dan Lambda sama-sama object Proc.

```ruby
proc = Proc.new { puts "Halo Dunia!" }
lam = lambda { puts "Halo Dunia!" }

proc.class
lam.class 

puts proc
puts lam
```

Output:

    Proc
    Proc
    #<Proc:0x000000024a38f8@lambda.rb:1>
    #<Proc:0x000000024a38d0@lambda.rb:2 (lambda)>

Lalu apa yang membedakan Lambda dengan Proc?

1. Lambda mengecek jumlah argumen

```ruby
lam = lambda { |x| puts x }    # hanya ada satu argumen
lam.call(2)                    # outputnya 2
lam.call                       # ArgumentError
lam.call(1,2,3)                # ArgumentError
```

Sebaliknya di Proc tidak akan terjadi error

```ruby
proc = Proc.new { |x| puts x } # hanya ada satu argumen
proc.call(2)                   # outputnya 2
proc.call                      # outputnya nil
proc.call(1,2,3)               # outputnya 1 dan menghiraukan argumen lainnya
```

2. Lambda dan Proc memperlakukan keyword `return` di dalam blok dengan berbeda

```ruby
def lambda_test
  lam = lambda { return }
  lam.call
  puts "Halo Dunia!"
end

lambda_test
```

Output:

    Halo Dunia!

`return` yang berada di dalam proc akan memicu kode yang berada di luar method di mana proc dieksekusi

```ruby
def proc_test
  proc = Proc.new { return }
  proc.call
  puts "Halo Dunia!"
end

proc_test 
```

Outputnya tidak ada sama sekali

Referensi :
http://www.eriktrautman.com/posts/ruby-explained-blocks-procs-and-lambdas-aka-closures

### Class dan Object ###

Ruby adalah bahasa pemrograman yang benar-benar *Object Oriented*. Fitur utama pemrograman berbasis objek adalah:

1. Data Encapsulation
2. Data Abstraction
3. Polymorphism
4. Inheritance

Program berbasis objek akan terdapat objek dan class. Class adalah cetak biru atau acuan untuk membuat individu objek. Sebagai contoh kita memiliki class Avanza maka objek dari Avanza misalkan adalah avanza1, avanza2, dan avanzan. Masing-masing objek avanza memiliki fitur dan method yang sama misalkan memiliki roda, mesin 1300 cc, jendela, kursi, dan lain sebagainya. Yang membedakan antara objek avanza yang satu dengan avanza lainnya misalkan nomor plat mobil, warna mobil, dan aksesoris yang dimiliki.

#### Mendefinisikan Class ####

Pada contoh kali ini kita akan mendefinisikan class Avanza.

```ruby
# Avanza.rb
class Avanza
end
```

Setelah class didefinisikan, selanjutnya adalah membuat objet dari class tersebut. Proses pembuatan objek dari class disebut *instantiation*.

```ruby
avanzaku = Avanza.new
# avanzaku adalah objek dari class Avanza
# Avanza.new berarti membuat objek baru dari class Avanza
```

Setiap class memiliki atribut atau fitur dan method atau fungsi. Sebagai contoh Avanza memiliki fitur warna dan plat nomor. Sedangkan methodnya adalah maju, mundur, dan rem.

#### Instance Variable ####

Variabel instans diawali dengan karakter @. Berikut contoh penggunaan variabel instans pada class Avanza.

```ruby
# Avanza.rb
class Avanza
   def initialize(plat, warna)
      @plat=plat
      @warna=warna
   end
   def detil()
      puts "Plat: #@plat"
      puts "Warna: #@warna"
   end
   def maju()
      puts "Avanza melaju ke depan"
   end
   def mundur()
      puts "Avanza mundur ke belakang"
   end
   def rem()
      puts "Avanza rem"
   end
end

avanzaku = Avanza.new("B 235 SFW", "Merah")
avanzaku.detil()
avanzaku.maju()
avanzaku.rem()
avanzaku.mundur()
```

Output:

    $ ruby Avanzaku.rb
    Plat: B 235 SFW
    Warna: Merah
    Avanza melaju ke depan
    Avanza rem
    Avanza mundur ke belakang

#### Class Variable ####

Variabel class diawali dengan @@ dan harus diberikan nilai di awal sehingga bisa digunakan di method. Sekarang mari kita modifikasi class Avanza di atas menjadi memiliki variabel class mesin_cc dan posisi_setir

```ruby
# Avanza.rb
class Avanza
   @@mesin_cc = "1300"
   @@posisi_setir = "kanan"

   # membuat method untuk menampilkan variabel class
   def self.mesin_cc
      @@mesin_cc
   end
   # membuat method untuk menampilkan variabel class
   def self.posisi_setir
      @@posisi_setir
   end

   # memberikan nilai awal ketika objek pertama kali dibuat
   def initialize(plat, warna)
      @plat=plat
      @warna=warna
   end
   def detil() # menampilkan detil mobil avanza
      puts "Plat: #{@plat}"
      puts "Warna: #{@warna}"
   end
   def maju()
      puts "Avanza melaju ke depan"
   end
   def mundur()
      puts "Avanza mundur ke belakang"
   end
   def rem()
      puts "Avanza rem"
   end
end

avanzaku = Avanza.new("B 235 SFW", "Merah")
puts "Avanzaku memiliki kapasistas mesin #{Avanza.mesin_cc} dan posisi setir ada di #{Avanza.posisi_setir}"
avanzaku.detil()
avanzaku.maju()
avanzaku.rem()
avanzaku.mundur()
```

Output:

    $ ruby Avanza.rb
    Avanzaku memiliki kapasistas mesin 1300 dan posisi setir ada di kanan
    Plat: B 235 SFW
    Warna: Merah
    Avanza melaju ke depan
    Avanza rem
    Avanza mundur ke belakang

