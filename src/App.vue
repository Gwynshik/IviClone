<template>
	<Header />
	<div class="footer"></div>
</template>

<script>
  import Header from '@/components/Header.vue'
  export default {
    name: 'App',
    components:{
      Header,
  }}
</script>

<style>
  *{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  html, body {
    width: 100%;
    height: 100%;
  }	
  .container{
    width: 100%;
    padding-left: 20%;
    padding-right: 20%;
  }
</style>
