# Clinical Trial Patient Matching System

## Overview

This system is a clinical trial recommendation tool designed to match patients with trials based on eligibility and relevance. The approach combines strict rule-based filtering with AI-inspired scoring mechanisms to generate ranked recommendations. The project is structured to reflect a solid understanding of clinical criteria handling, patient profiling, and intelligent decision support.

---

## Problem Understanding

Patients often face difficulty identifying appropriate clinical trials, especially when they must meet specific inclusion and exclusion criteria. Age limits, diagnosis specificity, prior treatment history, and geographic location can all affect eligibility. Furthermore, among the eligible trials, there is a need to prioritize those that offer the most suitable match.

This system was built to address that challenge. It ensures that only relevant trials are shown to the patient by first eliminating those that do not satisfy medical criteria. From the remaining options, the system computes and compares trial scores to highlight the best fits.

---

## How the System Works

1. **Patient Input Collection**  
   The system prompts the user to enter their age, diagnosis (can be multiple), current location, and treatment history. Basic validation ensures the data is clean and reasonable before it is processed.

2. **Eligibility Filtering**  
   Each trial defines specific inclusion and exclusion criteria. The system compares the patient profile against these constraints:
   - Age is checked against the allowed range.
   - Diagnosis must match the trial requirement.
   - Trials can exclude patients who have undergone certain treatments.

   Trials failing any of these checks are immediately discarded.

3. **Rule-Based Scoring**  
   Eligible trials are scored using a weighted model:
   - Diagnosis relevance is the most critical (50% weight).
   - Age proximity to the trial’s target range is also considered (30%).
   - Location match contributes moderately (20%) to encourage accessibility.

4. **AI-Inspired Scoring**  
   To simulate machine learning behavior, a cosine similarity score is computed between the patient and trial vectors. This allows for a more nuanced match based on pattern alignment rather than just hard rules. Vectorization includes normalized age, diagnosis match, and location encoding.

5. **Ranking and Output**  
   A composite score is calculated by combining rule-based and similarity scores (60:40 ratio). The output is a ranked list of trials, each annotated with:
   - Total score
   - Rule-based score
   - AI similarity score
   - Matched inclusion criteria

   This structured ranking helps highlight the most suitable options for the patient.

---

## What the Code Demonstrates

- **AI/ML Concepts**: cosine similarity offers an intuitive ML-inspired mechanism for smart matching.
- **Modular Design**: Functions are clearly separated by responsibility—data collection, validation, eligibility checks, scoring, and ranking.
- **Ethical Consideration**: Patient data is processed at runtime, avoiding storage or hardcoding to protect confidentiality.
- **Scalability**: The current mock database can be replaced with CSV, database, or API integration in future iterations.


## Potential Enhancements

- **Dynamic Trial Loading**: Allow importing trial data from external files or APIs.
- **Fuzzy Diagnosis Matching**: Expand condition matching to accommodate similar or related terms.
- **Learning-Based Models**: Use historical data to train predictive models for ranking effectiveness.
- **Interface Integration**: Convert the script into a web interface or connect it to hospital databases via REST APIs.

---

## Conclusion

This project showcases a practical and thoughtful approach to solving a real-world problem using a mix of deterministic logic and AI-inspired techniques. It focuses not just on functionality, but also on fairness, extensibility, and clarity. The current system serves as a solid foundation for building advanced patient-matching platforms in clinical research.
