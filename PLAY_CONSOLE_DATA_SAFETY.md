# Kisi-kisi Google Play Console — Data Safety & Store Listing

> Untuk app **Andalusia** (`com.AndalusiaProject.Andalusia`)  
> Privacy policy: https://andalusiagame.github.io/andalusia-privacypolicy/  
> Kontak privasi: andalusiagame@gmail.com

Isi form Play Console **sesuai kondisi app saat rilis v1** (progress lokal, Firebase Auth, tanpa IAP).

---

## A. Store listing (Informasi dasar)

| Pertanyaan / Field | Jawaban disarankan |
|--------------------|-------------------|
| Nama app | Andalusia |
| Deskripsi singkat | Game edukasi sejarah Andalusia untuk SMP (platformer + kuis) |
| Kategori | Pendidikan / Educational |
| Konten rating (IARC) | Isi kuesioner jujur (kekerasan kartun ringan platformer, tidak ada konten seksual, dll.) |
| Target usia | Remaja / 12+ (sesuai policy: 12–15 tahun) |
| Privacy policy URL | `https://andalusiagame.github.io/andalusia-privacypolicy/` |
| Email developer | `andalusiagame@gmail.com` |
| Apakah app gratis? | **Ya** |
| In-app purchases? | **Tidak** |
| Iklan? | **Tidak** (jika memang tidak ada AdMob/ads) |

---

## B. Data safety — Langkah 1: Kumpulkan / bagikan data?

| Pertanyaan | Jawaban v1 |
|------------|------------|
| Apakah app mengumpulkan data pengguna? | **Ya** |
| Apakah semua data dienkripsi in transit? | **Ya** (HTTPS untuk Firebase Auth) |
| Apakah pengguna bisa meminta penghapusan data? | **Ya** → email `andalusiagame@gmail.com` |
| Apakah data wajib (tidak bisa opt-out)? | **Sebagian** — progress game wajib untuk fitur; akun wajib jika login dipakai |

---

## C. Data safety — Tipe data (centang yang **benar-benar** dipakai)

### 1. Informasi pribadi

| Tipe data | Dikumpulkan? | Dibagikan ke pihak ketiga? | Wajib? | Tujuan |
|-----------|-------------|----------------------------|--------|--------|
| **Alamat email** | ✅ Ya (Firebase Auth) | ✅ Ya → Google (Firebase) | Opsional* | Account management, Authentication |
| **User IDs** | ✅ Ya (Firebase UID) | ✅ Ya → Google | Opsional* | Account management |
| Nama | ❌ Tidak | — | — | — |
| Alamat fisik | ❌ Tidak | — | — | — |
| Nomor telepon | ❌ Tidak | — | — | — |

\* *Opsional jika user bisa main tanpa login; wajib jika login dipakai di sekolah.*

### 2. Data aplikasi / performa (Analytics)

| Tipe data | Dikumpulkan? | Catatan |
|-----------|-------------|---------|
| Crash logs | ⚠️ Cek Firebase/Crashlytics | Centang **hanya jika** aktif di Firebase console |
| Diagnostics | ⚠️ Sama | Device model, OS — via Analytics SDK |
| App interactions | ⚠️ Sama | Event analytics agregat |

**Sebelum centang Analytics:** buka [Firebase Console](https://console.firebase.google.com/) → project `andalusia-45298` → Analytics — pastikan aktif atau nonaktif, lalu sesuaikan form.

### 3. Data yang **TIDAK** dikumpulkan (jangan centang)

- Lokasi (approximate / precise)
- Kontak
- Foto / video
- Audio (mikrofon)
- File / dokumen pengguna
- Info pembayaran
- Data kesehatan
- Pesan SMS / panggilan

### 4. Progress pembelajaran (App activity / Other)

| Data | Dikumpulkan? | Disimpan di | Dibagikan? |
|------|-------------|-------------|------------|
| Skor, level, clue, jawaban kuis | ✅ Ya | **Hanya lokal di perangkat** | ❌ Tidak ke pihak ketiga (v1) |
| Preferensi audio | ✅ Ya | Lokal (`PlayerPrefs`) | ❌ Tidak |

> **Penting:** Jangan centang "cloud storage / sync" untuk progress di Data safety **sampai** fitur sync Firebase benar-benar dirilis.

---

## D. Data safety — Praktik keamanan

| Pertanyaan | Jawaban |
|------------|---------|
| Data dienkripsi in transit? | **Ya** |
| Pengguna bisa minta hapus data? | **Ya** — uninstall/hapus data app (progress lokal) + email untuk akun Firebase |
| Data diproses ephemerally? | **Tidak** (progress disimpan sampai dihapus) |
| Kepatuhan Families / anak | Target SMP — pastikan tidak ada behavioral ads |

---

## E. Firebase & pihak ketiga (Data sharing)

Centang **Google** sebagai pihak ketiga untuk:

| Layanan | Data yang diproses Google |
|---------|---------------------------|
| Firebase Authentication | Email, User ID, credential (password di-hash Firebase) |
| Firebase Analytics | *(jika aktif)* device, app version, usage agregat |
| Google Play | Distribusi, crash report sistem (jika Pre-launch report) |

Link ke kebijakan Google: https://policies.google.com/privacy

---

## F. Checklist sebelum submit

- [ ] Privacy policy URL live & versi **1.1** (22 Jun 2026)
- [ ] Bag. 10 sudah merujuk **Bagian 16** (bukan 14)
- [ ] Data safety = selaras dengan app (progress **lokal**, cloud **belum**)
- [ ] Firebase Analytics: cek aktif/tidak → form disesuaikan
- [ ] Login Firebase: uji sign-up/sign-in di build release
- [ ] Tidak ada permission GPS, kamera, mikrofon di manifest
- [ ] Closed testing / internal testing sudah diisi tester
- [ ] Content rating selesai
- [ ] Screenshot & icon store listing

---

## G. Pertanyaan yang perlu Anda putuskan nanti

1. **Apakah login wajib** sebelum main, atau opsional? → affects "Required vs Optional" di Data safety.
2. **Apakah Firebase Analytics aktif** di project `andalusia-45298`? → affects diagnostics section.
3. **Kapan cloud sync progress dirilis?** → update policy + Data safety saat fitur live.
4. **Apakah fitur feedback** (komentar + device model) akan dirilis? → tambah ke policy & form jika ya.
5. **Splash screen Unity** — ganti logo (tidak affect privacy, backlog terpisah).

---

*Dokumen panduan internal tim AndalusiaProject — bukan bagian dari kebijakan privasi publik.*
