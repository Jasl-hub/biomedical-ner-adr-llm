# Biomedical NER and ADR Extraction Using Large Language Models

This project focuses on extracting biomedical named entities such as **Drugs**, **Diseases**, **Symptoms**, and **Adverse Drug Reactions (ADRs)** from unstructured patient forum text using a transformer-based model. The goal is to enable structured analysis of medical text by mapping extracted ADRs to standard **SNOMED CT** codes.

---

## 📌 Objectives

- Perform **Named Entity Recognition (NER)** on patient-reported medical forum posts.
- Label text using the **BIO (Beginning, Inside, Outside)** tagging format.
- Normalize extracted **ADR** mentions using **SNOMED CT** medical codes.
- Convert model output to `.ann` format for compatibility with existing annotation pipelines.
- Evaluate the pipeline's performance using both string-based and embedding-based matching techniques.

---

## 🧠 Dataset

- **Dataset Used:** [CADEC.v2 Dataset (CSIRO)](https://data.csiro.au/collection/csiro:10948?q=CADEC)  
  A curated dataset of patient forum posts mentioning medications and medical conditions.

- **Directory Structure:**
  - `text/` – Raw patient forum posts
  - `original/` – Ground truth annotations in `.ann` format
  - `meddra/` – MedDRA-based ADR labels
  - `sct/` – SNOMED CT mappings for standardization

---

## 🛠️ Technologies Used

- **Programming Language:** Python 3.10+
- **Transformer Model:** [`d4data/biomedical-ner-all`](https://huggingface.co/d4data/biomedical-ner-all)
- **Libraries & Tools:**  
  - Hugging Face Transformers  
  - PyTorch  
  - NumPy, Pandas, JSON  
  - Sentence Transformers (for embeddings)  
  - FuzzyWuzzy (for approximate string matching)

---

## 🚀 Features

- ✅ Extraction of biomedical entities: Drugs, Diseases, Symptoms, ADRs  
- ✅ BIO tagging of clinical text using a pre-trained NER model  
- ✅ ADR normalization using **SNOMED CT** codes  
- ✅ Output annotation format compatible with `.ann` files  
- ✅ Performance evaluation via:
  - Exact string match
  - Fuzzy matching
  - Embedding-based similarity scoring

---

## 📊 Sample Output

```json
{
  "text": "I experienced dizziness and nausea after taking the medication.",
  "entities": [
    {"label": "Symptom", "text": "dizziness"},
    {"label": "ADR", "text": "nausea"}
  ],
  "normalized_ADRs": [
    {
      "text": "nausea",
      "term": "Nausea",
      "code": "422587007"
    }
  ]
}
``` 
## 📁 Project Structure 

<pre><code>
  ├── nlp_assignment.py # Main ADR extraction pipeline script 
  ├── entities_by_file.json # Extracted entities per file 
  ├── normalized_adr_results.json # ADRs normalized to SNOMED codes 
  ├── fuzzy_adr_matches.json # Fuzzy match results for ADRs 
  ├── embedding_adr_matches.json # Embedding-based ADR matches 
  ├── venn.png # Venn diagram: fuzzy vs embedding matches 
  ├── bar.png # Bar chart visualization of match results 
  ├── pie.png # Pie chart of match types 
  ├── README.md # Project documentation (this file) 
  </code></pre>


---

## 📈 Evaluation

Model performance was evaluated using:

- Ground truth annotations from `original/` and `meddra/`
- Entity-level comparison across:
  - ✅ Exact String Match
  - ✅ Fuzzy String Matching (via FuzzyWuzzy)
  - ✅ Embedding Similarity (via Sentence Transformers)

---

## 📊 Visualizations

- `venn.png`: Overlap between fuzzy and embedding-based matches  
- `bar.png`: Distribution of ADR match types  
- `pie.png`: Proportion of exact, fuzzy, and embedding-based matches  

---

## 💡 Future Improvements

- Fine-tune biomedical LLMs like **BioGPT** or **SciBERT** for improved tagging accuracy    
- Integrate with annotation tools (e.g., brat, doccano) for real-time labeling
- Deploy the pipeline as a REST API using FastAPI or Flask for integration with healthcare systems
- Build a Streamlit dashboard or Gradio UI for interactive exploration and verification of extracted ADRs

---

## 🙋‍♀️ Author

**Jasleen Kaur**  
M.Tech (ESC), NIT Rourkela  
[LinkedIn](https://www.linkedin.com/in/jas03leen/) | [GitHub](https://github.com/Jasl-hub)

---

## 📜 License

This project is intended for **educational and research purposes only**.  
All rights to the CADEC dataset belong to **CSIRO, Australia**.

---

## 📬 Contact

For questions, suggestions, or collaboration inquiries, feel free to open an issue or reach out on [LinkedIn](https://www.linkedin.com/in/jas03leen/).

