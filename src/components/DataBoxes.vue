<template>
    <div class="grid gap-4 md:grid-cols-2">
        <div class="shadow-md bg-yellow-100 p-10 text-center rounded">
            <!-- box 1 -->
            <h3 class="text-3xl text-yellow-900 font-bold mb-4">
                Cases
            </h3>
            <div class="text-2x mb-4">
                <span class="font-bold">
                    New:
                </span>
                {{numberWcoma(stats.NewConfirmed)}}
            </div>
            <div class="text-2x mb-4">
                <span class="font-bold">
                    Total:
                </span>
                {{numberWcoma(stats.TotalConfirmed)}}
            </div>
    </div>
        <div class="shadow-md bg-yellow-200 p-10 text-center rounded">
            <!-- box 2 -->
            <h3 class="text-3xl text-yellow-900 font-bold mb-4">
                Death
            </h3>
            <div class="text-2x mb-4">
                <span class="font-bold">
                    New Death:
                </span>
                {{numberWcoma(stats.NewDeaths)}}
            </div>
            <div class="text-2x mb-4">
                <span class="font-bold">
                    Total Death:
                </span>
                {{numberWcoma(stats.TotalDeaths)}}
            </div>
        </div>
        </div>
</template>

<script>
export default {
    name:'DataBoxes',
    props:['stats'],
    methods:{
        numberWcoma(x){
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
        }
    }
}
</script>

<style>

</style>