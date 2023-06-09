<template>
<h1>Create Form</h1>
<form action="">
    <input type="text" v-model="property.address" placeholder="address">
    <input type="text" v-model="property.city" placeholder="city">
    <input type="text" v-model="property.img" placeholder="img">
    <input type="text" v-model="property.state" placeholder="state">
    <input type="text" v-model="property.type" placeholder="type">
    <input type="text" v-model="property.zip" placeholder="zip">
</form>
<button @click="addProperty()"> submit </button>
</template>

<script>
import axios from 'axios';

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
        addProperty(){
            axios
                .post("http://localhost:8000/house", {
                    address: this.property.address,
                    city: this.property.city,
                    img: this.property.img,
                    price: this.property.price,
                    state: this.property.state,
                    type: this.property.type,
                    zip: this.property.zip
                })
                .then((res)=>{
                    if(res.status ==201) {
                        console.log("succesful")
                    }
        })}
    
}
}
</script>