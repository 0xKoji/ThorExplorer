<template>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark p-3 mb-4" style="background-color: #111111!important;">
    <div class="container-fluid">
        <a class="navbar-brand" href="/" style="font-size: 30px;"><span style="color: #00D2FF;">THOR</span>Explorer</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
                <a class="nav-link active">Rune: ${{parseFloat(results.runePriceUSD).toFixed(2)}}</a>
            </li>
        </ul>
            <Search />
        </div>
    </div>
    </nav>
</template>

<script>
export default {
    data(){
        return{
            results: {},
        }
    },

    activated() {
      // Call fetch again if last fetch more than 30 sec ago
      if (this.$fetchState.timestamp <= Date.now() - 30000) {
        this.$fetch()
      }
    },

    async fetch(){
        // Fetch tx details from api
        this.results = await fetch(`https://midgard.thorchain.info/v2/stats`)
        .then(res => res.json())

    },
}
</script>

<style>

</style>