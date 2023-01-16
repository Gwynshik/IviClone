<template>
	<div class="main">
		<div class="container">
			<div class="header-text">
				<h1>Фильмы</h1>
				<span class="header-text__filter-text">описание</span>
			</div>
			<Filter
				@select-genre="selectGenre"
				@select-country="selectCountry"
				@select-year="selectYaer"
			/>
			<div>
				<ul>
					<li>{{ filteredFilmsText }}</li>
				</ul>
			</div>
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
				{id: 0, title: 'Мстители', genresId: [25], countryId: [25], yearsId: [11, 12]},
				{id: 1, title: 'Аватар', genresId: [2, 25], countryId: [25], yearsId: [13]},
				{id: 2, title: 'Гарри Поттер', genresId: [26], countryId: [6], yearsId: [13]},
				],
				filtersFilms: [],
			}
		},
		methods:{
			selectGenre(genre){
				if (this.filtersFilms.length == 0) {
					return this.filtersFilms = this.films.filter(film => film.genresId == genre.id)
				}
				this.filtersFilms = this.filtersFilms.filter(film => film.genresId == genre.id)
			},
			selectCountry(country){
				console.log('main', country)
			},
			selectYaer(yaer){
				console.log('main', yaer)
			},
		},
		components:{
			Filter,
			Catalog,
			Slider
		},
		computed:{
			filteredFilmsText(){
				if (this.filtersFilms.length > 0) {
					console.log(this.filtersFilms.map(film => film.title))
					return this.filtersFilms.map(film => film.title)
				}
            },
		}
	}
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