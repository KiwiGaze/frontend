<template>
    <div class="chat-bot">
      <div class="chat-history">
        <div v-for="(message, index) in chatHistory" :key="index" :class="['message', message.sender]">
          <span>{{ message.sender === 'user' ? 'You' : 'Bot' }}:</span>
          <span>{{ message.text }}</span>
        </div>
      </div>
      <div class="chat-input">
        <input
          type="text"
          v-model="userMessage"
          @keyup.enter="sendMessage"
          placeholder="Type your message here..."
        />
        <button @click="sendMessage">Send</button>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'ChatBot',
    data() {
      return {
        userMessage: '',
        chatHistory: [],
      };
    },
    methods: {
      async sendMessage() {
        if (!this.userMessage.trim()) return;
  
        // Add user's message
        this.chatHistory.push({ text: this.userMessage, sender: 'user' });
  
        // Send to backend
        try {
          const response = await axios.post('/api/chat/', { message: this.userMessage });
          this.chatHistory.push({ text: response.data.reply, sender: 'bot' });
        } catch (error) {
          this.chatHistory.push({ text: 'Error: Could not contact server.', sender: 'bot' });
        }
  
        // Clear input
        this.userMessage = '';
      },
    },
  };
  </script>
  
  <style scoped>
  .chat-bot {
    display: flex;
    flex-direction: column;
    width: 400px;
    margin: auto;
  }
  
  .chat-history {
    flex: 1;
    overflow-y: auto;
    border: 1px solid #ccc;
    padding: 10px;
  }
  
  .message {
    margin-bottom: 10px;
  }
  
  .message.user {
    text-align: right;
    color: blue;
  }
  
  .message.bot {
    text-align: left;
    color: green;
  }
  
  .chat-input {
    display: flex;
  }
  
  input[type="text"] {
    flex: 1;
    padding: 5px;
  }
  
  button {
    padding: 5px 10px;
  }
  </style>
  