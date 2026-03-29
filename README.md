# 🎯 Trivia API

![Flask](https://img.shields.io/badge/Flask-2.2-blue?logo=flask)
![React](https://img.shields.io/badge/React-16-61DAFB?logo=react)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-12+-336791?logo=postgresql)
![License](https://img.shields.io/badge/License-MIT-green)

A full-stack trivia web application built with **Flask** and **React**. Manage trivia questions by category and difficulty, search the question bank, and play a quiz game — all from a clean browser UI.

**Features:**

1. Display questions (all or by category) with question, category, difficulty, and show/hide answer.
2. Delete questions.
3. Add questions with required question and answer text.
4. Search for questions based on a text query string.
5. Play the quiz game, randomizing either all questions or within a specific category.

## Getting Started

### Prerequisites

- Python 3.7+
- Node.js & npm
- PostgreSQL

### Installing Dependencies

#### Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

#### Frontend

```bash
cd frontend
npm install
```

### Virtual Environment

Working within a virtual environment is recommended.

### Database Setup

With Postgres running, restore the database using the provided seed file:

```bash
createdb trivia
psql trivia < backend/trivia.psql
```

### Running the Server

From the `backend` directory:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

### Running the Frontend

```bash
cd frontend
npm start
```

Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

### Testing

```bash
dropdb trivia_test
createdb trivia_test
psql trivia_test < backend/trivia.psql
cd backend && python test_flaskr.py
```

## API Reference

- **Base URL:** `http://127.0.0.1:5000/`
- **Authentication:** None (not yet implemented)

### Error Handling

Errors are returned as JSON:

```json
{
  "success": false,
  "error": 422,
  "message": "Unprocessable entity"
}
```

Error codes: `400`, `404`, `422`, `500`

### Endpoints

#### GET /categories

Returns all categories.

```bash
curl http://127.0.0.1:5000/categories
```

#### GET /questions

Returns paginated questions. Use `?page=` query parameter.

```bash
curl http://127.0.0.1:5000/questions?page=1
```

#### DELETE /questions/<id\>

Deletes a question by id.

```bash
curl http://127.0.0.1:5000/questions/6 -X DELETE
```

#### POST /questions

Creates a new question or searches (if body contains `searchTerm`).

```bash
curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" \
  -d '{"question": "...", "answer": "...", "difficulty": 3, "category": "6"}'
```

#### GET /categories/<id\>/questions

Returns questions for a specific category.

```bash
curl http://127.0.0.1:5000/categories/1/questions
```

#### POST /quizzes

Returns a random question not in `previous_questions` for the given category.

```bash
curl http://127.0.0.1:5000/quizzes -X POST -H "Content-Type: application/json" \
  -d '{"previous_questions": [5, 9], "quiz_category": {"type": "History", "id": "4"}}'
```

## Authors

- **Sanjay Santhanam** — API, test suite, and project maintenance
- **Udacity** — Starter files and frontend scaffold

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
