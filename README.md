# Job Search Chatbot UI Documentation

## Overview
This React component provides a simple interface for interacting with an AI-powered job search chatbot. Users can input their queries, and the chatbot responds with job listings or relevant information. It utilizes the Flask-based API for processing job-related queries.

## Features
- **User Input Handling**: Allows users to type queries related to job searches.
- **API Integration**: Sends user queries to the backend API (`http://127.0.0.1:5000/get_job_response`).
- **Dynamic Message Display**: Displays messages from both the user and the bot.
- **Job Listing Formatting**: Displays job details in a structured format with links.
- **Loading State**: Shows a typing indicator while waiting for the bot's response.

## Installation and Setup
Ensure you have Node.js installed, then install dependencies:

```bash
npm install axios react
```

## Component Breakdown

### `useState` Hooks
- `userInput`: Stores the user's query input.
- `messages`: Stores conversation messages.
- `loading`: Indicates when the bot is processing a request.

### `sendMessage` Function
- **Clears previous messages** before sending a new request.
- **Validates input** to ensure it's not empty.
- **Sends a request** to the chatbot API.
- **Handles API response** by displaying job listings or error messages.
- **Handles errors gracefully** if the API request fails.

### UI Structure
- **Chat Container**: A centered, styled card layout.
- **Message Display**: A scrollable chat window for displaying bot and user messages.
- **Input Field**: A text input with an `Enter` key listener.
- **Send Button**: Triggers message sending, disabled while loading.

## API Request Format
### Request

```json
{
  "user_input": "I am looking for a job in New York with Python skills"
}
```

### Response
#### Successful Job Search
```json
{
  "jobs": [
    {
      "title": "Software Developer",
      "company": "Tech Co.",
      "date": "2025-01-25",
      "location": "New York",
      "skills": ["Python", "Django"],
      "link": "https://example.com/job/1"
    }
  ]
}
```

#### No Matching Jobs
```json
{
  "response": "Sorry, I could not find relevant job listings."
}
```

## Running the Component
To use this component within a React project, import and render it:

```jsx
import JobSearchChatbot from "./JobSearchChatbot";

function App() {
  return <JobSearchChatbot />;
}

export default App;
```

## Notes
- Ensure the Flask API is running on `http://127.0.0.1:5000/`.
- Modify styles and API URLs as needed for production deployment.
- Consider adding more error handling and user feedback mechanisms.

This documentation provides a guide for setting up and integrating the chatbot UI into your project. 🚀

