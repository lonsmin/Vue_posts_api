<template>
    <button class="btn"
    :style="{background: color}">
    {{text}}
    </button>
</template>
<script>


export default {
    name: 'Button',
    props:{
        text:{
            type:String,
            default:'Tlačítko'
        },
        color:{
            type:String,            
        },
       
    },
}
</script>

