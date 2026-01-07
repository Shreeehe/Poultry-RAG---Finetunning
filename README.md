# Poultry Domain LLM Fine-Tuning

This repository contains a complete pipeline for fine-tuning the Microsoft Phi-3 Mini model on domain-specific poultry data. The goal is to create a specialized assistant capable of understanding complex poultry management, nutrition, and health information.

## 🚀 Overview
The project automates the transition from raw, unstructured documents to a specialized fine-tuned model:
1.  **Data Extraction:** Automatically parses PDF, PPTX, and DOCX files from a dedicated "Poultry Data" directory.
2.  **Preprocessing:** Cleans text by removing unnecessary line breaks, page numbers, and formatting artifacts.
3.  **Chunking:** Splits large text files into 500-word segments with overlap to preserve context.
4.  **Fine-Tuning:** Utilizes QLoRA (4-bit quantization) to fine-tune `Phi-3-mini-4k-instruct` for domain adaptation.

## 🛠️ Requirements
The following libraries are required for data processing and training:
- `pymupdf` (for PDF extraction)
- `python-pptx` (for PowerPoint extraction)
- `docx2txt` (for Word extraction)
- `unstructured`
- `transformers`, `peft`, `trl` (for model training)
- `faiss-cpu` & `sentence-transformers`

## 📂 Project Structure
- `Poultry_base_data_finetunning.ipynb`: The main notebook containing extraction, cleaning, and training logic.
- `poultry_text/`: Directory for raw extracted text.
- `poultry_clean/`: Directory for cleaned text files.
- `poultry_chunks/`: Segmented text ready for dataset creation.
- `poultry_cpt_model/`: Final fine-tuned model output.

## 🧠 Model Configuration
The project uses the following training parameters for fine-tuning:
- **Base Model:** `microsoft/phi-3-mini-4k-instruct`
- **Training Method:** PEFT (LoRA)
- **Quantization:** 4-bit (bitsandbytes)
- **LoRA Rank (r):** 16
- **LoRA Alpha:** 32
- **Learning Rate:** 2e-4
- **Epochs:** 2

## 📝 Usage
1.  **Data Setup:** Place your poultry-related documents in a Google Drive folder named `/Poultry Data/`.
2.  **Extraction:** Run the extraction cells to convert documents into text.
3.  **Training:** Execute the SFTTrainer cells to begin the fine-tuning process. The notebook includes Hugging Face login support to save/upload your final model.

## 📊 Dataset Details
The model was trained on a dataset derived from approximately 798 documents, including specialized texts like "Poultry Nutrition and Feeding" and "World of Microbiology".
