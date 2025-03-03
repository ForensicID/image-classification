# CNN Image Classification - Cats vs Dogs 🐱🐶

## 📌 Overview
Proyek ini merupakan implementasi **Convolutional Neural Network (CNN)** untuk klasifikasi gambar **kucing dan anjing**. Model dilatih menggunakan **TensorFlow & Keras**, serta disimpan dalam beberapa format:  
- **SavedModel** (untuk TensorFlow Serving)
- **TFLite** (untuk mobile & embedded devices)
- **TensorFlow.js** (untuk deployment di web)

## 📂 Struktur Folder
```
image-classification
│
├── saved_model
│   ├── variables
│   └── saved_model.pb
│
├── tfjs_model
│   ├── group1-shard1of4.bin
│   ├── group1-shard2of4.bin
│   ├── group1-shard3of4.bin
│   ├── group1-shard4of4.bin
│   └── model.json
│
├── tflite
│   ├── label.txt
│   └── model.tflite
│
├── notebook.ipnyb
├── README.md
└── requirements.txt
```

## 📊 Dataset
Dataset yang digunakan berisi **gambar kucing dan anjing** yang diambil dari **Kaggle**. Dataset ini dibagi menjadi:
- **80%** Train set  
- **10%** Validation set  
- **10%** Test set  

## 🏗️ Model Arsitektur
Model CNN dibuat menggunakan **Keras Sequential API** dengan arsitektur sebagai berikut:
- **Conv2D + ReLU + MaxPooling**
- **Conv2D + ReLU + MaxPooling**
- **Flatten + Dense Layers**
- **Dropout untuk regularisasi**
- **Softmax Activation (2 kelas: Cat & Dog)**

## 🏋️ Training
- **Optimizer**: Adam  
- **Loss Function**: Categorical Crossentropy  
- **Batch Size**: 32  
- **Epochs**: 30  
- **Callbacks**: EarlyStopping & ReduceLROnPlateau

## 📈 Hasil Evaluasi
| Metrik       | Akurasi |
|-------------|---------|
| Training    | **91.15%** |
| Validation  | **91.44%** |
| Testing     | **92.12%** |

## 🚀 Cara Menjalankan Model
### 1️. Menjalankan Model SavedModel
```bash
tensorflow_model_server --rest_api_port=8501 --model_name=cats_dogs --model_base_path=$(pwd)/saved_model
```
### 2. Menjalankan Model di TFJS
```javascript
const model = await tf.loadLayersModel('tfjs_model/model.json');
```
### 3. Menjalankan Model di TFJS
Gunakan TensorFlow Lite Interpreter untuk menjalankan model di mobile/embedded devices.

## Dependencies
install library dengan versinya:
```bash
pip install -r requirements.txt
