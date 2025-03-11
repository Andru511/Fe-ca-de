# Singleton 

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
  
## 3. Kelebihan dan Kekurangan Command Pattern

| **Kelebihan** | **Kekurangan** |
|--------------|--------------|
| memberikan cara untuk mengakses instance dari kelas di seluruh aplikasi tanpa perlu membuat objek baru di setiap titik penggunaan | Ketergantungan yang Tinggi  |
|Kontrol Sumber Daya | Masalah Skalabilitas |
| Penghematan Memori  | Tidak Fleksibel |

## 4. Contoh Implementasi Command Pattern dalam Java

```java
// Interface Command
interface Command {
    void execute();
}

// Kelas Receiver (Penerima Perintah)
class Light {
    void turnOn() {
        System.out.println("Lampu menyala");
    }

    void turnOff() {
        System.out.println("Lampu mati");
    }
}

// Concrete Command untuk menyalakan lampu
class LightOnCommand implements Command {
    private Light light;

    public LightOnCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOn();
    }
}

// Concrete Command untuk mematikan lampu
class LightOffCommand implements Command {
    private Light light;

    public LightOffCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOff();
    }
}

// Invoker (Pengendali perintah)
class RemoteControl {
    private Command command;

    public void setCommand(Command command) {
        this.command = command;
    }

    public void pressButton() {
        command.execute();
    }
}

// Main Class
public class CommandPatternExample {
    public static void main(String[] args) {
        Light lampu = new Light();
        Command turnOn = new LightOnCommand(lampu);
        Command turnOff = new LightOffCommand(lampu);

        RemoteControl remote = new RemoteControl();
        remote.setCommand(turnOn);
        remote.pressButton(); // Output: Lampu menyala

        remote.setCommand(turnOff);
        remote.pressButton(); // Output: Lampu mati
    }
}
```

## 5. Output Program
```
Lampu menyala
Lampu mati
```

## 6. Sumber Referensi
- [Refactoring Guru - Command Pattern](https://refactoring.guru/design-patterns/command)
- [Geeks for Geeks - Command Pattern in Java](https://www.geeksforgeeks.org/command-pattern/)
- [TutorialsPoint - Command Pattern](https://www.tutorialspoint.com/design_pattern/command_pattern.htm)
-
