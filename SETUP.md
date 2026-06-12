# Setup Guide

## Prerequisites

* Python 3.11+
* Node.js 22+
* Git

---

## Backend Installation

Create a virtual environment:

```bash
python -m venv venv

source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Environment Variables

Create a `.env` file in the project root.

Required:

```env
GEMINI_API_KEY=
```

Optional:

```env
AMADEUS_API_KEY=
AMADEUS_API_SECRET=
SERPAPI_KEY=

BOOKING_API_KEY=
AIRBNB_API_KEY=

GOOGLE_PLACES_API_KEY=
GOOGLE_MAPS_API_KEY=

VIATOR_API_KEY=
YELP_API_KEY=

OPENWEATHER_API_KEY=

OPENAI_API_KEY=
EXCHANGE_RATE_API_KEY=
```

---

## Run Backend

```bash
uvicorn backend.app:app --reload
```

---

## Run Frontend

```bash
cd frontend

npm install

npm run dev
```

Frontend will be available at:

```text
http://localhost:5173
```

---

## CLI Mode

```bash
python main.py
```

---

## Troubleshooting

### Invalid Gemini API Key

Generate a valid key through Google AI Studio and verify it is correctly loaded through the `.env` file.

### ChromaDB Issues

Delete:

```text
data/chroma_db
```

and restart the application.

### Missing Python Packages

```bash
pip install -r requirements.txt
```

### Node.js Version Errors

Use Node.js version 22 or newer.
