# Singleton
# Command Pattern dalam Java

## 1. Penjelasan tentang Command Pattern
Command Pattern adalah pola desain perilaku (behavioral design pattern) yang mengubah permintaan atau perintah menjadi objek yang dapat dieksekusi, disimpan, atau dikembalikan nanti. Pola ini berguna dalam mengimplementasikan undo/redo, log transaksi, dan queueing sistem.

## 2. Kapan Command Pattern Perlu Digunakan?
Command Pattern cocok digunakan dalam situasi berikut:
- Saat kita ingin menyimpan daftar perintah yang bisa dieksekusi ulang (undo/redo).
- Dalam sistem menu UI di mana setiap tindakan pengguna harus bisa dieksekusi ulang atau dibatalkan.
- Dalam aplikasi game untuk mengelola input pemain sebagai kumpulan perintah yang bisa dianalisis.
- Dalam sistem multi-threading, untuk menunda atau mengantri eksekusi perintah.

## 3. Kelebihan dan Kekurangan Command Pattern

| **Kelebihan** | **Kekurangan** |
|--------------|--------------|
| Memisahkan objek yang meminta perintah dari objek yang menjalankannya | Bisa menambah kompleksitas kode jika tidak diperlukan |
| Memudahkan implementasi fitur undo/redo | Membutuhkan lebih banyak kelas dibandingkan metode langsung |
| Memungkinkan perekaman dan eksekusi perintah secara terstruktur | Bisa mempengaruhi performa jika perintah disimpan dalam jumlah besar |

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
