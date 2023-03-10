<template>
  <div id="app">
    <h1>{{message}}</h1>
  
    <!-- Edit Me Modal -->
    <div class="editMeModal">
      
      <h2 class="editModalH2"> Edit Modal </h2>
      <label for="editModalID">Edit ID</label>
      <input class="editModalID" type="number">
      <label for="editModalName">Edit Name</label>
      <input class="editModalName" type="text">
      <label for="editModalSpecialty">Edit Specialty</label>
      <input class="editModalSpecialty" type="text">
      
      <button class="editMeModalBtn" @click="editMeModal">Edit Me Modal</button>
      
    </div>
    
     <div class="entryContainer">
      <!-- Create new value using v-model? and add new entry -->
      <h2>{{ title }}</h2>
    
    <button @click="recordEntries">Click For Race Entries</button>
    
    <div class="output"></div>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Race Widget',
      entries:
        [
          {ID: 1, name: 'John'}, {ID: 2, name: 'Tyler'}, {ID: 3, name: 'Nick'}, {ID: 4, name: 'Billy'}
        ],
      
    };
  },
  methods: {
    recordEntries() {
      let output = document.querySelector(".output");
      
      output.innerHTML = `<h2> The list of entrants are: ${this.entries}`;
    }
  }
};
</script>

<style lang="scss">
#app {
  text-align: center;
  color: #2c3e50;
  margin: 1rem;
}
  
  h1 {
    font-size: 1.5rem;
    padding: 1rem;
  }

  button {
    background-color: lightgreen;
    color: black;
    border-radius: 20px;
    padding: 0.5rem;
  }
  
  button:hover {
    cursor: pointer;
    background-color: white;
    color: red;
  }
</style>
