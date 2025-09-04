# Parts-of-Speech-POS-Tagging-System
Implementation of a Parts-of-Speech (POS) Tagging System from scratch using Hidden Markov Models and the Viterbi Algorithm.
# 📝 Parts-of-Speech (POS) Tagging using Hidden Markov Models

This repository contains my implementation of a **Parts-of-Speech Tagging System** from scratch using **Hidden Markov Models (HMM)** and the **Viterbi Algorithm**.  
Given a sentence, the model predicts the most likely **POS tags** for each word.

---

## 🚀 Project Overview

**Parts-of-Speech Tagging** is the process of assigning labels like *noun*, *verb*, *adjective*, etc., to words in a sentence.  
For example:

> **Input Sentence:**  
`The well is dry.`  

> **POS Tags:**  
`DET NOUN VERB ADJ`

This project builds a **statistical POS tagger** from the ground up using:

- Transition probabilities between POS tags.
- Emission probabilities for words given tags.
- The **Viterbi decoding algorithm** to find the most probable sequence of tags.

---

## 🧠 Concepts Implemented

### **1. Hidden Markov Model (HMM)**
- **States** → POS tags (e.g., NOUN, VERB, ADJ)
- **Observations** → Words in the input sentence
- **Transition Matrix (A):**  
  - Probability of transitioning from one tag to another.
- **Emission Matrix (B):**  
  - Probability of a word appearing given a particular tag.

### **2. Viterbi Algorithm**
Used to compute the **most likely sequence of POS tags** for a given sentence based on HMM probabilities.

---

## 📌 Implementation Details

### **1. Build Transition & Emission Matrices**

```python
def create_transition_matrix(tag_counts, transition_counts):
    A = {}
    for prev_tag in tag_counts.keys():
        A[prev_tag] = {}
        for tag in tag_counts.keys():
            A[prev_tag][tag] = transition_counts.get((prev_tag, tag), 0) / tag_counts[prev_tag]
    return A
