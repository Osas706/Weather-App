<script>
import Weather from '@/components/weather.vue'
import { defineComponent } from 'vue'
export default defineComponent({
  name:'App',
  components: {
    Weather
  },
  data(){
    return{
      city: '',
      showWeather: false
    }
  },
  methods:{
    async searchWeather(){
      this.showWeather = false;
      await this.$nextTick();
      this.showWeather = true;
    }
  }
})

</script>

<template>
  <div class="app">
    <div class="header container h-10 p-5">
      <h1 class="mb-5">Weather App</h1>
      <div class="d-flex justify-content-center h-80">
        <div class="searchbar w-50 mx-2">
          <input type="text" class="input form-control" v-model="city" placeholder="Enter a city">
        </div>
        <button class="btn-search btn btn-primary" @click="searchWeather">
          Search <i class="fa fa-search"></i>
        </button>
      </div>
    </div>
    <br>
    
    <Weather :city="city" v-if="showWeather"/>
  </div>
</template>

<style>
body{
  background-color: #121212 !important;
  margin: 0;
  padding: 0;
}

.app{
  width: 90vw;
  height: 100vh;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.header{
  background-color: #212730;
  border-radius: 20px;
  color: #fff;
  text-align: center;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

.btn{
  background-image: linear-gradient(to right, cyan, magenta);
  height: 2.4rem;
}


</style>
