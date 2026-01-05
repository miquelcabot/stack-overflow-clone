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

## Installation

```bash
# Clone the repository
git clone <repository-url>
cd jira-cli

# Build the project
cargo build --release

# Run the application
cargo run
```

## Usage

```bash
cargo run
```

Once running, the API will be available for HTTP requests (e.g. via `curl`, Postman, or a frontend client).

## Development

### Running Tests

```bash
cargo test
```

### Building for Release

```bash
cargo build --release
```
