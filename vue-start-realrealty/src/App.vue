<template>
    
    <div>
    <CityImg/>
    <navBar/> 
    <dataProperty/> 
    </div>
    
</template>

<script>
import navBar from './components/navBar.vue';
import CityImg from './components/cityImg.vue';
import dataProperty from './components/dataProperty.vue';
export default {
    components: {
    navBar,
    CityImg,
    dataProperty,
},

}
</script>