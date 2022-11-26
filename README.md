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
