<template>
  <div class="sidebar-container">
    <div class="sidebar">
      <div class="user-info">
        <img src="@/image.png/user.png1.png" class="user-avatar" />
        <span class="status-dot online"></span>
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
          <div class="avatar-container"></div>
            <img :src="chat.avatar" class="avatar" />
            <span class="status-dot-list" :class="chat.status"></span>
          <div class="chat-details">
            <h4>{{ chat.name }} <span class="time">{{ chat.time }}</span></h4>
            <p>{{ chat.lastMessage }}</p>
          </div>
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
  left:310px ;
  top: 198px;
  width:340px; 
  height:800px;
  right: 1px;
  font-size: 20px;
  background: rgb(255, 255, 255);
  border-right: 1px solid #ddd;
  overflow-y:hidden; 
}

.sidebar {
 width: 309px;
 height:110px;
 border-radius: 4px;
 gap: 8px;
 padding-top: 18px;
 padding-right: 12px;
 padding-bottom: 8px;
 padding-left: 12px;
 border-width: 1px;

}

.user-info {
  display: flex;
  width:301px ;
  height: 59px;
  align-items: center;
  gap:20px;
  padding-bottom: 10px;

}

.user-avatar {
  width: 60px;
  height: 60px;
  border-radius: 50px;
}

.user-details {
  flex: 1;
}

.username {
  font-size: 14px;
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

.options-icon {
  color: gray;
  cursor: pointer;
}

.search-container {
  position: relative;
  width: 302px;
  height: 40px;
  margin: 15px 0;
}

.search {
  width: 302px;
  height: 40px;
  padding: 10px 35px;
  font-size: 12px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

.search-icon {
  position: absolute;
  size: 10px;
  left: 10px;
  top: 50%;
  transform: translateY(-50%);
  color: gray;
}


.recent-chats {
  display: flex;
  justify-content: space-between;
  font-size: 12px;
  font-weight:bold;
  color: gray;
  margin-bottom: 10px;
}

.chat-list {
  max-height: calc(100vh - 200px); 
  overflow-y:hidden;
}

.chat-list li {
  display: flex;
  align-items: center;
  margin-left:-40px;
  gap: 10px;
  padding: 12px;
  cursor: pointer;
  border-radius: 5px;
  transition: background 0.3s;
}

.chat-list li:hover {
  background: #e2e2e2;
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}

.chat-details {
  flex:1px;
}

h4 {
  font-size: 12px;
  left:30px;
  margin: 0;
  display: flex;
  justify-content: space-between;
}

.time {
  font-size: 10px;
  color: gray;
}

.status-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  border: 2px solid white;
  margin-left:-30px;
  margin-bottom:-35px; 
  left:5px; 
}
.status-dot-list{
  width: 11px;
  height: 11px;
  border-radius: 50%;
  border: 2px solid white;
  margin-left:-20px;
  margin-bottom:-35px; 
  left:5px; 
}

p {
  font-size: 10px;
  margin: 0;
  color: gray;
}

.online {
  background:rgba(54, 199, 108, 1);
}

.offline {
  background:rgba(255, 102, 146, 1);
}

.busy {
  background: rgba(255, 214, 72, 1);
}
</style>
