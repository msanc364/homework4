<script setup>
    import {defineprops} from 'vue'
    const props = defineProps({
        total: {
            type: Number,
            require: true,
        }
    })

</script>


<template>
    <h4> Your Balance</h4>
    <h1 id="balance">{{ total }}</h1>



</template>