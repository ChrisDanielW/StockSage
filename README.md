# Stock Sage 

A machine learning-powered stock price prediction and analysis web application built with Flask and TensorFlow. Stock Sage uses LSTM (Long Short-Term Memory) neural networks to analyze historical stock data and predict future price movements.

## Features

- **User Authentication**: Secure Firebase-based user authentication with registration and login
- **Stock Price Analysis**: Real-time stock data retrieval using Yahoo Finance API
- **LSTM Predictions**: Advanced machine learning model for 30-day price forecasting
- **Interactive Visualizations**: Dynamic charts showing:
  - Historical prices with moving averages (100-day & 200-day MA)
  - Actual vs predicted prices comparison
  - Future price predictions
- **User Preferences**: Save and manage favorite stock tickers
- **Analysis History**: Track all your previous stock analyses
- **Personalized Dashboard**: User-specific data and prediction history

## Technologies Used

### Backend
- **Flask** - Web framework
- **TensorFlow/Keras** - LSTM neural network model
- **scikit-learn** - Data preprocessing and scaling
- **yfinance** - Real-time stock data fetching
- **Firebase Admin SDK** - User authentication
- **SQLAlchemy** - Database ORM
- **SQLite** - Local database storage

### Frontend
- **HTML/CSS/JavaScript** - User interface
- **Matplotlib** - Chart generation

## Installation

### Prerequisites
- Python 3.7+
- pip package manager

### Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd "Stock Sage"
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   
   Create a `.env` file in the project root with your Firebase credentials:
   ```env
   # Firebase Service Account Credentials
   FIREBASE_TYPE=service_account
   FIREBASE_PROJECT_ID=your-project-id
   FIREBASE_PRIVATE_KEY_ID=your-private-key-id
   FIREBASE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"
   FIREBASE_CLIENT_EMAIL=your-service-account-email
   FIREBASE_CLIENT_ID=your-client-id
   FIREBASE_AUTH_URI=https://accounts.google.com/o/oauth2/auth
   FIREBASE_TOKEN_URI=https://oauth2.googleapis.com/token
   FIREBASE_AUTH_PROVIDER_X509_CERT_URL=https://www.googleapis.com/oauth2/v1/certs
   FIREBASE_CLIENT_X509_CERT_URL=your-cert-url
   FIREBASE_UNIVERSE_DOMAIN=googleapis.com

   # Database Configuration
   DATABASE_URI=sqlite:///stock_predictions.db
   ```

5. **Initialize the database**
   ```bash
   python app.py
   ```
   The database will be automatically created on first run.

## Usage

1. **Start the application**
   ```bash
   python app.py
   ```

2. **Access the application**
   
   Open your browser and navigate to `http://localhost:5000`

3. **Create an account**
   
   Register a new account using the registration page

4. **Analyze stocks**
   
   - Enter a stock ticker symbol (e.g., AAPL, GOOGL, TSLA)
   - View historical data with moving averages
   - See LSTM-based price predictions for the next 30 days
   - Compare actual vs predicted prices

5. **Manage preferences**
   
   Save your favorite stocks for quick access

## Project Structure

```
Stock Sage/
├── app.py                    # Main Flask application
├── requirements.txt          # Python dependencies
├── .env                      # Environment variables (not in git)
├── .gitignore               # Git ignore file
├── static/                  # Static assets
│   ├── analysis.css         # Analysis page styles
│   ├── index.css            # Home page styles
│   ├── login.css            # Login page styles
│   ├── register.css         # Registration page styles
│   └── script.js            # Frontend JavaScript
├── templates/               # HTML templates
│   ├── analysis.html        # Analysis page
│   ├── index.html           # Home page
│   ├── login.html           # Login page
│   └── register.html        # Registration page
└── stock_predictions.db     # SQLite database (auto-generated)
```

## API Endpoints

### Public Routes
- `GET /` - Home page
- `GET /login` - Login page
- `GET /register` - Registration page
- `GET /analysis` - Analysis page

### Protected Routes (Require Authentication)
- `GET /analyze?ticker=SYMBOL` - Analyze stock and generate predictions
- `GET /history` - Get user's analysis history
- `POST /preferences` - Save favorite stock ticker
- `GET /preferences` - Get user's favorite tickers
- `DELETE /preferences/<ticker>` - Remove favorite ticker

## Model Details

### LSTM Architecture
- 3 LSTM layers (100, 75, 50 units)
- Dropout layers (0.3, 0.2, 0.2) for regularization
- Dense layers for final prediction
- Adam optimizer with MSE loss
- 60-day time step for sequence learning

### Training
- 80/20 train-test split
- 20 epochs with batch size of 32
- MinMax scaling (0-1 range)

## Security

- **Environment Variables**: All sensitive credentials stored in `.env` file
- **Firebase Authentication**: Secure user authentication with JWT tokens
- **Git Ignore**: `.env` file excluded from version control
- **Authorization Middleware**: Protected routes require valid authentication tokens

## Important Notes

 **Disclaimer**: Stock predictions are based on historical data and machine learning models. They should not be used as the sole basis for investment decisions. Always do your own research and consult with financial advisors.

 **API Limits**: The Yahoo Finance API has rate limits. Excessive requests may result in temporary blocks.

## Future Enhancements

- [ ] Real-time stock price updates
- [ ] Multiple ML model comparison
- [ ] Sentiment analysis integration
- [ ] Portfolio tracking
- [ ] Email notifications for price alerts
- [ ] Mobile responsive design improvements
- [ ] Export analysis reports to PDF

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the [MIT License](LICENSE).

## Contact

For questions or support, please open an issue in the repository.

---

Made for smarter stock analysis
