<template>
    <div class="filter">
        <div class="filter__container">
            <div class="filter__inner-container genre">
                <div class="filter__select-genre" @click="changeDisplayFilterDropdown">
                    <div class="filter__text-wrapper">
                        <span class="filter__title">Жанры</span>
                        <span class="filter__select-genre-text">{{ selectedGenresText }}</span>
                    </div>
                    <div class="filter__icon">v</div>
                </div>
                <div class="filter-dropdown" :class="{'filter-dropdown_active': FilterDropdownIsActive}">
                    <!-- <div class="filter__dropdown-slider">
                        <div class="filter__slider-item">1</div>
                        <div class="filter__slider-item">2</div>
                        <div class="filter__slider-item">3</div>
                        <div class="filter__slider-item">4</div>
                    </div> -->
                    <ul class="filter-dropdown__list">
                        <li v-for="genre of genres" class="filter-dropdown__item" >
                            <label for="checkbox-genre" class="filter-dropdown__label" >
                                <input type="checkbox" id="checkbox-genre" style="display: none">
                                <div class="filter-dropdown__text" @click="selectGenre(genre)">{{ genre.title }}</div>
                                <div class="filter-dropdown__checkbox-wrapper">
                                    <div class="filter-dropdown__checkbox">
                                        <img src="@/images/check-icon.svg" alt="checkbox" class="filter-dropdown__icon">
                                    </div>
                                </div>
                            </label>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
        <div class="filter__btn-reset" @click="resetFilters()">Сбросить фильтры</div>
    </div>
</template>



<script>
    export default {
        props: ['films'],
        data() {
            return {
                genres: [
                    {id:0,title:"Артхаус",selected:false},
                    {id:1,title:"Биография",selected:false},
                    {id:2,title:"Боевик",selected:false},
                    {id:3,title:"Вестерн",selected:false},
                    {id:4,title:"Военные",selected:false},
                    {id:5,title:"Детективы",selected:false},
                    {id:6,title:"Для детей",selected:false},
                    {id:7,title:"Документальные",selected:false},
                    {id:8,title:"Драма",selected:false},
                    {id:9,title:"Зарубежные",selected:false},
                    {id:10,title:"Исторические",selected:false},
                    {id:11,title:"Катастрофы",selected:false},
                    {id:12,title:"Комедии",selected:false},
                    {id:13,title:"Криминал",selected:false},
                    {id:14,title:"Мелодрамы",selected:false},
                    {id:15,title:"Мистические",selected:false},
                    {id:16,title:"Музыкальные",selected:false},
                    {id:17,title:"По комиксам",selected:false},
                    {id:18,title:"Приключения",selected:false},
                    {id:19,title:"Русские",selected:false},
                    {id:20,title:"Семейные",selected:false},
                    {id:21,title:"Советские",selected:false},
                    {id:22,title:"Спорт",selected:false},
                    {id:23,title:"Триллеры",selected:false},
                    {id:24,title:"Ужасы",selected:false},
                    {id:25,title:"Фантастика",selected:false},
                    {id:26,title:"Фэнтези",selected:false}
                ],
                countClick: 0,
                FilterDropdownIsActive: false,
            }
        },
        computed:{
            selectedGenres(){
                return this.genres.filter(genre => genre.selected);
            },
            selectedGenresText(){
                if (this.selectedGenres.map(genre => genre.title).join(', ').length > 15) {
                    return this.selectedGenres.map(genre => genre.title).join(', ').slice(0, 14).concat('...')
                }
                return this.selectedGenres.map(genre => genre.title).join(', ')
            }
        },
        methods: {
            changeDisplayFilterDropdown(){
                this.FilterDropdownIsActive = !this.FilterDropdownIsActive
            },
            selectGenre(genre){
                genre.selected = !genre.selected;
                console.log(genre)
            },
            resetFilters() {
                for (let i = 0; i < this.genres.length; i++) {
                    this.genres[i].selected = false
                }
            },
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
    .filter-dropdown_active{
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
    .filter-dropdown__item{
        position: relative;
        width: 30%;
        list-style: none;
    }
    .filter-dropdown__label{
        display: flex;
        cursor: pointer;
        align-items: center;
    }
    .filter-dropdown__label:hover .filter-dropdown__icon{
        opacity: 0.5;
    }
    .filter-dropdown__text{
        width: 180px;
        overflow: hidden;
    }
    .filter-dropdown__icon{
        width: 24px;
        opacity: 0;
    }
    .filter-dropdown__icon:active{
        opacity: 1;
    }
    .filter__btn-reset{
        position: absolute;
        bottom: 30px;
        cursor: pointer;
    }
</style>
