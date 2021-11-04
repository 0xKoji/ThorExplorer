<template>
  <div>
    <div class="row align-items-center justify-content-around mt-4">
        <div class="col-sm-4 col-10 mt-4 mb-4">
            <div class="card">
                <div class="card-body">
                    <h2 class="text-center fw-bold">{{new Intl.NumberFormat().format(results.addLiquidityCount)}}</h2>
                    <p class="text-center text-muted text-decoration-underline fw-bold fs-5">Add Liquidity Count</p>
                </div>
            </div>
        </div>
        <div class="col-sm-4 col-10 mt-4 mb-4">
            <div class="card">
                <div class="card-body">
                    <h2 class="text-center fw-bold">{{new Intl.NumberFormat().format(results.dailyActiveUsers)}}</h2>
                    <p class="text-center text-muted text-decoration-underline fw-bold fs-5">Daily Active Users</p>
                </div>
            </div>
        </div>
        <div class="col-sm-4 col-10 mt-4 mb-4">
            <div class="card">
                <div class="card-body">
                    <h2 class="text-center fw-bold">{{new Intl.NumberFormat().format(results.withdrawCount)}}</h2>
                    <p class="text-center text-muted text-decoration-underline fw-bold fs-5">Withdraw Count</p>
                </div>
            </div>
        </div>
    </div>
  </div>
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