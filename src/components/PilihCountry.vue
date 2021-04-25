<template>
  <select @change="pilCountry()" v-model="selected" class="form-select mt-10 block w-full border p-3 rounded">
      <option value="0">Select Countries</option>
      <option v-for="country in countries" :value="country.ID">
          {{country.Country}}
      </option>
  </select>
</template>

<script>
export default {
    name:'PilihCountry',
    props:['countries'],
    data(){
        return{
            selected: 0,
        }
    },
    methods:{
        pilCountry(){
            const country = this.countries.find((item) => item.ID === this.selected)

            this.$emit('get-country', country)
        }
    }
}
</script>

<style>

</style>