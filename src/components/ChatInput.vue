<template>
    <div class="chat-container">
      
      <div class="chat-header">
        <div class="user-avatar-container">
          <img :src="currentUserAvatar" class="user-avatar-large" />
          <span class="status-indicator"></span>
        </div>
        <div>
         <p class="user-name">Away</p>
       </div>
       <div class="icon-container">
        <i class="bi bi-ban icon purple" @click="openModal('block')"></i>
        <i class="bi bi-trash icon red" @click="openModal('delete')"></i>
        <i class="bi bi-telephone icon black"></i>
        <i class="bi bi-camera-video icon black"></i>
        <i class="bi bi-list icon black"></i>
       </div>
      </div>
       
      <ul class="chat-messages">
        <li v-for="(msg, index) in messages" :key="index" 
            :class="{'chat-message': true, 'sent': msg.isSender}">
          <img :src="msg.avatar" class="user-avatar" />
          <div class="message-content">
            <p v-if="msg.type === 'text'">{{ msg.content }}</p>
            <img v-if="msg.type === 'image'" :src="msg.content" class="message-image" />
            <span class="message-time">{{ msg.time }}</span>
          </div>
        </li>
      </ul>
  
      <div class="chat-input">
        <button class="icon-btn"><i class="far fa-smile"></i></button>
        <input type="text" v-model="message" placeholder="Type a message..." @keyup.enter="sendMessage" />
        <button class="icon-btn"><i class="fas fa-image"></i></button>
        <button class="icon-btn"><i class="fas fa-link"></i></button>
        <button class="icon-btn"><i class="fas fa-microphone"></i></button>
      </div>

      <div v-if="showModal" class="modal">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>
        <h3>{{ modalTitle }}</h3>
        <p>{{ modalMessage }}</p>
        <div class="buttons">
          <button class="cancel" @click="closeModal">Cancel</button>
          <button class="confirm" @click="confirmAction">Yes</button>
        </div>
      </div>
    </div>
    </div>
</template>
  
<script>
export default {
  data() {
    return {
      message: "",
      showModal: false,
      modalTitle: "",
      modalMessage: "",
      currentUserAvatar: require("@/image.png/user.png2.png"), 
      messages: [
        { content: "If I don't like something, I'll stay away from it.", isSender: false, avatar: require("@/image.png/user.png4.png"), type: "text", time: "2 hours ago" },
        { content: "I want more detailed information.", isSender: false, avatar: require("@/image.png/user.png4.png"), type: "text", time: "2 hours ago" },
        { content: "They got there early, and they got really good seats.", isSender: true, avatar: require("@/image.png/user.png4.png"), type: "text", time: "2 hours ago" },
        { content: require("@/image.png/media1.jpg"), isSender: false, avatar: require("@/image.png/user.png4.png"), type: "image", time: "2 hours ago" }
      ]
    };
  },
  methods: {
    sendMessage() {
      if (this.message.trim() !== "") {
        this.messages.push({
          content: this.message,
          isSender: true,
          avatar: this.currentUserAvatar,
          type: "text",
          time: "Just now"
        });
        this.message = "";
      }
    },
    openModal(action) {
      this.showModal = true;
      if (action === "block") {
        this.modalTitle = "Block User";
        this.modalMessage = "You are going to block this user. Are you sure?";
      } else if (action === "delete") {
        this.modalTitle = "Delete Conversation";
        this.modalMessage = "Are you sure you want to delete this conversation? This action cannot be undone.";
      }
    },
    closeModal() {
      this.showModal = false;
    },
    confirmAction() {
      alert("Action confirmed!"); 
      this.closeModal();
    }

  }
};
</script>
  
<style scoped>
.modal {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 0;
  left: 40%;
  width: 29%;
  height: 100%;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 10px;
  text-align: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.close {
  position: absolute;
  top: 10px;
  right: 15px;
  cursor: pointer;
  font-size: 20px;
}

.buttons {
  margin-top: 20px;
}

button {
  padding: 7px 15px;
  border: none;
  cursor: pointer;
  border-radius: 10%;
}

.cancel {
  background: gray;
  color: white;
}

.confirm {
  background: blueviolet;
  color: white;
}
.chat-container {
  display: flex;
  align-items: center;
  flex-direction: column;
  position:absolute;
  right:19%; 
  top:27%;
  width:540px; 
  height: 100vh; 
  padding: 20px;
  border-radius: 10px;
  background: white;
  border: 1px solid #ececec;
  
}

.chat-header {
  display: flex;
  align-items: center;
  width: 540px;
  height:76px;
  background:rgb(255, 255, 255);
  border-bottom: 1px solid #efeeee;
}

.user-avatar-container {
  position: relative;
  display: inline-block;
  background:white;
}

.user-avatar-large {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  margin-right: 10px;
}

.status-indicator {
  position: absolute;
  bottom: 3px;
  right: 3px;
  width:12px;
  height: 12px;
  background: green;
  border-radius: 50%;
  border: 2px solid white;
}
.user-name {
  font-size:20px;
  font-weight: lighter;
}
.icon-container,.icon {
  display: flex;
  gap:10px; 
  align-items:center;
  font-size:13px; 
  margin-left: auto;
}

.purple {
  color: #6c5ce7; 
}

.red {
  color: #d63031; 
}

.black {
  color: #2d3436; 
}

.chat-messages {
  flex-grow: 1;
  padding: 15px;
  width:540px;
  height: 697px;
  list-style: none;
  overflow-y:hidden;
  background:white;
}

.chat-message {
  flex-grow: 1;
  overflow-y: hidden;
  padding: 15px;
  background: white;
}

.chat-message.sent {
  flex-direction: row-reverse;
  text-align: right;
  background:white;
}

.user-avatar {
  width: 35px;
  height: 35px;
  border-radius: 50%;
}

.message-content {
  background: #f0f0f0;
  padding: 10px 9px;
  top: 32%;
  border-radius: 10px;
  max-width: 60%;
  font-size: 12px;
  position: relative;
}

.chat-message.sent .message-content {
  background: #dcf8c6;
  right: -40%;
}

.message-time {
  display: block;
  font-size: 12px;
  color: rgb(167, 166, 166);
  margin-top: 5px;
}

.message-image {
  width: 114px;
  height: 86px;
  max-width: 100%;
  border-radius: 10px;
}

.chat-input {
  position:absolute;
  bottom: 0;
  left:0;
  width: 100%; 
  background: #fff;
  padding: 10px;
  border-top: 1px solid #d5d4d4;
}

.chat-input input {
  flex: 1;
  padding:0px;
  font-size: 14px;
  width:297px;
  height: 30px;
  border: none;
  top: 1px;
  outline: none;
  border-radius: 5px;
  background: #ffffff;
}

.icon-btn {
  background: none;
  border: none;
  font-size: 18px;
  cursor: pointer;
  margin-right: 7px;
  color:rgba(22, 22, 22, 0.787);
  transition: 0.3s;
}

.icon-btn:hover {
  color: rgb(128, 128, 128);
}

</style>
