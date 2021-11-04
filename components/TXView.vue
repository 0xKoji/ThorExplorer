<template>

    <div class="container mx-auto mt-5">
        <div class="card" style="max-width: 100%">
            <div class="card-body">
                <div class="row align-items-center justify-content-around">
                    <div class="col-sm-4 col-8 mt-4 mb-4">
                        <h2 class="text-muted text-truncate">{{id}}</h2>
                    </div>
                    <div class="col-sm-4 col-8 mt-4 mb-4">
                        <div class="text-center">
                            <h2 class="type p-2" style="background-color: #c3272a!important;" v-if="type === 'refund'">{{type}}</h2>
                            <h2 class="type p-2" style="" v-else>{{type}}</h2>
                        </div>
                    </div>
                    <div class="col-sm-4 col-8 mt-4 mb-4">
                        <h2 class="text-muted">{{date}}</h2>
                    </div>
                </div>

                <div class="row align-items-center justify-content-around">
                    <div class="col-sm-3 col-6 mt-4 mb-4">
                        <div v-for="item in txIn" :key="item.address">
                            <div v-for="coin in item.coins" :key="coin.amount">
                                <h2>{{coin.amount / 1e8}} <span style="color: #ffb700;">{{coin.asset.split('-')[0]}}</span></h2>
                            </div>
                            <a :href="`/address/${item.address}`"><h2 class="text-truncate" style="color: #00D2FF; font-weight: bold;">{{item.address}}</h2></a>
                            <svg xmlns="http://www.w3.org/2000/svg" style="width: 30px;" class="h-6 w-6 mb-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18" />
                            </svg>
                        </div>
                    </div>
                    <div class="col-sm-3 col-6 mt-4 mb-4">
                        <div v-for="item in out" :key="item.address">
                            <div v-for="coin in item.coins" :key="coin.amount">
                                <h2>{{coin.amount / 1e8}} <span style="color: #ffb700;">{{coin.asset.split('-')[0]}}</span></h2>
                            </div>
                            <a :href="`/address/${item.address}`"><h2 class="text-truncate" style="color: #00D2FF; font-weight: bold;">{{item.address}}</h2></a>
                            <svg xmlns="http://www.w3.org/2000/svg" style="width: 30px;" class="h-6 w-6 mb-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
                            </svg>
                        </div>
                    </div>
                </div>
                <div class="row align-items-center justify-content-around">
                    <div class="col-sm-4 col-8 mt-4">
                        <h2 v-if="pools[0]">Pool: <span style="color: #ffb700;">{{pools[0].split('-')[0]}}</span></h2>
                    </div>
                    <div class="col-sm-4 col-8 mt-4">
                        <h2>Status: <span v-if="status === 'success'" style="color: #04e762;">{{status}}</span><span v-else style="color: #c3272a;">{{status}}</span></h2>
                    </div>
                    <div class="col-sm-4 col-8 mt-4">
                        <h2>Block: {{height}}</h2>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {

    props: ['id', 'type', 'date', 'txIn', 'out', 'height', 'pools', 'status']

}
</script>

<style>

span {
    display: inline-block;
}

h2{
    font-size: 100%;
}

.card{
    background-color: #1c1c1e;
}

.type{
    border-radius: 6px;
    background-color: #04e762;
    color: white;
    font-weight: bold;
    font-size: 100%;
}
</style>