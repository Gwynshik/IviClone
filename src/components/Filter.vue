<template>
    <div class="filter">
        <div class="filter__container">
            <div class="filter__inner-container genres">
                <div class="select select-genres" @click="changeDisplayDropdownMenuGenres">
                    <div class="select__text-wrapper">
                        <span class="select__title">Жанры</span>
                        <span class="select__text">{{ selectedGenresText }}</span>
                    </div>
                    <div class="select__icon-wrapper">
                        <img class="select__icon" src="@/images/select-icon.svg" alt="select-icon" :class="{'select__icon_active': dropdownMenuGenresIsActive}">
                    </div>
                </div>
                <div class="dropdown-menu dropdown-menu-genres" :class="{'dropdown-menu_active': dropdownMenuGenresIsActive}">
                    <!-- <div class="dropdown-menu__slider">
                        <div class="dropdown-menu__slider-item">1</div>
                        <div class="dropdown-menu__slider-item">2</div>
                        <div class="dropdown-menu__slider-item">3</div>
                        <div class="dropdown-menu__slider-item">4</div>
                    </div> -->
                    <ul class="dropdown-menu__list">
                        <li v-for="genre of genres" class="dropdown-menu__item">
                            <label for="checkbox-genre" class="dropdown-menu__label">
                                <input type="checkbox" id="checkbox-genre" style="display: none">
                                <div class="dropdown-menu__text" @click="selectTitle(genre)">{{ genre.title }}</div>
                                <div class="dropdown-menu__checkbox-wrapper">
                                    <div class="dropdown-menu__checkbox">
                                        <img src="@/images/check-icon.svg" alt="checkbox" class="dropdown-menu__icon" :class="{'dropdown-menu__icon_active': genre.selected}">
                                    </div>
                                </div>
                            </label>
                        </li>
                    </ul>
                </div>
            </div>
            <div class="filter__inner-container country">
                <div class="select select-country" @click="changeDisplayDropdownMenuCountry">
                    <div class="select__text-wrapper">
                        <span class="select__title">Страна</span>
                        <span class="select__text">{{ selectedCountryText }}</span>
                    </div>
                    <div class="select__icon-wrapper">
                        <img class="select__icon" src="@/images/select-icon.svg" alt="select-icon" :class="{'select__icon_active': dropdownMenuCountryIsActive}">
                    </div>
                </div>
                <div class="dropdown-menu dropdown-menu-country" :class="{'dropdown-menu_active': dropdownMenuCountryIsActive}">
                    <!-- <div class="select__slider">
                        <div class="filter__slider-item">1</div>
                        <div class="filter__slider-item">2</div>
                        <div class="filter__slider-item">3</div>
                        <div class="filter__slider-item">4</div>
                    </div> -->
                    <ul class="dropdown-menu__list">
                        <li v-for="country of country" class="dropdown-menu__item" >
                            <label for="checkbox-country" class="dropdown-menu__label">
                                <input type="checkbox" id="checkbox-country" style="display: none">
                                <div class="dropdown-menu__text" @click="selectTitle(country)">{{ country.title }}</div>
                                <div class="dropdown-menu__checkbox-wrapper">
                                    <div class="dropdown-menu__checkbox">
                                        <img src="@/images/check-icon.svg" alt="checkbox" class="dropdown-menu__icon" :class="{'dropdown-menu__icon_active': country.selected}">
                                    </div>
                                </div>
                            </label>
                        </li>
                    </ul>
                </div>
            </div>
            <div class="filter__inner-container years">
                <div class="select select-years" @click="changeDisplayDropdownMenuYears">
                    <div class="select__text-wrapper">
                        <span class="select__title">Годы</span>
                        <span class="select__text">{{ selectedYearsText }}</span>
                    </div>
                    <div class="select__icon-wrapper">
                        <img class="select__icon" src="@/images/select-icon.svg" alt="select-icon" :class="{'select__icon_active': dropdownMenuYearsIsActive}">
                    </div>
                </div>
                <div class="dropdown-menu dropdown-menu-years" :class="{'dropdown-menu_active': dropdownMenuYearsIsActive}">
                    <ul class="dropdown-menu__list list-years">
                        <li v-for="years of years" class="dropdown-menu__item item-years" >
                            <label for="radio-years" class="dropdown-menu__label" >
                                <input type="radio" id="radio-years" style="display: none">
                                <div class="dropdown-menu__text" @click="selectYears(years)">{{ years.title }}</div>
                                <div class="dropdown-radio-wrapper">
                                    <div class="dropdown-menu__radio">
                                        <img src="@/images/radio-icon.svg" alt="radio" class="dropdown-menu__icon" :class="{'dropdown-menu__icon_active': years.selected}">
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
                    {id:0,title:"Австралия",selected:false},
                    {id:1,title:"Аргентина",selected:false},
                    {id:2,title:"Армения",selected:false},
                    {id:3,title:"Беларусь",selected:false},
                    {id:4,title:"Бельгия",selected:false},
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
                    {id:22,title:"Польша",selected:false},
                    {id:23,title:"Россия",selected:false},
                    {id:24,title:"СССР",selected:false},
                    {id:25,title:"США",selected:false},
                    {id:26,title:"Таиланд",selected:false},
                    {id:27,title:"Турция",selected:false},
                    {id:28,title:"Украина",selected:false},
                    {id:29,title:"Финляндия",selected:false},
                    {id:30,title:"Франция",selected:false},
                    {id:31,title:"Швейцария",selected:false},
                    {id:32,title:"Швеция",selected:false},
                    {id:33,title:"ЮАР",selected:false},
                    {id:34,title:"Южная Корея",selected:false},
                    {id:35,title:"Япония",selected:false},
                ],
                years:[
                    {id:0,title:"Все годы",selected:false},
                    {id:1,title:"2022 год",selected:false},
                    {id:2,title:"2021 год",selected:false},
                    {id:3,title:"2020 год",selected:false},
                    {id:4,title:"2019 год",selected:false},
                    {id:5,title:"2018 год",selected:false},
                    {id:6,title:"2017 год",selected:false},
                    {id:7,title:"2016 год",selected:false},
                    {id:8,title:"2021-2022",selected:false},
                    {id:9,title:"2020-2022",selected:false},
                    {id:10,title:"2019-2020",selected:false},
                    {id:11,title:"2010-2020",selected:false},
                    {id:12,title:"2010-2015",selected:false},
                    {id:13,title:"2000-2010",selected:false},
                    {id:14,title:"1990-2000",selected:false},
                    {id:15,title:"1980-1990",selected:false},
                    {id:16,title:"до 1980",selected:false}
                ],
                countClick: 0,
                dropdownMenuGenresIsActive: false,
                dropdownMenuCountryIsActive: false,
                dropdownMenuYearsIsActive: false,
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
            },
            selectedCountry(){
                return this.country.filter(country => country.selected);
            },
            selectedCountryText(){
                if (this.selectedCountry.map(country => country.title).join(', ').length > 15) {
                    return this.selectedCountry.map(country => country.title).join(', ').slice(0, 14).concat('...')
                }
                return this.selectedCountry.map(country => country.title).join(', ')
            },
            selectedYears(){
                return this.years.filter(years => years.selected);
            },
            selectedYearsText(){
                return this.selectedYears.map(years => years.title).join('')
            },
        },
        methods: {
            changeDisplayDropdownMenuGenres(){
                this.dropdownMenuGenresIsActive = !this.dropdownMenuGenresIsActive
            },
            changeDisplayDropdownMenuCountry(){
                this.dropdownMenuCountryIsActive = !this.dropdownMenuCountryIsActive
            },
            changeDisplayDropdownMenuYears(){
                this.dropdownMenuYearsIsActive = !this.dropdownMenuYearsIsActive
            },
            selectTitle(title){
                title.selected = !title.selected;
                console.log(title)
            },
            selectYears(years){
                if (years.selected) {
                    years.selected = !years.selected
                }
                else { 
                    for (let i = 0; i < this.years.length; i++) {
                        this.years[i].selected = false
                    }
                    years.selected = !years.selected
                }
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
    @import url('@/css/filter.css');
</style>
