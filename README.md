# Loan Approval Prediction Web App Using Streamlit

An interactive web application built with **Streamlit** that predicts whether a bank loan will be approved or rejected based on applicant details. The app uses a pre-trained machine learning model and stores each prediction to a **MySQL database** for record-keeping.

---

## 📖 Project Overview

Loan approval is a critical decision-making process in the banking sector. This project delivers a user-friendly web interface where applicants can enter their financial and personal details and instantly receive a **loan approval prediction**. Every prediction is automatically saved to a MySQL database, enabling banks to maintain a structured record of all applications.

---

## 📂 Repository Structure

```
Streamlit/
│
├── app.py                  # Main Streamlit application
├── build.pkl               # Pre-trained ML model (Pickle file)
├── index.html              # Supporting HTML file
├── style.css               # Custom CSS styling
├── requirements.txt        # Python dependencies
└── README.md               # Project overview and instructions
```

---

## 🔍 Input Features

The application accepts the following applicant details as input:

| Feature | Type | Description |
|---------|------|-------------|
| `Customer Age` | Number | Age of the loan applicant (18–100) |
| `Family Member` | Number | Number of dependents |
| `Income` | Number | Monthly/Annual income of the applicant |
| `Loan Amount` | Number | Requested loan amount |
| `CIBIL Score` | Number | Credit score of the applicant (300–900) |
| `Tenure` | Number | Loan repayment duration in months |
| `Gender` | Dropdown | Male / Female |
| `Married` | Dropdown | Yes / No |
| `Education` | Dropdown | Graduate / Not Graduate |
| `Self Employed` | Dropdown | Yes / No |
| `Previous Loan Taken` | Dropdown | Yes / No |
| `Property Area` | Dropdown | Urban / Semiurban / Rural |
| `Customer Bandwidth` | Dropdown | Low / Medium / High |

---

## 🎯 Output

| Prediction | Result |
|------------|--------|
| `0` | ✅ **Loan Approved** |
| `1` | ❌ **Loan Rejected** |

---

## 🛠️ Technologies Used

| Category | Tools / Libraries |
|----------|-------------------|
| **Web Framework** | Streamlit |
| **Data Processing** | Pandas, NumPy |
| **Model Serialization** | Pickle |
| **Database** | MySQL (via `mysql-connector-python`) |
| **Styling** | Custom CSS (`style.css`) |

---

## 🚀 Implementation Steps

### 1. Model Loading
- Loads the pre-trained ML model from `build.pkl` using Python's `pickle` module
- Handles missing file errors and corrupted pickle files gracefully with user-friendly error messages

### 2. User Input Collection
- Collects 13 applicant features via Streamlit input widgets (`number_input`, `selectbox`)
- Input validation ensures values stay within acceptable ranges (e.g., CIBIL Score: 300–900)

### 3. Prediction
- Maps user inputs into a Pandas DataFrame with the exact column names expected by the model
- Runs `model.predict()` and displays the result as **Loan Approved** or **Loan Rejected**

### 4. Database Storage
- Connects to a **MySQL database** (`bankloan`) on localhost
- Inserts all input features along with the prediction result into the `loan_applications` table
- Confirms successful save with a success message in the UI

---

## 🗄️ Database Schema

**Database:** `bankloan`
**Table:** `loan_applications`

| Column | Type | Description |
|--------|------|-------------|
| `customer_age` | INT | Age of applicant |
| `family_member` | INT | Number of dependents |
| `income` | FLOAT | Applicant income |
| `loan_amount` | FLOAT | Requested loan amount |
| `cibil_score` | INT | Credit score |
| `tenure` | INT | Loan tenure in months |
| `gender` | VARCHAR | Male / Female |
| `married` | VARCHAR | Yes / No |
| `education` | VARCHAR | Graduate / Not Graduate |
| `self_employed` | VARCHAR | Yes / No |
| `previous_loan_taken` | VARCHAR | Yes / No |
| `property_area` | VARCHAR | Urban / Semiurban / Rural |
| `customer_bandwidth` | VARCHAR | Low / Medium / High |
| `prediction` | VARCHAR | Loan Approved / Loan Rejected |

---

## 🏁 Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/shreyaa-1702/Streamlit.git
   cd Streamlit
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up MySQL Database**
   - Create a database named `bankloan`
   - Create the `loan_applications` table using the schema above
   - Update the database credentials in `app.py` if needed:
     ```python
     host='localhost',
     port=3306,
     user='root',
     password='your_password',
     database='bankloan'
     ```

4. **Place the model file**
   - Ensure `build.pkl` is in the correct path as referenced in `app.py`

5. **Run the Streamlit app**
   ```bash
   streamlit run app.py
   ```

6. **Open in browser**
   - The app will automatically open at `http://localhost:8501`

---

## ⚙️ Requirements

```
streamlit
numpy
pandas
scikit-learn
mysql-connector-python
```

Install all at once:
```bash
pip install streamlit numpy pandas scikit-learn mysql-connector-python
```

---

## 💡 Key Insights

- **CIBIL Score** is one of the strongest indicators of loan approval — scores above 750 are generally considered creditworthy
- The app handles model loading errors and database connection failures **gracefully**, ensuring users always receive a clear message
- All predictions are **persisted to MySQL**, enabling historical analysis and audit trails of loan applications
- The modular code structure separates database connection, model loading, and UI rendering for easy maintenance

---

## 📄 License

This project is licensed under the terms specified in the [LICENSE](LICENSE) file.

---

## 🙋 Contributing

Contributions and suggestions are welcome. Feel free to open an issue or submit a pull request for any improvements or enhancements.
