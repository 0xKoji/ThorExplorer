<template>
    <div class="row row-cols-lg-auto g-3 align-items-center">
        <div class="col-12">
            <input class="form-control" type="search" name="search" v-model="search">
        </div>
        <div class="col-12">
            <button class="btn btn-primary" v-on:click="searchInput()">Submit</button>
        </div>
    </div>
</template>

<script>

export default{
    data() { 
        return {
            search: ""
        }
    },

    methods: {
        searchInput(){
            window.location.href = `/tx/${this.search}`
        }
    }
}
</script>

<style>

</style>