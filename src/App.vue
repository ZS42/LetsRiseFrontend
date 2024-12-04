<template>
  <div class="app-container">
    <header class="app-header">
      <img src="./assets/LetsRiseLogo.png" alt="Company Logo" class="logo" />
    </header>
    <div class="dashboard">
      <h1 v-if="!isFormVisible">Student Dashboard</h1>

    <div v-if="!isApplying" class="role-cards-container">
      <RoleCard
        v-for="(role, index) in recommendedRoles"
        :key="index"
        :title="role.title"
        :description="role.description"
        @apply="showForm"
      />
    </div>
    <div v-else>
     <!-- Conditional rendering of the Application Form -->
     <ApplicationForm 
     v-if="isFormVisible" 
     @cancel="hideForm" 
     :role="selectedRole"
     @mounted="console.log('ApplicationForm mounted')"
     />
    </div>  
    </div>     
  </div>
</template>

<script>
// Import necesssary components
import RoleCard from './components/RoleCard.vue';
import ApplicationForm from './components/ApplicationForm.vue';
import { recommendedRoles } from './mockData'

export default {
  components: {
    RoleCard,
    ApplicationForm
  },
  data() {
    return  {
      // Use the imported mock data here
      recommendedRoles,
      isFormVisible: false,
      isApplying: false,
      selectedRole: ''
    };
  },
  methods: {
    showForm(role) {
      this.selectedRole = role;  
      this.isFormVisible = true; 
      this.isApplying = true;
    },
    hideForm() {
      this.isFormVisible = false;
      this.isApplying = false;
    }
  }
};
</script>

<style scoped>

.app-header {
  display: flex;
  align-items: center;
  padding: 10px 20px;
  background-color: #3f3f3f;
  color: white;
  position: fixed;
  top: 0;
  z-index: 1000; /* Ensures it stays on top during scroll */
  width: 100vw;
  max-width: 100%;
}
.app-header-content {
  width: 100%;
  max-width: 1200px; 
  padding: 10px 20px;
}
.logo {
  height: 50px;
  margin-right: 15px;
}

h1 {
  font-size: 3.2rem;
  color: white;
}

.role-cards-container {
  width: 100%;
  max-width: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
  margin-top: 20px;
  padding: 0 20px;
}

.dashboard {
  text-align: center;
  padding: 20px;
  background: linear-gradient(to bottom, #FF4D85, #5D3FD3);
  min-height: 100vh;
  width: 100vw;
  margin: 0;
  box-sizing: border-box;
  color: white;
  display: flex;
  flex-direction: column; /* Ensure proper layout for children */
  justify-content: center; 
  align-items: center; 
  overflow-x: hidden; 
}

@media (max-width: 768px) {
  .logo {
    height: 40px; /* Smaller logo */
  }
  .app-header h1 {
    font-size: 1.2rem; /* Smaller font for title */
  }
  .role-cards-container {
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));  /* Adjust for smaller screens */
  }
}

@media (max-width: 480px) {
  .role-cards-container {
    grid-template-columns: 1fr;  /* Single column layout for very small screens */
  }
}
</style>
