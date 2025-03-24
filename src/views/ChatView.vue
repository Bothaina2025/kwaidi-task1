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
    background-color: #ffffff;
  }
  
</style>
  