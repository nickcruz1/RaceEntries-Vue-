<!-- Continue adding features to this app -->
<!-- List of New Features: 


-->

<template>
  <div id="app">
    <h1>{{ message }}</h1>
    
    
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
      
        <!-- Add New Entrant ID -->
       <label for="newEntrantID">Enter New Entrant ID Below:</label>
 <input
        id="newEntrantID"
        v-model="newEntrantID"
        class="entryValue"
        type="number"
      />
      
       <!-- Add New Entrant Name -->
      <label for="newEntrantName">Enter New Entrant Name Below:</label>
        <input
        id="newEntrantName"
        v-model="newEntrantName"
        class="entryValue"
        type="text"
      />
       <!-- Add New Entrant Specialty -->
        <label for="enterEntrant">Enter Entrant Specialty Below:</label>
         <input
        id="newEntrantSpecialty"
        v-model="newEntrantSpecialty"
        class="entryValue"
        type="text"
      />
   
      <input v-model="newEntrant" class="entryValue" type="text" />
      <button @click="recordEntries">Click For Race Entries</button>

      <h2 class="entryH2">List of Entrants: {{ newEntrant }}</h2>

      <div class="output"></div>
      
      <!-- Displays entries length using v-if and v-else below -->
      <div v-if="this.entries.length == 0">
        {{ this.entries.length }} Entries Left :(
      </div>
      
       <!-- v-else statement -->
      <div v-else>
        <p>Number Of Entrants: {{ this.entries.length }}</p>
      </div>

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
      message: "Race Widget",
      title: "Entry List",
      newEntrant: "",
      editModalID: "",
      editModalname: "",
      editModalspecialty: "",
      entries: [
        { ID: 1, name: "John", specialty: "5k" },
        { ID: 2, name: "Tyler", specialty: "10k" },
        { ID: 3, name: "Nick", specialty: "50k" },
        { ID: 4, name: "Billy", specialty: "Marathon" },
         { ID: 5, name: "Sam", specialty: "100m Dash" }
      ]
    };
  },
  methods: {
    recordEntries() {
       let output = document.querySelector(".output");
      let entryValues = document.querySelectorAll(".entryValue");
      let entrantList = document.querySelector(".entrantList");
      let entries = this.entries;
      let newID = document.querySelector("#newEntrantID");
      let newName = document.querySelector("#newEntrantName");
      let newSpecialty = document.querySelector("#newEntrantSpecialty");
      let newEntryValue = document.querySelectorAll(".entryValue");

     
      let theO = `Entrant ID: ${newID.value} 
          <br />
          Name: ${newName.value}
          <br />
          Specialty:  ${newSpecialty.value}`;

      if (newName.value == "" || newSpecialty.value == "" || newID.value == 0) {
        alert("Not cool");
      } else {
        console.log("Entry Added");
        // entries.unshift(theO);
        // newID.innerHTML == "";
        // newName.value == "";
        // newSpecialty.value == "";
      }
    },
    deleteMe() {
      let entrantList = document.querySelector(".entrantList");
      let entries = this.entries;

      entries.shift();
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

<style lang="scss">
$lightC: rgb(0, 0, 0, 0.4);

body {
  background-color: $lightC;
}

#app {
  text-align: center;
  color: #2c3e50;
  margin: 1rem;
}

.entryH2 {
  margin: 1rem;
}

.entryContainer {
  background-color: lightgray;
  border: 3px solid black;
  padding: 2rem;
  border-radius: 10px;
  display: flex;
  width: 60%;
  max-width: 1000px;
  justify-content: center;
  flex-direction: column;
  margin: auto;

  input[type="text"] {
    width: 50%;
    display: block;
    margin: auto;
  }

  .entrantList {
    display: block;
    margin-left: auto;
    margin-right: auto;
    border: 2px solid blue;
    padding: 0.5rem;
    width: 80%;
  }

  .btnContainer {
    display: flex;
    justify-content: center;
  }

  .editMeBtn {
    @extend .deleteMeBtn;
    background-color: darkblue !important;
  }

  .deleteMeBtn {
    background-color: red;
    color: white;
    width: 70px;
  }

  button {
    width: 50%;
    margin: 1.5rem auto auto auto;
  }
}
  
   .editMeModal {
     .editModalH2 {
       text-align: center;
       margin-bottom: 0.5rem;
     }
     
    background-color: green;
    display: flex;
    flex-direction: column;
    border: 3px solid white;
     border-radius: 20px;
     color: white;
    padding: 2rem;
    position: absolute;
    top: 50%;
    left: 70%;
    transform: translate(-50%, -50%);
     
     .editMeModalBtn {
       margin-top: 1rem;
     }
}
  
  

h1 {
  color: rgb(255, 255, 255, 0.8);
  font-size: 1.5rem;
  padding: 1rem;
}

h2 {
  font-size: 1.2rem;
  font-weight: bold;
  text-align: left;
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

// Media Queries Section //

@media screen and (min-width: 1000px) {
  .entryContainer {
    width: 60%;
  }
}

@media screen and (max-width: 750px) {
  .entryContainer {
    width: 70%;
  }
}

@media screen and (max-width: 500px) {
  .entryContainer {
    width: 80%;
  }
}
</style>
