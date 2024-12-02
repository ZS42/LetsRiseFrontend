<!-- src/components/ApplicationForm.vue -->
<template>
  <div class="application-form">
    <h2>Application Form for {{ role.title}}</h2>
    <form @submit.prevent="submitApplication">
      <label for="name">Full Name:</label>
      <input 
       type="text" 
       id="name" 
       v-model="name" 
       autocomplete="name"
       required 
      />

      <label for="email">Email Address:</label>
      <input 
       type="email" 
       id="email" 
       v-model="email"
       autocomplete="email" 
       required 
      />

      <label for="message">Why do you want this role?</label>
      <textarea 
       id="message" 
       v-model="message"
       autocomplete="off" 
       required
       ></textarea>

      <button type="submit">Submit Application</button>
    </form>
    <button @click="cancel">Cancel</button>
  </div>
</template>

<script>
export default {
  mounted() {
    console.log('Application form is mounted', this.role);
  },
  props: {
    role: {
        type: Object,
        required: true
        }
  },
  data() {
    return {
      name: '',
      email: '',
      message: ''
    };
  },
  methods: {
    submitApplication() {
      // In a real app, you would send this data to a server
      console.log('Application submitted for:', this.role);
      // Clear the form after submission
      this.name = '';
      this.email = '';
      this.message = '';
      alert('Application submitted!');
      this.$emit('cancel');
    },
    cancel() {
      // Close the application form
      this.$emit('cancel');
    }
  }
};
</script>

<style scoped>
.application-form {
  background: #fff;
  color: black;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 100%;
  margin: auto;
  box-sizing: border-box;
}

h2 {
  text-align: center;
  margin-bottom: 20px;
}

label {
  display: block;
  margin-top: 10px;
}

input, textarea {
  width: 100%;
  padding: 4px;
  margin-top: 5px;
  border: 1px solid #ddd;
  border-radius: 10px;
  background-color: #C0C0C0;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #5D3FD3;
  color: white;
  border: none;
  border-radius: 4px;
  margin-top: 20px;
  cursor: pointer;
}

button:hover {
  background-color: #6e4fd3;
}
</style>
