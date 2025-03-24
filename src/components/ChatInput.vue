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
      <i class="bi bi-list icon black" @click="openModal('list')"></i>
     </div>
    </div>
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
      <img v-if="modalImage" :src="modalImage" :alt="modalTitle" class="modal-icon" />
      <h3>{{ modalTitle }}</h3>
      <p class="modal-message">{{ modalMessage }}</p>

      <div class="buttons">
       <button class="cancel" @click="closeModal">Cancel</button>
       <button class="confirm" @click="confirmAction">Yes</button>
     </div>
   </div>
  </div>
</div>

<ul class="chat-messages">
  <template v-for="(msg, index) in messages" :key="index">
    <li :class="{'chat-message': true, 'sent': msg.isSender, 'move-left': msg.class ,'move-right':msg.class}">
      <img v-if="!msg.isSender" :src="msg.avatar" class="user-avatar" />
      <span v-if="!msg.isSender" class="message-time user-time">{{ msg.time }}</span>
      <span v-if="msg.isSender" class="message-time sender-time">{{ msg.time }}</span>

      <div v-if="msg.type === 'text'" class="message-content">
        <p>{{ msg.content }}</p>
      </div>

      <div v-if="msg.type === 'image'" class="image-container">
        <img :src="msg.content" class="message-image" />
      </div>
    </li>
  </template>
</ul>
</template>


<script>
export default {
data() {
  return {
    message: "",
    showModal: false,
    modalTitle: "",
    modalMessage: "",
    modalImage: "",
    currentUserAvatar: require("@/image.png/user.png2.png"), 
    messages: [
     { content: "If I don't like something, I'll stay away from it.", isSender: false, avatar: require("@/image.png/user.png4.png"), type: "text", time: "Andrew. 2 hours ago" },
     { content: "If I don't like something, I'll stay away from it.",isSender: true, type: "text", time: "2 hours ago" },
     { content: "I want more detailed information.", isSender: false, avatar: require("@/image.png/user.png4.png"), type: "text", class:"move-right",time: "Andrew. 2 hours ago" },
     { content: "If I don't like something, I'll stay away from it.", isSender: true, type: "text", time: "2 hours ago"},
     { content: "They got there early, and they got really good seats.", isSender: true, type: "text" , class: "move-left"},
     { content: require("@/image.png/media1.jpg"), isSender:false, avatar: require("@/image.png/user.png4.png"),type: "image", time: "Andrew. 2 hours ago" }
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
      this.modalImage =require("@/image.png/block.png");
    } else if (action === "delete") {
     this.modalTitle = "Delete Conversation";
     this.modalMessage = "Are you sure you want to delete this conversation? This action cannot be undone.";
     this.modalImage = require("@/image.png/trach.png");
    } else if (action ===  "list") {
      this.modalTitle = "unlock user";
      this.modalMessage = "you are going to unblock this user , are you sure?";
      this.modalImage = require("@/image.png/lock.png");
    }

    this.showModal=true;
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
.chat-container {
position:absolute;
left:650px ;
top: 198px;
right:20px; 
width:770px; 
height:800px; 
border-radius:7px;
background: white;
border-right: 1px solid #c7c4c4;
box-shadow: rgb(255, 255, 255);
overflow-y:hidden; 

}
.chat-header {
display: flex;
align-items: center;
top:99px;
width:766px;
height:90px;
padding:20px;
gap: 30px;
background:rgb(255, 255, 255);
border-bottom: 1px solid #efeeee;
}
.chat-messages {
position:absolute;
left:660px ;
top:300px;
margin-left:-8px;
width:500px; 
height:635px; 
border-radius:7px;
background: rgb(255, 255, 255);
box-shadow: rgba(224, 230, 235, 1);
overflow-y:hidden; 
}

.chat-message {
max-width: 500px;
display: flex;
flex-direction: column; 
margin-bottom:26px;
margin-bottom:50px;
background: white;

}

.chat-message.sent {
flex-direction: row-reverse;
text-align:center;
margin-left: 50px;
margin-bottom:-16px;
background:rgb(255, 255, 255);
overflow: hidden;
}

.message-content {
position: relative;
background: rgba(239, 244, 250, 1);
text-align:center; 
width:270px;
height:36px;
line-height:39px;
top:6px;
left:40px;
font-size: 11px;
border-radius: 4px;
}

.chat-message.sent .message-content {
background:rgba(236, 253, 253, 1);
text-align:center; 
margin-right:-40px;
margin-top:20px;
line-height: 26px;
letter-spacing: 0%;
border-radius:8px;
font-size: 11px;
position: relative;

}

.chat-message.sent.move-left .message-content {
  left:-40px;
  top:2px;
  width:290px;
  height:40px;
}

.chat-message.move-right .message-content {
  left:40px;
  top:7px;
  width:200px;
  height:40px;
}

.image-container {
  display: flex;
  justify-content: center;
  width:100px;
}

.user-time {
  font-size: 11px;
  color: gray;
  margin-bottom: 4px;
  margin-left:50px;
  margin-top:-25px;
  display: block;
}

.sender-time {
  font-size: 12px;
  color: gray;
  margin-bottom: 2px;
  display: block;
  text-align: right;
}
.message-image {
width: 114px;
height: 80px;
max-width: 100px;
margin-top:15px;
margin-left:100px;
border-radius: 1px;
}

.user-avatar-container {
position: relative;
display: inline-block;
background:rgb(255, 255, 255);
}

.user-avatar-large {
width: 48px;
height: 48px;
border-radius: 50px;
margin-right: 10px;
}

.status-indicator {
position: absolute;
bottom: 3px;
right: 3px;
width:12px;
height: 12px;
background:rgba(54, 199, 108, 1);
border-radius: 50%;
border: 2px solid white;
}

.user-name {
font-size:14px;
line-height: 20px;
color: rgba(152, 164, 174, 1);
margin-left:-30px;
margin-bottom:9px;
font-weight: lighter;
}

.icon-container,.icon {
display: flex;
gap:10px; 
align-items:center;
font-size:13px; 
margin-left: auto;
}

.user-avatar {
width: 35px;
height: 35px;
border-radius: 50px;
margin-left:2px;
}

.chat-input input {
  flex: 1;
  padding:0px;
  font-size: 14px;
  width:270px;
  height: 30px;
  border: none;
  top: 1px;
  outline: none;
  border-radius:2px;
  background: #ffffff;
}


.chat-input {
  position:absolute;
  bottom: 0px;
  left:0px;
  width:599px; 
  background: #fff;
  padding:10px;
  border-radius:1px solid #d7d7d7;
  border-top: 1px solid #d7d7d7;
}
.icon-btn {
  background: none;
  border: none;
  font-size: 18px;
  margin-left: 22px;
  cursor: pointer;
  margin-right: 7px;
  color:rgba(22, 22, 22, 0.787);
  transition: 0.3s;
}

.icon-btn:hover {
color: rgb(128, 128, 128);
}

.modal {
display: flex;
align-items: center;
justify-content: center;
position: absolute;
top:90px;
left:20px;
width:500px;
height:400px;
border-radius:0px;
}

.modal-content {
background: white;
padding:20px;
border-radius: 10px;
text-align: center;
box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.modal-icon {
width: 80px;  
height: auto;
display: block;
margin: 0 auto 10px;
}

.modal-message {
  color:rgba(113, 113, 113, 1);
  font-size: 16px;
}


.close {
position: absolute;
top:10px;
right: 15px;
cursor: pointer;
font-size: 20px;
}

.buttons {
  display: flex;
  justify-content:center;
  gap: 20px; 
  margin-top: 15px;
}

.button {
  width: 150px;
  height: 48px;
  border: none;
  cursor: pointer;
  border-radius:5px;
}

.cancel, .confirm {
  flex: 1;
  max-width:150px ;
  height: 48px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 14px;
}

.cancel {
background:rgba(149, 149, 149, 1);
color: white;
}

.confirm {
background:rgba(87, 92, 212, 1);
color: white;
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
</style>