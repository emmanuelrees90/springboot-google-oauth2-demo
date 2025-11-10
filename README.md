# Spring Boot Google OAuth2 Demo 🚀

A simple demo application showing how to integrate **Google OAuth 2.0 login** using **Spring Boot 3** and **Spring Security**.  
After logging in with your Google account, the app returns your profile information (name, email, and picture) in JSON format.

---

## 📸 Demo Flow

1. User clicks “Sign in with Google”.
2. The app redirects to the Google OAuth 2.0 consent screen.
3. After successful authentication, Google redirects back to your app.
4. Spring Security handles the OAuth callback and populates the authenticated `OAuth2User`.
5. The `/user` endpoint returns user details as JSON.

---

## 🧱 Tech Stack

- **Spring Boot 3**
- **Spring Security (OAuth2 Client)**
- **Maven**
- **Java 17**
- (Optional) **Thymeleaf** or any frontend (Angular/React) to consume the API

---

## 📂 Project Structure

springboot-google-oauth2-demo/
├── src/
│ ├── main/
│ │ ├── java/com/example/oauthdemo/
│ │ │ ├── OauthDemoApplication.java
│ │ │ ├── config/SecurityConfig.java
│ │ │ └── controller/UserController.java
│ │ └── resources/
│ │ ├── application.yml # (gitignored for safety)
│ │ ├── application-template.yml
│ │ └── templates/ # Optional (for HTML login pages)
├── pom.xml
├── .gitignore
└── README.md


---

## ⚙️ Setup Instructions

### 1. Clone the Repository

git clone https://github.com/<your-username>/springboot-google-oauth2-demo.git
cd springboot-google-oauth2-demo


### 2. Create a Google OAuth 2.0 Client

Go to Google Cloud Console

Create a new project (or use an existing one)

Navigate to APIs & Services → Credentials → Create Credentials → OAuth Client ID

Choose Web application

Under Authorized redirect URIs, add:
http://localhost:8080/login/oauth2/code/google


### 3. Configure Secrets Locally

In your project’s src/main/resources folder, create a file:

spring:
  security:
    oauth2:
      client:
        registration:
          google:
            client-id: YOUR_GOOGLE_CLIENT_ID
            client-secret: YOUR_GOOGLE_CLIENT_SECRET
            scope:
              - openid
              - profile
              - email
server:
  port: 8080
  
  
### 4. Run the Application  

mvn spring-boot:run





