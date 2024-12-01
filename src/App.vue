<template>
  <div class="dashboard">
    <h1>Student Dashboard</h1>
    <div class="role-cards-container">
      <RoleCard
        v-for="(role, index) in recommendedRoles"
        :key="index"
        :title="role.title"
        :description="role.description"
      />
    </div>
  </div>
</template>

<script>
import RoleCard from './components/RoleCard.vue';

export default {
  components: {
    RoleCard
  },
  data() {
    return {
      recommendedRoles: [
        {
          title: "Backend Engineer Intern",
          description: "Collaborate with a team to develop server-side applications and ensure data flows smoothly between users and servers."
        },
        {
          title: "Frontend Engineer Intern",
          description: "Build interactive and responsive user interfaces, ensuring seamless user experiences across devices."
        },
        {
          title: "UI/UX Designer Intern",
          description: "Design user-friendly interfaces and enhance the user experience."
        },
        {
          title: "Data Engineer Intern",
          description: "Design and maintain robust data pipelines to collect, process, and analyze data for actionable insights."
        },
        {
          title: "AI Engineer Intern",
          description: "Develop AI-driven solutions and apply machine learning techniques to optimize processes and solve complex challenges."
        }
      ]
    };
  }
};
</script>

<style>
.dashboard {
  text-align: center;
  padding: 20px;
  background: linear-gradient(to bottom, #FF4D85, #5D3FD3); /* Apply gradient */
  min-height: 100vh; /* Ensures the background covers the entire viewport */
  color: white; /* Adjust text color for readability on the gradient */
  display: flex;
  flex-direction: column; /* Ensure proper layout for children */
  justify-content: center; /* Center content vertically */
  align-items: center; /* Center content horizontally */
}

h1 {
  color: white;
}

.role-cards-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

@media (max-width: 768px) {
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


<!-- <script setup>
import HelloWorld from './components/HelloWorld.vue'
</script> -->

<!-- <template>
  <div>
    <a href="https://vite.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template> -->

<!-- <style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style> -->