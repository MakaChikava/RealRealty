<template>
    <div>
        <h1>Property Data</h1>
        <form>
            <input type="text">
            <button>search</button>
        </form>
        <ul>
            <li v-for="property in properties" :key="property.id">
                <img src= {{ property.img }} alt="fgd">
                <p>{{ property.price }}</p>
                <p>{{ property.address }}, {{ property.city }} {{property.state}}, {{ property.zip }}</p>
                <p>{{  }}</p>
            </li>
        </ul>
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

    async mounted() 
    {
        let res = await axios.get('http://localhost:8000');
        console.log(res.data)
        this.properties = res.data

    },
    }
</script>