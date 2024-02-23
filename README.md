# Social Network API

This project is an API for a social network web application where users can share their thoughts, react to friends' thoughts, and create a friend list. It utilizes Express.js for routing, MongoDB for the database, and Mongoose as the ODM (Object Data Modeling) tool.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Routes](#api-routes)
- [Models](#models)
- [Controllers](#controllers)
- [Walkthrough Video](#walkthrough-video)
- [Contributing](#contributing)
- [License](#license)

## Installation

Make sure you have MongoDB installed on your machine. Follow the [MongoDB installation guide](https://docs.mongodb.com/manual/installation/) if you haven't already.

## Usage
The server will start listening on port 3001 by default, or you can specify a different port using the `PORT` environment variable.

## API Routes

### Users

- `GET /api/users`: Get all users.
- `GET /api/users/:id`: Get a single user by ID.
- `POST /api/users`: Create a new user.
- `PUT /api/users/:id`: Update a user by ID.
- `DELETE /api/users/:id`: Delete a user by ID.

#### Friend Routes

- `POST /api/users/:userId/friends/:friendId`: Add a new friend to a user's friend list.
- `DELETE /api/users/:userId/friends/:friendId`: Remove a friend from a user's friend list.

### Thoughts

- `GET /api/thoughts`: Get all thoughts.
- `GET /api/thoughts/:id`: Get a single thought by ID.
- `POST /api/thoughts`: Create a new thought.
- `PUT /api/thoughts/:id`: Update a thought by ID.
- `DELETE /api/thoughts/:id`: Delete a thought by ID.

#### Reaction Routes

- `POST /api/thoughts/:thoughtId/reactions`: Create a reaction for a specific thought.
- `DELETE /api/thoughts/:thoughtId/reactions/:reactionId`: Remove a reaction from a thought.

## Models

### User

- `username`: String (required, unique)
- `email`: String (required, unique, validated)
- `thoughts`: Array of ObjectIDs referencing the Thought model
- `friends`: Array of ObjectIDs referencing other User models

### Thought

- `thoughtText`: String (required, min 1 character, max 280 characters)
- `createdAt`: Date (default: current timestamp)
- `username`: String (required)
- `reactions`: Array of Reaction objects

### Reaction (Subdocument)

- `reactionId`: ObjectId (default: new ObjectId)
- `reactionBody`: String (required, max 280 characters)
- `username`: String (required)
- `createdAt`: Date (default: current timestamp)

## Controllers

- `userController.js`: Handles user-related logic and operations.
- `thoughtController.js`: Handles thought-related logic and operations.

## Authors
Winston Steidley
