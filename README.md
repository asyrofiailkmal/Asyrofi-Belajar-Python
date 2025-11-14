# Asyrofi-Belajar-Python
# MESIN KASIR SEDERHANA
# Hanya menggunakan: input, print, if, loop, dan function

# 1. Function untuk input daftar barang
def input_daftar_barang():
    daftar_barang = []  # akan berisi tuple: (nama, harga, jumlah)

    print("=== INPUT BARANG ===")
    print('Ketik "0" pada nama barang jika sudah selesai.\n')

    while True:
        nama = input("Nama barang : ")

        # jika nama = "0", keluar dari loop
        if nama == "0":
            break

        # input harga & jumlah (diubah ke int)
        harga = int(input("Harga satuan: "))
        jumlah = int(input("Jumlah      : "))

        # simpan ke list sebagai tuple
        daftar_barang.append((nama, harga, jumlah))
        print("Barang ditambahkan!\n")

    return daftar_barang


# 2. Function untuk menghitung total belanja
def hitung_total(daftar_barang):
    total = 0
    for barang in daftar_barang:
        nama, harga, jumlah = barang
        subtotal = harga * jumlah
        total += subtotal
    return total


# 3. Function untuk menghitung diskon
def hitung_diskon(total):
    # Aturan: jika total >= 100.000 dapat diskon 10%
    if total >= 100000:
        diskon = int(0.10 * total)
    else:
        diskon = 0
    return diskon


# 4. Function untuk mencetak struk
def cetak_struk(daftar_barang, total, diskon, dibayar):
    print("\n========== STRUK BELANJA ==========")
    for barang in daftar_barang:
        nama, harga, jumlah = barang
        subtotal = harga * jumlah
        print(f"{nama} x{jumlah} @ {harga} = {subtotal}")

    print("-----------------------------------")
    print(f"Total       : {total}")
    print(f"Diskon      : {diskon}")
    grand_total = total - diskon
    print(f"Grand Total : {grand_total}")
    print(f"Dibayar     : {dibayar}")
    kembalian = dibayar - grand_total
    print(f"Kembalian   : {kembalian}")
    print("===================================\n")


# 5. Function utama (main) untuk mengatur alur program
def main():
    # langkah 1: input barang
    daftar_barang = input_daftar_barang()

    # jika tidak ada barang, langsung selesai
    if len(daftar_barang) == 0:
        print("Tidak ada barang yang dibeli.")
        return

    # langkah 2: hitung total
    total = hitung_total(daftar_barang)

    # langkah 3: hitung diskon
    diskon = hitung_diskon(total)
    grand_total = total - diskon

    # langkah 4: input uang bayar
    print(f"\nTotal belanja (setelah diskon) : {grand_total}")
    dibayar = int(input("Uang dibayar pelanggan        : "))

    # (opsional) cek jika uang kurang
    if dibayar < grand_total:
        print("Uang kurang! Transaksi dibatalkan.")
        return

    # langkah 5: cetak struk
    cetak_struk(daftar_barang, total, diskon, dibayar)


# 6. Panggil main() agar program berjalan
main()
