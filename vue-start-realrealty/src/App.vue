<template>
    <CityImg/>
    <navBar/> 
    <createForm/>
    <dataProperty/>
</template>

<script>
import navBar from './components/navBar.vue';
import CityImg from './components/cityImg.vue';
import dataProperty from './components/dataProperty.vue';
import createForm from './components/createForm.vue';
export default {
    components: {
    navBar,
    CityImg,
    dataProperty,
    createForm
},

}
</script>