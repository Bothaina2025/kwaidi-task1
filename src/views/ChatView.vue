<template>
    <div class="chat-container">
      
      <SidebarChat />
      <ChatHeader />

      <div class="chat-main">
        <ChatInput />
      </div>
  
      <AttachmentsSidebar />
    </div>
</template>
  
<script>
  import SidebarChat from "@/components/SidebarChat.vue";
  import ChatInput from "@/components/ChatInput.vue";
  import AttachmentsSidebar from "@/components/AttachmentsSidebar.vue";
  
  export default {
    name: "ChatView",
    components: {
      SidebarChat,
      ChatInput,
      AttachmentsSidebar
    }
  };
</script>
  
<style scoped>
  .chat-container {
    display: flex;
    height: 100vh;
    background-color: #f8f9fa;
  }
  .chat-main {
    flex: 2;
    display: flex;
    flex-direction: column;
    border-left: 1px solid #ddd;
    border-right: 1px solid #ddd;
    background: white;
  }
</style>
  