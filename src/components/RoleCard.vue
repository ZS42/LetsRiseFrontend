<template>
  <div class="role-card">
    <h2>{{ title }}</h2>
    <p>{{ description }}</p>
    <button class="apply-button" @click="applyForRole">Apply</button>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    description: String
  },
  methods: {
    applyForRole() {
      alert(`You have applied for the role: ${this.title}`);
    }
  }
};
</script>

<style scoped>
.role-card {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: transform 0.3s ease;
}

.role-card:hover {
  transform: translateY(-10px);
}

h2 {
  color: #333;
  font-size: 1.5rem;
}

p {
  color: #666;
  font-size: 1rem;
  margin: 10px 0;
}

.apply-button {
  padding: 10px 20px;
  background-color: #BFA8FF;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.apply-button:hover {
  background-color: #D1C1FF;
}
</style>
