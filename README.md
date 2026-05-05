#  Semantic Patient-to-Trial Matching Engine

An AI-powered system that matches patient profiles to relevant clinical trials using **semantic understanding of medical language**, combining transformer embeddings with rule-based clinical eligibility logic.

---

##  The Problem

Clinical trial matching is still largely:

* Manual and time-consuming
* Based on keyword search and rigid filters
* Unable to capture **semantic meaning in medical language**
* Prone to missing relevant trials due to terminology mismatch

Example:
A patient with **“NSCLC”** may not match a trial mentioning **“non-small cell lung cancer”** using traditional systems.

---

##  The Solution

This system introduces **semantic search for healthcare**:

 Understands *meaning*, not just keywords
 Matches patients to trials using **AI embeddings**
 Applies **clinical eligibility rules** for accuracy
 Produces a **ranked list of trials by eligibility score**

---

##  What It Does

*  Converts patient profiles & trial criteria into **dense vector embeddings**
*  Performs **semantic similarity search** using FAISS
*  Applies **hard clinical eligibility filters** (age, ECOG, etc.)
*  Combines semantic + rule-based signals into a **composite score**
*  Ranks clinical trials by **true eligibility likelihood**

---

##  Core Concepts & Technologies

###  Semantic Search

Moves beyond keyword matching → understands meaning
(NSCLC ≈ non-small cell lung cancer)

---

###  Dense Vector Embeddings

* Text → numerical vectors
* Similar meaning → similar vectors in space
* Enables AI-based similarity comparison

---

###  BioBERT

* BERT model trained on biomedical data (PubMed, clinical notes)
* Understands:

  * medical terminology
  * drug names
  * disease relationships

---

###  BERT Architecture

* Bidirectional context understanding
* Reads text both left-to-right and right-to-left
* Captures deeper meaning of clinical text

---

### 🧾 Sentence Transformers

* Converts full sentences into fixed-size vectors
* Enables comparison between:

  * patient profiles
  * trial eligibility criteria

---

###  FAISS (Similarity Search)

* High-speed nearest-neighbour search
* Matches patient → trials in milliseconds
* Scales to large datasets

---

###  Cosine Similarity

* Measures similarity between embeddings
* Range: 0 → 1
* Higher value = more semantic similarity

---

###  IndexFlatIP

* FAISS exact search index
* Uses inner product = cosine similarity (with normalized embeddings)
* Accurate and reliable for small–medium datasets

---

##  Clinical Logic Layer

###  Hard Eligibility (Strict Rules)

* Age limits
* ECOG performance status
* Pregnancy status
* Mandatory inclusion/exclusion criteria

 Violations result in penalties or disqualification

---

###  Soft Eligibility (Semantic Matching)

* How well patient matches trial intent
* Based on embedding similarity

---

###  Biomarker Matching

* EGFR, BRCA, PD-L1, etc.
* Represented as structured features
* Matched against trial criteria

---

##  Composite Scoring

Final ranking score:

```text id="2c7p4m"
Score = Semantic Similarity
        − (Hard Fail Count × 25)
        − (Warning Count × 10)
```

* Combines neural and rule-based signals
* Ensures **clinical correctness + semantic relevance**

---

##  Techniques Used

| Technique                  | Purpose                                    |
| -------------------------- | ------------------------------------------ |
| Text-to-Embedding Pipeline | Convert clinical text to vectors           |
| Normalized Embeddings      | Enable cosine similarity via inner product |
| FAISS IndexFlatIP          | Fast exact similarity search               |
| Hybrid Matching            | Combine semantic + rule-based filtering    |
| Composite Scoring          | Merge neural + rule signals                |
| Batch Embedding            | Efficient encoding of multiple inputs      |

---


##  Use Cases

* Clinical trial recruitment platforms
* Healthcare AI systems
* Pharma research tools
* Patient eligibility screening
* Precision medicine applications

---

##  Key Impact

This system enables:

* Faster clinical trial matching
* Improved patient-trial alignment
* Reduced manual screening effort
* Better utilization of clinical trials
* AI-driven healthcare decision support

---

##  Example Output

```json id="x2p6z9"
{
  "patient_id": "P123",
  "matched_trials": [
    {
      "trial_id": "T456",
      "score": 82.5,
      "eligibility": "High",
      "notes": "Strong semantic match, meets all clinical criteria"
    }
  ]
}
```

---

## Author

**Danish Zulfiqar**
Machine Learning | AI Systems | Healthcare AI | NLP

---
