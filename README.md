# Jarkom-Modul-4-F09-2022

## Anggota Kelompok

<table>
    <tr>
	    <th>Nama</th>
        <th>NRP</th>
    </tr>
    <tr>
        <td>Muhammad Lintang Panjerino</td>
        <td>5025201045</td>
    </tr>
    <tr>
        <td>Sayid Ziyad Ibrahim Alaydrus</td>
        <td>5025201147</td>
    </tr>
    <tr>
        <td>Wahyu Tri Saputro</td>
        <td>5025201217</td>
    </tr>
<table>

# Routing dan Subnetting dengan VLSM di GNS3

# Topologi

![TOPOLOGI](img/VLSM/Topologi.png)

Berikut adalah topologi di GNS3, topologi tersebut sudah dibuat subnet nya juga, sehingga nanti memudahkan dalam menghitung pembagian IP. Setelah itu, kita hitung jumlah alamt IP yang dilakukan oleh tiap subnet sekaligus nanti kita berikan label netmask berdasarkan jumlah alamat IP yang dibutuhkan. Kemudian kita total semua jumlah IP untuk menentukan "start" netmask yang dibutuhkan untuk menghitung pembagian IP.

![LABELLING](img/VLSM/IP.png)

Berdasarkan tabel tersebut, subnet besar yang dibentuk memiliki NID 10.33.0.0 dengan netmask /20, maka kita tinggal hitung pembagian IP seperti berikut :

![IPTREE](img/VLSM/IPTree.png)
Setelah didapatkan IP dan netmask untuk masing - masing subnet, kita bisa masukkan ke tabel terlebih dahulu untuk merapikan dan menata IP

![HASIL](img/VLSM/HasilPerhitungan.png)

Setelah itu kita tinggal menyetting/menyamakan IP per node di dalam GNS3 dengan cara membuka Network Configuration nya.

# Routing

Setelah menyetting IP di GNS3 nya, kita bisa menambahkan routing dengan cara menambahkan line berikut di console :

`route add -net <NID subnet> netmask <netmask> gw <IP gateway>`

Routing ditambahkan sesuai tujuan, untuk mengecek bisa dengan perintah seperti berikut :

`route -n`

Setelah routing dilakukan, maka kita bisa mengetes dengan cara ping dari client - client atau client - server, salah satu contoh bisa dilihat pada screenshot berikut :

![ROUTING](img/VLSM/Routing.png)

## CIDR (Classless Inter Domain Routing) - CPT (CISCO PACKET TRACER)

### Topologi

Berikut adalah topologi CPT dari kelompok kami:

![topologiCIDR](/img/CIDR/TopologiCIDR.png)

### Subnetting

Pada subnetting menggunakan perhitungan CIDR ini, terdapat 10 langkah penggabungan subnet yang kami lakukan dari step A sampai step J. Penggabungan subnet tersebut dimulai dari subnet terkecil.

#### Langkah 1

![stepA](/img/CIDR/stepA.png)

#### Langkah 2

![stepB](/img/CIDR/stepB.png)

#### Langkah 3

![stepC](/img/CIDR/stepC.png)

#### Langkah 4

![stepD](/img/CIDR/stepD.png)

#### Langkah 5

![stepE](/img/CIDR/stepE.png)

#### Langkah 6

![stepF](/img/CIDR/stepF.png)

#### Langkah 7

![stepG](/img/CIDR/stepG.png)

#### Langkah 8

![stepH](/img/CIDR/stepH.png)

#### Langkah 9

![stepI](/img/CIDR/stepI.png)

#### Langkah 10

![stepJ](/img/CIDR/stepJ.png)

### Pohon Pembagian IP

Berdasarkan perhitungan subnet dan penggabungan subnet yang telah dilakukan, didapatkan subnet terbesar J1 dengan netmask /17. Sehingga didapatkan pembagian IP yang diilustrasikan dengan tree pada gambar berikut ini.

![cidr_tree](/img/CIDR/treeCIDR.png)

### Tabel Pembagian IP

Kemudian untuk tabel pembagian IP yang lebih detail berada pada <a href="/Tabel%20Pembagian%20IP%20CIDR.pdf">file berikut</a>.

### Setting IP pada CPT

Berikut adalah contoh setting IP pada CPT:

Untuk router, setting IP dan subnet mask dapat dilakukan dengan double click node > Config > Interface. Sedangkan untuk host bisa dilakukan dengan click node > Desktop > IP Configuration

Berikut adalah salah satu contoh konfigurasi interface pada router utama Resonance dan client Ashaf

![setting-resonance](/img/CIDR/setting_router.png)
![setting-ashaf](/img/CIDR/setting_client.png)

### Routing

Routing pada CPT dapat dilakukan dengan click node router > Config > Routing > Static

#### Default Routing

Default Routing dilakukan pada semua router selain router utama (The Resonance). Default router dilakukan pada router yang berada pada tingkatan lebih bawah dan mengarah pada router diatasnya.

Salah satu contohnya adalah pada router The Magical ke router The Resonance.

![default_magical](/img/CIDR/defaul_routing.png)

Untuk default routing, network dan mask akan diisi 0.0.0.0 . Sedangkan next hop diisi dengan interface dari router diatasnya/sebelumnya.

#### Static Routing

Static Routing dilakukan agar router dapat terhubung dengan client. Pada kali ini karena menggunakan teknik CIDR di CPT, maka Static Routing dilakukan pada semua subnet agar dapat saling terhubung. Namun yang dimasukkan dalam Static Routing tidak perlu semua IP router, hanya subnet nya saja (dapat dilihat pada pohon pembagian IP).

Salah satu contohnya adalah pada router The Order, Static Routing yang dilakukan hanya 1 kali, yaitu pada subnet C1 - 10.33.64.0/21 melalui interface 10.33.72.2

![static_order](/img/CIDR/static_routing.png)

Pada The Order, network dan mask yang dipakai adalah NID dan subnet mask dari subnet di bawahnya (subnet C1). Sedangkan next hop merupakan interface milik router dibawahnya yang terhubung dengan router yang akan dirouting, pada kasus ini interface yang dipakai merupakan interface dari The Minister dengan FastEthernet 0/0 yang terhubung dengan The Order. Hal ini juga dilakukan pada router-router lain.

Contoh lain:

![resonance](/img/CIDR/resonance.png)
![instrument](/img/CIDR/instrument.png)
![firefist](/img/CIDR/firefist.png)
