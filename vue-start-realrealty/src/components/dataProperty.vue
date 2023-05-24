<template>
    <div>
        <h1>Property Data</h1>
    </div>

</template>

<script>
import axios from 'axios';


export default {
    setup() {
    axios
        .get('http://localhost:8000')
        .then((res)=>{
            console.log(res.data )
        })
    }
}
</script>