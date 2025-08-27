# Auto PPT Generator

A web application that automatically generates a PowerPoint presentation from bulk text, using an LLM to structure the content and applying the style from a user-provided template.

## ✨ Features

- **Paste Text**: Input any large block of text, prose, or markdown.
- **Style from Template**: Upload your own `.pptx` or `.potx` file to be used as a style template.
- **LLM-Powered**: Uses a Large Language Model (with your own API key) to intelligently structure the text into slides.
- **Download**: Get a ready-to-use `.pptx` file that matches your template's look and feel.

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- An LLM API Key (e.g., from OpenAI)

### Installation & Usage

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/auto-ppt-generator.git](https://github.com/23f1002155/auto-ppt-generator.git)
    cd auto-ppt-generator
    ```

2.  **Install the dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the Streamlit app:**
    ```bash
    streamlit run app.py
    ```

4.  Open your web browser and navigate to the local URL provided by Streamlit (usually `http://localhost:8501`).

---

## ⚙️ Technical Overview

This application transforms raw text into a styled PowerPoint presentation by orchestrating a Large Language Model (LLM) and a presentation library.

### Text Parsing and Slide Mapping

The core of the content generation lies in a carefully crafted prompt sent to an LLM. When a user submits their text and optional guidance, the application constructs a detailed prompt instructing the model to act as a presentation expert. It asks the LLM to analyze the text, determine a logical number of slides, and structure the information into a clear hierarchy. The output is strictly formatted as a JSON object containing a list of slides, where each slide has a title and an array of content points. This structured data is then easily parsed by the Python backend.

### Template Style Application


To match the user's desired aesthetic, the app uses the `python-pptx` library to analyze the uploaded `.pptx` or `.potx` template. It doesn't just copy the file; it inspects the template's slide masters to identify available layouts (e.g., 'Title and Content'). When generating the new presentation, each new slide is created directly from one of these master layouts. This ensures that all generated slides automatically inherit the template's predefined fonts, color schemes, and placeholder positioning. This method ensures the final output feels consistent with the user's brand identity without requiring complex style-inference logic.
