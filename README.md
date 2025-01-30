# chat-bot-ui

JobSearchChatbot Component
This component provides an AI-powered chatbot interface where users can ask for job listings. The chatbot will send the user input to a backend API and display job information, such as job titles, companies, dates, and application links.

State Variables
userInput:

Type: string
Description: Holds the value of the user's current input in the chat.
messages:

Type: array
Description: Stores the conversation messages, both user and bot messages. Each message is an object with sender (either 'user' or 'bot') and text (message content).
loading:

Type: boolean
Description: Indicates whether the bot is currently processing a request. Used to show a "Bot is typing..." message when the bot is processing a request.
Functions
sendMessage:

Description:
This function handles the sending of user input to the backend API and updates the chat messages.
It performs the following steps:
Clears previous messages before sending the new message.
Sends the user input to the backend API endpoint (/get_job_response) via a POST request.
Receives job listings or a fallback message from the backend and updates the chat with the response.
Handles errors in case the API request fails.
Parameters: None
Returns: None (updates state variables)
setUserInput:

Description:
This function updates the userInput state when the user types into the input field.
Parameters:
e: Event object from the input field.
Returns: None
setMessages:

Description:
This function updates the messages state with the new messages (both user and bot).
Parameters:
A callback function that modifies the previous state.
Returns: None
UI Structure
Container:

A flexbox container centered on the screen that holds the chat interface.
Messages Section:

Displays the list of conversation messages. The messages are styled based on whether they are sent by the user or the bot.
The bot's replies are displayed with HTML content, allowing for clickable links to job applications.
Loading Indicator:

A loading message is displayed when the bot is processing a request.
Input Section:

Text Input: A text field where the user can type their query.
Send Button: A button to submit the user input. The button is disabled while the bot is processing the request.
Styling Classes:
w-full: Sets width to 100% of the container.
h-screen: Sets height to 100% of the viewport height.
bg-[#001399]: Sets background color to a custom blue shade.
p-24: Adds padding of 24 units.
max-w-xl: Limits the maximum width of the container to extra-large.
mx-auto: Centers the container horizontally.
my-auto: Centers the container vertically.
bg-white: Sets the background color to white.
rounded-lg: Rounds the corners of the container.
shadow-lg: Adds a large shadow to the container.
overflow-y-auto: Enables vertical scrolling when the message container overflows.
bg-gray-100: Sets background color for the message container.
text-blue-500: Sets the link color to blue.
p-2: Padding of 2 units.
text-gray-500: Sets text color to gray for the loading text.
bg-blue-500: Background color for the send button.
self-end: Aligns the user message to the end.
Backend API Endpoint
Endpoint: http://127.0.0.1:5000/get_job_response
Method: POST
Request Payload:
{ user_input: string }
The backend should return a JSON object with either:
A response field containing a text response, or
A jobs field containing an array of job listings, each with title, company, date, and link.
Example Response (from backend)

{
  "jobs": [
    {
      "title": "Software Engineer",
      "company": "Tech Corp",
      "date": "2025-01-30",
      "link": "http://example.com/job1"
    },
    {
      "title": "Frontend Developer",
      "company": "Design Inc.",
      "date": "2025-01-29",
      "link": "http://example.com/job2"
    }
  ]
}








