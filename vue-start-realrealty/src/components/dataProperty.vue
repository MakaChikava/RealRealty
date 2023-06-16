<template>
    <div>

        <div>

<!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
    <img src="https://cdn3.iconfinder.com/data/icons/font-awesome-regular-1/512/pen-to-square-512.png" class=''>
</button>

<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog">
    <div class="modal-content">
        <div class="modal-header">
        <h1 class="modal-title fs-5" id="exampleModalLabel">Create listing</h1>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">

        <form action="">
            <input type="text" v-model="property.img" placeholder="img">
            <input type="text" v-model="property.bedrooms" placeholder="bedrooms">
            <input type="text" v-model="property.baths" placeholder="baths">
            <input type="text" v-model="property.address" placeholder="address">
            <input type="text" v-model="property.city" placeholder="city">
            <input type="text" v-model="property.state" placeholder="state">
            <input type="text" v-model="property.zip" placeholder="zip">
            <input type="text" v-model="property.type" placeholder="type">
        </form>
        <button @click="addProperty()"> submit </button>

        </div>
        <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="addProperty()">Submit</button>
        </div>
    </div>
    </div>
</div>
    
</div>

        <h1>Property Data</h1>
        <form>
            <input type="text">
            <button>search</button>
        </form>

        <div class="container text-center">
            <ul>
                <div class="row row-cols-2 row-cols-lg-4 g-2 g-lg-3">
                <li v-for="property in properties" :key="property._id">
                <div class="card" style="width: 18rem;">
                    <img :src="property.img" class="card-img-top" alt="...">
                <div class="card-body">
                    <p class="card-text">{{ property.price }}</p>
                    <p class="card-text">bedrooms: {{ property.bedrooms }}</p>
                    <p class="card-text">baths: {{ property.baths }}</p>
                    <p class="card-text">{{ property.address }}, {{ property.city }} {{property.state}}, {{ property.zip }}</p>
                    <button @click="deleteProperty(property._id)">delete</button>

                    <details>
                        <summary>Edit</summary>
                        <form>
                            <input type="text" v-model="changeProperty.img" placeholder="img">
                            <input type="text" v-model="changeProperty.bedrooms" placeholder="bedrooms">
                            <input type="text" v-model="changeProperty.baths" placeholder="baths">
                            <input type="text" v-model="changeProperty.address" placeholder="address">
                            <input type="text" v-model="changeProperty.city" placeholder="city">
                            <input type="text" v-model="changeProperty.state" placeholder="state">
                            <input type="text" v-model="changeProperty.zip" placeholder="zip">
                            <input type="text" v-model="changeProperty.type" placeholder="type">
                        </form>
                        <button @click="editProperty(property._id)">submit</button>
                    </details>
                    
                </div>
                </div>
                
                </li>
                </div>
        </ul>
        </div>
    </div>
</template>

<script>
import axios from 'axios';



export default {
    data() 
    {
        return {
            properties:[],
            property: {
                address: "",
                bedrooms: "",
                baths: "",
                city: "",
                img: "",
                price: "",
                state: "",
                type: "",
                zip: ""

            },
            changeProperty:{
                address: "",
                bedrooms: "",
                baths: "",
                city: "",
                img: "",
                price: "",
                state: "",
                type: "",
                zip: ""
            }
        }
    },

    methods:{

        refreshData(){
            axios
                .get('http://localhost:8000')
                .then((res)=>{
                    this.properties=res.data
                })
        },

        addProperty(){
            axios
                .post("http://localhost:8000/house", {
                    address: this.property.address,
                    city: this.property.city,
                    img: this.property.img,
                    price: this.property.price,
                    state: this.property.state,
                    type: this.property.type,
                    zip: this.property.zip,
                    bedrooms: this.property.bedrooms,
                    baths: this.property.baths
                })
                .then((res)=>{
                    this.refreshData()
                    if(res.status ==201) {
                        console.log("succesful")
                    }
        })},
        
        
        deleteProperty(id){
            axios
                .delete(`http://localhost:8000/house/${id}`)
                .then(()=>{
                    this.refreshData();
                })
        },

        editProperty(id){
            axios
                .put(`http://localhost:8000/house/${id}`, {
                    address: this.changeProperty.address,
                    city: this.changeProperty.city,
                    img: this.changeProperty.img,
                    price: this.changeProperty.price,
                    state: this.changeProperty.state,
                    type: this.changeProperty.type,
                    zip: this.changeProperty.zip,
                    bedrooms: this.changeProperty.bedrooms,
                    baths: this.changeProperty.baths
                })
                .then(()=>{
                    this.refreshData()
                })
        }
    },

    mounted:function() 
    {
        this.refreshData();

    },
    }
</script>