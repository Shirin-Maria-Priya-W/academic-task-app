# Academic Task Management System

A comprehensive task management system designed specifically for academic environments, built with Spring Boot, MySQL, and modern web technologies.

## Features

### Core Task Management
- ✅ Create, edit, and delete academic tasks
- 🎯 Priority levels (Low, Medium, High, Urgent)
- 📚 Custom categories with icons and colors
- 📅 Deadline tracking with overdue warnings
- ✔️ Task completion with timestamp tracking

### Subtasks System
- 📝 Optional subtasks for complex assignments
- 📊 Progress tracking with visual progress bars
- 🔄 Auto-completion of main task when all subtasks are done
- 🎛️ Individual subtask management (add, complete, delete)

### Advanced Features
- 🔥 Streak tracking with motivational messages
- 📈 Comprehensive statistics dashboard
- 🎨 Custom category creation with emoji icons
- 📋 Table view with configurable columns
- 📤 CSV export functionality
- 🔍 Advanced filtering and sorting options

### User Experience
- 📱 Responsive design for all devices
- 🎭 Beautiful animations and micro-interactions
- 🌟 Achievement system with streak levels
- 📊 Visual progress indicators
- 🎯 Smart task organization by category

## Technology Stack

### Backend
- **Spring Boot 2.7.0** - Main framework
- **Spring Data JPA** - Database abstraction
- **MySQL 8.0** - Primary database
- **Maven** - Dependency management
- **Java 11** - Programming language

### Frontend
- **HTML5** - Structure and semantics
- **CSS3** - Styling with custom properties and grid/flexbox
- **Vanilla JavaScript** - Interactive functionality
- **Font Awesome** - Icon library
- **Responsive Design** - Mobile-first approach

### DevOps
- **Jenkins** - CI/CD pipeline
- **Maven** - Build automation
- **MySQL** - Production database

## Project Structure

```
academic-task-manager/
├── src/main/java/com/academic/taskmanager/
│   ├── model/
│   │   ├── Task.java
│   │   ├── SubTask.java
│   │   └── Category.java
│   ├── repository/
│   │   ├── TaskRepository.java
│   │   ├── SubTaskRepository.java
│   │   └── CategoryRepository.java
│   ├── service/
│   │   ├── TaskService.java
│   │   └── CategoryService.java
│   ├── controller/
│   │   ├── TaskController.java
│   │   └── CategoryController.java
│   └── TaskManagerApplication.java
├── src/main/resources/
│   └── application.properties
├── html-frontend/
│   ├── index.html
│   ├── styles.css
│   └── script.js
├── sql-schema/
│   └── schema.sql
├── jenkins/
│   └── Jenkinsfile
└── pom.xml
```

## Setup Instructions

### Prerequisites
- Java 11 or higher
- Maven 3.6+
- MySQL 8.0+
- Jenkins (for CI/CD)

### Database Setup
1. Install MySQL and create a database:
```sql
CREATE DATABASE academic_task_manager;
```

2. Update `application.properties` with your database credentials:
```properties
spring.datasource.username=your_username
spring.datasource.password=your_password
```

3. Run the schema script:
```bash
mysql -u your_username -p academic_task_manager < sql-schema/schema.sql
```

### Backend Setup
1. Clone the repository
2. Navigate to the project directory
3. Install dependencies:
```bash
mvn clean install
```

4. Run the application:
```bash
mvn spring-boot:run
```

The backend will start on `http://localhost:8080`

### Frontend Setup
1. Serve the HTML files using any web server
2. For development, you can use Python's built-in server:
```bash
cd html-frontend
python -m http.server 3000
```

3. Open `http://localhost:3000` in your browser

### Jenkins Setup
1. Create a new Jenkins pipeline job
2. Point it to your repository
3. Use the provided `Jenkinsfile`
4. Configure the following credentials in Jenkins:
   - `mysql-root-password`: MySQL root password

## API Endpoints

### Tasks
- `GET /api/tasks` - Get all tasks
- `POST /api/tasks` - Create new task
- `PUT /api/tasks/{id}` - Update task
- `DELETE /api/tasks/{id}` - Delete task
- `PATCH /api/tasks/{id}/toggle` - Toggle task completion
- `GET /api/tasks/stats` - Get task statistics
- `GET /api/tasks/streak` - Get streak data
- `GET /api/tasks/filter` - Get filtered tasks

### Subtasks
- `POST /api/tasks/{id}/subtasks` - Add subtask
- `PATCH /api/tasks/subtasks/{id}/toggle` - Toggle subtask completion
- `DELETE /api/tasks/subtasks/{id}` - Delete subtask

### Categories
- `GET /api/categories` - Get all categories
- `POST /api/categories` - Create new category
- `DELETE /api/categories/{id}` - Delete category

## Database Schema

### Tables
- **categories**: Store task categories with icons and colors
- **tasks**: Main task information with foreign key to categories
- **subtasks**: Optional subtasks linked to main tasks

### Key Features
- Foreign key constraints for data integrity
- Indexes for optimal query performance
- Default categories automatically created
- Cascade delete for related records

## Development Workflow

### Two-Person Development Strategy

**Person A - Backend Developer:**
1. Implement entity models and relationships
2. Create repository interfaces with custom queries
3. Build service layer with business logic
4. Develop REST API controllers
5. Write unit and integration tests

**Person B - Frontend Developer:**
1. Design responsive HTML structure
2. Implement CSS with modern design principles
3. Create interactive JavaScript functionality
4. Integrate with backend APIs
5. Optimize user experience and accessibility

### Git Workflow
1. Create feature branches for each component
2. Use pull requests for code review
3. Maintain separate branches for frontend/backend development
4. Merge to main branch after testing

## Testing Strategy

### Backend Testing
- Unit tests for service layer methods
- Integration tests for repository queries
- API endpoint testing with MockMvc
- Database testing with H2 in-memory database

### Frontend Testing
- Manual testing across different browsers
- Responsive design testing on various devices
- API integration testing
- User experience testing

## Deployment

### Production Deployment
1. Build the JAR file: `mvn clean package`
2. Deploy to application server
3. Configure production database
4. Set up reverse proxy (nginx/Apache)
5. Configure SSL certificates

### Jenkins CI/CD
The included Jenkinsfile provides:
- Automated building and testing
- Database schema deployment
- Application deployment
- Health checks
- Email notifications

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.
