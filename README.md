# Hybrid Anime Recommendation System

A full-stack web application that provides personalized anime recommendations. This project uses a content-based filtering model built in a **Jupyter Notebook**, served via a **Python Flask API**, and presented through a clean, interactive **HTML/JavaScript** front-end.

This project demonstrates an end-to-end machine learning application, starting from data exploration and model development in a Jupyter Notebook to deploying the model as a live service. The core of the system is a content-based recommendation engine that analyzes anime genres and synopses to find shows with similar content. Using **TF-IDF vectorization** and **cosine similarity**, the model calculates a similarity score between anime, allowing it to suggest relevant titles based on a user's input.

The backend is built with **Flask**, providing a lightweight API to serve the model's predictions. The front-end is a responsive, single-page application built with **HTML** and styled with **Tailwind CSS**, offering a user-friendly interface for discovering new anime. This architecture creates a robust and scalable system, separating the machine learning logic from the user presentation layer, which is a common practice in production environments.

# Table of Contents

- [Features](#features)

- [Project Structure](#project-structure)

- [Tech Stack](#tech-stack)

- [Setup and Installation](#setup-and-installation)

- [How It Works](#how-it-works)

- [Snapshots](#snapshots)

- [Data Source](#data-source)

# Features

**Content-Based Recommendations**: Enter an anime you like and get a list of the top 10 most similar anime.

**Interactive Web UI**: A simple and modern user interface for easy interaction.

**Dynamic Search**: Autocomplete suggestions help you find anime titles quickly.

**Decoupled Architecture**: A Flask backend serves the model, making the system scalable and maintainable.

# Project Structure

Here is an overview of the project's file structure:

    .
    ├── 📄 anime-dataset-2023.csv
    ├── 📄 users-details-2023.csv
    ├── 📓 Anime-Recommendation-System.ipynb
    ├── 🐍 app.py
    ├── 📄 anime_cleaned.csv
    ├── 📄 cosine_sim.npy
    ├── 📄 index.html
    ├── 📄 instructions.md
    └── 📄 README.md

`Anime-Recommendation-System.ipynb`: The original Jupyter Notebook containing all the data cleaning, analysis, and model building steps (TF-IDF and Cosine Similarity).

`app.py`: The Flask API backend. It loads the pre-computed similarity matrix and provides recommendation endpoints.

`index.html`: The single-page front-end application that users interact with.

`anime_cleaned.csv` & `cosine_sim.npy`: The processed data and similarity matrix exported from the notebook, which are used by the Flask app.

`*.csv`: The raw datasets used for analysis.

`README.md`: Project documentation.

# Tech Stack

- **Backend**: Python, Flask, Pandas, NumPy, Scikit-learn

- **Frontend**: HTML, Tailwind CSS, JavaScript

- **Data Analysis**: Jupyter Notebook

# Setup and Installation

Follow these steps to get the project running on your local machine.

### 1. Prerequisites

- Python 3.8+

- pip (Python package installer)

### 2. Clone the Repository

    git clone https://github.com/YashovardhanGupta/Anime-Recommendation-System.git
    cd hybrid-anime-recommendation-system

### 3. Set Up Python Environment & Install Dependencies

It's recommended to use a virtual environment.

    # Create a virtual environment
    python -m venv venv

    # Activate it
    # On Windows
    venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate

    # Install the required packages
    pip install Flask flask-cors numpy pandas scikit-learn

### 4. Generate the Model Files

You need to run the Jupyter Notebook (`Anime-Recommendation-System.ipynb`) one time to generate the necessary files for the API.

- Open the notebook.

- Ensure the input data files (`anime-dataset-2023.csv`) are in the correct path.

- Run all the cells in the notebook. This will execute the data processing and model creation, and a final cell should save two files:

    - `anime_cleaned.csv`

    - `cosine_sim.npy`

### 5. Run the Backend Server

Once the files from the previous step are generated, you can start the Flask server.

    python app.py

The server will start running on `http://127.0.0.1:5000`.

### 6. Launch the Front-End

Simply open the `index.html` file in your web browser. The application will automatically connect to your running local server to fetch anime titles and recommendations.

# How It Works

1. **Backend**: The Flask server (app.py) loads the anime_cleaned.csv dataset and the pre-computed cosine_sim.npy similarity matrix into memory. It exposes two main API endpoints:

    - `/anime-list`: Provides a full list of anime names for the search bar's autocomplete.

    - `/recommend`: Takes an anime title as a query parameter, finds its index, retrieves its similarity scores against all other anime, and returns the top 10 matches.

2. **Frontend**: When the `index.html` page loads, it calls the `/anime-list` endpoint to populate the search options. When a user searches for an anime, a `fetch` request is sent to the `/recommend` endpoint. The returned JSON data is then dynamically rendered as recommendation cards on the page.

# Snapshots
Landing Page: 

![Landing Page](https://github.com/YashovardhanGupta/Anime-Recommendation-System/blob/main/snapshots/Landing_Page.png?raw=true)

Drop Down Suggestions:

![Drop Down Suggestions](https://github.com/YashovardhanGupta/Anime-Recommendation-System/blob/main/snapshots/Drop_Down_Suggestions.png?raw=true)

Recommendations:

![Recommendations](https://github.com/YashovardhanGupta/Anime-Recommendation-System/blob/main/snapshots/Recommendations.png?raw=true)

# Data Source

The dataset used for this project is the **Anime Dataset 2023** from [Kaggle](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset/data), which contains information on thousands of anime and user details.
