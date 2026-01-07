# Online Course Recommendation System

This project builds a hybrid online course recommendation engine using popularity-based, content-based, and collaborative filtering approaches. Multiple ML algorithms were implemented and evaluated, and the best-performing Item–Item KNN model was integrated into a Streamlit web application for interactive real-time recommendations.

## Key Features
- Popularity-Based Recommendations
- Content-Based Filtering using TF-IDF & metadata
- Collaborative Filtering (User–User KNN, Item–Item KNN, SVD, NCF)
- Hybrid Modeling combining multiple approaches
- Streamlit Web App for real-time recommendations
- Model evaluation using RMSE & MAE

## Model Performance
| Model           | RMSE   | MAE   |
|----------------|--------|-------|
| User–User KNN  | 13.98  | 11.43 |
| Item–Item KNN  | **13.94** | **11.30** |
| SVD            | 24.38  | 20.35 |
| Hybrid         | 14.32  | 11.77 |
| NCF            | 16.38  | 13.28 |

**Conclusion:** Item–Item KNN achieved the best accuracy and is used in the deployed recommendation system.

## Demo Screenshot
<img width="1920" height="1080" alt="recommendation_demo" src="https://github.com/user-attachments/assets/d6126a94-1ac3-4bad-bbca-566f1b111dd7" />


## Project Structure
online-course-recommendation-system/

│

├── README.md

├── requirements.txt

│

├── notebooks/

│   └── online_course_recommendation.ipynb

│

├── data/

│   └── courses.csv


## How to Run
Install dependencies:
pip install -r requirements.txt

Run app:
streamlit run streamlit_app.py


Open browser at: `http://localhost:8501`

## Usage
1. Select or enter a user ID  
2. View previous course interactions  
3. Enter number of recommendations  
4. System displays ranked suggestions based on Item–Item KNN similarity  
5. Explore course similarity explanations

## Techniques Used
- TF-IDF Vectorization  
- Cosine Similarity  
- KNN Collaborative Filtering  
- SVD Matrix Factorization  
- Neural Collaborative Filtering (NCF)  
- Pandas, NumPy, Scikit-learn, Surprise  
- Streamlit for deployment

## Future Improvements
- Add implicit feedback modeling
- Deploy on Render/HuggingFace
- Add user authentication & database logging
- Implement ranking-based hybrid blending
- API endpoints for integration with LMS platforms

## Author
**Nithin Vudikala**  
Aspiring Data Scientist  
GitHub • LinkedIn
