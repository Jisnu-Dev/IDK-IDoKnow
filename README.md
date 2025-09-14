# GenAI-XChange: Misinformation Analysis API

## Overview

The GenAI-XChange Misinformation Analysis API is a comprehensive solution designed to combat misinformation through advanced AI-powered analysis. This system provides automated classification, significance scoring, and summarization of text content to help identify and prioritize potential misinformation for verification and fact-checking.

## Features

### Core Functionality

- **Multi-dimensional Classification**: Categorizes content based on verification source requirements (Person, Organization, Social, Critical, STEM)
- **Intelligent Triage Scoring**: Assigns priority scores (0-100) to determine urgency of fact-checking needs
- **Comprehensive Summarization**: Generates clear, contextual summaries preserving all critical information
- **Source Detection**: Automatically identifies presence of external links and sources
- **RESTful API**: Easy integration with existing systems and workflows

### Key Components

1. **Fake News Detector**: Advanced classification system that determines the type of verification sources needed
2. **Significance Score Provider**: Priority scoring algorithm for misinformation triage
3. **Comprehensive Summarizer**: AI-powered text summarization with information retention
4. **FastAPI Framework**: High-performance REST API with automatic documentation

## Architecture

### System Design

```
GenAI-XChange/
├── Module1 (Score)/
│   ├── backend/
│   │   ├── main.py                 # FastAPI application entry point
│   │   └── Modules/
│   │       ├── Classifier/         # Fake news classification module
│   │       ├── SignificanceScore/  # Priority scoring module
│   │       └── Summarizer/         # Text summarization module
│   └── requirements.txt            # Python dependencies
└── README.md                       # Project documentation
```

### Technical Stack

- **Backend Framework**: FastAPI
- **AI Model**: Google Gemini-2.0-Flash
- **Language**: Python 3.8+
- **Environment Management**: python-dotenv
- **API Documentation**: Automatic OpenAPI/Swagger generation

## Installation

### Prerequisites

- Python 3.8 or higher
- Google AI API key (Gemini)
- Git

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd GenAI-XChange
   ```

2. **Install dependencies**
   ```bash
   cd "Module1 (Score)"
   pip install -r requirements.txt
   ```

3. **Configure environment variables**
   
   Create a `.env` file in the `Module1 (Score)/backend/` directory:
   ```env
   # API Configuration
   API_KEY=your_google_ai_api_key_here
   
   # Model Configuration
   MODEL_NAME=gemini-2.0-flash
   
   # Server Configuration
   HOST=127.0.0.1
   PORT=8000
   
   # Application Configuration
   APP_TITLE=Misinformation Analysis API
   APP_DESCRIPTION=API for analyzing text for misinformation using classification, significance scoring, and summarization
   APP_VERSION=1.0.0
   ```

4. **Run the application**
   ```bash
   cd backend
   python main.py
   ```

## API Documentation

### Endpoints

#### POST /analyze
Analyzes text for misinformation potential and returns comprehensive results.

**Request Body:**
```json
{
  "text": "Text content to analyze for misinformation"
}
```

**Response:**
```json
{
  "classification": {
    "person": 25.0,
    "organization": 15.0,
    "social": 30.0,
    "critical": 20.0,
    "stem": 10.0
  },
  "significance_score": 75,
  "summary": "Comprehensive summary of the analyzed content...",
  "source": true
}
```

#### GET /health
Health check endpoint for monitoring system status.

#### GET /
Root endpoint providing API information and available endpoints.

### Classification Categories

- **Person (0-100%)**: Requires verification through personal sources, biographical records, or individual statements
- **Organization (0-100%)**: Requires verification through organizational sources, company statements, or institutional records
- **Social (0-100%)**: Requires verification through social news sources, community reports, or social media verification
- **Critical (0-100%)**: Requires verification through emergency services, government alerts, or security agencies
- **STEM (0-100%)**: Can be verified using established facts, scientific principles, historical records, or objective data

### Significance Scoring

Priority scores range from 0-100 with the following guidelines:

- **85-100**: Critical Priority (public safety, medical dangers)
- **60-84**: High Priority (elections, political figures, market manipulation)
- **30-59**: Medium Priority (public figures, unconfirmed studies)
- **5-29**: Low Priority (celebrity gossip, entertainment rumors)
- **0-4**: No Priority (personal, nonsensical content)

## Usage Examples

### Basic Text Analysis

```python
import requests

# Analyze a text for misinformation
response = requests.post(
    "http://localhost:8000/analyze",
    json={"text": "Breaking: New study shows miracle cure for common cold"}
)

result = response.json()
print(f"Significance Score: {result['significance_score']}")
print(f"Summary: {result['summary']}")
```

### Health Check

```python
response = requests.get("http://localhost:8000/health")
print(response.json())  # {"status": "healthy", "message": "API is running"}
```

## Development

### Environment Variables

The application uses environment variables for configuration:

- `API_KEY`: Google AI API key (required)
- `MODEL_NAME`: AI model name (default: gemini-2.0-flash)
- `HOST`: Server host (default: 127.0.0.1)
- `PORT`: Server port (default: 8000)
- `APP_TITLE`: Application title
- `APP_DESCRIPTION`: Application description
- `APP_VERSION`: Application version

### Local Development

1. Set up the development environment as described in the installation section
2. Access the interactive API documentation at `http://localhost:8000/docs`
3. Use the health endpoint to verify the system is running correctly

## Security Considerations

- API keys are managed through environment variables and never committed to version control
- Input validation is implemented for all API endpoints
- Error handling prevents sensitive information exposure
- Rate limiting and authentication should be implemented for production deployments

## Contributing

This project is developed for the GenAI-XChange global hackathon. For contributions:

1. Follow the existing code structure and naming conventions
2. Ensure all environment variables are properly configured
3. Test all API endpoints before submitting changes
4. Maintain comprehensive error handling and logging

## License

This project is developed for the GenAI-XChange hackathon. Please refer to the hackathon guidelines for usage and distribution terms.

## Support

For technical support or questions regarding this implementation, please refer to the hackathon documentation or contact the development team through the official hackathon channels.
