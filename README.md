# Singleton 
# Nama Kelompok
- Andru                     (23100009)
- Pingo                     
- Dennis Hansen Stutanto     
## 1. Penjelasan
adalah salah satu pola desain (design pattern) yang memastikan hanya ada satu instance (contoh objek) dari sebuah kelas yang dibuat selama siklus hidup aplikasi dan memberikan akses global ke instance tersebut.

## 2. Kapan  Perlu Digunakan?
Singelton Pattern Cocok digunakan : 
- Koneksi Database
  Ketika aplikasi membutuhkan koneksi ke database dan Anda ingin memastikan bahwa hanya ada satu koneksi yang digunakan selama siklus hidup aplikasi, maka Singleton pattern sangat cocok.
  
- Konfigurasi Global
  Ketika aplikasi  memiliki pengaturan atau konfigurasi global yang perlu diakses di berbagai bagian aplikasi (misalnya pengaturan API, pengaturan sistem, atau pengaturan aplikasi lainnya
  
- Akses ke API
  Dalam situasi di mana aplikasi berinteraksi dengan layanan eksternal atau API yang memerlukan kredensial atau pengaturan yang konsisten, Anda bisa menggunakan Singleton untuk memastikan bahwa hanya ada satu objek yang menangani komunikasi dengan layanan tersebut.
  
## 3. Kelebihan dan Kekurangan Singelton 

| **Kelebihan** | **Kekurangan** |
|--------------|--------------|
| Penggunaan Global Instance | Ketergantungan yang Tinggi  |
|Kontrol Sumber Daya | Masalah Skalabilitas |
| Penghematan Memori  | Tidak Fleksibel |

## 4. Contoh Implementasi Command Pattern dalam Java

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

