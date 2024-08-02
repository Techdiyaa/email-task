# Email Scheduling API

## Overview

This project provides a RESTful API for scheduling and managing emails. Users can schedule emails to be sent at a later time, view scheduled emails, retrieve details of specific scheduled emails, and cancel scheduled emails.

## API Endpoints

### 1. Schedule an Email

- **Endpoint:** `POST /schedule-email`
- **Description:** Schedules an email to be sent at a specified time.
- **Request Body:**
  ```
  {
  "recipient": "shahkathanshah@gmail.com @example.com",
  "subject": "Immediate Email Test",
  "body": "This is an email sent immediately.",
  "scheduleType": "once",
  "scheduleTimes": ["2024-08-02T14:30:00Z"],  // Correct ISO 8601 format for UTC time
  "attachments": [
    {
      "filename": "test.txt",
      "content": "dGVzdCBjb250ZW50"  // Base64 encoded content of "test content"
    }]
}
```
- **Response:**
  - **Success (201 Created):**
    ```json
    {
      "id": "unique-id",
      "recipient": "example@example.com",
      "subject": "Email Subject",
      "body": "Email body text.",
      "sendAt": "2024-08-01T12:00:00Z"
    }
    ```
  - **Error (400 Bad Request):**
    ```json
    {
      "error": "Invalid request data."
    }
    ```

### 2. Retrieve Scheduled Emails

- **Endpoint:** `GET /scheduled-emails`
- **Description:** Retrieves a list of all scheduled emails.
- **Response:**
  ```json
  [
    {
      "id": "unique-id",
      "recipient": "example@example.com",
      "subject": "Email Subject",
      "body": "Email body text.",
      "sendAt": "2024-08-01T12:00:00Z"
    },
    ...
  ]
  ```

### 3. Retrieve Details of a Specific Scheduled Email

- **Endpoint:** `GET /scheduled-emails/{id}`
- **Description:** Retrieves details of a specific scheduled email.
- **Parameters:**
  - `id`: The unique identifier of the scheduled email.

- **Response:**
  ```json
  {
    "id": "unique-id",
    "recipient": "example@example.com",
    "subject": "Email Subject",
    "body": "Email body text.",
    "sendAt": "2024-08-01T12:00:00Z"
  }
  ```
- **Error (404 Not Found):**
  ```json
  {
    "error": "Scheduled email not found."
  }
  ```

### 4. Delete a Scheduled Email

- **Endpoint:** `DELETE /scheduled-emails/{id}`
- **Description:** Cancels a scheduled email.
- **Parameters:**
  - `id`: The unique identifier of the scheduled email.

- **Response:**
  - **Success (204 No Content):** Email is successfully canceled.
  - **Error (404 Not Found):**
    ```json
    {
      "error": "Scheduled email not found."
    }
    ```

## Setup



2. **Install Dependencies:**

   ```bash
   npm install
   ```

3. **Configure Environment Variables:**

   Create a `.env` file in the root directory and add your configuration settings:

   ```plaintext
 
PORT=5000
MONGO_URI=mongodb+srv://diyacpatel2003:p7idngkMMkeDa1en@cluster0.qfzzf52.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0
EMAIL_USER=earnestine21@ethereal.email
EMAIL_PASS=3nUYJGeMZdQEEzaurA


4. **Start the Server:**

   ```bash
   npm start
   ```

   The server will start on `http://localhost:5000`.

## Testing

You can test the API using tools like Postman or curl.

## Contributing

Feel free to submit issues or pull requests. For major changes, please open an issue first to discuss what you would like to change.



### Explanation:

- **API Endpoints:** Describes the available endpoints, their methods, request formats, and responses.
- **Setup:** Provides instructions on how to clone the repository, install dependencies, configure environment variables, and start the server.
- **Testing:** Offers example `curl` commands for interacting with the API.
- **Contributing:** Encourages contributions and provides guidelines for submitting changes.
- **License:** States the license under which the project is distributed.
