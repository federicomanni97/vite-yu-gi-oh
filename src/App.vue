<template>
  <div>
    <body>
      <div class="bg-white">
        <img class="logo" src="images/Yugioh_anime_logo.webp" alt="logo">
        <span class="fs-1 align-middle"> Yu-Gi-Oh API</span>
      </div>  
      <main class="container">
        <div class="row g-5 mt-4 bg-light">
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
import CardComponent from './components/CardComponent.vue';
import { store } from './data/store.js'
import axios from 'axios'
export default {
  name: 'App',
  components: {
      CardComponent,
    },
  data() {
    
    return {
      store
    }
  },
  methods: {
      getCards(){
        const url = store.apiUrl;
        axios.get(url).then((response) =>{
          store.cardList = response.data.data;
        })
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