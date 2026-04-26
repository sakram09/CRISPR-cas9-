# CRISPR-cas9-

PROJECT DOCUMENTATION: AI-DRIVEN CRISPR OFF-TARGET PREDICTION (PATHOGEN FOCUS)
================================================================================

1. PROJECT OVERVIEW
--------------------------------------------------------------------------------
Title: Deep-CRISPR-Pathogen: ML-Driven Off-Target Assessment for Viral Genomes
Objective: To develop a machine learning pipeline that identifies potential 
off-target binding sites for CRISPR-Cas9 within viral pathogens, ensuring 
high specificity and host safety.

2. PROBLEM STATEMENT
--------------------------------------------------------------------------------
In CRISPR-Cas9 gene editing, unintended "off-target" cuts can lead to 
unpredictable mutations. While most research focuses on human genome safety, 
using CRISPR as a "molecular antibiotic" against viruses (like HSV-1) 
requires ensuring that the guide RNA (gRNA) hits the virus effectively without 
cross-reacting with the human host.

3. WORKFLOW & METHODOLOGY (What we did)
--------------------------------------------------------------------------------
Step 1: Data Acquisition
- Integrated Biopython to fetch real genomic data from NCBI.
- Target Pathogen: Herpes Simplex Virus 1 (HSV-1), Accession: NC_001806.

Step 2: Biological Feature Engineering
- Sequence Encoding: Converted DNA strings into numerical data.
- Hamming Distance: Calculated total mismatch counts between gRNA and DNA.
- Biological Risk Scoring: Implemented a weighted scoring system based on 
  the "Seed Region" (the 8-12 bases near the PAM site). Mismatches here are 
  weighted higher as they more significantly disrupt Cas9 binding.
- GC-Content: Calculated GC percentage as a proxy for thermodynamic binding stability.

Step 3: Machine Learning Implementation
- Algorithm: Random Forest Classifier.
- Training: Used a synthetic dataset modeled after GUIDE-seq results to teach 
  the model the relationship between mismatch position and binding probability.
- Evaluation: Achieved high accuracy in classifying "Safe" vs "High-Risk" sites.

Step 4: Pathogen-Host Safety Scan
- Performed a "Sliding Window" scan of the HSV-1 genome.
- Visualized results in a "CRISPR Safety Map" (Genome-wide risk distribution).
- Cross-Reactivity Filter: Compared viral hits against simulated human 
  sequences to ensure no overlap exists.

4. KEY OUTPUTS (What the project provides)
--------------------------------------------------------------------------------
- Safety Map Graph: A visual hotspot map showing risky regions in the pathogen.
- Predictive Model: A trained Random Forest that goes beyond simple 
  mismatch counting.
- Specificity Report: Quantitative proof that a gRNA is "Pathogen-Specific."

5. RESEARCH ALIGNMENT (Dr. Blake's Lab Interests)
--------------------------------------------------------------------------------
- Antimicrobial/Antiviral CRISPR: Moves beyond human genetics into 
  pathogen-host interactions.
- Computational Biology: Demonstrates the ability to use Python/AI to 
  solve molecular biology bottlenecks.
- Clinical Safety: Prioritizes host-safety metrics crucial for PhD research.

6. FUTURE IMPROVEMENTS (For Research Extension)
--------------------------------------------------------------------------------
- Thermodynamic Integration: Using RNAfold or ViennaRNA libraries to calculate 
  actual Gibbs Free Energy (ΔG) for binding.
- Multi-Genome Scanning: Scaling the pipeline to scan the entire 
  human genome (GRCh38) in real-time for each gRNA.
- Explainable AI (XAI): Implementing SHAP or LIME to visualize exactly 
  which nucleotide positions are driving the "Off-Target" prediction.
- Deep Learning Upgrade: Moving from Random Forest to a Siamese CNN 
  (Convolutional Neural Network) for direct sequence-to-sequence comparison.
- Web Deployment: Hosting the tool via Streamlit for public lab use.

================================================================================
Developed by: Saira Akram Mughal
Master of Science in Biotechnology
================================================================
