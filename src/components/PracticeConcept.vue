<template>
    <div class="practice-concept">
      <h2>Practice the Concept</h2>
      <textarea v-model="userInput" placeholder="Type your answer please ..." class="answer-textbox"></textarea>
      <button @click="compareAnswers" class="compare-button">Compare</button>
      <div v-if="showAnswer" class="answer-section">
        Your Answer:
        <p>{{ userInput }}</p>
        <br>
        
      </div>
      <div class="btnDisplay" >
      <button @click="clearAnswers" class="clear-button">Clear Answer</button>
        <button @click="toggleConceptVisibility" class="toggle-concept-button">{{ showConcept ? 'Hide Concept' : 'Show Concept' }}</button>
    </div>
      <div v-if="showWarning" class="warning-message">
        You forgot to type an answer!  Enter answer Please!
      </div>
      <Concept v-if="showConcept" />
    </div>
  </template>
  
  <script>
  import Concept from "@/components/ConceptStore.vue";
  
  export default {
    data() {
      return {
        userInput: "",
        correctAnswer: "The correct answer", 
        showAnswer: false,
        showConcept: true, 
        showWarning: false
      };
    },
    mounted() {
      this.userInput = localStorage.getItem("userInput") || "";
      this.showAnswer = localStorage.getItem("showAnswer") === "true";
      this.showConcept = localStorage.getItem("showConcept") !== "true";
    },
    methods: {
      compareAnswers() {
        if (this.userInput.trim() === "") {
          this.showWarning = true;
          return; 
        }
  
        this.showWarning = false; 
        this.showAnswer = true; 
        localStorage.setItem("showAnswer", "true");
      },
      clearAnswers() {
        this.userInput = "";
        this.showAnswer = false;
        this.showWarning = false; 
        localStorage.removeItem("userInput");
        localStorage.removeItem("showAnswer");
      },
      toggleConceptVisibility() {
        this.showConcept = !this.showConcept;
        localStorage.setItem("showConcept", this.showConcept.toString());
      }
    },
    watch: { 
      userInput: {
        handler(newValue) {
          localStorage.setItem("userInput", newValue);
        },
        immediate: true
      },
      showAnswer: {
        handler(newValue) {
          localStorage.setItem("showAnswer", newValue.toString());
        },
        immediate: true 
      },
      showConcept: {
        handler(newValue) {
          localStorage.setItem("showConcept", newValue.toString());
        },
        immediate: true
      }
    },
    components: {
      Concept
    }
  };
  </script>
  
  <style scoped>

.practice-concept {
  text-align: center;
  margin-top: 20px;
}

.answer-textbox {
  width: 100%;
  height: 100px; 
  padding: 10px;
  font-size: 16px;
  margin-bottom: 10px;
}

.compare-button {
    padding: 5px;
    border-radius: 5px;
    background-color:#72A537;
}
.compare-button:hover {
    transition: 0.4s background-color;
    background-color: #000000;
    color: rgb(255, 255, 255);
}
.btnDisplay{
    display: block;

}
.answer-section {
  margin-top: 20px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 18px; 
  line-height: 1.5;  
  max-height: 300px; 
  overflow-y: auto; 
  padding: 10px; 
}
.clear-button{
    background-color: #C43302;
    color: rgb(255, 255, 255);
}
.clear-button:hover{
    transition: 0.4s background-color;
    background-color: #010221;
}
.toggle-concept-button{
    background-color:#EDAA25;
    color: black;
}
.toggle-concept-button:hover{
    transition: 0.4s background-color;
    background-color: #010221;
    color: rgb(255, 255, 255);
}
.clear-button, .toggle-concept-button{
    padding: 5px;
    border-radius: 5px;
  }
.answer-section{
    text-shadow: #000000 1px 1px 3px ;
    font-family: 'Franklin Gothic Medium',  Arial, sans-serif;
    font-style: italic;
}
.warning-message {
  color: #860d00;
  margin-top: 10px;
  font-weight: bold;
  background-color: #f39c12;
  padding-block: 10px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
</style>
