
# TariffAI 🤖📞

An AI-powered full-stack web application that analyzes telecom customer usage patterns to provide personalized, cost-effective tariff plan recommendations. Built to reduce churn and optimize revenue.

[![React](https://img.shields.io/badge/React-18.3.1-61DAFB?logo=react)](https://reactjs.org/)
[![Flask](https://img.shields.io/badge/Flask-3.0.0-000000?logo=flask)](https://flask.palletsprojects.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?logo=mongodb)](https://www.mongodb.com/atlas)
[![License](https://img.shields.io/badge/License-Proprietary-blue)](#license)

![TariffAI Dashboard](https://via.placeholder.com/800x400.png?text=TariffAI+Dashboard+Screenshot) <!-- Replace with actual screenshot link -->

## ✨ Features

- **🧠 AI-Powered Recommendations:** Get top 3 personalized plan suggestions using machine learning clustering.
- **👥 Role-Based Dashboards:**
  - **Customer View:** See your usage patterns and recommended plans.
  - **Admin View:** Analyze customer segments, plan performance, and business KPIs.
- **💬 Intelligent Chatbot:** Integrated AI assistant (powered by Groq's Llama 3.3) for real-time plan inquiries.
- **📊 Data Visualization:** Interactive charts for call patterns, SMS/data usage, and customer demographics.
- **⚡ Modern Tech Stack:** Built with React 18, Vite, Flask, and MongoDB Atlas for performance and scalability.

## 🏗️ Architecture

TariffAI follows a client-server architecture:

```
+-------------------+       HTTP/HTTPS       +---------------------+      MongoDB Driver     +-------------------+
|   React Frontend  | <--------------------> |    Flask Backend    | <--------------------> |  MongoDB Atlas    |
|  (Vite + Tailwind)| (API Calls, Sessions)  |   (RESTful API)     |   (CRUD Operations)   |   (Cloud DB)      |
+-------------------+                        +---------------------+                        +-------------------+
         ^                                          ^
         |                                          | Groq API Call
         | User Interaction                         v
+-------------------+                        +---------------------+
|   User Browser    |                        |      Groq API       |
|                   |                        | (Llama 3.3-70B)    |
+-------------------+                        +---------------------+
```

## 🛠️ Tech Stack

**Frontend:**
- **Framework:** React 18.3.1
- **Build Tool:** Vite 6.3.5
- **Styling:** Tailwind CSS 3.4.1
- **Routing:** React Router DOM 7.8.2
- **Icons:** Lucide React

**Backend:**
- **Framework:** Flask 3.0.0 (Python)
- **Database:** MongoDB Atlas (with PyMongo)
- **AI:** Groq API (Llama-3.3-70b-versatile model)
- **Data Processing:** Pandas

## 📦 Installation & Setup

### Prerequisites

- **Node.js** (v18 or higher)
- **Python** (v3.9 or higher)
- **pip** (Python package manager)
- A MongoDB Atlas cluster URI ([Get one here](https://www.mongodb.com/atlas/database))
- A Groq API key ([Get one here](https://console.groq.com/))

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/tariffai.git
cd tariffai
```

### 2. Backend Setup

```bash
# Navigate to the backend directory
cd backend

# Create a virtual environment (recommended)
python -m venv venv

# Activate the virtual environment
# On macOS/Linux:
source venv/bin/activate
# On Windows:
.\venv\Scripts\activate

# Install Python dependencies
pip install -r requirements.txt
```

**Configure Environment Variables:**
Create a `.env` file in the `backend` directory:

```ini
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.b6rfjh1.mongodb.net/?retryWrites=true&w=majority
GROQ_API_KEY=your_actual_groq_api_key_here
SECRET_KEY=your_very_secure_random_secret_key_here
FLASK_ENV=development
```

**Run the Backend Server:**
```bash
python app.py
```
The backend API will start on `http://localhost:5000`.

### 3. Frontend Setup

Open a new terminal window and navigate to the project root.

```bash
# Navigate to the frontend directory
cd frontend

# Install npm dependencies
npm install
```

**Configure Environment Variables:**
Create a `.env` file in the `frontend` directory:

```ini
VITE_API_URL=http://localhost:5000
```

**Start the Development Server:**
```bash
npm run dev
```
The frontend will start on `http://localhost:5173`.

## 🚀 Usage

1.  **Access the Application:** Open your browser and go to `http://localhost:5173`.
2.  **Customer Login:** Use a phone number from the sample data (e.g., check `backend/data/processed/customers_with_clusters.csv`).
3.  **Admin Login:** Click "Admin Login" and use the credentials configured in the backend.
4.  **Interact with the Chatbot:** Use the chat icon in the bottom corner to ask questions about plans.

## 📁 Project Structure

```
tariffai/
├── backend/                 # Flask API server
│   ├── data/               # ML data and processed CSVs
│   ├── app.py              # Main application file
│   ├── requirements.txt    # Python dependencies
│   └── .env               # Environment variables (create it)
├── frontend/               # React application
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── pages/         # Page components
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   └── .env               # Environment variables (create it)
└── README.md
```

## 🔌 API Reference

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/api/login` | POST | Authenticate a user (customer or admin) |
| `/api/user` | POST | Get user data and top 3 plan recommendations |
| `/api/admin/dashboard` | GET | Get aggregate metrics and chart data (Admin only) |
| `/api/chat` | POST | Send a message to the AI chatbot |
| `/healthz` | GET | Health check endpoint |

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

Please ensure your code follows the existing style and includes relevant tests.

## 📄 License

This project is proprietary and confidential. All rights reserved by [Your Company Name]. The use and distribution of this software is subject to the terms of a license agreement.

**Note:** This software includes numerous open-source dependencies, each governed by its own license (e.g., MIT, Apache 2.0). Please refer to the respective `package.json` and `requirements.txt` files for a full list of dependencies.

## 🆘 Support

For support, please open an issue in this GitHub repository or contact our development team at dev-support@yourcompany.com.

---

**Disclaimer:** This is a demonstration project. Ensure you comply with all relevant data protection regulations (like GDPR, CCPA) before using real customer data in a production environment.
