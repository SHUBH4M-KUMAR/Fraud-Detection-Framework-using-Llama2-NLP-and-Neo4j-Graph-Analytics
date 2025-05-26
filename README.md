
# 🕵️‍♂️ FraudSightNL – Financial Fraud Detection using Llama2 and Neo4j

This project is a hybrid AI-based fraud detection system that combines **Llama2** for contextual natural language understanding with **Neo4j** for analyzing entity relationships in financial transactions. A user can describe suspicious behavior in natural English, and the system will generate Cypher queries, search the graph database, and visualize the transaction network.

---

## 🔍 Features

- 🤖 Llama2-based NLP model translates natural language queries into Cypher queries.
- 🌐 Neo4j graph database represents and queries relationships between accounts, transactions, and behaviors.
- 🔎 Detects fraud patterns in `TRANSFER`, `CASH_OUT`, `CASH_IN`, and `PAYMENT` types.
- 📊 Streamlit app for live interaction, visualization, and fraud report generation.
- 🌈 Interactive PyVis network graph highlighting suspicious nodes in red.

---

## 🛠️ Tech Stack

- **Llama2 (via HuggingFace T5 model)** – Natural Language to Cypher generation
- **Neo4j** – Graph database for storing and querying transactions
- **Streamlit** – Frontend UI for user input and results
- **PyVis** – Visualization of transaction graphs
- **Python Libraries**: `torch`, `transformers`, `neo4j`, `streamlit`, `re`, `pyvis`

---

## 🗃️ Dataset Import (Neo4j Cypher)

```cypher
LOAD CSV WITH HEADERS FROM 'file:///yourfile.csv' AS row
CREATE (t:Transaction {
  step: toInteger(row.step),
  type: row.type,
  amount: toFloat(row.amount),
  nameOrig: row.nameOrig,
  oldbalanceOrg: toFloat(row.oldbalanceOrg),
  newbalanceOrig: toFloat(row.newbalanceOrig),
  nameDest: row.nameDest,
  oldbalanceDest: toFloat(row.oldbalanceDest),
  newbalanceDest: toFloat(row.newbalanceDest),
  isFraud: toInteger(row.isFraud),
  isFlaggedFraud: toInteger(row.isFlaggedFraud)
})
```

---

## 🚀 How to Run

### 1. Clone the Repository & Set Up Environment
```bash
git clone https://github.com/yourusername/fraudsightnl
cd fraudsightnl
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

### 2. Load Data into Neo4j
Place your CSV file in Neo4j's import directory and run the Cypher query above.

### 3. Configure Llama2 Model
Edit paths in your script to point to the correct:
```python
saved_model_path = "path/to/your/t5-model"
saved_tokenizer_path = "path/to/your/t5-tokenizer"
```

### 4. Run the Streamlit App
```bash
streamlit run app.py
```

---

## 🧠 Example Natural Queries

- _"Check whether the transfer of $1200 from account C12345 might be fraudulent."_
- _"Please check whether the cash_out of $351843.08 from account C1394122484 might be fraudulent. It started with a balance of $351843.08 and ended with $0.0."_


---

## 📬 Contact
 
📫 Email: shubhambpn1234@gmail.com
