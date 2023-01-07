<template>
    <Header />
    <Main v-bind:films="films"/>
    <div class="footer"></div>
</template>

<script>
    import Header from '@/components/Header.vue'
    import Main from '@/components/Main.vue'
    export default {
        name: 'iviClone',
        data() {
            return{
                films: [
                {id: 1, title: 'Мстители', genre: 'Фантастика'},
                {id: 2, title: 'Аватар', genre: ['фантастика', 'боевик']},
                {id: 3, title: 'Гарри Поттер', genre: ['фэнтези', 'приключения']},
                ],
            }
        },
        components:{
            Header,
            Main
    }}
</script>

<style>
    *{
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }
    html, body {
        width: 100%;
        height: 100%;
    }	
    .container{
        width: 100%;
        padding-left: 10%;
        padding-right: 10%;
    }
</style>
