# TrelloClone

## Overview
TrelloClone is an innovative web-based project management tool inspired by traditional Kanban boards. It enhances team collaboration and efficiency, particularly in software development projects. The application offers an intuitive tracking of tasks across various stages (Todo, Doing, Done) and provides insightful analytics on task duration and team workload.

## Key Features
- **Task Management**: Create, modify, and delete tasks with descriptions, comments, and states.
- **User Assignment**: Assign tasks to team members (John, Paul, George, Ringo).
- **Data-Driven Insights**: Analyze task progression and team performance.
- **Interactive Kanban Board**: Visualize and manage tasks on a dynamic interface.

## Technologies Used
- **Backend**: Spring Boot (RESTful API)
- **Database**: MySQL
- **Frontend**: React (TBD)
- **Testing**: JUnit, Mockito

## Getting Started

### Prerequisites
- Java JDK 11
- MySQL Server
- Node.js and npm (for the frontend)

### Installation
1. **Clone the repository**:
   ```bash
   git clone https://github.com/your_username_/TrelloClone.git
   ```

2. **Configure MySQL**:
   - Start MySQL server and log in to MySQL.
   - Create a new database:
     ```sql
     CREATE DATABASE trello_clone_db;
     ```
   - Set up the database schema:
     ```sql
     USE trello_clone_db;
     CREATE TABLE users (
         id INT AUTO_INCREMENT PRIMARY KEY,
         name VARCHAR(100) NOT NULL
     );
     CREATE TABLE tasks (
         id INT AUTO_INCREMENT PRIMARY KEY,
         description TEXT,
         state ENUM('Todo', 'Doing', 'Done') DEFAULT 'Todo',
         assigned_to INT,
         creation_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
         FOREIGN KEY (assigned_to) REFERENCES users(id)
     );
     ```

3. **Configure Spring Boot Application**:
   - Edit `application.properties` to connect to your MySQL database:
     ```properties
     spring.datasource.url=jdbc:mysql://localhost:3306/trello_clone_db
     spring.datasource.username=[your_mysql_username]
     spring.datasource.password=[your_mysql_password]
     spring.jpa.hibernate.ddl-auto=update
     ```

4. **Run the Backend**:
   ```bash
   cd backend
   ./mvnw spring-boot:run
   ```

5. **Install and Run the Frontend** (assuming React):
   ```bash
   cd frontend
   npm install
   npm start
   ```

### Accessing the Application
Navigate to `http://localhost:3000` to view the TrelloClone interface.

## API Documentation
- **Create Task**: POST `/api/task`
- **Modify Task**: PUT `/api/task/{taskId}`
- **Delete Task**: DELETE `/api/task/{taskId}`
- **Show Board**: GET `/api/board`