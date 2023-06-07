<template>
<h1>Create Form</h1>
<form action="">
    <input type="text" v-model="property.address" placeholder="address">
    <input type="text" v-model="property.city" placeholder="city">
    <input type="text" v-model="property.img" placeholder="img">
    <input type="text" v-model="property.state" placeholder="state">
    <input type="text" v-model="property.type" placeholder="type">
    <input type="text" v-model="property.zip" placeholder="zip">
    <input type="submit">
    <button @click="{{ addProperty }}"> submit </button>

</form>
</template>

<script>
import axios from 'axios';
import { response } from 'express';

export default {
    data: function (){
        return {
            property: {
                address: "",
                city: "",
                img: "",
                price: "",
                state: "",
                type: "",
                zip: ""

            }
        }
    },
    method: {
        handleChange(){
        
        },
        addProperty (){
            axios
                .post("http://localhost:8000", {
                    property: this.property
                })
                .then((res)=>{
                    if(res.status ==201) {
                        console.log("succesful")
                    }
        })}
    
}
}
</script>