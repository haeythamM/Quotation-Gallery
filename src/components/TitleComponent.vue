<template>
  <link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Lobster&display=swap" rel="stylesheet">
    <div class="appTitle">
      <h1>{{ titleText }}</h1>
      <h3>{{ subtitleText }}</h3>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      titleText: {
        type: String,
        required: true
      },
      subtitleText: {
        type: String,
        required: true
      }
    }
  };
  </script>
  
  <style scoped>
  .appTitle{
    padding-top: 2rem;
    text-align: center;
    font-family: 'Lobster', sans-serif;
  }
  </style>
  