<template>
    
    <div>
    <CityImg/>
    <navBar/> 
    <ModalTest/>
    <dataProperty/> 
    </div>
    
</template>

<script>
import navBar from './components/navBar.vue';
import CityImg from './components/cityImg.vue';
import dataProperty from './components/dataProperty.vue';
import modalTest from './components/modalTest.vue';
import ModalTest from './components/modalTest.vue';
export default {
    components: {
    navBar,
    CityImg,
    dataProperty,
    modalTest,
    ModalTest
},

}
</script>