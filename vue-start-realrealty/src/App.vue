<template>
    <CityImg/>
    <navBar/> 
    <p>Page content here</p>
</template>

<script>
import navBar from './components/navBar.vue';
import CityImg from './components/cityImg.vue';

export default {
    components: {
    navBar,
    CityImg
},

}
</script>