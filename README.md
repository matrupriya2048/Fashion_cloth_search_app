# Fashion Cloth Search App

This is a simple fashion search application built using **CLIP ViT-B-32** model for text-to-image search. You can search through a dataset of clothing images using natural language queries, and the application will return the most relevant images based on the query. This project leverages several AI tools and libraries such as **Haystack**, **Streamlit**, **Gradio**, **FastAPI**, and more to create an interactive search experience.

## Table of Contents
1. [Features](#features)
2. [Requirements](#requirements)
3. [Setup and Installation](#setup-and-installation)
4. [How It Works](#how-it-works)
5. [Usage](#usage)
6. [File Structure](#file-structure)
7. [Contributing](#contributing)
8. [License](#license)

## Features

- **Text-to-Image Search**: Allows you to search through a dataset of clothing images using natural language queries.
- **Streamlit UI**: Provides an interactive interface where you can input queries and view the results.
- **CLIP Model**: Utilizes the `clip-ViT-B-32` model from Sentence Transformers to match text queries to images.
- **Real-time Results**: Displays the top 3 most relevant images along with similarity scores.

## Requirements

Before you can run the project, make sure to install the following dependencies:

- `farm-haystack`: For managing document stores and running multimodal retrieval.
- `gradio`: An easy-to-use interface to build and demo the app (optional if using Gradio UI).
- `streamlit`: For building the web-based UI.
- `fastapi`: For backend API handling.
- `uvicorn`: For serving the FastAPI app.
- `python-multipart`: Required for handling file uploads in FastAPI.
- `jinja2`: For rendering HTML templates.

## Setup and Installation

Follow these steps to get the project running locally.

### 1. Clone the repository

```bash
git clone https://github.com/matrupriya2048/fashion_cloth_search_app.git
cd fashion-cloth-search-app
```

### 2. Create a virtual environment (optional but recommended)

```bash
python3 -m venv env
source env/bin/activate
```

### 3. Install the required packages

```bash
pip install -r requirements.txt
```

### 4. Add your image dataset

- Create a folder named `new_data` in the project root.
- Add the clothing images you want to search through inside the `new_data` folder.

### 5. Run the application

To run the Streamlit application, use:

```bash
streamlit run app.py
```

To run the FastAPI server with Uvicorn:

```bash
uvicorn main:app --reload
```

## How It Works

### Multimodal Search

This application uses the **CLIP ViT-B-32** model to perform **text-to-image** search by encoding both text queries and images into a shared embedding space. Here’s how the search process works:

1. **Document Store**: The images from the `new_data` folder are loaded and stored in an `InMemoryDocumentStore`.
2. **Embeddings**: The images are converted into embeddings using the CLIP model. These embeddings are stored in the document store for fast retrieval.
3. **Search**: When a user inputs a query, the query is converted into an embedding using the CLIP model. The app then retrieves the most relevant images by comparing the similarity of query embeddings to image embeddings.
4. **Display Results**: The top 3 most relevant images are displayed with their similarity scores.

## Usage

### Search Interface

1. Launch the application.
2. Enter a query (e.g., "red dress", "blue jeans", etc.) into the search bar.
3. Click the **Search** button.
4. The app will return the top 3 images matching the query along with their similarity scores.

### Example Queries

- "Black t-shirt"
- "White sneakers"
- "Denim jeans"

## File Structure

```
fashion-cloth-search-app/
│
├── app.py                    # Streamlit app to handle UI
├── multimodal_search.py       # Core logic for performing text-to-image search
├── new_data/                  # Directory to store your images
├── requirements.txt           # List of project dependencies
├── main.py                    # FastAPI app (if needed)
└── README.md                  # Documentation
```

## Contributing

Feel free to fork this repository, submit issues, or contribute through pull requests. Any suggestions or improvements are welcome!

## License

This project is licensed under the MIT License.

---

### Additional Notes:

- Ensure that your `new_data` folder contains the images in `.jpg`, `.jpeg`, or `.png` formats.
- You can customize the search model by replacing the `clip-ViT-B-32` with other models from the Hugging Face `sentence-transformers` repository.

