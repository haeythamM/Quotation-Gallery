<!-- This is footer component  -->
<template>
    <div class="app-footer">
      <!-- to display the author name - Haeytham Almalak date time  -->
      <p><small>&copy; {{author}}</small></p>
      <P><small> {{ dateTimeTitle }}  {{ currentDate }} </small></p>
        <p><small>User language : {{ userRegion }}</small></p>
    </div>
  </template>
  <script>
  export default {
    data() {
      return {
        author: 'Haeytham Almalak',
        dateTimeTitle : 'The time and the date in your region are',
        currentDate: new Date().toLocaleString(),
        userRegion: window.navigator.language,
      };
    }
  };
  </script>
  <style scoped>
  .app-footer {
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    background-color: #3333;
    color: white;
    text-align: center;
    padding: 1rem;
    position: fixed  ;
    width: 100%;
    bottom: 0;
    text-shadow: black 1px 1px 2px;
  }
  </style>