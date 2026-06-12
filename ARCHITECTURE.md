# System Architecture

## Overview

The Multi-Agent AI Travel Planner follows a hybrid architecture that combines:

* Multi-agent reasoning
* Real-time travel APIs
* Retrieval-Augmented Generation (RAG)
* Parallel asynchronous execution

The goal is to reduce hallucinations by separating factual data retrieval from AI reasoning.

---

## Architecture Diagram

![System Architecture](docs/architecture.png)

---

## AI Agents

### Travel Manager

The Travel Manager converts natural language requests into structured travel requirements.

Responsibilities:

* Destination extraction
* Date extraction
* Budget analysis
* Preference identification
* Constraint detection

---

### Knowledge Expert

The Knowledge Expert retrieves contextual travel knowledge from the RAG layer.

Responsibilities:

* Cultural insights
* Visa information
* Local customs
* Travel recommendations
* Practical destination guidance

---

### Itinerary Compiler

The Itinerary Compiler synthesizes all collected information into a final travel itinerary.

Responsibilities:

* Aggregate service results
* Incorporate travel knowledge
* Optimize daily schedules
* Generate personalized recommendations

---

## Service Layer

### Flight Service

Providers:

* Amadeus
* SerpApi

Provides:

* Flight search
* Airline information
* Fare comparison

---

### Accommodation Service

Providers:

* Booking.com
* Airbnb

Provides:

* Hotel recommendations
* Rental recommendations
* Accommodation comparison

---

### Activity Service

Providers:

* Google Places
* Viator
* Yelp Fusion

Provides:

* Attractions
* Restaurants
* Tours
* Local experiences

---

### Logistics Service

Providers:

* Google Maps
* OpenWeatherMap
* Exchange Rate API
* REST Countries API
* Travel Briefing API

Provides:

* Routing
* Weather forecasts
* Currency conversion
* Destination information

---

## RAG Pipeline

```text
Travel Documents
      ↓
Document Chunking
      ↓
Embedding Generation
      ↓
ChromaDB Vector Store
      ↓
Similarity Search
      ↓
Knowledge Expert Agent
```

The RAG layer supplies travel-specific knowledge that is not available through real-time APIs.

---

## Design Principles

### Separation of Concerns

* AI agents perform reasoning
* APIs provide factual information
* RAG provides contextual knowledge

### Reduced Hallucination Risk

Travel recommendations are generated from real-world API responses rather than solely relying on model knowledge.

### Scalability

New providers can be added without modifying agent logic.

### Performance

External services execute concurrently using asyncio.gather().
