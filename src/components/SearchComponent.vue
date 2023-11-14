<template>
    <div>
        <select v-model='selectAll' @change="$emit('selectElement', selectAll)" class="p-2 my-4" name="" id="">
            <option value="">All</option>
            <option :value="element.archetype_name" v-for="element in store.archetypesList">{{ element.archetype_name }}</option>
        </select>
    </div>
</template>

<script>
import { store } from '../data/store'
    export default {
        name: 'SearchComponent',
        data(){
            return{
                selectAll: '',
                store
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>