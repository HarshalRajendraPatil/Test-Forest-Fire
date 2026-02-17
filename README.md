# 🔥 Fire Weather Index (FWI) Prediction Web Application

A comprehensive end-to-end machine learning project that predicts the Fire Weather Index (FWI) for Algerian forest fires using weather and fuel moisture data. This project includes data analysis, model training, and a beautiful web application for real-time predictions.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.0+-green.svg)
![scikit-learn](https://img.shields.io/badge/scikit--learn-Latest-orange.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Dataset](#dataset)
- [Model Details](#model-details)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [UI/UX Design](#uiux-design)
- [Development Workflow](#development-workflow)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

The Fire Weather Index (FWI) is a crucial metric used by fire management agencies to assess the risk of wildfires. This project leverages machine learning to predict FWI values based on meteorological and fuel moisture conditions, specifically trained on Algerian forest fire data.

**Key Objectives:**
- Predict FWI values using weather and fuel moisture indices
- Provide an intuitive web interface for real-time predictions
- Support fire risk assessment and management decisions
- Demonstrate end-to-end ML pipeline from data to deployment

---

## ✨ Features

### Core Functionality
- **Real-time FWI Prediction**: Enter weather parameters and get instant FWI predictions
- **9 Input Parameters**: Comprehensive input fields for accurate predictions
  - Temperature (°C)
  - Relative Humidity (RH)
  - Wind Speed (Ws)
  - Rainfall (Rain)
  - Fine Fuel Moisture Code (FFMC)
  - Duff Moisture Code (DMC)
  - Initial Spread Index (ISI)
  - Fire Classes (encoded)
  - Region (encoded)

### User Experience
- **Modern, Responsive Design**: Beautiful dark-themed UI with gradient backgrounds
- **Intuitive Form Interface**: Clean, organized input form with labeled fields
- **Visual Result Display**: Highlighted prediction results with clear formatting
- **Mobile-Friendly**: Responsive design that works on all devices

### Technical Features
- **Ridge Regression Model**: Robust regression model for FWI prediction
- **StandardScaler Preprocessing**: Normalized inputs for consistent predictions
- **Flask Web Framework**: Lightweight and efficient web application
- **Pickle Model Serialization**: Fast model loading and inference

---

## 🛠 Technology Stack

### Backend
- **Python 3.8+**: Core programming language
- **Flask 2.0+**: Web framework for API and routing
- **scikit-learn**: Machine learning library (Ridge Regression, StandardScaler)
- **NumPy**: Numerical computations
- **Pandas**: Data manipulation and analysis

### Frontend
- **HTML5**: Semantic markup
- **CSS3**: Modern styling with custom design system
- **Google Fonts**: Syne (headings) and DM Sans (body)
- **Responsive Design**: Mobile-first approach

### Data Science & ML
- **Jupyter Notebooks**: Data exploration and model training
- **Matplotlib/Seaborn**: Data visualization
- **Pickle**: Model serialization

---

## 📁 Project Structure

```
End to end project with web app/
│
├── application.py                 # Flask application and routes
├── requirement.txt               # Python dependencies
├── README.md                     # Project documentation
│
├── data/
│   ├── Algerian_forest_fires_cleaned_dataset.csv
│   └── Algerian_forest_fires_dataset_UPDATE.csv
│
├── models/
│   ├── ridge.pkl                 # Trained Ridge Regression model
│   └── scaler.pkl                 # StandardScaler for preprocessing
│
├── notebooks/
│   ├── 2.0-EDA And FE Algerian Forest Fires.ipynb
│   └── 3.0-Model Training.ipynb
│
├── static/
│   └── css/
│       └── style.css             # Custom stylesheet
│
└── templates/
    ├── index.html                # Landing page
    └── home.html                 # Prediction form page
```

---

## 📊 Dataset

### Dataset Information
- **Source**: Algerian Forest Fires Dataset
- **Records**: 243 samples (after cleaning)
- **Time Period**: 2012 (June-September)
- **Regions**: Two regions (encoded as 0 and 1)

### Features

#### Weather Parameters
- **Temperature**: Air temperature in degrees Celsius
- **RH**: Relative Humidity percentage
- **Ws**: Wind Speed (km/h)
- **Rain**: Rainfall amount (mm)

#### Fire Weather Indices
- **FFMC**: Fine Fuel Moisture Code (0-101)
- **DMC**: Duff Moisture Code (0-300+)
- **DC**: Drought Code (0-800+)
- **ISI**: Initial Spread Index (0-56+)
- **BUI**: Build-Up Index (0-200+)

#### Target Variable
- **FWI**: Fire Weather Index (0-31+) - **Prediction Target**

#### Additional Features
- **Classes**: Fire occurrence (0 = not fire, 1 = fire)
- **Region**: Geographic region (0 or 1)
- **day, month, year**: Temporal information

### Data Preprocessing
- Missing value handling
- Encoding of categorical variables (Classes: "not fire" → 0, "fire" → 1)
- Feature selection (removed temporal features for prediction)
- Train-test split (75% train, 25% test, random_state=42)

---

## 🤖 Model Details

### Algorithm: Ridge Regression

Ridge Regression is a linear regression technique with L2 regularization, chosen for its ability to:
- Handle multicollinearity in features
- Prevent overfitting through regularization
- Provide stable predictions
- Work well with small to medium-sized datasets

### Model Training
- **Training Set**: 182 samples (75%)
- **Test Set**: 61 samples (25%)
- **Random State**: 42 (for reproducibility)
- **Preprocessing**: StandardScaler normalization applied to all features

### Model Files
- `models/ridge.pkl`: Serialized Ridge Regression model
- `models/scaler.pkl`: Serialized StandardScaler for feature normalization

### Input Features (11 features)
1. Temperature
2. RH (Relative Humidity)
3. Ws (Wind Speed)
4. Rain (Rainfall)
5. FFMC (Fine Fuel Moisture Code)
6. DMC (Duff Moisture Code)
7. DC (Drought Code)
8. ISI (Initial Spread Index)
9. BUI (Build-Up Index)
10. Classes (encoded)
11. Region (encoded)

**Note**: The web application uses 9 features (excluding DC and BUI from the original dataset).

---

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package installer)
- Git (optional, for cloning)

### Step-by-Step Installation

1. **Clone or download the repository**
   ```bash
   git clone <repository-url>
   cd "End to end project with web app"
   ```

2. **Create a virtual environment (recommended)**
   ```bash
   python -m venv venv
   
   # On Windows
   venv\Scripts\activate
   
   # On macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirement.txt
   ```

4. **Ensure model files exist**
   - Verify that `models/ridge.pkl` and `models/scaler.pkl` are present
   - If missing, run the model training notebook (`notebooks/3.0-Model Training.ipynb`)

---

## 💻 Usage

### Running the Application

1. **Start the Flask server**
   ```bash
   python application.py
   ```

2. **Access the application**
   - Open your web browser
   - Navigate to: `http://localhost:5000` or `http://127.0.0.1:5000`

3. **Using the Application**
   - **Landing Page** (`/`): View the welcome page and click "Predict FWI"
   - **Prediction Page** (`/predictdata`): Enter the required parameters and click "Predict"
   - **View Results**: The predicted FWI value will be displayed below the form

### Example Input Values

```
Temperature: 28.5
RH: 45
Ws: 12
Rain: 0.0
FFMC: 85.2
DMC: 45.3
ISI: 8.1
Classes: 0
Region: 0
```

### Expected Output
The application returns a predicted FWI value (rounded to 2 decimal places), which indicates the fire weather severity.

---

## 🌐 API Endpoints

### GET `/`
- **Description**: Landing page
- **Response**: Renders `index.html`

### GET `/predictdata`
- **Description**: Display prediction form
- **Response**: Renders `home.html` (empty form)

### POST `/predictdata`
- **Description**: Submit form data and get FWI prediction
- **Method**: POST
- **Content-Type**: `application/x-www-form-urlencoded`
- **Parameters**:
  - `temperature` (float): Temperature in °C
  - `RH` (float): Relative Humidity
  - `Ws` (float): Wind Speed
  - `Rain` (float): Rainfall amount
  - `FFMC` (float): Fine Fuel Moisture Code
  - `DMC` (float): Duff Moisture Code
  - `ISI` (float): Initial Spread Index
  - `Classes` (float): Fire class (0 or 1)
  - `Region` (float): Region code (0 or 1)
- **Response**: Renders `home.html` with `result` variable containing predicted FWI

---

## 🎨 UI/UX Design

### Design Philosophy
The application features a modern, dark-themed design inspired by forest and fire aesthetics, creating an intuitive and visually appealing user experience.

### Color Palette
- **Background**: Deep dark (`#0a0e14`) with gradient overlays
- **Accent Colors**: 
  - Flame Orange (`#e8a84a`) for primary actions
  - Forest Green (`#3d8b6e`) for badges and highlights
- **Text**: Cream white (`#f0ebe3`) for primary text, muted gray for secondary

### Typography
- **Headings**: Syne (Google Fonts) - Bold, modern sans-serif
- **Body**: DM Sans (Google Fonts) - Clean, readable sans-serif

### Key Design Elements
- **Gradient Backgrounds**: Layered radial gradients for depth
- **Glass Morphism**: Frosted glass effect on cards with backdrop blur
- **Smooth Animations**: Hover effects and transitions
- **Responsive Grid**: Adaptive form layout for all screen sizes
- **Visual Hierarchy**: Clear distinction between sections and elements

### Pages

#### Landing Page (`index.html`)
- Full-viewport hero section
- Centered content with badge, heading, subtitle
- Single prominent call-to-action button
- Subtle background pattern

#### Prediction Page (`home.html`)
- Fixed back navigation link
- Page header with title and description
- Card-based form layout
- Responsive input grid (2-3 columns on desktop, 1 column on mobile)
- Highlighted result display box
- Styled form inputs with focus states

---

## 🔬 Development Workflow

### Data Science Pipeline

1. **Exploratory Data Analysis** (`2.0-EDA And FE Algerian Forest Fires.ipynb`)
   - Data loading and inspection
   - Missing value analysis
   - Feature engineering
   - Data visualization
   - Correlation analysis

2. **Model Training** (`3.0-Model Training.ipynb`)
   - Data preprocessing
   - Feature encoding
   - Train-test split
   - Model training (Ridge Regression)
   - Model evaluation
   - Model serialization (pickle)

3. **Web Application Development**
   - Flask application setup
   - Route configuration
   - Template creation
   - CSS styling
   - Form handling and prediction logic

### Model Training Process

```python
# Key steps from training notebook:
1. Load cleaned dataset
2. Encode categorical variables (Classes)
3. Separate features (X) and target (y = FWI)
4. Split data (75% train, 25% test)
5. Apply StandardScaler
6. Train Ridge Regression model
7. Evaluate model performance
8. Save model and scaler as pickle files
```

---

## 🔮 Future Enhancements

### Potential Improvements
- [ ] Add model performance metrics display (MAE, RMSE, R²)
- [ ] Implement multiple model comparison (Linear Regression, Random Forest, etc.)
- [ ] Add data visualization dashboard
- [ ] Include historical prediction logs
- [ ] Add FWI risk level interpretation (Low, Moderate, High, Extreme)
- [ ] Implement batch prediction API
- [ ] Add user authentication and prediction history
- [ ] Deploy to cloud platform (Heroku, AWS, etc.)
- [ ] Add unit tests and integration tests
- [ ] Implement API documentation (Swagger/OpenAPI)
- [ ] Add data validation and error handling improvements
- [ ] Include feature importance visualization
- [ ] Add export functionality for predictions

---

## 🤝 Contributing

Contributions are welcome! If you'd like to contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Contribution Guidelines
- Follow PEP 8 style guidelines for Python code
- Write clear commit messages
- Add comments for complex logic
- Test your changes before submitting
- Update documentation as needed

---

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 👤 Author

**Harshal Patil**

---

## 🙏 Acknowledgments

- Algerian Forest Fires Dataset providers
- Flask and scikit-learn communities
- Google Fonts for typography
- Open-source contributors

---

## 📞 Support

For questions, issues, or suggestions:
- Open an issue on GitHub
- Contact the project maintainer

---

## 📚 References

- [Fire Weather Index System](https://cwfis.cfs.nrcan.gc.ca/background/summary/fwi)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [scikit-learn Documentation](https://scikit-learn.org/)
- [Ridge Regression](https://scikit-learn.org/stable/modules/linear_model.html#ridge-regression)

---

**Note**: This application is for educational and research purposes. Always consult with fire management professionals for critical fire risk assessments.

---

*Last Updated: February 2026*
