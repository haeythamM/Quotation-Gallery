<template>
  <header-page></header-page>
  <title-component titleText="Have Fun" />
  <title-component subtitleText="Quotation Gallery &ndash; Vue.js Concepts" />
  <quote-component></quote-component>
  <div>
    <hr>
  </div>
  <div id="app">
    <ConceptContainer />
    <p><a
        href="https://www.indeed.com/career-advice/interviewing/object-oriented-programming-interview-questions#:~:text=Here%20are%20a%20few%20knowledge-specific%20questions%20with%20sample,Describe%20two%20differences%20between%20procedural%20programming%20and%20OOP."
        target="_blank">Resource of the Questions and the Answers</a></p>
  </div>
  <footer-page></footer-page>
</template>
<!-- imports part  -->
<script>
import HeaderPage from './components/HeaderPage.vue';
import FooterPage from './components/FootersPage.vue';
import QuoteComponent from './components/QuoteComponent.vue';
import TitleComponent from './components/TitleComponent';
import ConceptContainer from "@/components/ConceptContainer.vue";

export default {
  name: 'App',
  components: {
    HeaderPage,
    FooterPage,
    QuoteComponent,
    TitleComponent,
    ConceptContainer,
  }
}
</script>

<style>
* {
  padding: 0;

  margin: 0;
}

/* his is my colors plate to use it 
 Color Theme Swatches in Hex
.RockON!-1-hex { color: #010221; }
.RockON!-2-hex { color: #0A7373; }
.RockON!-3-hex { color: #B7BF99; }
.RockON!-4-hex { color: #EDAA25; }
.RockON!-5-hex { color: #C43302; }

/* Color Theme Swatches in RGBA */
/* .RockON!-1-rgba { color: rgba(1, 2, 33, 1); }
.RockON!-2-rgba { color: rgba(10, 114, 114, 1); }
.RockON!-3-rgba { color: rgba(182, 191, 153, 1); }
.RockON!-4-rgba { color: rgba(237, 169, 36, 1); }
.RockON!-5-rgba { color: rgba(196, 50, 1, 1); } */

/* Color Theme Swatches in HSLA */
/* .RockON!-1-hsla { color: hsla(238, 94, 6, 1); }
.RockON!-2-hsla { color: hsla(180, 83, 24, 1); }
.RockON!-3-hsla { color: hsla(72, 22, 67, 1); }
.RockON!-4-hsla { color: hsla(39, 84, 53, 1); }
.RockON!-5-hsla { color: hsla(15, 98, 38, 1); } */

body {
  background-color: #B7BF99;
  overflow-x: hidden;
}

#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  padding-bottom: 5rem;
  align-items: center;
}
</style>
 