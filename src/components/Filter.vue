<template>
    <div class="filter">
        <div class="filter__container">
            <div class="filter__inner-container genre">
                <div class="filter__select-genre" @click="changeDisplayFilterDropdown">
                    <div class="filter__text-wrapper">
                        <span class="filter__title">Жанры</span>
                        <span class="filter__select-genre-text"></span>
                    </div>
                    <div class="filter__icon">v</div>
                </div>
                <div class="filter-dropdown">
                    <!-- <div class="filter__dropdown-slider">
                        <div class="filter__slider-item">1</div>
                        <div class="filter__slider-item">2</div>
                        <div class="filter__slider-item">3</div>
                        <div class="filter__slider-item">4</div>
                    </div> -->
                    <ul class="filter-dropdown__list">
                        <FilterDropdownList v-for="genre of genres" :genre="genre" :films="films"/>
                    </ul>
                </div>
            </div>
        </div>
        <div class="filter__btn-reset" @click="resetFilters">Сбросить фильтры</div>
    </div>
</template>

<script>
    import FilterDropdownList from '@/components/FilterDropdownList.vue'
    export default {
        props: ['films'],
        data() {
            return {
                genres: ['Артхаус', 'Биография', 'Боевик', 'Вестерн', 'Военные', 'Детективы', 'Для детей', 'Документальные', 'Драма', 'Зарубежные', 
                'Исторические', 'Катастрофы', 'Комедии', 'Криминал', 'Мелодрамы', 'Мистические', 'Музыкальные', 'По комиксам', 'Приключения', 'Русские',
                'Семейные', 'Советские', 'Спорт', 'Триллеры', 'Ужасы', 'Фантастика', 'Фэнтези'],
                countClick: 0,
            }
        },
        components:{
            FilterDropdownList
        },
        methods: {
            changeDisplayFilterDropdown(){
                const dropdownMenu = document.querySelector('.filter-dropdown')
                this.countClick++;
                if (this.countClick % 2) {
                    dropdownMenu.classList.add('isActive')
                }
                else dropdownMenu.classList.remove('isActive')
            },
            resetFilters() {
                console.log('resetFilters', this.test)
            }
        }
    }
    
</script>

<style>
    .filter{
        height: 150px;
        display: flex;
        flex-direction: column;
        gap: 30px;
        background-color: #e0552a;
        padding: 30px;
        border-radius: 15px;
        position: relative;
    }
    .filter__container{
        display: flex;
        width: 100%;
        justify-content: space-between;
    }
    .filter__inner-container{
        width: 20%;
        display: flex;
        flex-direction: column;
        gap: 10px;
    }
    .filter__select-genre{
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #e76a44;
        padding: 15px 10px 15px 10px;
        border-radius: 5px;
        cursor: pointer;
    }
    .filter__text-wrapper{
        display: flex;
        flex-direction: column;
    }
    .filter-dropdown{
        overflow: hidden;
        width: 630px;
        background-color: #e76a44;
        z-index: 100;
        padding: 15px;
        border-radius: 5px;
        display: none;
    }
    .isActive{
        display: block;
    }
    .filter-dropdown_slider{
        display: flex;
    }
    .filter-dropdown__list{
        display: flex;
        flex-wrap: wrap;
        flex-direction: revert;
        justify-content: space-between;
        gap: 7px;
    }
    .filter__btn-reset{
        position: absolute;
        bottom: 30px;
        cursor: pointer;
    }
</style>

<!-- export default {
    name: 'App',
    components:{
      Post
    },
    data(){
      return{
        countPage: 0,
        posts: []
      }
    },
    methods: {
      async load(){
        this.countPage++;
        console.log(this.countPage);
        const loadedPost = await fetch(`https://jsonplaceholder.typicode.com/posts?_page=${this.countPage}_limit=12`).then(response => response.json());
        console.log(loadedPost);
        this.posts = this.posts.concat(loadedPost);
      }
    }
  } -->