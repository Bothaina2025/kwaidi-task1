<template>
    <aside class="sidebar">
      <div class="logo">
      </div>
  
      <nav>
        <router-link
          v-for="item in filteredMenuItems"
          :key="item.name"
          :to="item.route"
          class="nav-item"
        >
          <i :class="item.icon" class="icon"></i>
          <span>{{ item.name }}</span>
        </router-link>

        <div class="nav-item dropdown" @click="toggleDropdown">
          <i class="fas fa-shield-alt icon"></i>
          <span>Permissions</span>
          <i :class="dropdownOpen ? 'fas fa-chevron-down' : 'fas fa-chevron-right'" class="arrow-icon"></i>
        </div>
        
        <div v-show="dropdownOpen" class="submenu">
          <router-link
            v-for="sub in permissionsSubmenu"
            :key="sub.name"
            :to="sub.route"
            class="nav-item sub-item"
          >
            <i :class="sub.icon" class="icon"></i>
            <span>{{ sub.name }}</span>
          </router-link>
        </div>
      </nav>
    </aside>
</template>
  
<script>
export default {
  data() {
    return {
      dropdownOpen: false,
      menuItems: [
        { name: "Dashboard", route: "/dashboard", icon: "fas fa-home" },
        { name: "Orders", route: "/orders", icon: "fas fa-box" },
        { name: "Passenger", route: "/passenger", icon: "fas fa-user" },
        { name: "Captains", route: "/captains", icon: "fas fa-car" },
        { name: "Categories", route: "/categories", icon: "fas fa-file" },
        { name: "Settlement", route: "/settlement", icon: "fas fa-file-invoice-dollar" },
        { name: "Contact", route: "/contact", icon: "fas fa-phone" },
        { name: "Reviews", route: "/reviews", icon: "fas fa-star" },
      ],
      permissionsSubmenu: [
        { name: "Translation", route: "/translation", icon: "fas fa-globe" },
        { name: "Education Video", route: "/education-video", icon: "fas fa-video" },
        { name: "Settings", route: "/settings", icon: "fas fa-cog" },
        { name: "Content", route: "/content", icon: "fas fa-file-alt" }
      ]
    };
  },
  computed: {
    filteredMenuItems() {
      return this.menuItems.filter(item => item.shouldShow !== false);
    }
  },
  methods: {
    toggleDropdown() {
      this.dropdownOpen = !this.dropdownOpen;
    }
  }
};
</script>
  
<style scoped>
.sidebar {
  width: 300px; 
  height:1219px; 
  background: #ffffff;
  display: flex;
  flex-direction: column;
  padding: 20px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.nav-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px;
  text-decoration: none;
  color: #98A4AE;
  font-size: 15px;
  border-radius: 8px;
  transition: background 0.3s ease;
}

.nav-item:hover {
  background:#635BFF;
}

.active {
  color: white;
}

.icon {
  font-size: 15px;
  width: 24px; 
  text-align: center;
}

.submenu {
  padding-left: 20px;
}

.sub-item {
  background: rgb(255, 255, 255);
  padding: 8px 12px;
  border-radius: 5px;
  font-size: 14px;
}

.sub-item:hover {
  background:#635BFF;
}

.arrow-icon {
  margin-left: auto;
  transition: transform 0.3s ease;
}


.dropdown .arrow-icon {
  transform: rotate(90deg);
}
</style>