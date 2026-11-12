# Simple Social – FastAPI Application

A lightweight social media application built with **FastAPI** and **Streamlit**, featuring user authentication, media uploads, and a personalized social feed.

## Overview

Simple Social is a full-stack application that allows users to create accounts, authenticate securely, upload images and videos, and interact with posts through a simple interface.

The project demonstrates REST API development, authentication, database integration, media management, and frontend-backend communication using Python.

## Key Features

- **User Authentication:** User registration and login using JWT authentication.
- **Protected APIs:** Secure endpoints accessible to authenticated users.
- **Media Upload:** Upload images and videos with captions.
- **Cloud Storage:** Store media using ImageKit.
- **Social Feed:** Retrieve posts with author information and media URLs.
- **Post Management:** Allow users to delete their own posts.
- **Interactive Frontend:** Streamlit interface integrated with FastAPI.
- **API Documentation:** Interactive API documentation through Swagger UI.

## Technology Stack

| Category | Technologies |
|---|---|
| Backend | Python, FastAPI, Uvicorn |
| Frontend | Streamlit |
| Database | SQLite, SQLAlchemy |
| Authentication | FastAPI Users, JWT |
| Validation | Pydantic |
| Media Storage | ImageKit |
| Environment Management | uv |

## Project Structure

```text
simple-social-fastapi/
│
├── src/
│   └── app/
│       ├── __init__.py
│       ├── app.py
│       ├── db.py
│       ├── images.py
│       ├── schemas.py
│       └── users.py
│
├── main.py
├── frontend.py
├── pyproject.toml
├── uv.lock
├── .gitignore
└── README.md
```

## Application Workflow

1. Users register and log in through the Streamlit frontend.
2. FastAPI authenticates users and generates JWT tokens.
3. The frontend uses the token to access protected API endpoints.
4. Users upload images or videos with captions.
5. FastAPI uploads media to ImageKit.
6. Media URLs and post information are stored in SQLite.
7. The feed API retrieves posts along with author information.
8. Users can view posts and delete their own content.

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/VikashBasfore/simple-social-fastapi.git
cd simple-social-fastapi
```

### 2. Install Dependencies

```bash
uv sync
```

### 3. Configure Environment Variables

Create a `.env` file in the project root and configure the required credentials.

```env
IMAGEKIT_PRIVATE_KEY=your_private_key
IMAGEKIT_PUBLIC_KEY=your_public_key
IMAGEKIT_URL=your_imagekit_url
```

Keep your `.env` file private. Never commit credentials or secret keys to GitHub.

### 4. Run the FastAPI Backend

```bash
uv run python main.py
```

The backend is configured to run using:

```python
uvicorn.run(
    "app.app:app",
    host="0.0.0.0",
    port=8000,
    reload=True,
    app_dir="src"
)
```

### 5. Run the Streamlit Frontend

Open another terminal and execute:

```bash
uv run python -m streamlit run frontend.py
```

## Application URLs

| Service | URL |
|---|---|
| FastAPI Backend | http://localhost:8000 |
| Swagger API Documentation | http://localhost:8000/docs |
| Streamlit Frontend | http://localhost:8501 |

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/auth/register` | Register a new user |
| POST | `/auth/jwt/login` | Authenticate a user |
| GET | `/users/me` | Retrieve authenticated user details |
| POST | `/upload` | Upload an image or video |
| GET | `/feed` | Retrieve social media posts |
| DELETE | `/posts/{post_id}` | Delete an owned post |

## Security and Configuration

- JWT-based authentication for protected endpoints.
- Environment variables for sensitive credentials.
- Database-backed user and post management.
- `.gitignore` configured to exclude environment files, local databases, and Python cache files.

## Learning Outcomes

Through this project, I gained practical experience in:

- Building RESTful APIs using FastAPI.
- Implementing JWT authentication.
- Working with asynchronous database operations.
- Integrating SQLAlchemy with SQLite.
- Handling image and video uploads.
- Integrating third-party cloud storage.
- Connecting a Streamlit frontend with a FastAPI backend.
- Structuring and managing a Python application.

---

**Developer:** Vikash Basfore

**GitHub Repository:** https://github.com/VikashBasfore/simple-social-fastapi