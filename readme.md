# SchoolSync

A web-based **School Management System** built with Django to streamline academic and administrative operations while providing dedicated dashboards for **Administrators, Teachers, and Students**.

SchoolSync combines a public-facing school website with an internal management system for handling students, teachers, curriculum, attendance, assessments, fees, academic activities, and other school-related information.

## Features

### Public School Website

The system includes a public-facing website that provides information about the school and its services.

- Home and About pages
- Academic information
- Admission information
- Curriculum and offered subjects
- Academic calendar
- News and events
- Campus information
- Co-curricular activities
- Uniform retailer information
- Careers and job listings
- Alumni page
- Contact form
- Search and page suggestions

### Role-Based Dashboards

SchoolSync supports three main user roles:

- **Admin**
- **Teacher**
- **Student**

After login, users are redirected to their respective dashboards based on their assigned role.

---

## Admin Features

The administrator is responsible for managing the overall academic and administrative structure of the school.

### Student Management

- View registered students
- Add new students
- Assign students to grades
- Create student user accounts
- Store student personal information
- Manage parent/guardian information
- Edit student details

### Teacher Management

- Add and manage teachers
- Create teacher user accounts
- Assign teachers to specific grades and subjects
- View teacher assignments
- Update teacher information

### Curriculum Management

The system organizes academic information through the following relationship:

```text
Grade
  └── Curriculum / Subject
        └── Weekly Course Content
```

Each curriculum can contain:

- Subject name
- Course details
- Syllabus link
- Total number of classes
- Remaining attendance sessions
- Weekly content and learning material

### Fee Management

Administrators can:

- Generate fee challans for students of a specific grade
- Select the fee month
- Define fee amounts
- Track challan payment status
- Update challan information

---

## Teacher Features

Teachers have access to a dedicated dashboard for managing their assigned classes and subjects.

### Subject and Grade Assignment

Teachers are connected to specific:

- Grades
- Curriculums
- Subjects

This relationship ensures that teachers can manage the academic activities associated with their assigned classes.

### Attendance Management

Teachers can:

- Select their assigned grade and subject
- View students in the selected grade
- Mark students as present or absent
- Record attendance for each class session
- Track the remaining number of classes for a curriculum

### Student Grading

Teachers can record student assessment results, including:

- Total marks
- Obtained marks
- Grade
- Subject
- Assessment date

### Curriculum Access

Teachers can view:

- Their assigned grades
- Assigned subjects
- Students associated with those classes

---

## Student Features

Students have access to their own dashboard where they can view academic and personal information.

### Student Profile

Students can access:

- Personal information
- Grade information
- Parent/guardian details

### Attendance Tracking

Students can view attendance information for each subject, including:

- Subject name
- Assigned teacher
- Attendance percentage
- Remaining classes

### Course Information

Students can access detailed course information, including:

- Subject details
- Teacher information
- Weekly course content

### Grades and Results

Students can view their assessment results, including:

- Total marks
- Obtained marks
- Percentage
- Grade
- Pass/Fail status

### Fee Challans

Students can:

- View their fee challans
- Check payment status
- Mark challans as paid

---

## Database Design

The system is designed around several core entities.

### User

The `User` model manages authentication and role information.

```text
User
├── Student
└── Teacher
```

Each user has one of the following roles:

- Student
- Teacher
- Admin

### Academic Structure

```text
Grade
  │
  ├── Students
  │
  └── Curriculum
        │
        ├── Weekly Content
        ├── Quizzes
        └── Teacher Assignment
```

### Teacher Assignment

The `TeacherGradeCurriculum` model connects:

```text
Teacher + Grade + Curriculum
```

This allows the system to track which teacher is responsible for teaching a particular subject to a particular grade.

### Student Information

Each student is associated with:

- A user account
- A grade
- Parent or guardian information
- Attendance records
- Quiz results
- Fee challans

---

## REST API

SchoolSync also includes a Django REST Framework API layer.

The API is used to provide and consume data for different parts of the application, including:

- Grades
- Curriculum information
- Teacher assignments
- Events
- Retailers
- Jobs
- Academic calendar
- Contact submissions

The web application uses these API endpoints to retrieve and display dynamic information on the frontend.

---

## Technology Stack

### Backend

- Python
- Django
- Django REST Framework

### Database

- SQLite

### Frontend

- HTML
- CSS
- JavaScript
- Django Templates

### Additional Libraries

- Requests

---

## Project Structure

```text
SchoolSync/
│
├── Pipfile
├── Pipfile.lock
│
└── se_project/
    │
    ├── manage.py
    ├── db.sqlite3
    │
    ├── se_project/
    │   ├── settings.py
    │   ├── urls.py
    │   ├── wsgi.py
    │   └── asgi.py
    │
    ├── sms/
    │   ├── models.py
    │   ├── views.py
    │   ├── api_views.py
    │   ├── serializers.py
    │   ├── urls.py
    │   ├── form.py
    │   ├── admin.py
    │   │
    │   ├── migrations/
    │   ├── static/
    │   └── templates/
    │       └── sms_app/
    │
    └── media/
```

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/alit9876/SchoolSync.git
```

### 2. Navigate to the project directory

```bash
cd SchoolSync
```

### 3. Install dependencies

If using Pipenv:

```bash
pipenv install
pipenv shell
```

Alternatively, install the required dependencies manually:

```bash
pip install django djangorestframework requests pillow
```

### 4. Navigate to the Django project

```bash
cd se_project
```

### 5. Apply migrations

```bash
python manage.py migrate
```

### 6. Run the development server

```bash
python manage.py runserver
```

Open the application in your browser at:

```text
http://127.0.0.1:8000/
```

## Future Improvements

Potential improvements for SchoolSync include:

- Secure password hashing using Django's authentication system
- Improved role-based access control
- Real online payment gateway integration
- Email notifications
- Parent dashboard
- Assignment and homework management
- Exam and report card generation
- Timetable management
- Improved API authentication
- Cloud database support
- Deployment configuration

## Author

**Ali Tariq**

## License

This project is intended for educational and learning purposes.