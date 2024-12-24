# Spring Security OAuth2 with Google Login

This project demonstrates a simple Spring Boot application with Google OAuth2 login using Spring Security.

---

## Features

- Google OAuth2 login for authentication.
- Displays user information (name and email) after login.
- Logout functionality.
- Secure endpoints that require authentication.

---

## Getting Started

### Prerequisites

1. **Java Development Kit (JDK):** Ensure you have JDK 11 or higher installed.
2. **Maven:** Make sure Maven is installed or use the Maven Wrapper provided (`mvnw`).

### Setting Up Google Console

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project (or use an existing project).
3. Navigate to **APIs & Services** > **Credentials**.
4. Click on **Create Credentials** > **OAuth 2.0 Client IDs**.
   - **Application Type:** Web Application.
   - **Authorized redirect URI:** `http://localhost:8080/login/oauth2/code/google`.
5. Copy the generated **Client ID** and **Client Secret**.
6. Set up environment variables in your system:
   - On macOS/Linux:
     ```bash
     export GOOGLE_CLIENT_ID=your_client_id
     export GOOGLE_CLIENT_SECRET=your_client_secret
     ```
   - On Windows:
     ```cmd
     setx GOOGLE_CLIENT_ID "your_client_id"
     setx GOOGLE_CLIENT_SECRET "your_client_secret"
     ```

---

### Configuration

The application uses environment variables to store sensitive information. Ensure the following variables are set in your environment:

- `GOOGLE_CLIENT_ID`
- `GOOGLE_CLIENT_SECRET`

The `application.yml` file is configured to use these variables:

```yaml
spring:
  security:
    oauth2:
      client:
        registration:
          google:
            client-id: ${GOOGLE_CLIENT_ID}
            client-secret: ${GOOGLE_CLIENT_SECRET}
            scope: openid, profile, email
            redirect-uri: "{baseUrl}/login/oauth2/code/{registrationId}"
        provider:
          google:
            issuer-uri: https://accounts.google.com
```
---

### Running the App

1. Clone the repo:

``` bash
git clone https://github.com/RezaeiAlireza/spring-security-oauth2-google.git
cd spring-security-oauth2-google
```

2. Build the App

```bash
./mvnw clean install
```

3. Run the App:

```bash
./mvnw spring-boot:run
```

4. Visit the link

- http://localhost:8080
