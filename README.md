# data-encryption-standard
Kuis 3 Kriptografi - Felix Joshua Paulus 105222032 - Muhammad Rizqi Ferdhinandito 105222041 

---

## 📂 Fitur Utama

| Bagian Kode / Fitur           | Deskripsi                                                                                       | Contoh Kode (Potongan)                                                    |
|-------------------------------|-------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| **Impor Pustaka**             | Mengimpor modul yang diperlukan: `DES` dari `Crypto.Cipher` untuk enkripsi DES, `pad` dari `Crypto.Util.Padding` untuk padding, dan `base64` untuk encoding. | ```python<br>from Crypto.Cipher import DES<br>from Crypto.Util.Padding import pad<br>import base64<br>``` |
| **Fungsi `des_encrypt`**      | Fungsi utama yang menerima `plain_text` (string) dan `key` (string) sebagai input, dan mengembalikan ciphertext yang sudah di-encode Base64 (string). | ```python<br>def des_encrypt(plain_text, key):<br> ...<br>``` |
| **Validasi Panjang Kunci**    | Memeriksa apakah panjang `key` tepat 8 byte. DES memerlukan kunci 64-bit (8 byte). Jika tidak, memunculkan `ValueError`. | ```python<br>if len(key) != 8:<br> raise ValueError("Key harus sepanjang 8 byte")<br>``` |
| **Inisialisasi Cipher DES**   | Membuat objek cipher DES. Kunci string diubah menjadi byte (`key.encode()`). Mode operasi yang digunakan: **ECB**. | ```python<br>cipher = DES.new(key.encode(), DES.MODE_ECB)<br>``` |
| **Padding Plaintext**         | Plaintext (string) diubah menjadi byte (`plain_text.encode()`). Karena DES adalah block cipher, plaintext di-padding agar panjangnya menjadi kelipatan dari ukuran blok DES (8 byte). | ```python<br>padded_text = pad(plain_text.encode(), DES.block_size)<br>``` |
| **Enkripsi**                  | Melakukan enkripsi pada `padded_text` menggunakan objek cipher. Hasilnya adalah `encrypted_bytes`. | ```python<br>encrypted_bytes = cipher.encrypt(padded_text)<br>``` |
| **Encoding Base64**           | `encrypted_bytes` (biner) di-encode ke Base64. Hasil Base64 (byte) kemudian di-decode menjadi string. | ```python<br>encrypted_base64 = base64.b64encode(encrypted_bytes).decode()<br>``` |
| **Return Value**              | Fungsi `des_encrypt` mengembalikan `encrypted_base64` (string). | ```python<br>return encrypted_base64<br>``` |
| **Input Pengguna**            | Bagian `try-except` di luar fungsi menangani input pengguna untuk plaintext dan key. | ```python<br>plaintext = input("Teks yang ingin dienkripsi: ")<br>key = input("Input Key (8 karakter): ")<br>``` |
| **Pemanggilan Fungsi & Output** | Memanggil fungsi `des_encrypt` dengan input pengguna dan mencetak hasil enkripsi (Base64) ke konsol. | ```python<br>encrypted = des_encrypt(plaintext, key)<br>print("Hasil Enkripsi (base64):", encrypted)<br>``` |
| **Penanganan Error**          | Blok `except ValueError as ve:` menangkap error jika panjang kunci tidak valid dan mencetak pesan error. | ```python<br>except ValueError as ve:<br> print("Error:", ve)<br>``` |

---

## Langkah

Masukkan Plaintext yang ingin dienkripsi
dan Key (tepat 8 karakter)

## Lisensi

Felix Joshua Paulus (105222032) - Muhammad Rizqi Ferdhinandito (105222041)
