# Assignment: Vue.js – Simple To-Do List

## Identitas

- **Nama** : Ida Bagus Brahmanta Jayana
- **NIM** : FD22052
- **Mata Kuliah** : Pemrograman Web Lanjut
- **Assignment** : Week 12 - Vue.js To-Do List

---

## Deskripsi Tugas

Pada tugas ini saya membuat aplikasi To-Do List sederhana menggunakan Vue.js dengan fitur-fitur berikut:

### Fitur Aplikasi:

- ✅ **Menambah tugas** - Form input untuk menambahkan tugas baru
- ✅ **Menghapus tugas** - Tombol hapus untuk setiap item tugas
- ✅ **Menampilkan pesan saat daftar kosong** - Pesan "Tidak ada tugas" ketika list kosong
- ✅ **Menggunakan reaktifitas dengan `ref()`** - State management dengan Vue 3 Composition API
- ✅ **Event handling** - Submit form dan click events
- ✅ **Data binding** - Two-way binding dengan v-model

---

## Teknologi yang Digunakan

- **Vue.js 3** - Framework JavaScript
- **Vite** - Build tool dan development server
- **Composition API** - Vue 3 setup script dengan ref()
- **CSS3** - Styling dengan responsive design

---

## Struktur Kode

### 1. State Management

```javascript
// State menggunakan ref()
const tasks = ref([]); // Array untuk menyimpan daftar tugas
const newTask = ref(""); // String untuk input tugas baru
```

### 2. Fungsi Utama

```javascript
// Fungsi untuk menambah tugas
const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value.trim());
    newTask.value = ""; // Reset input
  }
};

// Fungsi untuk menghapus tugas
const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};
```

### 3. Template Features

- **Form dengan prevent modifier**: `@submit.prevent="addTask"`
- **Two-way binding**: `v-model="newTask"`
- **Conditional rendering**: `v-if="tasks.length === 0"`
- **List rendering**: `v-for="(task, index) in tasks" :key="index"`
- **Event handling**: `@click="deleteTask(index)"`

---

## Cara Menjalankan Aplikasi

### 1. Install Dependencies

```bash
npm install
```

### 2. Jalankan Development Server

```bash
npm run dev
```

### 3. Buka Browser

Aplikasi akan berjalan di `http://localhost:5173`

---

## Hasil

### 1. Screenshot Hasil Program

![To-Do List App](screenshots/todo-app-screenshot.png)
_Screenshot aplikasi To-Do List yang sudah berjalan_

### 2. Penjelasan Singkat

#### Cara Kerja `addTask()`

- Fungsi ini dipanggil ketika form di-submit
- Mengecek apakah input tidak kosong dengan `newTask.value.trim() !== ''`
- Menambahkan tugas baru ke array `tasks` menggunakan `tasks.value.push()`
- Mereset input field dengan `newTask.value = ''`

#### Cara Kerja `v-for` untuk Menampilkan Data

- Menggunakan `v-for="(task, index) in tasks"` untuk iterasi array tasks
- Setiap item memiliki `:key="index"` untuk tracking perubahan
- Menampilkan teks tugas dengan `{{ task }}`
- Menyediakan tombol hapus dengan index sebagai parameter

#### Cara Kerja Tombol Hapus

- Setiap tombol hapus memiliki event `@click="deleteTask(index)"`
- Fungsi `deleteTask(index)` menggunakan `splice()` untuk menghapus item pada index tertentu
- Vue secara otomatis me-render ulang list setelah data berubah

#### Reaktivitas Vue.js

- Menggunakan `ref()` untuk membuat reactive state
- Perubahan pada `tasks.value` atau `newTask.value` otomatis memperbarui UI
- Two-way binding dengan `v-model` menghubungkan input dengan state

---

## Fitur Tambahan (Improvisasi)

- 🎨 **Styling yang menarik** - Design modern dengan hover effects
- 📱 **Responsive design** - Tampilan yang baik di berbagai ukuran layar
- ✨ **Smooth animations** - Transisi halus pada hover dan interaksi
- 🔍 **Input validation** - Mencegah penambahan tugas kosong
- 🗑️ **Icon pada tombol** - Emoji untuk memperjelas fungsi tombol

---

## Struktur File

```
todoVue_FD2200123/
├── src/
│   ├── App.vue          # Komponen utama aplikasi
│   └── main.js          # Entry point aplikasi
├── public/
├── package.json
└── README.md           # Dokumentasi ini
```

---

## Kesimpulan

Aplikasi To-Do List ini berhasil mengimplementasikan semua requirement tugas:

- ✅ Setup proyek Vue dengan nama folder sesuai format
- ✅ State management menggunakan `ref()`
- ✅ Form input dengan v-model binding
- ✅ Fungsi addTask dengan event handling
- ✅ List rendering dengan v-for dan key
- ✅ Fungsi deleteTask dengan parameter index
- ✅ Conditional rendering untuk kondisi kosong
- ✅ Styling yang rapi dan user-friendly

Aplikasi berjalan tanpa error dan memiliki tampilan yang menarik serta fungsionalitas yang lengkap sesuai dengan requirement assignment.
