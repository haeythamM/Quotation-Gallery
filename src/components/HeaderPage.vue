<!-- Header component  -->
<template>
  <div class="app-header">
    <div>
      <!-- picture link  -->
    <img alt="Vue logo" :src="require('@/assets/logo.png')">
  </div>
    <h1>{{ title }}</h1>
     
  </div>
</template>

<script>

export default {
  data() {
    return {
      name: 'HeaderPage',
      title: "Quotation Gallery"
    };
  }
};
</script>

<style scoped>
img{
  width: 6%;
  /* picture size  */
}
.app-header {
  background-color: #EDAA25;
  color: #000000;
  width: 100%;
  text-align: center;
  padding: 1em;
  font-family: sans-serif;   
}
</style>
