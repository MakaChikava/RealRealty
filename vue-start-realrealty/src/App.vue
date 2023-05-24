<template>
    <CityImg/>
    <navBar/> 
    <p>Page content here</p>
    <dataProperty/>
</template>

<script>
import navBar from './components/navBar.vue';
import CityImg from './components/cityImg.vue';
import dataProperty from './components/dataProperty.vue';
export default {
    components: {
    navBar,
    CityImg,
    dataProperty
},

}
</script>