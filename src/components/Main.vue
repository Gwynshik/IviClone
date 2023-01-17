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
				{{ filteredFilms }}
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
				{id: 0, title: 'Мстители', genres: [25], country: [25], years: [11, 12]},
				{id: 1, title: 'Аватар', genres: [2, 25], country: [25], years: [13]},
				{id: 2, title: 'Гарри Поттер', genres: [26], country: [6], years: [13]},
				],
				filtersFilms: [],
				workFilters: {
					genres: [],
					country: [],
					years: [],
				}
			}
		},
		methods:{
			selectGenre(genre){
				if (genre.selected) {
					return this.workFilters.genres.push(genre)
				}
				this.workFilters.genres = this.workFilters.genres.filter(item => item.id !== genre.id)
				
			},
			selectCountry(country){
				if (country.selected) {
					return this.workFilters.country.push(country)
				}
				this.workFilters.country = this.workFilters.country.filter(item => item.id !== country.id)
			},
			selectYaer(yaer){
				this.workFilters.years = yaer
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
			filteredFilms(){
				if (this.filtersFilms.length == 0) {
					if (this.workFilters.genres.length > 0) {
						for (let i = 0; i < this.workFilters.genres.length; i++) {
							if (this.workFilters.genres[i]) {
								
							}
						}
					}
					// return this.filtersFilms = this.films.filter(function(film){
					// 	let result = []
					// 	for (let i = 0; i < film.genres.length; i++) {
					// 		if (film.genres[i] == this.workFilters.genres) {result.push(film)}
					// 	}
					// 	if (result.length) {return result}
					// 	return
					// })
				}
				// return this.filtersFilms = this.filtersFilms.filter(function(film){
				// 	let result = []
				// 	for (let i = 0; i < film.genres.length; i++) {
				// 		if (film.genres[i] == genre.id) {
				// 			result.push(film)
				// 		}
				// 	}
				// 	if (result.length > 0) {
				// 		return result
				// 	}
				// 	return
				// })
			}
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