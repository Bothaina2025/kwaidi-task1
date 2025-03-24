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
  min-height:100px;
  background-color:rgba(244, 247, 251, 1);
}

</style>