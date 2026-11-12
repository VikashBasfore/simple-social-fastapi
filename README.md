# Simple Social

A media-sharing web application built using **FastAPI** and **Streamlit**. Users can create an account, log in securely, upload images or videos with captions, view posts in a feed, and delete their own posts.

## Features

- User registration and login
- JWT-based authentication
- Protected API endpoints
- Image and video uploads
- Media storage using ImageKit
- Post metadata stored in SQLite
- Feed displaying posts, captions, authors, and dates
- Delete functionality for post owners
- Interactive API documentation with Swagger UI

## Tech Stack

| Component | Technology |
|---|---|
| Backend | FastAPI |
| ASGI Server | Uvicorn |
| Frontend | Streamlit |
| Database | SQLite |
| ORM | SQLAlchemy |
| Authentication | FastAPI Users, JWT |
| Data Validation | Pydantic |
| Media Storage | ImageKit |
| Package Management | uv |

## Project Structure

```text
FastAPI-Tutorial/
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
├── frontend.py
├── main.py
├── pyproject.toml
├── uv.lock
├── .env
├── .gitignore
└── test.db
```

## How It Works

1. Users register or log in through the Streamlit interface.
2. FastAPI authenticates users and generates a JWT access token.
3. Streamlit sends the token in the authorization header for protected API requests.
4. Users upload images or videos with optional captions.
5. FastAPI uploads media files to ImageKit.
6. ImageKit returns a media URL.
7. Post details and media URLs are stored in the SQLite database using SQLAlchemy.
8. The Feed API retrieves posts and associated user information.
9. Streamlit displays posts, images, videos, and captions.
10. Users can delete their own posts.

## Getting Started

### Prerequisites

- Python
- uv
- ImageKit account

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd <your-project-folder>
```

### 2. Install Dependencies

```bash
uv sync
```

### 3. Configure Environment Variables

Create a `.env` file in the project root.

```env
IMAGEKIT_PRIVATE_KEY=your_private_key
IMAGEKIT_PUBLIC_KEY=your_public_key
IMAGEKIT_URL=your_imagekit_url_endpoint
```

Also configure the authentication secret required by your application.

**Important:** Never upload your `.env` file or API credentials to GitHub.

### 4. Start the FastAPI Backend

```bash
uv run python main.py
```

Backend URL:

http://127.0.0.1:8000

Swagger API Documentation:

http://127.0.0.1:8000/docs

### 5. Start the Streamlit Frontend

Open another terminal:

```bash
uv run python -m streamlit run frontend.py
```

Frontend URL:

http://localhost:8501

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/auth/register` | Register a new user |
| POST | `/auth/jwt/login` | Authenticate and generate JWT |
| GET | `/users/me` | Get logged-in user details |
| POST | `/upload` | Upload media and create a post |
| GET | `/feed` | Retrieve posts |
| DELETE | `/posts/{post_id}` | Delete a user's own post |

## Security

Add the following entries to `.gitignore`:

```gitignore
.env
.venv/
__pycache__/
*.py[cod]
test.db
.streamlit/secrets.toml
```

Never expose API keys, database credentials, or JWT secrets in a public repository.

## What I Learned

- Building REST APIs using FastAPI
- Creating GET, POST, and DELETE endpoints
- Working with Pydantic schemas
- Using dependency injection with `Depends`
- Connecting databases using SQLAlchemy
- Implementing JWT authentication
- Protecting API endpoints
- Uploading and retrieving media using ImageKit
- Connecting Streamlit with FastAPI
- Debug