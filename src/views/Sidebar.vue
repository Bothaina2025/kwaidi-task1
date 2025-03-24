<template>
    <div class="chat-container">
    
      <SidebarMenu />
  
      <div class="chat-main">
        <ChatHeader />
        <ChatMessages />
        <ChatInput />
      </div>
  
      <AttachmentsSidebar />
    </div>
</template>
  
<script>
  import SidebarMenu from "@/components/SidebarMenu.vue";
  import ChatHeader from "@/components/ChatHeader.vue";
  import ChatMessages from "@/components/ChatMessages.vue";
  import ChatInput from "@/components/ChatInput.vue";
  import AttachmentsSidebar from "@/components/AttachmentsSidebar.vue";
  
  export default {
    components: {
      SidebarMenu,
      ChatHeader,
      ChatMessages,
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
  