<template>
  <div class="container text-center border border-1 mt-3">
    <div class="row">
       <headercomponent branch="new capital">
        <template v-slot="top">
            <p>hello from top</p>
        </template>
        </headercomponent>
       <linkscomponent />
       <bodycomponent />
       <footercomponent />
    </div>
  </div>
</template>

<script>
import headercomponent from '@/components/headercomponent.vue'
import footercomponent from '@/components/footercomponent.vue'
import linkscomponent from '@/components/linkscomponent.vue'
import bodycomponent from '@/components/bodycomponent.vue'


export default {
    data(){
        return{

        }
    },
    methods:{

    },
    components:{
        headercomponent,
        footercomponent,
        linkscomponent,
        bodycomponent,
    }
}
</script>

<style>

</style>