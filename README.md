# pertemuan-10
PETA PERMODELAN DATA
mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)
dosen (kd_ds, nama)
matakuliah (kd_mk, nama, sks)
jadwalmengajar (kd_ds, kd_mk, hari, jam, ruang)
krsmahasiswa (nim, kd_mk, kd_ds, semester, nilai)
LANGKAH LANGKAH
1. MEMBUAT TABEL SISWA
   CREATE TABLE mahasiswa (
    nim VARCHAR(10) PRIMARY KEY,
    nama VARCHAR(25) NOT NULL,
    jenis_kelamin ENUM('Laki-Laki', 'Perempuan'),
    tgl_lahir DATE NOT NULL,
    jalan VARCHAR(15) NOT NULL,
    kota VARCHAR(15) NOT NULL,
    kodepos VARCHAR(5) NOT NULL,
    no_hp VARCHAR(15) NOT NULL,
    kd_ds VARCHAR(10) NOT NULL,
    FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds)
    );
   2. MEMBUAT TABEL DOSEN
      CREATE TABLE dosen (
    kd_ds VARCHAR(10) PRIMARY KEY,
    nama VARCHAR(35) NOT NULL
 3. MEMBUAT TABEL MATA KULIAH
    CREATE TABLE matakuliah (
    kd_mk VARCHARr(10) PRIMARY KEY,
    nama VARCHARr30) NOT NULL,
    sks INT NOT NULL
    );
    4. MEMBUAT TABEL JADWAL PENGAJAR:
     CREATE jadwalmengajar (
    kd_ds VARCHAR(10) NOT NULL,
    kd_mk VARCHAR(10) NOT NULL,
    hari ENUM('Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu', 'Minggu') NOT NULL,
    jam TIME NOT NULL,
    ruang VARCHAR(555) NOT NULL,
    PRIMARY KEY (kd_ds, kd_mk, hari, jam),
    FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds),
    FOREIGN KEY (kd_mk) REFERENCES Matakuliah(kd_mk)
    5. MEMBUAT KRS TABEL MAHASISWA
       CREATE TABLE KRSMahasiswa (
    nim VARCHAR(10) NOT NULL,
    kd_mk VARCHAR(10) NOT NULL,
    kd_ds VARCHAR(10) NOT NULL,
    semester VARCHAR(10) NOT NULL,
    nilai FLOAT NOT NULL,
    PRIMARY KEY (nim, kd_mk),
    FOREIGN KEY (nim) REFERENCES Mahasiswa(nim),
    FOREIGN KEY (kd_mk) REFERENCES Matakuliah(kd_mk),
    FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds)
  );
SOAL PRATIKUM
Berdasarkan tabel Mahasiswa pada praktikum sebelumnya: (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)

Isi data pada tabel tersebut sebanyak minimal 5 record data. Tampilkan semua isi/catatan tabel!
Ubah data tanggal lahir Mahasiswa yang bernama Ari menjadi: 1979-08-31!
Tampilkan satu baris / record data yang telah diubah tadi yaitu record dengan nama Ari saja!
Hapus Mahasiswa yang bernama Dina!
Tampilkan catatan atau data yang tanggal kelahirannya lebih dari atau sama dengan 2-1-1996!
Tampilkan semua Mahasiswa yang berasal dari Bekasi dan berjenis kelamin perempuan!
Tampilkan semua Mahasiswa yang berasal dari Bekasi dengan jenis kelamin laki-laki atau Mahasiswa yang berumur lebih dari 22 tahun dengan jenis kelamin wanita!
Tampilkan data nama dan alamat Mahasiswa saja dari tabel tersebut
Tampilkan data Mahasiswa terurut berdasarkan nama.
Mengisi tabel dengan minimal 5 data record :
INSERT INTO mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds) VALUES
(11223344,"ari santoso","Laki-laki","1998-10-12","","Bekasi","","",""), 
(11223345,"ario talib","Laki-laki","1999-11-16","","Cikarang","","",""), 
(11223346,"dina marlina","Perempuan","1997-12-01","","Karawang","","",""), 
(11223347,"lisa ayu","perempuan","1996-01-02","","Bekasi","","",""), 
(11223348,"tiara wahidah","perempuan","1980-02-05","","Bekasi","","",""), 
(11223349,"anton sinaga","laki-laki","1988-03-10","","Cikarang","","","");
A.Menampilkan semua isi/record pada tabel bisa menggunakan kode berikut :
SELECT * FROM mahasiswa;
B.Mengubah data tanggal lahir Mahasiswa yang bernama Ari menjadi : 1979-08-31 menggunakan kode berikut :
UPDATE mahasiswa SET tgl_lahir='1979-08-31' WHERE nama='Ari Santoso;
C.Menampilkan satu baris / record data yang telah diubah tadi yaitu record dengan nama Ari saja dengan cara sebagai berikut :
SELECT * FROM mahasiswa WHERE nama='Ari Santoso;
D.Menghapus Mahasiswa yang bernama Dina dengan cara sebagai berikut:
DELETE FROM mahasiswa WHERE nama='Dina Marlina'
E.Menampilkan record atau data yang tanggal kelahirannya lebih dari atau sama dengan 1996-1-2 dengan cara sebagai berikut :
SELECT * FROM mahasiswa WHERE tgl_lahir<='1996-01-02';
F.Menampilkan semua Mahasiswa yang berasal dari Bekasi dan berjenis kelamin perempuan dengan cara sebagai berikut :
G.Menampilkan semua Mahasiswa yang berasal dari Bekasi dengan jenis kelamin laki-laki atau Mahasiswa yang berumur lebih dari 22 tahun dengan jenis kelamin wanita dengan cara sebagai berikut :
SELECT * FROM mahasiswa WHERE kota='Bekasi' AND jenis_kelamin='Laki-laki' 
OR tgl_lahir<='2002-4-22' AND jenis_kelamin='Perempuan';
H.Menampilkan data nama dan jalan Mahasiswa saja dari tabel tersebut dengan cara sebagai berikut :
SELECT nama, jalan FROM mahasiswa;
I.Menampilkan data Mahasiswa terurut berdasarkan nama dengan cara sebagai berikut :
SELECT * FROM mahasiswa ORDER BY nama ASC;
