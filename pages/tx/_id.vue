<template>
    <div>
        <Navbar />
        <div class="w-1/2 text-center">
            <TXView :id="txId" :type="type" :date="date" :txIn="txIn" :out="out" :height="height" :pools="pools" :status="status"/>
        </div>
    </div>
</template>

<script>

export default{

    data() {
        return{
            txId: this.$route.params.id,
            results: [],
            type: "",
            date: "",
            txIn: [],
            out: [],
            height: "",
            pools: [],
            status: "",
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
        this.results = await fetch(`https://midgard.thorchain.info/v2/actions?txid=${this.txId}`)
        .then(res => res.json())

        this.type = this.results.actions[0].type
        this.txIn = this.results.actions[0].in
        this.out = this.results.actions[0].out
        this.height = this.results.actions[0].height
        this.pools = this.results.actions[0].pools
        this.status = this.results.actions[0].status
        this.date = new Date(this.results.actions[0].date/1000000).toLocaleString()

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