<template>
  <div>
    <Navbar />
    <div class="container mx-auto">
      <Stats />
      <HomeView :actions="actions" />
    </div>
  </div>
</template>

<script>
export default {

  data(){
    return{
      results: [],
      actions: [],

    }
  },

  activated(){
    // Call fetch again if last fetch more than 30 sec ago
    if (this.$fetchState.timestamp <= Date.now() - 30000) {
      this.$fetch()
    }
  },

  async fetch(){
    // Fetch tx details from api
    this.results = await fetch('https://midgard.thorchain.info/v2/actions')
    .then(res => res.json())

    this.actions = this.results.actions

  },

}
</script>

<style>
body{
    background-color: #111111;
    font-family: 'Roboto Condensed', sans-serif;
    color: white;
}

</style>