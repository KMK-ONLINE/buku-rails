# Rails #

## Apa itu Rails ##

Rails merupakan framework web yang dibuat dengan Ruby. Rails memiliki lisensi [MIT](https://en.wikipedia.org/wiki/MIT_License) dan pertama kali dikembangkan oleh David Heinemeier Hansson pada tahun 2003.

### Sejarah Rails ###

### Cara Instalasi Rails  ###

Pada modul ini, kita akan menginstall Ruby on Rails pada *Virtual Machine*. Tujuannya adalah memudahkan pembelajaran karena hanya akan ada satu sistem operasi yaitu Ubuntu Server versi 14.04.

Langkah-langkah yang perlu kita lakukan adalah:

1. Install [VirtualBox](http://virtualbox.org) sebagai *Virtual Machine*.
2. Install [Vagrant](http://vagrantup.com). Vagrant adalah alat yang memudahkan kita dalam menginstall banyak sistem operasi di virtual machine.
3. Install Ubuntu Server di VirtualBox dengan vagrant
4. Login ke Guest Machine dengan SSH
5. Update paket Ubuntu Server
6. Install Ruby
7. Install Dependecy
8. Install Database MySQL
9. Install Nodejs
10. Install Rails

#### VirtualBox ####

Download dan install [VirtualBox](http://virtualbox.org)

#### Vagrant ####

Download dan install [Vagrant](http://vagrantup.com). Setelah vagrant sukses terinstall maka perintah `vagrant` akan terintegrasi pada terminal atau command prompt.

#### Install Ubuntu ####

Sebelum menginstall Ubuntu Server di Virtual Machine, pilih terlebih dahulu berbagai macam *vagrant boxes* atau image sistem operasi yang sudah siap diunduh ke dalam Virtual Machine melalui [VagrantCloud](https://atlas.hashicorp.com/boxes/search?utm_source=vagrantcloud.com&vagrantcloud=1)

Kali ini, kita akan menggunakan Ubuntu Trusty 14.04 versi 32 bit [Ubuntu/trusty32](https://atlas.hashicorp.com/ubuntu/boxes/trusty32). Mengapa Ubuntu Trusty 32 bit? Pertama Ubuntu Trusty adalah Ubuntu versi LTS atau Ubuntu dengan masa dukungan dari Canonical selama 5 tahun. 32-bit agar komputer dengan sumber daya terbatas masih dapat menjalankan Ubuntu Server dengan lancar. Cukup 512 MB RAM sudah bisa menjalankan Ruby on Rails dengan baik.

Misalkan kita membuat folder `devel`

Di Windows `D:/devel`
Di Ubuntu `/home/user/devel`
Di Mac OS `/Users/devel`

    cd devel
    vagrant init ubuntu/trusty32

Kemudian akan muncul file `Vagrantfile` di dalam folder `devel`

Edit file `Vagrantfile` sehingga memiliki seting sebagai berikut:

``` ruby
Vagrant.configure(2) do |config|
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty32"

  # Port 3000 adalah port yang digunakan pada Rails
  config.vm.network "forwarded_port", guest: 3000, host: 3000

  # Box kita berikan IP Private agar dapat diakses dari HOST
  config.vm.network "private_network", ip: "192.168.33.11"

  # Berbagi folder dan dokumen antara HOST dan GUEST Machine
  # "." adalah folder yang aktif yaitu devel di HOST
  # "/home/vagrant" adalah folder yang dibagikan bersama pada GUEST
  config.vm.synced_folder ".", "/home/vagrant"

  config.vm.provider "virtualbox" do |vb|
    # atur memory di virtual machine sebesar 512 MB
    vb.memory = "512"
  end
end
```

Setelah kita edit Vagrantfile maka kita jalankan box nya dengan perintah

    vagrant up

Setelah berhasil, maka kita login ke Guest Machine dengan perintah

    vagrant ssh

Ketika ssh, kita akan diminta sekali password. Passwordnya adalah vagrant. Berikut tampilan setelah berada di dalam vagrant box Ubuntu Trusty 32

    Welcome to Ubuntu 14.04.3 LTS (GNU/Linux 3.13.0-66-generic x86_64)
    
    * Documentation:  https://help.ubuntu.com/
    
    System information as of Mon Oct 26 16:13:38 UTC 2015
    
    System load:  0.0               Processes:           74
    Usage of /:   2.9% of 39.34GB   Users logged in:     0
    Memory usage: 7%                IP address for eth0: 10.0.2.15
    Swap usage:   0%                IP address for eth1: 192.168.33.11
    
    Graph this data and manage this system at:
      https://landscape.canonical.com/
    
    Get cloud support with Ubuntu Advantage Cloud Guest:
       http://www.ubuntu.com/business/services/cloud
    
    
    Last login: Mon Oct 26 16:13:38 2015 from 10.0.2.2
    vagrant@vagrant-ubuntu-trusty-32:~$

Setelah berhasil login ke box ubuntu trusty 32, maka untuk selanjutnya agar lebih ringkat cukup gunakan tanda dolar `$` yang menandakan bahwa perintah berada di box ubuntu trusty 32.

Selanjutnya jalankan perintah ini langkah demi langkah:

##### Install Ruby terbaru #####

    $ sudo apt-get install software-properties-common
    $ sudo apt-add-repository ppa:brightbox/ruby-ng
    $ sudo apt-get update

    $ sudo apt-get install ruby2.2 ruby2.2-dev
    $ sudo apt-get install ruby-switch
    $ sudo apt-get install bundler
    $ sudo ruby-switch --set ruby2.2
    $ ruby -v

##### Install Dependencies #####

    $ sudo apt-get update
    $ sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev

##### Install Database MySQL #####
    
    $ sudo apt-get install mysql-server mysql-client libmysqlclient-dev

##### Install Database PostgreSQL #####

    $ sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-$ pgdg main" > /etc/apt/sources.list.d/pgdg.list'
    $ sudo apt-get install wget ca-certificates
    $ sudo apt-get update
    $ sudo apt-get upgrade
    $ sudo apt-get install postgresql-9.4 postgresql-common

##### Install ImageMagick #####

    $ sudo apt-get install imagemagick

##### Install NodeJS #####

    $ sudo add-apt-repository ppa:chris-lea/node.js
    $ sudo apt-get update
    $ sudo apt-get install nodejs

##### Install Rails #####

    $ sudo gem install rails --no-rdoc --no-ri

## Membuat Project dengan Rails  ##

### Membuat Project Baru ###

    $ rails new aplikasi
    $ cd aplikasi
    $ rails s -b 0.0.0.0

Buka browser dari Host langsung. Tuliskan di URL-nya http://localhost:3000 maka akan muncul *landing page* Ruby on Rails.

### Membuat Tampilan Sederhana ###

### Menjalankan aplikasi ###

### Mendeploy aplikasi ke server ###

## Membuat Tampilan dengan Laravel ##

### Controller dan View ###

### Menubar dan Navigasi ###

### Form Input ###

### List View ###

### Login dan Logout ###

## Akses Database dengan Rails ##

### Apa itu ActiveRecord ORM ###

### Desain skema database ###

### Konfigurasi koneksi database ###

### Mapping ActiveRecord Model ke Tabel Databaes ###

### Relasi One to Many dengan ActiveRecord Model ###

## Menggabungkan Tampilan dengan Akses Database ##

### Menampilkan data di tabel ###

### Menggunakan dropdown list ###

### Menyimpan data ke database ###

### Menyimpan data berelasi ke database

## Upload file ##

### Membuat Form Upload ###

### Lokasi penyimpanan hasil upload ###

### Menangani form upload ###

### Menampilkan hasil upload ###

## Security ##

### Skema database ###

### Implementasi Login ###

### Implementasi Logout ###

### Implementasi Ijin Akses ###



