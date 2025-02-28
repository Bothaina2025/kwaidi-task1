<template>
  <header class="header">
    <div class="header-left">
      <img src="@/image.png/logo.png" alt="Company Logo" class="logo">
      <h1 class="text">Hi TEAM</h1>
    </div>

    <div class="header-center">
      <i class="fas fa-search icon"></i>
      <i class="fas fa-th icon"></i>
    </div>

    <div class="header-right">
      <i class="fas fa-moon icon"></i>
      <i class="fas fa-bell icon"></i>
      <div class="language">
        <img src="@/image.png/eng.png" alt="English" class="language-icon">
      </div>
      <div class="profile">
        <img src="@/image.png/user.png1.png" alt="User Avatar" class="avatar">
        <i class="fas fa-chevron-down dropdown-icon"></i>
      </div>
    </div>
  </header>
</template>

<style scoped>

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px;
  background: white;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.header-left {
  display: flex;
  align-items: center;
}
.header-right{
  display: flex;
  align-items: center;
  color:#29343D;
  gap: 10px;
}

.header-center {
  display: flex;
  align-items: center;
  margin-left: -600px;
  color:#29343D;
  gap: 15px;
  width: 16.67px;
  height: 16.67px;
  top: 1.67px;
  border: 1.25px;
}

.logo {
  width: 50px;
  height: auto;
  margin-right: 10px;
}

.text {
  font-size: 14px;
  font-weight: normal;
  color: #3c3c3c;
}

.icon {
  font-size: 16px;
  color: #353535;
  margin: 0 10px;
  cursor: pointer;
}

.header-right {
  display: flex;
  align-items: center;
  gap: 15px; 
}


.language, .profile {
  display: flex;
  align-items: center;
  gap: 8px;
}

.language-icon {
  width: 28px;
  height: 28px;
  border-radius: 50%;
  object-fit: cover;
}


.avatar {
  width: 35px;
  height: 35px;
  border-radius: 50%;
  object-fit: cover;
  overflow: hidden;
  border: 2px solid #ddd;
}

.dropdown-icon {
  font-size: 14px;
  color: #333;
  cursor: pointer;
}
</style>
