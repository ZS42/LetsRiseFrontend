<template>
  <div class="app-container">
    <header class="app-header">
      <img src="./assets/Let's Rise logo.png" alt="Company Logo" class="logo" />
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
      isApplying: false, // New property to control visibility
      selectedRole: ''
    };
  },
  methods: {
    showForm(role) {
      this.selectedRole = role;  // Store the role that is being applied for
      this.isFormVisible = true; // Show the application form
      this.isApplying = true; // Hide the role cards
    },
    hideForm() {
      this.isFormVisible = false; // Hide the application form when canceled
      this.isApplying = false; // Show the role cards again
    }
  }
};
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  overflow-x: hidden; 
}
#app {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}
.app-header {
  display: flex;
  align-items: center;
  padding: 10px 20px;
  background-color: #3f3f3f; /* Header background color */
  color: white;
  position: fixed;
  top: 0;
  z-index: 1000; /* Ensures it stays on top during scroll */
  width: 100vw;
  max-width: 100%; /* Explicitly set full width */
}
.app-header-content {
  width: 100%; /* Make it as wide as the parent */
  max-width: 1200px; /* Optional: limit max content width */
  padding: 10px 20px; /* Add padding inside the content box */
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
  background: linear-gradient(to bottom, #FF4D85, #5D3FD3); /* Apply gradient */
  min-height: 100vh; /* Ensures the background covers the entire viewport */
  width: 100vw; /* Full viewport width */
  margin: 0;
  box-sizing: border-box;
  color: white; /* Adjust text color for readability on the gradient */
  display: flex;
  flex-direction: column; /* Ensure proper layout for children */
  justify-content: center; /* Center content vertically */
  align-items: center; /* Center content horizontally */
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
