<template>
    <div>
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
        }
    },

    methods:{
        refreshData(){
            axios
                .get('http://localhost:8000')
                .then((res)=>{
                    this.properties=res.data
                })
        }
    },

    mounted:function() 
    {
        this.refreshData();
        // let res = await axios.get('http://localhost:8000');
        // console.log(res.data)
        // this.properties = res.data

    },
    }
</script>