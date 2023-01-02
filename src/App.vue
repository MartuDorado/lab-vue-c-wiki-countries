<template>
  <div class="app">
    <NavbarComponent></NavbarComponent>
    
    
        <CountriesListComponent></CountriesListComponent>
      </div>
  
 
 
</template>

<script>
import NavbarComponent from './components/NavbarComponent.vue';
import CountriesListComponent from './components/CountriesListComponent.vue';
export default{
  components:{
    NavbarComponent,
    CountriesListComponent
  }
}
</script>

<style></style>
