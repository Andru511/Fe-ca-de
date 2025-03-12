# Singleton 
# Nama Kelompok
- Andru                     (23100009)
- Sylvinho Noviyan Wijaya   (                     
- Dennis Hansen Stutanto    ( 
## 1. Penjelasan
adalah salah satu pola desain (design pattern) yang memastikan hanya ada satu instance (contoh objek) dari sebuah kelas yang dibuat selama siklus hidup aplikasi dan memberikan akses global ke instance tersebut.

Menggunakan pola Singleton ketika  perlu memastikan bahwa hanya ada satu instance dari sebuah kelas dalam aplikasi Anda.

Gunakan pola ini ketika Anda ingin menyediakan cara yang sederhana bagi klien untuk mengakses instance tersebut dari lokasi tertentu dalam kode .

Jika Anda berpikir bahwa Anda mungkin ingin memperluas kelas di kemudian hari, pola Singleton adalah pilihan yang baik. Pola ini memungkinkan subclassing, sehingga klien dapat bekerja dengan versi yang diperluas tanpa mengubah Singleton asli.

Pola ini sering digunakan dalam situasi seperti pencatatan (logging), mengelola koneksi ke perangkat keras atau basis data, caching data, atau menangani thread pool, di mana memiliki hanya satu instance sangat masuk akal.


## 2. Kapan  Perlu Digunakan?
Singelton Pattern Cocok digunakan : 
- Koneksi Database
  Ketika aplikasi membutuhkan koneksi ke database dan ingin memastikan bahwa hanya ada satu koneksi yang digunakan selama siklus hidup aplikasi, maka Singleton pattern sangat cocok.
  
- Konfigurasi Global
  Ketika aplikasi  memiliki pengaturan atau konfigurasi global yang perlu diakses di berbagai bagian aplikasi (misalnya pengaturan API, pengaturan sistem, atau pengaturan aplikasi lainnya)
  
- Akses ke API
  Dalam situasi di mana aplikasi berinteraksi dengan layanan eksternal atau API yang memerlukan kredensial tau pengaturan yang konsisten,  Singleton dapat memastikan bahwa hanya ada satu objek yang menangani komunikasi dengan layanan tersebut.
  
## 3. Kelebihan dan Kekurangan Singelton 

| **Kelebihan** | **Kekurangan** |
|--------------|--------------|
| Penggunaan Global Instance | Ketergantungan yang Tinggi  |
|Kontrol Sumber Daya | Masalah Skalabilitas |
| Penghematan Memori  | Tidak Fleksibel |

Penggunaan Global Instance Singleton memberikan cara untuk mengakses instance dari kelas di seluruh aplikasi tanpa perlu membuat objek baru di setiap titik penggunaan. Ini memudahkan penggunaan global karena instance tersebut dapat diakses dari mana saja di dalam aplikasi.

Singleton memastikan bahwa hanya ada satu instance dari sebuah kelas yang dibuat. Ini sangat berguna ketika Anda perlu mengelola sumber daya terbatas, seperti koneksi database, file, atau perangkat keras lainnya. Hal ini menghindari pemborosan sumber daya dengan menciptakan banyak objek yang sebenarnya tidak diperlukan.

Penghematan Memori Karena hanya ada satu instance yang digunakan di seluruh aplikasi, penggunaan memori menjadi lebih efisien, terutama jika objek tersebut besar atau membutuhkan banyak sumber daya.



## 4. Contoh Implementasi  dalam Java

```class Database {
    private static Database dbObject;

    private Database() {      
    }

    public static Database getInstance() {
        if(dbObject == null) {
            dbObject = new Database();
        }
        return dbObject;
    }

    public void getConnection() {
        System.out.println("You are now connected to the database.");
    }

    public static void main(String[] args) {
        Database db1 = Database.getInstance();
        db1.getConnection();
    }
}

```

## 5. Output dari Program
```
You are now connected to the database.
```

## 6. Reference 
```````
https://www.geeksforgeeks.org/prototype-design-pattern/
https://www.programiz.com/java-programming/singleton#:~:text=In%20Java%2C%20Singleton%20is%20a,creation%20outside%20of%20the%20class
https://www.codepolitan.com/blog/mengenal-dan-belajar-design-pattern-singleton/
``````
