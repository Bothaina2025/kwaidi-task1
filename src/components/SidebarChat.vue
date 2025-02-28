<template>
  <div class="sidebar-container">
    <div class="sidebar">
      <div class="user-info">
        <img src="@/image.png/user.png1.png" class="user-avatar" />
        <div class="user-details">
          <h3 class="username">Mathew Anderson</h3>
          <p class="user-role">Marketing Director</p>
        </div>
        <i class="fas fa-ellipsis-v options-icon"></i>
      </div>

      <div class="search-container">
        <i class="fas fa-search search-icon"></i>
        <input type="text" class="search" placeholder="Search contacts" />
      </div>

      <div class="recent-chats">
        <span>Recent Chats</span>
        <i class="fas fa-chevron-down"></i>
      </div>

      <ul class="chat-list">
        <li v-for="chat in chats" :key="chat.id">
          <img :src="chat.avatar" class="avatar" />
          <div class="chat-details">
            <h4>{{ chat.name }} <span class="time">{{ chat.time }}</span></h4>
            <p>{{ chat.lastMessage }}</p>
          </div>
          <span class="status-dot" :class="chat.status"></span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      chats: [
        { id: 1, name: "Michell Flintoff", avatar: require("@/image.png/user.png2.png"), lastMessage: "You: Yesterday was great...", time: "15 minutes", status: "online" },
        { id: 2, name: "Bianca Anderson", avatar: require("@/image.png/user.png3.png"), lastMessage: "Nice looking dress you...", time: "30 minutes", status: "offline" },
        { id: 3, name: "Andrew Johnson", avatar: require("@/image.png/user.png4.png"), lastMessage: "Sent a photo", time: "2 hours", status: "busy" },
        { id: 4, name: "Mark Strokes", avatar: require("@/image.png/user.png5.png"), lastMessage: "Lorem ipsum text sud...", time: "5 days", status: "online" },
        { id: 5, name: "Mark, Stoinus & Rishvi..", avatar: require("@/image.png/user.png6.png"), lastMessage: "Lorem ipsum text ...", time: "5 days", status: "online" },
        { id: 2, name: "Bianca Anderson", avatar: require("@/image.png/user.png3.png"), lastMessage: "Nice looking dress you...", time: "30 minutes", status: "offline" }
      ]
    };
  }
};
</script>

<style scoped>
.sidebar-container {
  position:absolute;
  left:18%; 
  top: 27%; 
  width: 350px; 
  height: 100vh; 
  background: white;
  border-right: 1px solid #ddd;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
  overflow-y: auto; 
}

.sidebar {
  width: 100%; 
  height: 100%;
  padding: 20px;
}

.user-info {
  display: flex;
  align-items: center;
  gap: 10px;
  padding-bottom: 15px;
  border-bottom: 1px solid #ddd;
}

.user-avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
}

.user-details {
  flex: 1;
}

.username {
  font-size: 16px;
  font-weight:bold;
  margin: 0;
}

.user-role {
  font-size: 12px;
  color: gray;
  margin: 0;
}

.user-status {
  font-size: 12px;
  margin-top: 2px;
  display: inline-block;
  padding: 2px 6px;
  border-radius: 10px;
  font-weight: bold;
}

.online {
  color: green;
}

.offline {
  color: red;
}

.busy {
  color: orange;
}

.options-icon {
  color: gray;
  cursor: pointer;
}

.search-container {
  position: relative;
  margin: 15px 0;
}

.search {
  width: 100%;
  padding: 10px 35px;
  font-size: 14px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

.search-icon {
  position: absolute;
  left: 10px;
  top: 50%;
  transform: translateY(-50%);
  color: gray;
}


.recent-chats {
  display: flex;
  justify-content: space-between;
  font-size: 14px;
  font-weight: bold;
  color: gray;
  margin-bottom: 10px;
}

.chat-list {
  max-height: calc(100vh - 200px); 
  overflow-y: auto;
}

.chat-list li {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 12px;
  cursor: pointer;
  border-radius: 5px;
  transition: background 0.3s;
}

.chat-list li:hover {
  background: #f5f5f5;
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}

.chat-details {
  flex: 1;
}

h4 {
  font-size: 14px;
  margin: 0;
  display: flex;
  justify-content: space-between;
}

.time {
  font-size: 12px;
  color: gray;
}

p {
  font-size: 12px;
  margin: 0;
  color: gray;
}

.status-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
}

.online {
  background: green;
}

.offline {
  background: red;
}

.busy {
  background: yellow;
}
</style>
