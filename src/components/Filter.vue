<template>
    <div class="filter">
        <div class="filter__container">
            <div class="filter__inner-container genres">
                <div class="select-genres" @click="changeDisplayDropdownMenuGenres">
                    <div class="select-genres__text-wrapper">
                        <span class="select-genres__title">Жанры</span>
                        <span class="select-genres__text">{{ selectedGenresText }}</span>
                    </div>
                    <div class="select-genres__icon">v</div>
                </div>
                <div class="dropdown-menu-genres" :class="{'dropdown-menu-genres_active': dropdownMenuGenresIsActive}">
                    <!-- <div class="dropdown-menu-genres__slider">
                        <div class="dropdown-menu-genres__slider-item">1</div>
                        <div class="dropdown-menu-genres__slider-item">2</div>
                        <div class="dropdown-menu-genres__slider-item">3</div>
                        <div class="dropdown-menu-genres__slider-item">4</div>
                    </div> -->
                    <ul class="dropdown-menu-genres__list">
                        <li v-for="genre of genres" class="dropdown-menu-genres__item" >
                            <label for="checkbox-genre" class="dropdown-menu-genres__label" >
                                <input type="checkbox" id="checkbox-genre" style="display: none">
                                <div class="dropdown-menu-genres__text" @click="selectGenre(genre)">{{ genre.title }}</div>
                                <div class="dropdown-menu-genres__checkbox-wrapper">
                                    <div class="dropdown-menu-genres__checkbox">
                                        <img src="@/images/check-icon.svg" alt="checkbox" class="dropdown-menu-genres__icon">
                                    </div>
                                </div>
                            </label>
                        </li>
                    </ul>
                </div>
            </div>
            <div class="filter__inner-container country">
                <div class="filter__select-country" @click="changeDisplayDropdownMenuCountry">
                    <div class="filter__text-wrapper">
                        <span class="filter__title">Страна</span>
                        <span class="filter__select-country-text">{{ selectedCountryText }}</span>
                    </div>
                    <div class="filter__icon">v</div>
                </div>
                <div class="dropdown-menu-country" style="display: none" :class="{'dropdown-menu-country_active': dropdownMenuCountryIsActive}">
                    <!-- <div class="filter__dropdown-slider">
                        <div class="filter__slider-item">1</div>
                        <div class="filter__slider-item">2</div>
                        <div class="filter__slider-item">3</div>
                        <div class="filter__slider-item">4</div>
                    </div> -->
                    <ul class="dropdown-menu-country__list">
                        <li v-for="genre of genres" class="dropdown-menu-country__item" >
                            <label for="checkbox-genre" class="dropdown-menu-country__label" >
                                <input type="checkbox" id="checkbox-genre" style="display: none">
                                <div class="dropdown-menu-country__text" @click="selectCountry(country)">{{ country.title }}</div>
                                <div class="dropdown-menu-country__checkbox-wrapper">
                                    <div class="dropdown-menu-country__checkbox">
                                        <img src="@/images/check-icon.svg" alt="checkbox" class="dropdown-menu-country__icon">
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
                country: [
                    {id:1,title:"Австралия",selected:false},
                    {id:2,title:"Аргентина",selected:false},
                    {id:3,title:"Армения",selected:false},
                    {id:4,title:"Беларусь",selected:false},
                    {id:5,title:"Бельгия",selected:false},
                    {id:5,title:"Бразилия",selected:false},
                    {id:6,title:"Великобритания",selected:false},
                    {id:7,title:"Венгрия",selected:false},
                    {id:8,title:"Германия",selected:false},
                    {id:9,title:"Гонконг",selected:false},
                    {id:10,title:"Дания",selected:false},
                    {id:11,title:"Индия",selected:false},
                    {id:12,title:"Ирландия",selected:false},
                    {id:13,title:"Испания",selected:false},
                    {id:14,title:"Италия",selected:false},
                    {id:15,title:"Казахстан",selected:false},
                    {id:16,title:"Канада",selected:false},
                    {id:17,title:"Китай",selected:false},
                    {id:18,title:"Колумбия",selected:false},
                    {id:19,title:"Мексика",selected:false},
                    {id:20,title:"Новая Зеландия",selected:false},
                    {id:21,title:"Норвегия",selected:false},
                    {id:23,title:"Польша",selected:false},
                    {id:24,title:"Россия",selected:false},
                    {id:25,title:"СССР",selected:false},
                    {id:26,title:"США",selected:false},
                    {id:27,title:"Таиланд",selected:false},
                    {id:28,title:"Турция",selected:false},
                    {id:29,title:"Украина",selected:false},
                    {id:30,title:"Финляндия",selected:false},
                    {id:31,title:"Франция",selected:false},
                    {id:32,title:"Швейцария",selected:false},
                    {id:33,title:"Швеция",selected:false},
                    {id:34,title:"ЮАР",selected:false},
                    {id:35,title:"Южная Корея",selected:false},
                    {id:36,title:"Япония",selected:false},
                ],
                countClick: 0,
                dropdownMenuGenresIsActive: false,
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
            changeDisplayDropdownMenuGenres(){
                this.dropdownMenuGenresIsActive = !this.dropdownMenuGenresIsActive
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
    .select-genres{
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #e76a44;
        padding: 15px 10px 15px 10px;
        border-radius: 5px;
        cursor: pointer;
    }
    .select-genres__text-wrapper{
        display: flex;
        flex-direction: column;
    }
    .dropdown-menu-genres{
        overflow: hidden;
        width: 630px;
        background-color: #e76a44;
        z-index: 100;
        padding: 15px;
        border-radius: 5px;
        display: none;
    }
    .dropdown-menu-genres_active{
        display: block;
    }
    .dropdown-menu-genres_slider{
        display: flex;
    }
    .dropdown-menu-genres__list{
        display: flex;
        flex-wrap: wrap;
        flex-direction: revert;
        justify-content: space-between;
        gap: 7px;
    }
    .dropdown-menu-genres__item{
        position: relative;
        width: 30%;
        list-style: none;
    }
    .dropdown-menu-genres__label{
        display: flex;
        cursor: pointer;
        align-items: center;
    }
    .dropdown-menu-genres__label:hover .dropdown-menu-genres__icon{
        opacity: 0.5;
    }
    .dropdown-menu-genres__text{
        width: 180px;
        overflow: hidden;
    }
    .dropdown-menu-genres__icon{
        width: 24px;
        opacity: 0;
    }
    .dropdown-menu-genres__icon:active{
        opacity: 1;
    }
    .filter__btn-reset{
        position: absolute;
        bottom: 30px;
        cursor: pointer;
    }
</style>
