# Book-Review-App

A full-stack web application for book reviews, allowing users to sign in, sign up, view books, write reviews, and manage their own reviews. The application is built with a React frontend and a Spring Boot backend, with data stored in a MySQL database.

## Features
- **User Authentication**: Sign in and sign up pages are implemented using `SignIn.js` and `SignUp.js`.
- **Home Page**: Displays book cards with descriptions and average ratings, implemented using `HomePage.js` and `BookCard.js`.
- **Book Descriptions**: Each book card includes a short description and average rating, included in `BookCard.js`.
- **Review Button**: Each book card has a "Review" button, which navigates to a detailed review page.
- **Review Page**: Users can add their reviews for a specific book on the review page (`ReviewPage.js`).
- **View Others Reviews**: Ability to see reviews by other users for a specific book on the review page.
- **Profile Page**: A dedicated profile page for users to view all their reviews (`ProfilePage.js`).
- **Update and Delete Reviews**: Users can update or delete their own reviews from the profile page.
- **Sorting Books by Rating**: Books are sorted by average rating on the home page (`HomePage.js`).
- **Sorting Reviews by Date**: Reviews are sorted by the most recent on the profile page (`ProfilePage.js`).

## Tech Stack
- **Frontend**: React, Axios, Material-UI
- **Backend**: Spring Boot, Java
- **Database**: MySQL
- **Build Tools**: Maven, npm

## Setup Instructions

### 1. Clone the Repository

  - git clone https://github.com/adevmini/book-review.git
  - cd book-review


### 2. Backend Setup

#### Prerequisites:
- Install IntelliJ IDEA.
- Install Java 17 or later.
- Install MySQL.

#### Steps:
1. Open the backend project in IntelliJ IDEA:
   - Navigate to the `backend` folder.
   - Open it as a Maven project.

2. Create the database in MySQL:
   ```sql
   CREATE DATABASE book_review_app;

   USE book_review_app;

   CREATE TABLE users (
       id BIGINT AUTO_INCREMENT PRIMARY KEY,
       username VARCHAR(100) NOT NULL,
       email VARCHAR(255) NOT NULL,
       password VARCHAR(255) NOT NULL,
       UNIQUE KEY username_unique (username(50)),
       UNIQUE KEY email_unique (email(191))
   );

   CREATE TABLE book_reviews (
       id BIGINT AUTO_INCREMENT PRIMARY KEY,
       title VARCHAR(255) NOT NULL,
       author VARCHAR(255) NOT NULL,
       rating INT NOT NULL CHECK (rating BETWEEN 1 AND 5),
       review_text TEXT NOT NULL,
       date_added TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
       user_id BIGINT NOT NULL,
       CONSTRAINT fk_user FOREIGN KEY (user_id) REFERENCES users (id) ON DELETE CASCADE
   );

   INSERT INTO users (username, email, password)
   VALUES
   ('john_doe', 'john@example.com', 'password123'),
   ('jane_doe', 'jane@example.com', 'password456');

   INSERT INTO book_reviews (title, author, rating, review_text, user_id)
   VALUES
   ('The Great Gatsby', 'F. Scott Fitzgerald', 5, 'A masterpiece of 20th-century literature.', 1),
   ('To Kill a Mockingbird', 'Harper Lee', 4, 'A powerful story about justice and morality.', 2);

   

*Run the backend application:*
   Start the MySQL server.
   In IntelliJ, locate the Book-Review-App-Backend and run it.



**3. Frontend Setup**

*Prerequisites:*
  Install Node.js and npm.

  
*Steps:*

  1. Navigate to the Book-Review-App-Frontend folder:
     'cd Book-Review-App-Frontend'

  2. Install dependencies:
     'npm install'

  3. Start the development server:
     'npm run dev'



# Usage
   1. Sign Up or Sign In using the React app.
   2. View Books on the home page with descriptions and average ratings.
   3. Add Reviews for books by clicking on the "Review" button.
   4. Manage Reviews (view, update, delete) from your profile page.
   5. Sort Books by average rating on the home page.
   6. Sort Reviews by date on the profile page.


# Note on Integration:

Currently, the backend is not generating proper URLs due to an unresolved issue. As a result:

Hardcoded Data: The frontend uses hardcoded book and review data for demonstration purposes.
Demonstration Purpose: While the frontend and backend are designed to integrate, the frontend is temporarily independent of the backend to showcase the UI functionality.





