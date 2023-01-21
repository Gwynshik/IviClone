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
				{id: 0, title: 'Мстители', genres: [25], country: [25], years: [11, 12]},
				{id: 1, title: 'Аватар', genres: [2, 25], country: [25], years: [13]},
				{id: 2, title: 'Гарри Поттер', genres: [26], country: [6], years: [13]},
				],
				filtersFilms: [],
				filters: {
					genres: [],
					country: [],
					years: [],
				},
				countFilter: {
					genres: 0,
					country: 0,
					years: [],
				},
			}
		},
		methods:{
			selectGenre(genre){
				if (genre.selected) {
					return this.filters.genres.push(genre)
				}
				this.filters.genres = this.filters.genres.filter(item => item.id !== genre.id)
			},
			selectCountry(country){
				if (country.selected) {
					return this.filters.country.push(country)
				}
				this.filters.country = this.filters.country.filter(item => item.id !== country.id)
			},
			selectYaer(yaer){
				this.filters.years = yaer
			},
		},
		components:{
			Filter,
			Catalog,
			Slider
		},
		computed:{
			filteredFilmsText(){
				console.log('----------------------', this.filteredFilms)
				if (this.filtersFilms.length > 0) {
					return this.filtersFilms.map(film => film.title)
				}
            },
			filteredFilms(){
				if (this.countFilter.genres > this.filters.genres.length || this.countFilter.country > this.filters.country.length || this.countFilter.years.id !== this.filters.years.id) {
					this.filtersFilms = []
				}
				if (this.filtersFilms.length === 0) {
					for (let i = 0; i < this.films.length; i++) {
						this.filtersFilms.push(this.films[i])
					}
				}
				for (let i = 0; i < this.filters.genres.length; i++) {
					const filtersGenres = this.filters.genres[i].id
					console.log('filtersGenres', filtersGenres)
					this.filtersFilms = this.filtersFilms.filter(function(film){
						let result = []
						for (let i = 0; i < film.genres.length; i++) {
							if (film.genres[i] == filtersGenres) {
								result.push(film)
							}	
						}
						if (result.length) {return result}
						return
					})
				}
				for (let i = 0; i < this.filters.country.length; i++) {
					const filtersCountry = this.filters.country[i].id
					this.filtersFilms = this.filtersFilms.filter(function(film){
						let result = []
						for (let i = 0; i < film.country.length; i++) {
							if (film.country[i] == filtersCountry) {
								result.push(film)
							}	
						}
						if (result.length) {return result}
						return
					})
				}
				const filtersYears = this.filters.years	
				if (filtersYears.length !== 0) {
					this.filtersFilms = this.filtersFilms.filter(function(film){
						let result = []
						for (let i = 0; i < film.years.length; i++) {
							if (film.years[i] == filtersYears.id) {
								result.push(film)
							}	
						}
						if (result.length) {return result}
						return
					})
				}
				this.countFilter.genres = this.filters.genres.length
				this.countFilter.country = this.filters.country.length
				this.countFilter.years.id = this.filters.years.id
				return this.filtersFilms
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