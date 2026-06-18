# 🧬 Biomedical Entity Curation & Extraction Explorer

> **⚠️ Project Status: Human-in-the-Loop Verification Ongoing**
> 
> The datasets, pipelines, and mappings presented in this repository are currently undergoing rigorous **Human-in-the-Loop (HITL) validation** by domain experts to ensure the highest degree of accuracy. Once this verification phase is complete, the finalized dataset, methodology, and corresponding findings will be **submitted for peer-reviewed publication**. 

---

## 🔬 Overview

This directory contains the final compiled output and the **Interactive Explorer Application** (`index.html`) for our Antimicrobial Resistance Genes (ARG) Research project. The project focuses on the automated mining, AI-driven extraction, and rigorous curation of biomedical entities from thousands of scientific papers. 

The interactive HTML application allows researchers to locally browse, analyze, and cross-validate the AI-extracted entities against "Golden Standard" curated dictionaries.

## 🚀 Key Features of the Explorer App

Simply open `index.html` in any modern web browser to access the suite. No backend server is required (operates entirely client-side using JavaScript).

* **📊 Analytics Overview:** High-level dashboard showing total indexed papers, curated entity counts, geographical distribution, and downloadable consolidated datasets.
* **📖 Curated Dictionaries:** Browse the standard vocabulary maps (UMLS/PyMedTermino mapped) for Antibiotics/Chemicals, Diseases, Genes, and Pathogens.
* **🔬 Interactive Paper Inspector:** A comprehensive registry of all papers. Clicking on a paper allows you to audit the AI-extracted entities versus the curated entities side-by-side. Includes full-text and abstract readers.
* **🕸️ Mapping Matrix:** Discover and filter complex co-occurrence pathways (Disease → Pathogen → Gene → Antibiotic) found within specific research cohorts.
* **🧬 6-Column Entity Explorer:** Click any unique entity to instantly query the database and pull all associated scientific literature.
* **🗺️ Interactive Pipeline Flowcharts:** Built-in modal featuring zoomable, pan-able Mermaid.js diagrams explaining the complete system architecture.

## ⚙️ The Data Pipeline Workflow

The data presented in this explorer is the result of a complex, multi-stage AI and programmatic pipeline. You can view the interactive flowcharts for these pipelines directly within the Explorer UI.

### 1. Selection & Data Mining
* **Ingestion:** Fetches metadata and PMIDs from CrossRef and PubMed APIs based on initial queries.
* **Filtering:** Applies rule-based and Regex filters to ensure human-relevance (e.g., matching MeSH terms) and geographic scoping.
* **Output:** Generates a structured JSON of target papers to process.

### 2. Data Extraction
* **Chunking:** Handles large full-text documents by intelligently splitting text into chunks with overlaps to preserve context.
* **AI Extraction:** Utilizes Large Language Models (LLMs) to perform tree-based data extraction, parsing out raw mentions of diseases, pathogens, genes, and chemicals into structured JSON.

### 3. Post-Processing & Curation
* **Ensemble Normalization:** Uses an ensemble of models (Nemotron-3-Nano, Gemma-2-9B, Qwen2-7B) to curate raw entity strings.
* **Prompt Engineering:** Applies strict Few-Shot prompting, Chain-of-Thought, and JSON confidence checks to map raw text to preferred UMLS standard terms.
* **Refinement:** Rule-based fallback for complex ARG formatting and duplicate removal.

### 4. Data Compilation
* **Merging:** Standardizes IDs (PMID/PMCID) and performs dual-key left joins to unify paper metadata with the newly curated entity dictionaries.
* **Master Dataset:** Exports the final clean, high-confidence structured assets ready for UI consumption and statistical analysis.

---

## 🛠️ Built With

* **Tailwind CSS:** For modern, responsive UI design.
* **Chart.js:** For interactive analytics visualizations.
* **SheetJS:** For parsing local Excel (`.xlsx`) datasets dynamically in the browser.
* **Mermaid.js & SVG-Pan-Zoom:** For rendering interactive, zoomable pipeline architecture flowcharts.
* **FontAwesome:** For medical and scientific iconography.

## 📬 Contact

For questions regarding the methodology or data access prior to publication, please contact the primary researcher/maintainer.
