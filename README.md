# 🧠 Brain Activity Mapper

A Gradio application that visualizes potential brain activity based on a user's description of a task. It uses Google's Gemini API for advanced keyword extraction and GloVe word embeddings for semantic mapping to brain regions.

![App Screenshot](screenshot.png)
*(Suggestion: Run the app, take a screenshot of it in action, save it as `screenshot.png` in this folder, and it will appear here!)*

---

## ✨ Features

- **Natural Language Input**: Describe any activity, from "reading a book" to "playing the piano from sheet music."
- **AI-Powered Keyword Extraction**: Leverages the Gemini API to intelligently identify the most relevant keywords (actions, objects, concepts, senses).
- **Semantic Brain Mapping**: Uses GloVe word embeddings to calculate the semantic similarity between extracted keywords and the known functions of various brain regions.
- **Interactive SVG Visualization**: Displays a color-coded brain map where the top 3 most activated regions are highlighted. Hovering over a region shows its name.
- **Detailed Analysis**: Provides a ranked list of activated regions, their corresponding lobes, and the calculated similarity score.

## ⚙️ How It Works

The application follows a two-stage process:

1.  **Keyword Extraction**: The user's sentence is sent to the Gemini API with a specific prompt asking it to pull out essential keywords.
2.  **Vector Similarity Mapping**:
    *   The `BrainRegionMapper` class pre-loads a GloVe word embedding model (`glove-wiki-gigaword-100`).
    *   It creates an "average" vector for each brain region based on a predefined list of associated keywords (e.g., the "Visual Area" is represented by the average of the vectors for "see," "light," "color," etc.).
    *   When new keywords arrive from Gemini, their vectors are averaged to create an "input vector."
    *   **Cosine similarity** is calculated between this input vector and each of the pre-calculated brain region vectors.
    *   The regions with the highest similarity scores are considered the most "activated" and are highlighted on the map.

## 🚀 How to Run Locally

### Prerequisites
- Python 3.8+
- Git

### 1. Clone the Repository
Clone this repository to your local machine.

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git
cd YOUR_REPOSITORY_NAME