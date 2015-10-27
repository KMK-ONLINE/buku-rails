# Pemrograman Ruby #

## Apa itu Ruby ##

Ruby adalah bahasa pemrograman open source yang dinamis. Fokus Ruby adalah kesederhanaan dan produktivitas. Ruby bersifat multiparadigma yang berorientasi objek, imperatif, reflektif, dan fungsional.

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
1_234                # Fixnum decimal with underline
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

### Conditional ###

### Looping ###

### Block, Proc, dan Lambda ###

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

