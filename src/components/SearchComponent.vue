<template>
    <div>
        <select v-model='selectAll' @change="$emit('selectElement', selectAll)" class="p-2 my-4" name="" id="">
            <option value="">All</option>
            <option value="alien">Alien</option>
            <option value="crystal beast">Crystal Beast</option>
            <option value="elemental hero">Elemental HERO</option>
            <option value="egyptian god">Egyptian God</option>
            <option value="noble knight">Noble Knight</option>
        </select>
    </div>
</template>

<script>
    export default {
        name: 'SearchComponent',
        data(){
            return{
                selectAll: ''
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>