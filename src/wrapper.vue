<template>
  <div class="container">
    <div class="row text-center">
        <myheader/>
    </div>
    <div class="row text-center">
        <div class="col-4">
            <links/>
        </div>
        <div class="col-8">
            <mybody/>
        </div>
    </div>
    <div class="row text-center">
        <myfooter/>
    </div>
  </div>
  <!-- <lab1/> -->
</template>

<script>
import myfooter from '@/components/myfooter.vue'
import mybody from '@/components/mybody.vue'
import links from '@/components/links.vue'
import myheader from '@/components/myheader.vue'
import lab1 from '@/components/lab1.vue'

export default {
    components:{
        myheader,
        myfooter,
        links,
        mybody,
        lab1,
    }
}
</script>

<style>

</style>