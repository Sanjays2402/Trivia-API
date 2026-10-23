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

## Terms & Disclaimer

By using this project you agree to the following.

- **No warranty.** This software is provided "as is", without warranty of any kind, express or implied, including merchantability, fitness for a particular purpose, and non-infringement.
- **No liability.** To the maximum extent permitted by law, the author and contributors are not liable for any claim, loss, or damage (direct, indirect, incidental, or consequential, including lost data or profits) arising from its use.
- **Your responsibility.** You use it at your own risk and are responsible for complying with the laws that apply to you.
- **Your data.** Keep backups; data loss is possible. If you process other people's personal information, you are responsible for complying with privacy laws such as US state privacy laws (e.g. CCPA), PIPEDA and Quebec's Law 25 (Canada), and the Digital Personal Data Protection Act, 2023 (India).
- **Coursework.** This was built for a course or program. Starter code, project specifications, and datasets may belong to the course provider and are included only for learning. Not affiliated with or endorsed by the provider. If you are taking the same course, follow its academic-integrity rules; do not submit this as your own work.
- **Third parties.** Names, logos, APIs, and services of others belong to their owners and are used for identification only; no affiliation or endorsement is implied.
- **Your statutory rights.** Nothing here limits rights that cannot be waived by agreement, including under consumer-protection laws in the USA, Canada (including Quebec), and India (Consumer Protection Act, 2019).
- **License.** Use, copying, and distribution are governed by the [LICENSE](LICENSE) file; if anything here conflicts with it, the license controls.

## Content, Assets & Fair Use

- **Original work.** Unless noted otherwise (including below), the code, text, design, and images in this repository were created by the author.
- **Libraries, fonts, and icons.** Third-party libraries, fonts (for example Google Fonts), and icon sets belong to their creators and are used under their own licenses; see the dependency manifests and each source for terms.
- **Logos, brands, and screenshots.** Third-party names, logos, and screenshots appear only to identify or describe their products (nominative use). They remain the property of their owners and do not imply affiliation or endorsement.
- **Ideas and inspiration.** Where this project is inspired by another product, game, or idea, it is an independent implementation. It borrows only general ideas, mechanics, or styles, which are not anyone's exclusive property, and is meant to contain no third-party code or artwork used without permission.
- **Datasets.** Datasets belong to their publishers and are used under their licenses or terms for learning and research. They may be excluded from the repository; get them from the original source and follow its license.
- **Fair use and fair dealing.** Any third-party material is used in limited ways for purposes such as education, research, review, commentary, or identification, relying on fair use in the USA (17 U.S.C. § 107), fair dealing in Canada (Copyright Act, ss. 29–29.2), and fair dealing in India (Copyright Act, 1957, s. 52), where they apply.
- **Concerns and takedown requests.** If you own rights in something here and believe it is used improperly, [open an issue](https://github.com/Sanjays2402/Trivia-API/issues) or contact the author through their GitHub profile with a link to the material and your claim. It will be reviewed promptly and credited, changed, or removed as appropriate. You may also use GitHub's DMCA process.
- **Contributions.** By contributing, you confirm you have the right to submit your contribution and agree it is licensed under this repository's license.
