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
    
     <label for="enterEntrant">Enter Entrant Below:</label>
      <input v-model="newEntrant" class="entryValue" type="text" />
      <button @click="recordEntries">Click For Race Entries</button>

      <h2 class="entryH2">List of Entrants: {{ newEntrant }}</h2>

      <div class="output"></div>
      
         <p>Number Of Entrants: {{this.entries.length}}</p>
 <!-- Contains list of Entrants -->
      <div class="entrantList" v-for="entry in entries">
        <h2>
          Entrant ID: {{ entry.ID }}
          <br />
          Name: {{ entry.name }}
          <br />
          Speciality: {{ entry.specialty }}

          <div class="btnContainer">
            <button class="editMeBtn" @click="editMe">Edit Btn</button>
            <button class="deleteMeBtn" @click="deleteMe">Delete -</button>
          </div>
        </h2>
      </div>
      

 
      
      
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      message: 'Race Widget',
      entries:
        title: "Entry List",
      newEntrant: "",
      editModalID: "",
      editModalname: "",
      editModalspecialty: "",
        [
          {ID: 1, name: 'John'}, {ID: 2, name: 'Tyler'}, {ID: 3, name: 'Nick'}, {ID: 4, name: 'Billy'}
        ],
      
    };
    
  },
   entries: [
        { ID: 1, name: "John", specialty: "5k" },
        { ID: 2, name: "Tyler", specialty: "10k" },
        { ID: 3, name: "Nick", specialty: "50k" },
        { ID: 4, name: "Billy", specialty: "Marathon" }
      ]
    };
  },
 methods: {
    recordEntries() {
      let entryValue = document.querySelector(".entryValue");
      let output = document.querySelector(".output");

      output.innerHTML = `<h2> Entrant Added: ${entryValue.value}`;
    },
    deleteMe() {
      let entrantList = document.querySelector(".entrantList");
      let entries = this.entries;

      entries.pop();
      // entrantList.remove();
    },
    editMe() {
      let editModal = document.querySelector(".editMeModal");

      editModal.style.display = "block";
    },
    editMeModal() {
      let editMeModal = document.querySelector(".editMeModal")
      alert("Modal Edited")
      
      editMeModal.style.display = "none";
    }
  }
};
</script>
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
