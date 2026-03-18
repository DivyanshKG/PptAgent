# PptAgent: AI-Powered Research Paper Summarizer & Presentation Generator

PptAgent is a Python-based tool that automatically generates a PowerPoint presentation from a given research paper on arXiv. It leverages large language models (LLMs) and a retrieval-augmented generation (RAG) system to summarize the paper and create a well-structured and visually appealing presentation.

## Features

- **arXiv Integration**: Directly downloads the TeX source code of any paper from arXiv using its ID.
- **Content Summarization**: Utilizes LLMs to generate a comprehensive, slide-by-slide summary of the paper, including titles, key points, and paragraphs.
- **Image Extraction**: Automatically extracts images and diagrams from the paper's source files and intelligently places them in the presentation.
- **Vector-Based Retrieval**: Creates a vector database of the paper's content for efficient and relevant information retrieval during the summarization process.
- **Layout Engine**: A simple layout engine determines the best slide layout (e.g., text-only, text with image) for the content.
- **Customizable**: Easily change the paper ID to generate a presentation for any research paper. The presentation's styling (fonts, colors) can also be customized.

## How it Works

1.  **Paper Download**: The tool fetches the TeX source of the specified arXiv paper.
2.  **Vectorization**: The text content is chunked and converted into vector embeddings, which are stored locally.
3.  **Summarization (RAG)**: The agent retrieves relevant sections of the paper from the vector store and uses an LLM to generate a structured summary, formatted for presentation slides.
4.  **Image Processing**: It identifies and converts images from the source files (including PDFs and EPS) into a usable format.
5.  **Presentation Generation**: A second LLM call maps the summary and images into a final JSON structure. The `python-pptx` library then uses this data to build the final PowerPoint file (`final.pptx`), complete with titles, content, images, and footers.

## Getting Started

### Prerequisites

- Python 3.x
- An OpenAI API key (or an API key for a compatible service like OpenRouter).
- The notebook is set up to use a free model from OpenRouter, but you can change it to any OpenAI compatible model.

### Installation

1.  Clone the repository:
    ```bash
    git clone https://github.com/DivyanshKG/PptAgent.git
    cd PptAgent
    ```

2.  Install the required Python packages:
    ```bash
    pip install -r requirements.txt
    ```

3.  Create a `.env` file in the root directory and add your API key:
    ```
    KEY="YOUR_API_KEY"
    ```

### Usage

1.  Open the `a1.ipynb` notebook in a Jupyter environment.
2.  Set the `PAPER_ID` variable to the arXiv ID of the paper you want to present (e.g., `"2402.17764"`).
3.  Run all the cells in the notebook.
4.  The generated presentation will be saved as `final.pptx` in the root directory.

## Customization

-   **Paper**: Change the `PAPER_ID` in the first cell.
-   **Models**: You can change the LLMs used for summarization and presentation generation by editing the `model` parameter in the `client.chat.completions.create` calls.
-   **Styling**: Modify the font and color constants at the beginning of the notebook to change the presentation's appearance.
