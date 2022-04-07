<template>
    <header>
        <h1>{{title}}</h1>
        <!--<Button color="green" text="Add"/>-->
    </header>
</template>
<script>
import Button from './subcomponents/Button.vue'
export default {
    name: 'Header',
    props:{
        title:{
            type: String,
            default: 'Todo',
        }
    },
    components:{
        Button,
    }
}
</script>
<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-items:  center;
        margin-bottom: 20px;
    }
</style>
