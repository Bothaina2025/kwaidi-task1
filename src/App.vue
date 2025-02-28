<template>
  <div class="app-container">
    <HeaderMenu />
    <SidebarMenu />
    <ChatHeader />
    <div class="content">
      <router-view />
    </div>
  </div>
  <ChatView />
</template>

<script>
import ChatHeader from "@/components/ChatHeader.vue";
import HeaderMenu from "@/components/HeaderMenu.vue";
import SidebarMenu from "@/components/SidebarMenu.vue";
import ChatView from "@/views/ChatView.vue";
export default {
  components: {
    ChatHeader,
    HeaderMenu,
    SidebarMenu,
    ChatView
    
  }
  
};
</script>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.content {
  flex-grow: 1;
  padding-bottom: 50px; 
}
</style>