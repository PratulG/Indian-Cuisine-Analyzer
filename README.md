# Indian Cuisine Recipe Assistant and Flavor Profile Analyzer

This project is a comprehensive tool designed to explore the rich diversity of Indian cuisine. It leverages the OpenAI API and LangChain to provide insights into recipes, ingredient substitutions, and flavor profiles.

## Features

- **Recipe Discovery:** Access a wide array of Indian recipes.
- **Ingredient Substitutions:** Get suggestions for substituting ingredients to adapt recipes to your needs.
- **Flavor Analysis:** Understand the complex flavor profiles of Indian dishes.

## Technical Overview

The application integrates several data loaders within LangChain to manage and query diverse data types including CSV files, PDFs, web content, and YouTube transcripts. These loaders are combined into a unified index, allowing for efficient querying. The OpenAI API interacts with this index to deliver specific responses based on user queries.

## Getting Started

### Prerequisites

- Python 3.8 or later
- pip
- Access to the OpenAI API

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourgithub/indian-cuisine-assistant.git
   ```
2. Navigate to the project directory:
   ```bash
   cd indian-cuisine-assistant
   ```
3. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

### Usage

Run the main script to start the application:
```bash
python app.py
```

Enter your queries about Indian cuisine when prompted, and the system will respond with relevant information.

## Code Snippet

Here's a snippet showing how data loaders are setup and combined:

```python
from langchain.document_loaders import CSVLoader, WebContentLoader, PDFLoader, TXTLoader

# Setup data loaders
csv_loader = CSVLoader(file_path='path/to/IndianFoodDatasetCSV.csv')
web_loader = WebContentLoader(urls=["https://example.com"])
pdf_loader = PDFLoader(file_paths=['path/to/recipe-book.pdf'])
txt_loader = TXTLoader(file_paths=['path/combined_transcripts.txt'])

# Combine loaders and create index
all_loaders = [csv_loader, web_loader, pdf_loader, txt_loader]
index = VectorstoreIndexCreator().from_loaders(all_loaders)

# Query the index
query_and_display("What are the main ingredients in Chicken Tikka Masala?", index, OpenAI)
```
