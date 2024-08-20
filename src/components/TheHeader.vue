<script setup></script>

<template>
  <header class="header">
    <div class="container">
      <div class="logo">
        <h1 class="logo-text">OpenBS</h1>
      </div>
      <div class="nav">
        <ul class="nav-list">
          <li class="nav-link">Кредитный калькулятор</li>
          <li class="nav-link">Научные статьи</li>
        </ul>
      </div>
    </div>
  </header>
</template>

<style scoped>
.header {
  width: 100%;
  height: 80px;
  background-color: #2a17b1;
  display: flex;
  align-items: center;
  justify-content: center;
}

.container {
  
  display: flex;
  align-items: center;
  gap: 400px;
  padding: 0 15px;
  width: 100%;
  max-width: 1500px;
  font-family: "Kanit", sans-serif;
  
}



.logo-text {
  color: #ffffff;
  font-size: 32px;
  font-weight: 500;
}



.nav-list {
  display: flex;
  gap: 40px;
  cursor: pointer;
}

.nav-link {
  color: white;
  font-size: 16px;
}


</style>
