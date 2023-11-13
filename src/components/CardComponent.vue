<template>
    <div class="col-2">  
            <img :src="imageCard" :alt="nameCard"/>
            <div class="text-center">
                <h5>{{ nameCard }}</h5>
                <p>{{ archetypeCard }}</p>
            </div>
     </div>
</template>

<script>
import {store} from '../data/store.js'
export default {
    name: 'CardComponent',
    props: 
            {
                imageCard: String,
                nameCard: String,
                archetypeCard: String,
            },
    data() {
        return {
            store
        }
    }
}
</script>

<style lang="scss" scoped>
img{
    width: 100%;
}

</style>