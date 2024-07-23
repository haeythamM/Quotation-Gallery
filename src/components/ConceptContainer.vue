<!-- ConceptContainer.vue is the parent -->
<template>
    <fieldset>
        <legend>Second Part (Concept of the Day) :</legend>
    <div class="concept-container">
      <!-- toggle Concept button -->
      <button class="buttonText" @click="toggleConcept">{{ buttonText }}</button>
      <!-- loop to show the  concept  -->
      <Concept v-if="showConcept" />
      <PracticeConcept v-else />
    </div>
</fieldset>
  </template>
  <script>
  //import children 
  import Concept from "@/components/ConceptStore.vue";
  import PracticeConcept from "@/components/PracticeConcept.vue";
  
  export default {
    data() {
      return {
        showConcept: true
      };
    },
    methods: {
      toggleConcept() {
        this.showConcept = !this.showConcept;
      }
    },
    computed: {
      buttonText() {
        return this.showConcept ? "Practice the Concept" : "Back to Concept";
      }
    },
    components: {
      Concept,
      PracticeConcept
    }
  };
  </script>
 <style scoped>
 .concept-container {
   text-align: center;
   margin-top: 20px;
   padding : 4rem;
   max-width: 1000px;
   background-color:#0A7373 ;
   color: #ffffff;
 }
 .toggle-button {
   padding: 10px;
   font-size: 16px;
   background-color: #3498db;
   color: #ffffff;
   border: none;
   cursor: pointer;
 }
 .toggle-button{
    padding: 5px;
    font-size: 14px;
    margin-top: 10px;
    cursor: pointer;
}
.buttonText{
    padding: 5px;
    border-radius: 5px;
    background-color:#72A537;
}
.buttonText:hover{
    transition: 0.4s background-color;
    background-color: #C43302;
    color: rgb(255, 255, 255);
  }
 fieldset{
    padding: 10px;
    margin: 4rem;
 }
 </style>
  