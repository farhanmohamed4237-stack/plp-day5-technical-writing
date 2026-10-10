Exercise A: User Manual Procedure
How to Create a GitHub Repository and Make Your First Commit
Target audience: First-semester computing students with basic computer skills and no previous GitHub experience.
1. Prerequisites
Before starting, ensure you have:
A computer or laptop with an internet connection.
A web browser, such as Google Chrome or Microsoft Edge.
A GitHub account. If you do not have one, register at https://github.com/signup.
A project file ready to upload, such as a Python file (hello.py) or a text file (README.md).
Basic knowledge of creating and locating files on your computer.
2. Procedure: Creating a GitHub Repository
Step 1: Open GitHub
Action: Open https://github.com in your web browser.
Expected result: The GitHub homepage appears.
Step 2: Sign in
Action: Sign in using your GitHub account.
Expected result: Your GitHub dashboard appears.
Step 3: Start creating a repository
Action: Click the + icon in the upper-right corner and select New repository.
Expected result: The Create a New Repository page appears.
Step 4: Name your repository
Action: Enter my-first-project in the Repository name field.
Expected result: The repository name is displayed and GitHub checks whether it is available.
Step 5: Choose repository visibility
Action: Select Public under the repository visibility options.
Expected result: The Public option is selected, allowing other people to view your repository.
Step 6: Create the repository
Action: Click the green Create repository button.
Expected result: GitHub creates the repository and displays its main page.
Step 7: Open the file upload page
Action: Click uploading an existing file on the repository page.
Expected result: The Upload files page appears.
Step 8: Select a project file
Action: Click choose your files.
Expected result: A file selection window opens on your computer.
Step 9: Upload the project file
Action: Select your prepared project file and click Open.
Expected result: The filename appears on GitHub's Upload files page.
Step 10: Enter a commit message
Action: Type Add my first project file in the commit message field.
Expected result: The message appears in the commit message field.
Step 11: Make your first commit
Action: Click Commit changes.
Expected result: GitHub saves your uploaded file and displays it in the repository.
3. Screenshot Description
Figure 1: GitHub Repository After the First Commit
The screenshot should show the GitHub repository page after successfully uploading and committing the first project file.
The screenshot should clearly display:
The repository name (my-first-project).
The uploaded project file.
The latest commit message (Add my first project file).
Purpose: To help beginners confirm that they have successfully created a GitHub repository and made their first commit.
4. Troubleshooting
Problem: GitHub displays "Repository name already exists."
Possible cause: Another repository with the same name already exists under your GitHub account.
Solution: Enter a different repository name, such as my-first-project-2026, and try creating the repository again.
Expected result: GitHub accepts the new repository name and allows you to create the repository.



Exercise B: API Reference Entry
1. Create a New Task
API Name: Task Management API
HTTP Method: POST
Endpoint: /api/v1/tasks
Authentication: Required (Bearer Token)
Description
This endpoint allows an authenticated user to create a new task in a project management application.
The user provides a task title, an optional description, the ID of the person assigned to the task, a due date, and a priority level.
The priority level must be one of the following: low, medium, or high.
When the task is successfully created, the API returns the task details, including a unique task ID.
Base URL
https://api.example.com
Full Endpoint URL
https://api.example.com/api/v1/tasks

2. Request Parameters
The API accepts the following parameters when creating a new task.
Parameter
Location
Data Type
Required
Description
title
Body
String
Yes
The name of the task to be created.
description
Body
String
No
Additional details about the task.
assignee_id
Body
Integer
Yes
The unique ID of the user assigned to the task.
due_date
Body
String (YYYY-MM-DD)
Yes
The deadline for completing the task.
priority
Body
String
Yes
The task's priority level: low, medium, or high.

Path Parameters: None.
Query Parameters: None.
Request Body Format: JSON.
Important: All required fields must be provided for the API to create a task successfully.

3. Required Request Headers
The following HTTP headers must be included when sending a request to create a new task.
Header
Required
Description
Authorization
Yes
Contains a Bearer token used to verify the user's identity and permission to create tasks.
Content-Type
Yes
Specifies that the request body contains JSON data. Must be application/json.

Example Request Headers
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json
Note: Replace YOUR_ACCESS_TOKEN with a valid authentication token. Requests without a valid token will be rejected.

4. Example Request Body (JSON)
The following example shows a request to create a task in the project management application.
{
  "title": "Complete project documentation",
  "description": "Prepare and submit the technical documentation for the software project.",
  "assignee_id": 102,
  "due_date": "2026-11-15",
  "priority": "high"
}
Explanation
title: The name of the task.
description: Additional information about the task.
assignee_id: The unique ID of the person responsible for the task.
due_date: The date by which the task should be completed.
priority: The importance of the task. Accepted values are low, medium, and high.
Expected result: If the request contains valid information and the user is authenticated, the API creates a new task and returns an HTTP 201 Created response.

5. Example Successful Response
HTTP Status Code: 201 Created
Response Format: JSON
The following example shows the response returned when a new task is successfully created.
{
  "id": 501,
  "title": "Complete project documentation",
  "description": "Prepare and submit the technical documentation for the software project.",
  "assignee_id": 102,
  "due_date": "2026-11-15",
  "priority": "high",
  "status": "pending",
  "created_at": "2026-10-10T09:30:00Z"
}
Response Field Descriptions
Field
Description
id
Unique identification number assigned to the newly created task.
title
Name of the created task.
description
Additional details about the task.
assignee_id
ID of the user assigned to the task.
due_date
Deadline for completing the task.
priority
Priority level assigned to the task.
status
Current task status, initially set to pending.
created_at
Date and time when the task was created, in UTC.

Expected result: The API returns HTTP 201 Created and the details of the newly created task, confirming that it has been saved successfully.

6. HTTP Response Codes
The Task Management API may return the following HTTP status codes when a user attempts to create a new task.
HTTP Status Code
Meaning
Description
201 Created
Success
The task has been created successfully.
400 Bad Request
Invalid request
The request contains malformed JSON or invalid data types.
401 Unauthorized
Authentication failed
The authentication token is missing, invalid, or expired.
403 Forbidden
Access denied
The authenticated user does not have permission to create tasks.
404 Not Found
User not found
The specified assignee ID does not belong to an existing user.
409 Conflict
Conflict
The request conflicts with an existing task or a task-creation rule.
422 Unprocessable Content
Validation failed
A required field is missing, the due date is invalid, or the priority is not low, medium, or high.
429 Too Many Requests
Rate limit exceeded
The user has sent too many requests within a short period.
500 Internal Server Error
Server error
An unexpected error prevents the server from creating the task.
503 Service Unavailable
Service temporarily unavailable
The API is temporarily unavailable due to maintenance or an outage.

7. Error Handling
When a request fails, the API returns an appropriate HTTP status code and an error message explaining the problem.
Example Error Response (422 Unprocessable Content):
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid priority value.",
    "details": {
      "priority": "Priority must be low, medium, or high."
    }
  }
}
Expected result: The user receives a clear error message and can correct the request before trying again.


