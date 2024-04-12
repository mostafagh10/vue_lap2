<template>
   <div class="col-md-12 py-2 bg-info">
    <slot name="top" />
            <h2>welcome to our application</h2>
            <p>branch {{ branch }}</p>
    <slot name="bottom" />
           
    </div>
</template>

<script>
export default {
    data(){
        return{

        }
    },
    props:["branch"]
}
</script>

<style>

</style>