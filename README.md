<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FlowRight Plumbing Chatbot Demo</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background-color: #f4f6f8;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  .chat-container {
    width: 350px;
    max-height: 600px;
    background-color: #fff;
    border-radius: 15px;
    box-shadow: 0 5px 20px rgba(0,0,0,0.2);
    display: flex;
    flex-direction: column;
    overflow: hidden;
  }
  .chat-header {
    background-color: #0077cc;
    color: #fff;
    padding: 15px;
    text-align: center;
    font-weight: bold;
  }
  .chat-messages {
    flex: 1;
    padding: 15px;
    overflow-y: auto;
  }
  .chat-messages .message {
    margin-bottom: 10px;
    padding: 10px 15px;
    border-radius: 15px;
    max-width: 80%;
  }
  .user {
    background-color: #0077cc;
    color: #fff;
    align-self: flex-end;
  }
  .bot {
    background-color: #e2e2e2;
    color: #000;
    align-self: flex-start;
  }
  .chat-input {
    display: flex;
    border-top: 1px solid #ccc;
  }
  .chat-input input {
    flex: 1;
    border: none;
    padding: 10px;
    font-size: 16px;
  }
  .chat-input button {
    padding: 10px;
    border: none;
    background-color: #0077cc;
    color: #fff;
    cursor: pointer;
  }
</style>
</head>
<body>

<div class="chat-container">
  <div class="chat-header">FlowRight Plumbing</div>
  <div class="chat-messages" id="chat-messages">
    <div class="message bot">Hi there! 👋 Welcome to FlowRight Plumbing. How can I help you today?</div>
  </div>
  <div class="chat-input">
    <input type="text" id="user-input" placeholder="Type your message here...">
    <button onclick="sendMessage()">Send</button>
  </div>
</div>

<script>
  const chatMessages = document.getElementById('chat-messages');

  function sendMessage() {
    const input = document.getElementById('user-input');
    const userMessage = input.value.trim();
    if (!userMessage) return;

    // Add user message
    addMessage(userMessage, 'user');

    // Clear input
    input.value = '';

    // Bot response
    setTimeout(() => {
      addMessage(getBotResponse(userMessage), 'bot');
      chatMessages.scrollTop = chatMessages.scrollHeight;
    }, 500);
  }

  function addMessage(text, sender) {
    const msgDiv = document.createElement('div');
    msgDiv.classList.add('message', sender);
    msgDiv.innerText = text;
    chatMessages.appendChild(msgDiv);
    chatMessages.scrollTop = chatMessages.scrollHeight;
  }

  function getBotResponse(message) {
    message = message.toLowerCase();
    
    if (message.includes('book')) {
      return "Great! Can you tell me what service you need?";
    }
    if (message.includes('quote')) {
      return "Sure! Please describe the problem, and I’ll give you an estimated quote.";
    }
    if (message.includes('emergency')) {
      return "🚨 Emergency? Don’t worry! Please provide your location and a short description of the issue, and we’ll dispatch a plumber immediately.";
    }
    if (message.includes('leak') || message.includes('blocked') || message.includes('pipe')) {
      return "Thanks for the info! We can send a plumber to inspect. When would you like us to come?";
    }
    return "I’m here to help! You can ask me about services, quotes, or emergencies.";
  }
</script>

</body>
</html>

