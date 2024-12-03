<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <!-- Platform logo -->
      <a href="#" class="navbar-brand">
        <img src="../assets/vue.svg" height="28" alt="CoolBrand" />
      </a>
      <!-- Mobile toggle button -->
      <button
        type="button"
        class="navbar-toggler"
        data-bs-toggle="collapse"
        data-bs-target="#navbarCollapse"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <!-- Main menu -->
      <div class="collapse navbar-collapse" id="navbarCollapse">
        <div class="navbar-nav">
          <a href="#" class="nav-item nav-link active">Dashboard</a>
          <a href="#" class="nav-item nav-link">QR Codes</a>
          <a href="#" class="nav-item nav-link">Transactions</a>
          <a href="#" class="nav-item nav-link">Users</a>
        </div>
        <!-- Secondary actions -->
        <div class="navbar-nav ms-auto">
          <a href="#" class="nav-item nav-link">Notifications</a>
          <a href="#" class="nav-item nav-link">Settings</a>
          <!-- Logout button -->
          <button class="navbar__logout nav-item nav-link" @click="logout">
            Logout
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    logout() {
      // Logout logic
      console.log('User logged out');
    },
  },
};
</script>

<style scoped>
/* Navbar Styles */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #fd7e14;
  color: black;
  padding: 10px 20px;
}

.navbar__logout {
  background-color: transparent;
  border: none;
  color: black;
  font-size: 16px;
  display: flex;
  align-items: center;
  cursor: pointer;
  transition: color 0.2s;
}

.navbar__logout:hover {
  color: #e74c3c; /* Hover effect color */
}
</style>
