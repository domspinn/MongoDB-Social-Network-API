# Social Network API

## Project Description

This project is a RESTful API for a social network application that allows users to share their thoughts, react to friends' thoughts, and manage a friend list. It is built using Node.js, Express.js, and MongoDB with the Mongoose ODM. The API is designed to handle large amounts of unstructured data efficiently, making it suitable for social networking platforms.

## Table of Contents

- [Social Network API](#social-network-api)
  - [Project Description](#project-description)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Usage](#usage)
  - [API Endpoints](#api-endpoints)
    - [Users](#users)
    - [Thoughts](#thoughts)
  - [Models](#models)
    - [User](#user)
    - [Thought](#thought)
    - [Reaction](#reaction)
  - [Technologies Used](#technologies-used)
  - [License](#license)

## Tutorial Video

- Google Drive Link: https://drive.google.com/file/d/18Imax5cD_L955If28NiNA6u68_FLEiu3/view?usp=sharing

## Installation

1. **Clone the repository**

   ```bash
   git clone <your-repository-url>
   cd social-network-api

2. **Install Dependecies**

    ```bash
    npm install

3. **Set up environment variables**

    Create a .env file in the root of your project and add your MongoDB connection string:

    MONGODB_URI=mongodb://localhost/social_network_db

4. **Start MongoDB**    

    Ensure your MongoDB server is running. You can start it locally with:

    ```bash
    mongod

5. **Run the application**

    ```bash
    npm run dev

## Usage

To interact with the API, use an API client such as Postman or Insomnia to test the endpoints. Below are some examples of how to use the API.

## API Endpoints

### Users

- Get all users

GET /api/users

- Get a single user by ID

GET /api/users/:userId

- Create a new user

POST /api/users

- Request Body

json
{
  "username": "newuser",
  "email": "newuser@example.com"
}

- Update a user

PUT /api/users/:userId

- Request Body

json
{
  "username": "updateduser",
  "email": "updateduser@example.com"
}

- Delete a user

DELETE /api/users/:userId

- Add a friend

POST /api/users/:userId/friends/:friendId

- Remove a friend

DELETE /api/users/:userId/friends/:friendId

### Thoughts

- Get all thoughts

GET /api/thoughts

- Get a single thought by ID

GET /api/thoughts/:thoughtId

- Create a new thought

POST /api/thoughts

- Request Body

json
{
  "thoughtText": "Here's a cool thought...",
  "username": "userId"
}

- Update a thought

PUT /api/thoughts/:thoughtId

- Request Body

json
{
  "thoughtText": "Updated thought text"
}

- Delete a thought

DELETE /api/thoughts/:thoughtId

- Add a reaction

POST /api/thoughts/:thoughtId/reactions

- Request Body

{
  "reactionBody": "Nice thought!",
  "username": "anotherUser"
}

- Remove a reaction

DELETE /api/thoughts/:thoughtId/reactions/:reactionId

## Models

### User

- username (string, unique, required)
- email (string, required, unique, must match email format)
- thoughts (array of ObjectIds referencing Thought)
- friends (array of ObjectIds referencing User)

### Thought

- thoughtText (string, required, between 1-280 characters)
- createdAt (date, default value is Date.now)
- username (string, required)
- reactions (array of nested documents created with the reactionSchema)

### Reaction

- reactionId (ObjectId, default value is a new ObjectId)
- reactionBody (string, required, max 280 characters)
- username (string, required)
- createdAt (date, default value is Date.now)

## Technologies Used

- Node.js
- Express.js
- MongoDB
- Mongoose
- Nodemon

## License

This project is licensed under the MIT License.
   
