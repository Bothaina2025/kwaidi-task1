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
  top: 18%;
  left: 60%;
  transform: translate(-50%, -50%);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1.2vw 2vw;
  background-color:rgba(255, 255, 255, 1);
  border-radius:8px;
  border: 1px solid #e6e6e6;
  box-shadow: (0px 2px 4px -1px rgba(175, 182, 201, 0.2));
  width:1,158px;
  min-width: 1000px;
  max-width: 400px;
  height:60px;
}

.title-chat {
  color: black;
  font-size: 1.2vw;
  font-weight: 600;
  margin: 0;
}

.chat-controls {
  display: flex;
  align-items: center;
  gap: 1vw;
}

.icon-bar i {
  cursor: pointer;
  font-size: 1vw;
  color: #29343D;
}

.divider {
  font-size: 1vw;
  color: #888;
}


.chat-button {
  background-color:#635BFF;
  border: none;
  color: rgb(255, 255, 255);
  padding: 6px 14px;
  font-size: 0.85rem;
  font-weight: 500;
  cursor: pointer;
  border-radius: 6px;
  transition: background-color 0.3s, transform 0.2s;
}

.chat-button:hover {
  background-color: #635BFF;
  transform: scale(1.05);
}
</style>
