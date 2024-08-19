<template>
  <div v-if="isOpen" class="chatbot-container">
    <div class="chatbot-header">
      <h3>Docare</h3>
      <button @click="closeChat" class="close-btn">&times;</button>
    </div>
    <div class="chatbot-body">
      <!-- Messages container -->
      <div class="messages">
        <div class="message bot">
          <div class="message-content">Welcome! How can I assist you today?</div>
        </div>
      </div>
      <!-- Input field -->
      <div class="input-container">
        <input type="text" placeholder="Type a message..." />
        <button>Send</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    isOpen: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    closeChat() {
      this.$emit('close-chat');
    },
  },
};
</script>

<style scoped>
.chatbot-container {
  position: fixed;
  bottom: 90px;
  right: 20px;
  width: 320px;
  max-height: 500px;
  background-color: white;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  z-index: 1000;
}

.chatbot-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background-color: #00b9e3;
  color: white;
  border-radius: 10px 10px 0 0;
}

.chatbot-body {
  padding: 10px;
  flex: 1;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
}

.messages {
  flex: 1;
  overflow-y: auto;
  margin-bottom: 10px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.message {
  display: flex;
  max-width: 80%;
  padding: 8px;
  border-radius: 15px;
  font-size: 14px;
}

.message.bot {
  align-self: flex-start;
  background-color: #00b9e3;
  color: white;
}

.message-content {
  padding: 5px 10px;
}

.input-container {
  display: flex;
  align-items: center;
  margin-top: 10px;
}

input[type="text"] {
  flex: 1;
  padding: 10px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 15px;
  margin-right: 5px;
}

button {
  padding: 8px 12px;
  background-color: #00b9e3;
  color: white;
  border: none;
  border-radius: 15px;
  cursor: pointer;
}
</style>
