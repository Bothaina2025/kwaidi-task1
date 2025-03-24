<template>
  <div class="chat-container">
    <div class="icon-bar">
      <h3 class="title-chat">Chat</h3>
      <div class="chat-controls">
        <i class="fa-solid fa-house"></i>
        <span class="divider">/</span>
        <button class="chat-button">Chat</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.icon-bar {
  position:absolute;
  display: flex;
  top:140px;
  left:870px;
  transform: translate(-50%, -50%);
  align-items: center;
  justify-content: space-between;
  padding: 12px 20px;  
  border-radius: 8px;
  border: 1px solid #e6e6e6;
  background-color: rgba(255, 255, 255, 1);
  box-shadow: 0px 2px 4px -1px rgba(175, 182, 201, 0.2);
  width:1100px; 
  height: 60px;
}

.title-chat {
  color: black;
  font-size: 15px; 
  font-weight:500;
  margin: 0;
}

.chat-controls {
  display: flex;
  align-items: center;
  gap: 10px; 
}

.icon-bar i {
  cursor: pointer;
  font-size: 16px; 
  color: #29343D;
}

.divider {
  font-size: 16px; 
  color: #888;
}

.chat-button {
  background-color:rgba(221, 219, 255, 1);
  border: none;
  color:rgba(99, 91, 255, 1);
  padding: 6px 14px;
  font-size: 14px; 
  font-weight: 500;
  cursor: pointer;
  border-radius: 6px;
  transition: background-color 0.3s, transform 0.2s;
}

.chat-button:hover {
  transform: scale(1.05);
}

@media (max-width: 768px) {
  .icon-bar {
    width: 90%;  
    max-width: 320px;
    padding: 10px;
  }

  .title-chat {
    font-size: 16px;
  }

  .icon-bar i, .divider {
    font-size: 14px;
  }

  .chat-button {
    font-size: 12px;
    padding: 5px 12px;
  }
}
</style>
