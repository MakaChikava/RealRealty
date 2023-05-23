<template>
    <nav class="navbar sticky-top bg-body-tertiary bg-primary">
            <div class="container-fluid">
                <a class="navbar-brand text-light fs-2" href="#">{{ logo }}</a>
            </div>
    </nav>
</template>

<script>
export default {
    data() {
        return{
            logo: 'Real Realty',
            url: 'home.html'
        }
        
    }
}

</script>