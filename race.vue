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
