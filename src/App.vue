<template>
  <div>
    <body>
      <div class="bg-white">
        <img class="logo" src="images/Yugioh_anime_logo.webp" alt="logo">
        <span class="fs-1 align-middle"> Yu-Gi-Oh API</span>
      </div>  
      
      <main class="container">
        <SearchComponent @select-element="selectType"/>
        <div class="row g-4 mt-4 bg-light">
          <p class="text-light w-100 py-4 bg-dark">Found {{ store.cardList.length }} cards</p>
          <CardComponent
            v-for="(element, index) in store.cardList"
            :imageCard="element.card_images[0].image_url_small" 
            :nameCard="element.name" 
            :archetypeCard="element.archetype" 
          />
        </div>
      </main>
  </body>
  </div>
</template>

<script>
import SearchComponent from './components/SearchComponent.vue';
import CardComponent from './components/CardComponent.vue';
import { store } from './data/store.js'
import axios from 'axios'
export default {
  name: 'App',
  components: {
      CardComponent,
      SearchComponent
    },
  data() {
    
    return {
      store,
      params: null
    }
  },
  methods: {
      getCards(){
        const url = store.apiUrl;
        axios.get(url, {params: this.params}).then((response) =>{
          store.cardList = response.data.data;
        }) 
      },
      selectType(search){
        this.params = {archetype: search}
        this.getCards()
      }
    },
    created(){
      this.getCards()
    }
}
</script>

<style lang="scss" scoped>
body{
  background-color: orange;
}

.logo{
  width: 270px;
}

</style>