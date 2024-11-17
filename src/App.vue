<script setup>
import menuBar from './components/menuBar.vue';
import DashBoard from './components/dashBoard.vue';
import AboutPage from './components/aboutPage.vue';
import CasesPage from './components/casesPage.vue';
import AgentPage from './components/agentsPage.vue';

import { ref } from 'vue';


// Register your components
const componentsMap = {
  DashBoard: DashBoard,
  Cases: CasesPage,
  Agents: AgentPage,
  About: AboutPage,
};

// Define a reactive variable for the active component
const activeComponent = ref('Home');

// Function to update the active component
function updateComponent(componentName) {
  activeComponent.value = componentName;
}
</script>

<template>
  <div class="layout">
    <aside class="menu-bar">
      <menuBar @menu-item-click="updateComponent" />
    </aside>

    <div class="content">
      <!-- Dynamically load the component -->
      <component :is="componentsMap[activeComponent]" />
    </div>
  </div>
</template>

<style scoped>
.layout {
  display: flex;
  height: 100vh;
}

.menu-bar {
  width: 200px;
  background-color: white;
  color: white;
  padding: 10px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.content {
  flex-grow: 1;
  padding: 20px;
}
</style>
