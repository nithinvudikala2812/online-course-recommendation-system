# Online Course Recommendation System

This project implements an online course recommendation system using various machine learning approaches, including popularity-based, content-based, collaborative filtering (User-User KNN, Item-Item KNN, SVD, NCF), and a hybrid model. The goal is to enhance user experience by suggesting relevant courses based on their past interactions and course characteristics. The system is deployed as an interactive web application using Streamlit.

## Key Features

*   **Data Exploration (EDA):** Comprehensive analysis of course and user interaction data to understand underlying patterns and distributions.
*   **Data Preprocessing:** Handling missing values and outliers (through capping) to ensure data quality and model robustness.
*   **Popularity-Based Recommendations:** Suggesting top-rated and most enrolled courses as a baseline.
*   **Content-Based Recommendations:** Recommending courses similar to a user's preferences based on intrinsic course attributes (e.g., course name, instructor, difficulty level, course duration).
*   **Collaborative Filtering:**
    *   **User-User KNN:** Recommending courses based on the similarity between users.
    *   **Item-Item KNN:** Recommending courses based on the similarity between courses.
    *   **Singular Value Decomposition (SVD):** A matrix factorization technique used to discover latent features that represent user preferences and course characteristics.
    *   **Neural Collaborative Filtering (NCF):** A deep learning approach that leverages neural networks to model complex user-item interactions.
*   **Hybrid Recommendation System:** Combining the strengths of collaborative filtering, content-based, and popularity-based approaches to generate more robust and accurate recommendations.
*   **Model Evaluation:** Rigorous assessment of model performance using Root Mean Squared Error (RMSE) and Mean Absolute Error (MAE) metrics.
*   **Interactive Web Application:** A user-friendly interface built with Streamlit for real-time course recommendations.

## Model Evaluation Summary

The performance of various recommendation models was evaluated using Root Mean Squared Error (RMSE) and Mean Absolute Error (MAE). The results are summarized below:

| Model         | RMSE      | MAE       |
| :------------ | :-------- | :-------- |
| User-User KNN | 13.980    | 11.430    |
| Item-Item KNN | **13.940** | **11.304** |
| SVD           | 24.382    | 20.357    |
| Hybrid        | 14.327    | 11.772    |
| NCF           | 16.389    | 13.286    |

**Conclusion:**

Based on both RMSE and MAE metrics, the **Item-Item KNN** model emerged as the best-performing algorithm, demonstrating the lowest error rates (RMSE: 13.940, MAE: 11.304). This indicates that Item-Item KNN provides the most accurate predictions of user interaction (time spent on courses) for this dataset. While the Hybrid model showed competitive results, the Item-Item KNN offers a simpler yet highly effective solution. The SVD and NCF models did not perform as well in this evaluation. Therefore, the **Item-Item KNN model** is selected as the core recommendation engine for the Streamlit application due to its superior accuracy and efficiency.

## Deployment

The recommendation system is deployed as an interactive web application using Streamlit, providing a user-friendly interface to explore recommendations.

### Local Execution

To run the Streamlit application locally:

1.  **Ensure all dependencies are installed** (see Installation section).
2.  Navigate to the project directory in your terminal.
3.  Run the command:
    ```bash
    streamlit run streamlit_app.py
    ```
    This will open the application in your default web browser at `http://localhost:8501`.

### Public Access (Temporary using ngrok)

For temporary public access, `ngrok` can be used to tunnel your local Streamlit application:

1.  **Install ngrok:** If you haven't already, install `pyngrok` via pip:
    ```bash
    pip install pyngrok
    ```
2.  **Get an ngrok Authtoken:** Sign up at [ngrok.com](https://ngrok.com) and obtain your authtoken from your dashboard.
3.  **Set Authtoken:** Replace `"YOUR_AUTH_TOKEN"` in the relevant Python script (e.g., in a Colab cell or a separate deployment script) with your actual token.
4.  **Run ngrok:** Execute the Python code to start the ngrok tunnel (as demonstrated in the notebook):
    ```python
    from pyngrok import ngrok
    ngrok.set_auth_token("YOUR_AUTH_TOKEN") # Replace with your actual token
    tunnel = ngrok.connect(8501)
    print(f"Ngrok tunnel established at: {tunnel.public_url}")
    ```
    This will provide a public URL that can be shared, allowing anyone with the link to access your Streamlit application for the duration the tunnel is active.

## Installation

To set up the project locally, follow these steps:

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/online-course-recommendation.git
    cd online-course-recommendation
    ```

2.  **Create a Virtual Environment (Recommended):**
    ```bash
    python -m venv venv
    ```

3.  **Activate the Virtual Environment:**
    *   **On Windows:**
        ```bash
        .\venv\Scripts\activate
        ```
    *   **On macOS/Linux:**
        ```bash
        source venv/bin/activate
        ```

4.  **Install Dependencies:**
    Install all required Python packages using the provided `requirements.txt` file:
    ```bash
    pip install -r requirements.txt
    ```

5.  **Download Data and Model Artifacts:**
    Ensure the `online_course_recommendation.xlsx` dataset and all model artifact files (`.npy`, `.pkl` files) are present in your project directory. These files include:
    *   `online_course_recommendation.xlsx` (original dataset)
    *   `item_similarity.npy`
    *   `user_to_idx.pkl`
    *   `course_to_idx.pkl`
    *   `idx_to_course_id.pkl`
    *   `content_df.pkl`
    *   `aggregated_interaction_df.pkl`

## Usage

Once the Streamlit application is running (either locally or via ngrok):

1.  **Access the Application:** Open the provided local URL (`http://localhost:8501`) or ngrok public URL in your web browser.
2.  **Select User ID:** Use the dropdown menu to select a `user_id`. The application will then display courses already taken by this user.
3.  **Choose Number of Recommendations:** Adjust the slider to specify how many top recommendations you wish to see.
4.  **Get Recommendations:** Click the "Get Recommendations" button. The system will then display a list of recommended courses based on the Item-Item KNN model, including course details and the predicted time the user might spend on them.

## Project Structure

The main files and directories in this project are:

*   `online_course_recommendation.xlsx`: The raw dataset containing course and user interaction information.
*   `notebook.ipynb`: The Jupyter/Colab notebook containing all the data analysis, model development, and evaluation steps.
*   `streamlit_app.py`: The Python script for the Streamlit web application.
*   `requirements.txt`: Lists all Python dependencies required for the project.
*   `item_similarity.npy`: Saved NumPy array for the item-item similarity matrix used by the Item-Item KNN model.
*   `user_to_idx.pkl`: Pickle file containing the mapping from original user IDs to internal integer indices.
*   `course_to_idx.pkl`: Pickle file containing the mapping from original course IDs to internal integer indices.
*   `idx_to_course_id.pkl`: Pickle file containing the reverse mapping from internal integer indices to original course IDs.
*   `content_df.pkl`: Pickle file containing the `content_df` DataFrame, which stores unique course details used for content-based aspects and displaying recommendations.
*   `aggregated_interaction_df.pkl`: Pickle file containing the aggregated user-course interaction data, used to identify courses already taken by a user and for model predictions.
