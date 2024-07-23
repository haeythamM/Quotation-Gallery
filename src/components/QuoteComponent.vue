<template>
    <div class="quote-container">
      <div v-for="(quote, index) in quotes" :key="index" class="input-container quote-input">
        <input v-model="quote.title" placeholder="Enter Title" />
        <input v-model="quote.sourceLink" placeholder="Enter Source Link" />
        <textarea v-model="quote.quotation" placeholder="Enter Description"></textarea>
        <!-- BUtton Review quote  -->
        <button @click="toggleReviewStatus(index)">
          {{ quote.inReview ? 'Remove from Review' : 'Add Quotation' }}
        </button>
      </div>
      <div class="display-box" v-if="reviewedQuotes.length > 0">
       
        <h2>&nbsp;&nbsp;Saved quote</h2>
        <!-- TO DISPLAY Saved quote -->
        <div v-for="(quote, index) in reviewedQuotes" :key="index" class="quote-display">
          <h3>{{ quote.title }}</h3> 
          <blockquote>
            <!-- TO DISPLAY inReview  -->
            <p v-show="quote.inReview">{{ quote.showDescription ? quote.quotation : 'The quote is currently hidden!' }}</p>
            <footer>
              <!-- to display the link source  -->
              <a id="theLink" :href="quote.sourceLink" target="_blank" rel="noopener noreferrer">Source</a>
              <hr>
              <button @click="deleteReviewedQuote(index)">Delete</button> <!-- Delete button -->
              <button @click="toggleDescriptionVisibility(index)">
                {{ quote.showDescription ? 'Hide Quote' : 'Show Quote' }}
              </button>
            </footer>
          </blockquote>
        </div>
      </div>
      <button @click="addQuote">Add New Quote</button>
    </div>
  </template>
  <script>
  export default {
    data() { 
      return {
        quotes: JSON.parse(localStorage.getItem('quotes')) || [],//parse to JSON - localStorage see comment below
        reviewedQuotes: JSON.parse(localStorage.getItem('reviewedQuotes')) || [],
      };
    },
    methods: {
      //to add new quote to the array
      addQuote() {
        this.quotes.push({
          title: '',
          quotation: '',
          sourceLink: '',
          inReview: false,
          showDescription: false,
        });
        this.saveToLocalStorage();
      },
      //  quote  ( reviewedQuotes) array  
      toggleReviewStatus(index) {
        const quote = this.quotes[index];
        quote.inReview = !quote.inReview;
        quote.showDescription = false; // to reset "showDescription"  
  
        if (quote.inReview) {
          this.reviewedQuotes.push({ ...quote });//using push
          this.quotes.splice(index, 1);
        } else {
          this.quotes.push({ ...quote });
          this.reviewedQuotes.splice(index, 1);
        }
        this.saveToLocalStorage();
      },
      //to delete reviewed quote
      deleteReviewedQuote(index) {
        this.reviewedQuotes.splice(index, 1);
        this.saveToLocalStorage();
      },
      //this method to toggle description viability 
      toggleDescriptionVisibility(index) {
        const quote = this.reviewedQuotes[index];
        quote.showDescription = !quote.showDescription;
        this.saveToLocalStorage();
      },
        //to save in local storage (quotes  and reviewedQuotes)
       // declare var localStorage: Storage;
      // Available only in secure contexts. 
      saveToLocalStorage() {
        localStorage.setItem('quotes', JSON.stringify(this.quotes));
        localStorage.setItem('reviewedQuotes', JSON.stringify(this.reviewedQuotes));
      },
    },
  };
  </script>
  <style scoped>
  .quote-container {
    margin: 20px;
    padding: 2rem;
  }
  .quote-input {
    margin-bottom: 20px;
    background-color:#0A7373;
    padding: 2rem;
  }
  .quote-display {
    margin-bottom: 20px;
    border: 3px solid #ccc;
    padding: 3rem;
    border-radius: 10px;
    background-color: #72A537;
  }
  .input-container input,
  .input-container textarea {
    width: 100%;
    margin-bottom: 10px;
  }
  
  .display-box {
    margin-top: 20px;
    background-color:#0A7373;
    box-shadow: #525252 5px 5px 5px;
    border: #181b1b;
  }
  button{
    padding: 5px;
    border-radius: 5px;
    background-color:#72A537;
  }
  button:hover{
    transition: 0.4s background-color;
    background-color: #C43302;
    color: rgb(255, 255, 255);
  }

  footer > button{
    margin: 10px;
    display: inline-block;
    background-color: #0A7373;
    color: white;
}
footer > button:hover{
    transition: 0.4s background-color;
    background-color: #C43302;
    color: rgb(255, 255, 255);
}
h2{
    color: white;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: large;
  }
  hr{
    margin: 10px;
    background-color: #4d7025;
    
  }
  #theLink:hover{
    color: white;
  }
  p{
    padding: 10px;
  }
  </style>
  