# Jarvis Voice Control - Setup Guide

## Quick Start

### Prerequisites
- Android Studio (for Android development)
- Python 3.8+ (for backend)
- Google Cloud account (for Speech API)
- Stripe account (for payments)
- WhatsApp Business API access

## Backend Setup

### 1. Clone Repository
```bash
git clone https://github.com/rajeshsreeram143-ctrl/Jarvis-Voice-Control.git
cd Jarvis-Voice-Control/backend
```

### 2. Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables
```bash
cp .env.example .env
# Edit .env with your API keys
```

### 5. Run Backend Server
```bash
python main.py
```

Server will start at `http://localhost:5000`

## Android Setup

### 1. Open Project in Android Studio
```bash
cd android
# Open in Android Studio
```

### 2. Update Backend URL
In `JarvisService.java`, update:
```java
private static final String BASE_URL = "http://YOUR_BACKEND_URL:5000/";
```

### 3. Build and Run
```bash
./gradlew build
./gradlew installDebug
```

## Configuration

### Google Cloud Speech API
1. Create service account
2. Download JSON credentials
3. Set `GOOGLE_APPLICATION_CREDENTIALS` in `.env`

### Stripe API
1. Get API key from Stripe Dashboard
2. Set `STRIPE_API_KEY` in `.env`

### WhatsApp Business API
1. Register business account
2. Get API key and Account ID
3. Set in `.env`

## Testing

### Backend API Tests
```bash
curl -X POST http://localhost:5000/health
```

### Voice Command Test
```bash
# Record audio and send
curl -X POST http://localhost:5000/process-voice \
  -H "Content-Type: application/json" \
  -d '{"audio":"BASE64_ENCODED_AUDIO"}'
```

## Troubleshooting

### Backend Connection Issues
- Ensure backend URL is correct in Android code
- Check firewall allows port 5000
- Verify backend is running: `curl http://localhost:5000/health`

### Speech Recognition Issues
- Check microphone permissions on Android
- Ensure Google Cloud credentials are valid
- Check internet connection

### Payment Integration Issues
- Verify Stripe API key is correct
- Check payment method is supported
- Review Stripe dashboard for errors

## Next Steps

1. Implement advanced voice processing
2. Add database for transaction history
3. Implement voice authentication
4. Add multi-language support
5. Deploy to production

## Support

For issues, create a GitHub issue or check documentation.
