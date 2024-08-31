# SurveyGram Platform

SurveyGram is an innovative survey platform built with a Django backend and a React frontend. It allows companies to post surveys and users to complete them in exchange for various rewards, including cash, coupons, and credits. This platform aims to bridge the gap between businesses seeking valuable insights and users who wish to earn rewards for their time and opinions.

## Table of Contents
- [Important Note](#important-note)
- [Team SurveyGram](#meet-the-team)
- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
  - [Prerequisites](#prerequisites)
  - [Clone the Repository](#clone-the-repository)
  - [Backend Setup](#backend-setup)
  - [Frontend Setup](#frontend-setup)
- [Configuration](#configuration)
  - [Environment Variables](#environment-variables)
  - [Django Settings](#django-settings)
  - [React Settings](#react-settings)
- [Database Design](#database-design)
  - [Schema Overview](#schema-overview)
  - [Tables and Relationships](#tables-and-relationships)
  - [Indexing and Optimization](#indexing-and-optimization)
- [State Management](#state-management)
- [Authentication and Authorization](#authentication-and-authorization)
- [API Documentation](#api-documentation)
  - [Endpoints](#endpoints)
  - [Request and Response Examples](#request-and-response-examples)
- [UI/UX Design](#uiux-design)
  - [User Interface](#user-interface)
  - [User Experience](#user-experience)
- [Future Deployment](#deployment)
  - [Deployment for AWS Deployment](#deployment-on-aws)
  - [Docker Setup for centralization](#docker-setup)
- [Testing](#testing)
  - [Unit Testing](#unit-testing)
  - [Integration Testing](#integration-testing)
- [Acknowledgments](#acknowledgments)
- [Documents](#documents)

## Important Note

Currently SurveyGram is not licensed under any specific clause. To protect it from piracy and intellectual theft, I, Sumeet Katke, the team leader and owner of this repository, have decided not to disclose the source code. The repository includes proprietary components such as a `Custom State Manager`, `Custom SurveyCard Loading`, `Data Security Methodologies`, and `Database Schema` and many others, which constitute as my intellectual property. We will soon make it open-source and allow contributers to help us enhance our platform.

_The usage methods provided further may fail due to unavalabilty of source code in the repository._
### Educational Use
However, to support individuals who aim to use this for educational purposes, exceptions may be considered. If you are interested in using this repository for learning, please feel free to contact me via [LinkedIn](www.linkedin.com/in/sumeetkatke) or [email](mailto:snkatke9874@gmail.com). Your interest and commitment to learning are always appreciated.

# Meet the Team
## Guide:
###  Miss. Martha Simon [[LinkedIn]](https://www.linkedin.com/in/martha-simon-5511141bb/)
- Assistant Professor at MVJ College of Engineering
- Team guide and supervisor. 
- Continuous support and collaborative brainstorming, which provided invaluable insights and significantly contributed to the development process.
## Team:
### 1. Sumeetkumar Katke [[GitHub]](https://github.com/Sumeet-katke) [[LinkedIn]](www.linkedin.com/in/sumeetkatke)
- `Team leader` and core developer. 
- Handled complete `Database designing` with normalization upto Elementary Key Normalization Form (EKNF)
- Developed the entire `Authentication module`
- Responsible for `CORS`
- Built the entire Backend.
- Developed custom state manager `stateContext` for ReactJS
- Lead the front-end team while handling complete respondent module 
- Will Handle the complete `Docker` setup
---
### 2. Pragati Talekar [[LinkedIn]](https://www.linkedin.com/in/pragatitalekar/)

- Responsible for Wireframes and Mockups
- Key role in Front-end Development
- Handled majority of the styling

### 3. Suren Joshi [[LinkedIn]](https://www.linkedin.com/in/surenjoshi/)

- Assistance in data profiling segment
- Tester 

### 4. Vaibhav Kumar P [[LinkedIn]](). 
- Responsible for `Data Profiling Module` in current version
- lead the `analysis module` team for SurveyGram 2.0
- Tester


## Overview

SurveyGram is a comprehensive survey platform that allows businesses to create and manage surveys while enabling users to participate in these surveys for rewards. The platform ensures a seamless and engaging experience for both companies and users through its user-friendly interface and robust backend system.

## Features

- **User Registration and Authentication**: Secure sign-up and login functionality with JWT-based authentication.
- **Survey Management**: Companies can create, edit, and manage surveys, including setting rewards and target audiences.
- **User Dashboard**: Users can browse available surveys, view their history, track rewards, and manage their profiles.
- **Real-time Analytics**: Companies receive real-time data on survey completions, user engagement, and insights.
- **Responsive Design**: The platform is fully responsive, ensuring a consistent experience across devices.
- **State Management**: Efficient state management using custom state manager `StateContext` in React to handle various user and company operations.
- **Reward System**: Users earn rewards like cash, coupons, or credits for completing surveys.
- **Data Security**: Implemented data protection mechanisms to ensure user data privacy.

## Technologies Used

- **Frontend**: React.js, HTML5, CSS3, JavaScript
- **Backend**: Django, Django REST Framework
- **Database**: PostgreSQL
- **State Management**: React Context API (`StateContext`)
- **Authentication**: JSON Web Tokens (JWT)
- **Deployment**: Docker, AWS
- **Version Control**: Git, GitHub
- **Testing**: Jest (for React), PyTest (for Django)

## Installation

### Prerequisites

Before you begin, ensure you have the following installed:

- Python 3.8+
- Node.js 14+
- PostgreSQL
- Docker (optional for containerization)
- Git

### Clone the Repository

```bash
git clone https://github.com/yourusername/surveygram.git
cd surveygram
```
### Backend Setup

1. **Create a virtual environment:**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

2. **Install dependencies:**

   ```bash
   pip install -r backend/requirements.txt
   ```

3. **Apply migrations:**

   ```bash
   python manage.py migrate
   ```

4. **Create a superuser:**

   ```bash
   python manage.py createsuperuser
   ```

5. **Run the development server:**

   ```bash
   python manage.py runserver
   ```

### Frontend Setup

1. **Navigate to the frontend directory:**

   ```bash
   cd frontend
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Start the development server:**

   ```bash
   npm start
   ```

## Configuration

### Environment Variables

Create a `.env` file in the `backend` directory and populate it with the following:

```env
SECRET_KEY=your_secret_key
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
DATABASE_URL=postgresql://user:password@localhost:5432/surveygram
JWT_SECRET_KEY=your_jwt_secret_key
```

### Django Settings

Configure your `settings.py` in the Django project to ensure all necessary settings are correctly configured, such as `INSTALLED_APPS`, `MIDDLEWARE`, `DATABASES`, `AUTHENTICATION_BACKENDS`, etc.

### React Settings

Ensure that API endpoint URLs and other configuration options are correctly set in the React frontend, typically in the `src/config.js` file.

## Database Design

### Schema Overview

The SurveyGram platform uses a relational database structure with the following primary entities:

- **User**: Stores user details and authentication information.
- **Company**: Stores company details and survey metadata.
- **Survey**: Contains survey questions, target audience, and reward details.
- **Response**: Records user responses to surveys.
- **Reward**: Tracks rewards issued to users for completing surveys.

### Tables and Relationships

- **User Table**: Contains fields like `id`, `username`, `email`, `password`, and `profile`.
- **Company Table**: Contains fields like `id`, `name`, `industry`, `contact_info`, and `user_id`.
- **Survey Table**: Contains fields like `id`, `title`, `description`, `company_id`, `created_at`, `updated_at`, `reward_type`, `reward_amount`.
- **Response Table**: Contains fields like `id`, `survey_id`, `user_id`, `response_data`, `submitted_at`.
- **Reward Table**: Contains fields like `id`, `user_id`, `reward_type`, `reward_amount`, `issued_at`.

### Indexing and Optimization

- **Indexing**: Key indexes are applied to frequently queried fields such as `user_id`, `company_id`, and `survey_id`.
- **Optimization**: Query optimization techniques, such as `select_related` and `prefetch_related`, are employed to minimize database hits.


## State Management

State in the SurveyGram frontend is managed using the React Context API (`StateContext`). The state context handles operations like user authentication, survey navigation, and user response tracking.

## Authentication and Authorization

The platform uses JWT-based authentication for secure login and token management. Permissions and access levels are enforced in both the backend and frontend to ensure that only authorized users can perform certain actions.

## API Documentation

### Endpoints

SurveyGram's API provides a range of endpoints for interacting with the platform. Below are some of the key endpoints:

- **User Registration**: `POST /api/auth/register/`
- **User Login**: `POST /api/auth/login/`
- **Create Survey**: `POST /api/surveys/`
- **Get Surveys**: `GET /api/surveys/`
- **Submit Response**: `POST /api/surveys/{id}/response/`
- **Get User Rewards**: `GET /api/user/rewards/`

### Request and Response Examples

#### User Registration

```json
POST /api/auth/register/

Register-company

{
    "email":"company@surveygram.com",
    "userId":"userIdCompany",
    "first_name":"companyName",
    "last_name":"",
    "password":"12345",
    "roleId": "2",
    "url":"www.esport.com",
    "sector":"clothing"

}

Response:

{
  "message": "User registered successfully",
  "user_id": 1
}
```

#### Create Survey

```json
POST /api/surveys/

{
    "title": "Customer Satisfaction Survey 2",
    "rewardType": "coupons",
    "rewardQuantity": 100,
    "startdate": "2024-08-10",
    "deadLine": "2024-08-20",
    "age_groupFrom": 18,
    "age_groupTo": 35,
    "region": "North America",
    "description": "This survey aims to gather customer satisfaction feedback.",
    "no_of_question": 3,
    "TypeOfQuestion": "Multiple Choice",
    "questions": [
        {
            "question": "How satisfied are you with our service?",
            "options": ["Very satisfied", "Satisfied", "Neutral", "Dissatisfied", "Very dissatisfied"]
        },
        {
            "question": "How likely are you to recommend our service to others?",
            "options": ["Very likely", "Likely", "Neutral", "Unlikely", "Very unlikely"]
        },
        {
            "question": "What can we improve?",
            "options": ["Customer support", "Product quality", "Delivery time", "Pricing", "Other"]
        }
    ]
}

Response:

{
  "message": "Survey created successfully",
  "survey_id": 1
}
```

## UI/UX Design

### User Interface

The user interface is designed to be intuitive and user-friendly. The main components include:

- **Feed Page**: Displays available surveys in a card format, similar to Instagram.
- **Survey Detail Page**: Provides detailed information about a specific survey, including reward details and completion time.
- **User Dashboard**: Shows user activity, rewards, and survey history.

### User Experience

The user experience focuses on providing a seamless flow between discovering surveys, participating, and receiving rewards. The platform is designed to be engaging, with minimal friction in the user journey.

## Deployment

### Deployment on AWS

SurveyGram 2.0 will be built considering it's deployed on AWS using services like EC2, RDS (for PostgreSQL), and S3.

 The platform shall be containerized using Docker for easy deployment and scaling.

### Docker Setup

A `Dockerfile` and `docker-compose.yml` will included in the repository for setting up the platform in a containerized environment.

## Testing

### Unit Testing
The platform was currently tested manually considering the time and resource constraints but as we grow the test cases shall be created and implemented at the earliest. 


Unit tests shall be written for both frontend and backend components to ensure individual units of code work as expected.

- **Frontend**: Jest shall be used for testing React components.
- **Backend**: PyTest and similar tools will be used for testing Django models, views, and serializers. Major focus will be in testing this backend since we prioritize the user data highly

### Integration Testing

Integration tests are to be conducted to ensure that different modules of the platform interact correctly.

## Acknowledgments

We would like to thank all contributors, users, and supporters of SurveyGram. Your feedback and contributions are invaluable to the continuous improvement of this platform.

## Documents
A detailed report and several other key documentations including the schematics  are included for an in-depth understanding. Please refer them

--- 

Feedbacks, suggestions or contributions are always welcomed!! 