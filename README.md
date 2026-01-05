# StackOverflow Clone API

A backend API for a StackOverflow-like application, built in **Rust** using **Axum** and **PostgreSQL**, focused on learning real-world backend development patterns.

## Overview

This project implements a RESTful API for a simplified StackOverflow-style platform. The core functionality allows users to create, retrieve, and delete **Questions** and **Answers**.

## Features

- **Question Management**
  - Create questions
  - Retrieve questions
  - Delete questions

- **Answer Management**
  - Create answers for questions
  - Retrieve answers
  - Delete answers

- **REST API**
  - HTTP-based API using Axum
  - Clear separation between handlers, models, and persistence

- **Persistent Storage**
  - PostgreSQL-backed storage
  - SQL schema design
  - Data access via DAOs

- **Test-Driven Development**
  - Unit tests provided for guidance
  - Focus on correctness and maintainability

## Learning Objectives

This project is designed to help you learn and practice:

- Designing and building APIs
- Using a backend framework (**Axum**)
- Designing SQL schemas and models
- Working with **PostgreSQL**
- Implementing CRUD operations
- Using the DAO (Data Access Object) pattern
- Writing testable, maintainable Rust code
- Organizing code using Rust modules
- Navigating and contributing to an existing codebase

## Project Structure

The project is divided into **stages**, each building upon the previous one:

### Stage 1 – API Design
- Define API endpoints
- Implement stub handlers
- Define request and response models

### Stage 2 – Persistence
- Set up PostgreSQL
- Create database schema
- Implement DAOs for questions and answers

### Stage 3 – Full Integration
- Connect API handlers to DAOs
- Enable full create, retrieve, and delete functionality
- Complete a fully working API

## Prerequisites

- Rust and Cargo installed (visit [rustup.rs](https://rustup.rs/))
- PostgreSQL installed and running
- `sqlx-cli` for database migrations

## Installation

### 1. Clone the repository

```bash
git clone <repository-url>
cd stack-overflow-clone
```

### 2. Install sqlx-cli

```bash
cargo install sqlx-cli --no-default-features --features postgres
```

### 3. Set up PostgreSQL

Make sure PostgreSQL is running. You can start it via:

**Using Homebrew (macOS):**
```bash
brew services start postgresql
```

**Using Docker:**
```bash
docker run -d \
  --name postgres \
  -e POSTGRES_PASSWORD=your_password \
  -p 5432:5432 \
  postgres:latest
```

### 4. Configure environment variables

Create a `.env` file in the project root:

```bash
# .env
DATABASE_URL=postgres://username:password@localhost:5432/database_name
```

Replace `username`, `password`, and `database_name` with your PostgreSQL credentials.

### 5. Create the database

```bash
# Connect to PostgreSQL and create the database
createdb database_name

# Or using psql:
psql -U postgres -c "CREATE DATABASE database_name;"
```

### 6. Run migrations

```bash
sqlx migrate run
```

This will create the `questions` and `answers` tables in your database.

### 7. Build the project

```bash
cargo build
```

### 8. Run the application

```bash
cargo run
```

## Usage

Once the application is running, the API will be available at `http://127.0.0.1:8000`.

### API Endpoints

**Questions:**
- `POST /question` - Create a new question
- `GET /questions` - Retrieve all questions
- `DELETE /question` - Delete a question

**Answers:**
- `POST /answer` - Create a new answer
- `GET /answers` - Retrieve answers for a question
- `DELETE /answer` - Delete an answer

### Example Requests

**Create a question:**
```bash
curl -X POST http://127.0.0.1:8000/question \
  -H "Content-Type: application/json" \
  -d '{"title": "How do I learn Rust?", "description": "I want to learn Rust programming"}'
```

**Get all questions:**
```bash
curl http://127.0.0.1:8000/questions
```

## Database Schema

The application uses two main tables:

**questions:**
- `question_uuid` (UUID, Primary Key)
- `title` (VARCHAR)
- `description` (VARCHAR)
- `created_at` (TIMESTAMP)

**answers:**
- `answer_uuid` (UUID, Primary Key)
- `question_uuid` (UUID, Foreign Key → questions)
- `content` (VARCHAR)
- `created_at` (TIMESTAMP)

## Development

### Running Tests

```bash
cargo test
```

### Building for Release

```bash
cargo build --release
```
