# Sistem-Pendaftaran-Fun-Run-PBO

## Nama: Aliyah Azzah Sekedang
## Kelas: A Sistem Informasi
## NIM: 2409116021

import java.util.ArrayList;
import java.util.Scanner;
public class SistemPendaftaranFunRun {
    // Inner class untuk menyimpan data peserta
    static class Peserta {
        String nama;
        String telepon;

        Peserta(String nama, String telepon) {
            this.nama = nama;
            this.telepon = telepon;
        }
    }

    // ArrayList daftar peserta
    static ArrayList<Peserta> daftarPeserta = new ArrayList<>();
    static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int pilihan;

        do {
            // Tampilkan menu
            System.out.println("\n=== SISTEM PENDAFTARAN FUN RUN ===");
            System.out.println("1. Tambah Peserta");
            System.out.println("2. Lihat Peserta");
            System.out.println("3. Ubah Peserta");
            System.out.println("4. Hapus Peserta");
            System.out.println("5. Keluar");
            System.out.print("Pilih menu: ");
            pilihan = scanner.nextInt();
            scanner.nextLine(); // membersihkan buffer

            // Ganti switch dengan if-else
            if (pilihan == 1) {
                tambahPeserta();
            } else if (pilihan == 2) {
                lihatPeserta();
            } else if (pilihan == 3) {
                ubahPeserta();
            } else if (pilihan == 4) {
                hapusPeserta();
            } else if (pilihan == 5) {
                System.out.println("Thankyou and See You on Fun Run!");
            } else {
                System.out.println("Pilihan tidak valid, coba lagi.");
            }
        } while (pilihan != 5);
    }

    // CRUD - Tambah
    public static void tambahPeserta() {
        System.out.print("Masukkan nama peserta: ");
        String nama = scanner.nextLine();
        System.out.print("Masukkan nomor telepon: ");
        String telepon = scanner.nextLine();

        daftarPeserta.add(new Peserta(nama, telepon));
        System.out.println("Peserta berhasil ditambahkan!");
    }

    // CRUD - Lihat
    public static void lihatPeserta() {
        if (daftarPeserta.isEmpty()) {
            System.out.println("Belum ada peserta yang terdaftar.");
        } else {
            System.out.println("\n=== DAFTAR PESERTA FUN RUN ===");
            for (int i = 0; i < daftarPeserta.size(); i++) {
                Peserta p = daftarPeserta.get(i);
                System.out.println((i + 1) + ". Nama: " + p.nama + " | Telepon: " + p.telepon);
            }
        }
    }

    // CRUD - Ubah
    public static void ubahPeserta() {
        lihatPeserta();
        if (!daftarPeserta.isEmpty()) {
            System.out.print("Masukkan nomor peserta yang ingin diubah: ");
            int index = scanner.nextInt();
            scanner.nextLine(); // membersihkan buffer
            if (index > 0 && index <= daftarPeserta.size()) {
                Peserta p = daftarPeserta.get(index - 1);
                System.out.print("Masukkan nama baru (kosongkan jika tidak diubah): ");
                String namaBaru = scanner.nextLine();
                System.out.print("Masukkan telepon baru (kosongkan jika tidak diubah): ");
                String teleponBaru = scanner.nextLine();

                if (!namaBaru.isEmpty()) p.nama = namaBaru;
                if (!teleponBaru.isEmpty()) p.telepon = teleponBaru;

                System.out.println("Data peserta berhasil diubah!");
            } else {
                System.out.println("Nomor peserta tidak valid.");
            }
        }
    }

    // CRUD - Hapus
    public static void hapusPeserta() {
        lihatPeserta();
        if (!daftarPeserta.isEmpty()) {
            System.out.print("Masukkan nomor peserta yang ingin dihapus: ");
            int index = scanner.nextInt();
            scanner.nextLine(); // membersihkan buffer
            if (index > 0 && index <= daftarPeserta.size()) {
                daftarPeserta.remove(index - 1);
                System.out.println("Peserta berhasil dihapus!");
            } else {
                System.out.println("Nomor peserta tidak valid.");
            }
        }
    }   
}
