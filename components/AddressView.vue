<template>
  <div>
      <div v-for="item in actions" :key="item">
          <div class="row align-items-center justify-content-around m-3 p-3" style="background-color: #1c1c1e; border-radius: 6px;">
            <div class="col-sm-3 col-6 mt-4 text-center" v-for="inList in item.in" :key="inList">
                <a :href="`/tx/${inList.txID}`"><h2 class="text-truncate text-muted">{{inList.txID}}</h2></a>
                <a :href="`/address/${inList.address}`"><h2 class="text-truncate" style="color: #00D2FF; font-weight: bold;">{{inList.address}}</h2></a>
                <svg xmlns="http://www.w3.org/2000/svg" style="width: 30px;" class="h-6 w-6 mb-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18" />
                </svg>
                <h2 v-for="coins in inList.coins" :key="coins">{{coins.amount / 1e8}} <span style="color: #ffb700;">{{coins.asset.split('-')[0]}}</span></h2>
            </div>
            <div class="col-sm-3 col-6 mt-4 text-center" v-for="outList in item.out" :key="outList">
                <a :href="`/address/${outList.address}`"><h2 class="text-truncate" style="color: #00D2FF; font-weight: bold;">{{outList.address}}</h2></a>
                <svg xmlns="http://www.w3.org/2000/svg" style="width: 30px;" class="h-6 w-6 mb-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
                </svg>
                <h2 v-for="coins in outList.coins" :key="coins">{{coins.amount / 1e8}} <span style="color: #ffb700;">{{coins.asset.split('-')[0]}}</span></h2>
            </div>
            <div class="row align-items-center justify-content-around text-center">
                <div class="col-sm-3 col-6 mt-4 ">
                    <h2 class="type p-2" style="background-color: #c3272a!important;" v-if="item.type === 'refund'">{{item.type}}</h2>
                    <h2 class="type p-2" style="" v-else>{{item.type}}</h2>
                </div>
                <div class="col-sm-3 col-6 mt-4 ">
                    <h2><span v-if="item.status === 'success'" style="color: #04e762;">{{item.status}}</span><span v-else style="color: #c3272a;">{{item.status}}</span></h2>     
                </div>
                <div class="col-sm-3 col-6 mt-4 ">
            <h2 class="text-muted">{{ new Date(item.date/1000000).toLocaleString()}}</h2>
                    
                </div>
            </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {

    props: ['actions'],

}
</script>

<style>
.type{
    border-radius: 6px;
    background-color: #04e762;
    color: white;
    font-weight: bold;
    font-size: 100%;
}

a{
     text-decoration: none;
}
</style>