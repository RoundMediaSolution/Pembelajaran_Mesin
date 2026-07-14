# IT Service Desk Automation with Closed-Domain RAG & n8n Orchestration

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![n8n Compatibility](https://img.shields.io/badge/n8n-compatible-green.svg)](https://n8n.io/)
[![Groq API](https://img.shields.io/badge/LLM-Groq%20%2F%20Llama%203.3-orange.svg)](https://groq.com/)
[![License](https://img.shields.io/badge/license-MIT-purple.svg)](LICENSE)

Repositori ini berisi kode dan panduan implementasi sistem **AI Chat Agent untuk IT Service Desk** berbasis *Closed-Domain Retrieval-Augmented Generation* (RAG). Arsitektur ini dirancang secara mandiri (*self-hosted*) untuk memproses, membersihkan, dan mengekstrak dokumen tiket solusi historis (terbaca dari pangkalan data lokal), lalu mengotomatisasi respons interaksi pengguna melalui berbagai kanal komunikasi tanpa risiko kebocoran data.

---

## 🚀 Fitur Utama
* **Closed-Domain Constraint:** Membatasi kognisi LLM agar memberikan solusi *hanya* berdasarkan basis pengetahuan internal dan memicu *fallback response* otomatis jika kueri berada di luar konteks (Out-of-Context).
* **Automated Fault-Tolerance (Auto-Switch Model):** Proteksi kegagalan pengolahan token akibat batasan kuota (*Rate Limit Errors / Status 429*) di Groq API dengan peralihan dinamis otomatis dari model `llama-3.3-70b-versatile` menuju `llama-3.1-8b-instant` atau `gemma2-9b-it`.
* **Advanced Data Preprocessing:** Papan pembersihan (*data cleaning*) otomatis terintegrasi untuk menangani normalisasi teks (*case folding*), penghapusan noise/tautan internal, serta anonimisasi identitas email sensitif.
* **n8n Ready-to-Export:** Skrip pemrosesan mampu memformat pangkalan pengetahuan menjadi struktur array objek JSON standar yang siap dibaca secara asli oleh orkestrasi workflow n8n.
* **Comprehensive Quantitative Evaluation:** Script visualisasi mandiri yang melacak kinerja akurasi klasifikasi sistem melalui grafik distribusi dan matriks konfusi (*Confusion Matrix*).

---

## 📂 Struktur Repositori
```text
├── Summarizer.ipynb                 # Jupyter Notebook Utama (Eksperimen & Evaluasi Lengkap)
├── dataset_tiket_it_cleaned.csv     # Output data hasil pembersihan dan anonimisasi (Uji)
├── dataset_it_service_desk_n8n.json # Output file terformat untuk di-import langsung ke n8n
├── confusion_matrix_bab4_final.png  # Grafik visualisasi heatmap Confusion Matrix untuk Bab 4
└── README.md                        # Dokumentasi ini
