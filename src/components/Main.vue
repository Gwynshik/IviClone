<template>
	<div class="main">
		<div class="container">
			<div class="header-text">
				<h1>Фильмы</h1>
				<span class="header-text__filter-text">описание</span>
			</div>
			<Filter :films="films"/>
			<!-- <Catalog /> -->
			<!-- <Slider /> -->
		</div>
	</div>
</template>



<script>
	import Filter from '@/components/Filter.vue'
	import Catalog from '@/components/Catalog.vue'
	import Slider from '@/components/Slider.vue'
	export default {
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
			Filter,
			Catalog,
			Slider
	}}
</script>



<style>
	.main{
		padding-top: 50px;
	}
	.container{
		display: flex;
    	flex-direction: column;
    	gap: 40px;
	}
	.header-text{
		display: flex;
    	flex-direction: column;
    	gap: 15px;
	}
</style>