# CI/CD Tools and Practices Final Project - JavaScript/Node.js Version

This repository contains a Node.js/Express.js version of the counter service for the Final Project of the Coursera course **CI/CD Tools and Practices**.

## Features

- RESTful API for managing counters
- In-memory storage
- Comprehensive error handling
- Security middleware (Helmet, CORS)
- Logging middleware
- Full test coverage with Jest
- Docker support
- Health check endpoint

## API Endpoints

- `GET /` - Service information
- `GET /health` - Health check
- `GET /counters` - List all counters
- `POST /counters/:name` - Create a new counter
- `GET /counters/:name` - Read a specific counter
- `PUT /counters/:name` - Increment a counter
- `DELETE /counters/:name` - Delete a counter

## Github URL
https://github.com/Nezha99-8/ci-cd-final-project.git
## Setup

1. **Install dependencies:**
   ```bash
   npm install