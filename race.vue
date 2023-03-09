<template>
  <div id="app">
    <h1>{{message}}</h1>
  
    <div v-for="entry in entries">
      <h2>Marathon List:<br>{{ entry.ID }} {{ entry.name }}</h2>
    </div>
    
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
