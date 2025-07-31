<script setup lang="ts">
import EstimateTable from './components/EstimateTable.vue'
</script>

<template>
  <div id="app">
    <header class="app-header">
      <div class="container">
        <h1>Estimate Management System</h1>
        <p>Create and manage project estimates with ease</p>
      </div>
    </header>
    
    <main class="main-content">
      <EstimateTable />
    </main>
    
    <footer class="app-footer">
      <div class="container">
        <p>&copy; 2024 Estimate Management System. Built with Vue.js</p>
      </div>
    </footer>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.app-header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 40px 0;
  text-align: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.app-header h1 {
  font-size: 36px;
  font-weight: 700;
  margin-bottom: 10px;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
}

.app-header p {
  font-size: 18px;
  opacity: 0.9;
  font-weight: 300;
}

.main-content {
  flex: 1;
  padding: 40px 0;
}

.app-footer {
  background: #2c3e50;
  color: white;
  padding: 20px 0;
  text-align: center;
  margin-top: auto;
}

.app-footer p {
  font-size: 14px;
  opacity: 0.8;
}

@media (max-width: 768px) {
  .app-header {
    padding: 30px 0;
  }
  
  .app-header h1 {
    font-size: 28px;
  }
  
  .app-header p {
    font-size: 16px;
  }
  
  .main-content {
    padding: 20px 0;
  }
}
</style>
