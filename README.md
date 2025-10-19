# 🤖 Guard Bot - AI-Powered Insurance Recommendation System  

##  Overview  
Guard Bot is an intelligent recommendation system that helps users find the most suitable insurance policies based on their profile and requirements. The system supports multiple insurance types across different countries, leveraging machine learning and natural language processing to provide personalized recommendations with clear explanation. 
It uses a hybrid approach (ML + rule-based) so it stays smart, simple, and works on any kind of data.
And it’s not just a bot — it’s an intelligent, responsible and self-explanatory assistant that makes insurance easy to understand.

---
## 🔗 Final Project Deployed Link 

http://13.200.250.84/

## 🎥 Final Project Demo Video  

https://raw.githubusercontent.com/ARYABARAI30123/xAI/main/mufg-insurance-frontend/public/videos/demo.mp4

## 📄Final Project PPT

https://www.canva.com/design/DAGwnYX-Tq8/dV4hMY3JoScgAp563h85KA/edit?utm_content=DAGwnYX-Tq8&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton

##  Features <a name="features"></a>  

### Multi-Country Support  
- **India & Australia Coverage**  
- Region-specific policy recommendations  
- Currency and regulation compliance  

### Insurance Types  
- 🏥 Health Insurance  
- 💖 Life Insurance  
- ✈️ Travel Insurance  
- 🏠 House Insurance  
- 🚗 Vehicle Insurance  

### AI-Powered Features  
- **Smart Recommendations**: ML models trained on extensive insurance data  
- **Natural Language Processing**: Advanced chat interface using LangChain  
- **Real-time Premium Calculation**: Instant cost estimates  
- **Policy Explanation**: AI-generated simple explanations of complex terms  
- **Graph RAG Integration**:  
  - Retrieves knowledge from **40 PDFs** and **2 CSVs (10,000×25 rows each)**  
  - Data divided between India & Australia, aligned with **IRDAI & APRA regulations**  
  - Finds **relationships between user profiles, policies, and regulations**  
  - Ensures contextual and regulation-compliant recommendations  

---

##  Technology Stack <a name="technology-stack"></a>  

### Backend (FastAPI)  
- **Python + FastAPI**: High-performance API backend  
- **scikit-learn**: ML model training and inference  
- **LangChain**: Natural language processing and explanations  
- **ChromaDB**: Vector storage for RAG capabilities  
- **Neo4j**: Knowledge Graph for Graph RAG queries  
- **Pydantic**: Data validation and settings management  

### Frontend (React)  
- **React**: Modern UI framework  
- **Material-UI**: Component library  
- **React Router**: Navigation and routing  
- **Axios**: API integration  

---

##  Architecture <a name="architecture"></a>  

<img width="794" height="980" alt="diagram-export-8-22-2025-12_37_47-PM" src="https://raw.githubusercontent.com/ARYABARAI30123/xAI/main/mufg-insurance-frontend/public/images/architecture.png" />

## Dataset
https://drive.google.com/drive/folders/1-j18M_fTbyKM5-6jziycuqmet79JUO-E?usp=sharing - – dive into the raw data!

* **Synthetic Data** generated using **current trends + IRDAI (India) & APRA (Australia) regulations**
* **40 PDFs** → Insurance regulatory documents, clauses, and market reports
* **2 CSVs** → \~**10,000×25 rows each**, split between India & Australia
* Used for **model training, Graph RAG retrieval, and PowerBI dashboards**

**Data Processing Pipeline**:
![Data Processing Pipeline](https://raw.githubusercontent.com/ARYABARAI30123/xAI/main/mufg-insurance-frontend/public/images/data_pipeline.png)

---

## Scalability

* **Hybrid Architecture** → combines **ML-based predictive modeling** with **rule-based decision checks** for compliance and interpretability
* **Graph RAG with Neo4j** → scales to **millions of relationships**
* **Dockerized Deployment** → scalable across cloud 

---

## Neo4j + Graph RAG

* **Neo4j Graph Database** stores:

  * Policies, premiums, diseases, coverage, add-ons, exclusions, regulations

* **Graph RAG workflow**:

  * CSV/PDF embeddings → stored in ChromaDB
  * Linked into Neo4j graph relationships
  * Queries combine retrieved embeddings + graph reasoning
  * LLM uses this structured context to produce **explainable recommendations**

## Model Explainability

Our system features an interactive explainability demo that helps users understand how the AI makes decisions:

* **Decision Tree Visualization**: Clear representation of the model's decision-making process
* **Feature Importance Analysis**: Shows which factors most influence recommendations
* **Interactive Jupyter Notebook**: Allows users to explore and understand the model's behavior
* **Sample Decision Paths**: Visual examples of how different user inputs lead to specific recommendations

You can find the complete explainability demonstration in the `explainability_demo` folder, which includes:
* Interactive Jupyter notebook with visualizations
* Sample decision tree snippets
* Detailed analysis of feature importance

Here are some visualizations from our explainability analysis:

**SHAP Summary Plot**:
![SHAP Summary](https://raw.githubusercontent.com/ARYABARAI30123/xAI/main/explainability_demo/shap_summary.png)

**SHAP Force Plot**:
![SHAP Force Plot](https://raw.githubusercontent.com/ARYABARAI30123/xAI/main/explainability_demo/shap_force.png)

This transparency helps users trust our system's recommendations and understand the reasoning behind each suggestion.

---

## UI Screenshots

### Landing Page

![Landing Page](https://raw.githubusercontent.com/ARYABARAI30123/xAI/main/mufg-insurance-frontend/public/images/landing.png)


### Country Selection

![Country Selection](https://raw.githubusercontent.com/ARYABARAI30123/xAI/main/mufg-insurance-frontend/public/images/country.png)


### Insurance Type Selection

![Insurance Type Selection](https://raw.githubusercontent.com/ARYABARAI30123/xAI/main/mufg-insurance-frontend/public/images/insurance_type.png)


### Recommendations Page

![Recommendations Page](https://raw.githubusercontent.com/ARYABARAI30123/xAI/main/mufg-insurance-frontend/public/images/recommendations.png)


---

## Setup and Installation <a name="setup-and-installation"></a>

### Prerequisites

* Docker and Docker Compose
* Git

### Quick Start

Clone the repository:

```bash
git clone <https://github.com/DrishttiNarwal/MUFG-Hackathon>

```

Start with Docker Compose:

```bash
docker-compose up --build
```

---

### Manual Setup (Development)

#### Backend Setup

```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
.\\venv\\Scripts\\activate  # Windows
pip install -r requirements.txt
uvicorn app:app --reload --port 8000
```

#### Frontend Setup

```bash
cd mufg-insurance-frontend
npm install
npm start
```

---

Access the application:

* Frontend: [http://localhost:80](http://localhost:80)
* Backend API: [http://localhost:8000](http://localhost:8000)
* API Docs: [http://localhost:8000/docs](http://localhost:8000/docs)

## Usage Guide <a name="usage-guide"></a>

1. **Select Country**: Choose between India and Australia
2. **Choose Insurance Type**: Select from Health, Life, Travel, House, or Vehicle insurance
3. **Fill Details**: Provide required information
4. **Get Recommendations**: Receive AI-powered insurance suggestions


---

## API Documentation

### POST /recommend

Get insurance policy recommendations with explanations

**Request Body:**

```json
{
    "country": "india|australia",
    "policy": "health|life|travel|house|vehicle",
    "data": {
        // User profile and requirements data
    }
}
```

**Response:**

```json
{
    "country": "string",
    "policy": "string",
    "recommendation": { },
    "explanations": { }
}
```

---

## Project Structure

```
├── app.py                 # FastAPI application
├── requirements.txt       # Python dependencies
├── artifacts/             # ML model artifacts
│   ├── india_*/           # India models
│   └── australia_*/       # Australia models
├── scripts/
│   ├── api/               # API utilities
│   ├── llm/               # LLM integration
│   ├── preprocessing/     # Data preprocessing
│   ├── rag/               # RAG implementation
│   └── recommendation/    # ML prediction logic
├── mufg-insurance-frontend/
│   ├── src/               # React source code
│   └── public/            # Static assets
└── vectorstore/           # ChromaDB storage
```

---

## Hackathon Use Cases

* **Personalized Policy Recommendations**: ML + Graph RAG based
* **Explainable AI**: Transparent decision-making
* **Regulation-Aware Analytics**: IRDAI & APRA compliance
* **Dataset Visualization**: PowerBI dashboards for business teams
* **Responsible AI**: Considered Responsible AI features to mitigate bias
---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<p align="center">  
  Made with ❤️ by Team Insurance Bot  
</p>  
```

