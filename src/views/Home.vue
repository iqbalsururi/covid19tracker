<template>
  <main v-if="!loading" class="home">
    <DataTitle :text="title" :dataDate="dataDate" />

    <DataBoxes :stats="stats" />

    <PilihCountry @get-country="getCountryData" :countries="countries" />

    <button @click="ClearCountryData" v-if="stats.Country" class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600">
      Clear Country
    </button>
  </main>
  <main v-else class="flex flex-col align-center justify-center text-center">
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching Data
    </div>
    <img :src="loadingImage" class="w-24 m-auto " alt="loading" srcset="">
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle.vue'
import DataBoxes from '@/components/DataBoxes.vue'
import PilihCountry from '@/components/PilihCountry.vue'

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    PilihCountry
  },
  data(){
    return{
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/1490.gif')
    }
  },
  methods:{
    async ambilCovidData(){
      const dat = await fetch('https://api.covid19api.com/summary')
      const data = await dat.json()
      console.log(data)
      return data
    },
    getCountryData(country){
      this.stats = country
      this.title = country.Country

    },
    async ClearCountryData(){
      this.loading =- true
      const data = await this.ambilCovidData() 
      this.title = 'Global'
      this.stats = data.Global
      this.loading = false 
    }
  },
  async created(){
    const data = await this.ambilCovidData()
    
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  }
}
</script>
