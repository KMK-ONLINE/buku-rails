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



### Conditional ###

### Looping ###

### Block, Proc, dan Lambda ###

Referensi :
http://www.eriktrautman.com/posts/ruby-explained-blocks-procs-and-lambdas-aka-closures

### Class dan Object ###


