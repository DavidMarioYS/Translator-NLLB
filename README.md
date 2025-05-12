
# 🌐 Proyek Penerjemah Teks dengan NLLB

Proyek ini menggunakan model **NLLB (No Language Left Behind)** dari Meta AI untuk menerjemahkan teks antar bahasa menggunakan Python dan HuggingFace Transformers.

---

## 🎯 Tujuan

- Menerjemahkan teks dari satu bahasa ke bahasa lain.
- Mendukung banyak bahasa, termasuk Indonesia, Jepang, Korea, Cina, dan Thailand.
- Memanfaatkan model pre-trained dari HuggingFace untuk penerjemahan otomatis.

---

## 🧩 Dependensi

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
import torch
from IPython.display import display
```

- `transformers`: Mengakses model dan tokenizer NLLB.
- `torch`: Menjalankan model.
- `IPython.display`: Menampilkan hasil terjemahan di notebook.

---

## ⚙️ Langkah Kerja

1. **Load model dan tokenizer:**

   ```python
   model = AutoModelForSeq2SeqLM.from_pretrained("facebook/nllb-200-distilled-600M")
   tokenizer = AutoTokenizer.from_pretrained("facebook/nllb-200-distilled-600M")
   ```

2. **Tentukan bahasa input dan output:**

   ```python
   input_lang = "eng_Latn"
   output_lang = "ind_Latn"
   ```

3. **Tokenisasi input dan terjemahkan:**

   ```python
   tokenizer.src_lang = input_lang
   encoded = tokenizer("How are you?", return_tensors="pt")
   generated = model.generate(**encoded, forced_bos_token_id=tokenizer.lang_code_to_id[output_lang])
   ```

4. **Decode hasil terjemahan:**

   ```python
   result = tokenizer.batch_decode(generated, skip_special_tokens=True)[0]
   display(result)
   ```

---

## 🌍 Bahasa yang Dicoba

- Inggris → `eng_Latn`
- Indonesia → `ind_Latn`
- Jepang → `jpn_Jpan`
- Korea → `kor_Hang`
- Cina → `zho_Hans`
- Thailand → `tha_Thai`

---

## ✅ Hasil

Model berhasil menerjemahkan teks dengan akurat antar bahasa menggunakan model `facebook/nllb-200-distilled-600M` secara langsung di notebook.
