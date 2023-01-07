<template>
    <li class="filter-dropdown__item" >
        <label for="checkbox-genre" class="filter-dropdown__label">
            <input type="checkbox" id="checkbox-genre" style="display: none">
            <div class="filter-dropdown__text" @click="filterGenre">{{ genre }}</div>
            <div class="filter-dropdown__checkbox"></div>
        </label>
    </li>
</template>



<script>
    export default{
        props: ['genre', 'films'],
        data() {
            return {
                selectGenres: [],
                strSelectGenres: '',
            }
        },
        methods:{
            filterGenre(e){
                const value = e.target.innerHTML;
                const selectTitle = document.querySelector('.filter__select-genre-text');
                console.log('value', value);
                this.selectGenres.push(value);
                this.strSelectGenres = this.strSelectGenres.concat(this.selectGenres);
                selectTitle.innerHTML = this.strSelectGenres;
                console.log('this.selectGenres', this.selectGenres);
                console.log('this.strSelectGenres', this.strSelectGenres);
                // for (let i = 0; i < this.films.length; i++) {  
                //     if (value == this.films[i].genre) {
                //         this.selectGenres.push(this.films[i])
                //     }
                // }
                // console.log('this.selectGenres 2', this.selectGenres)
                // if (this.selectGenres.length === 0 ) {
                //     return
                // }
                // for (let i = 0; i < this.selectGenres.length; i++) {
                //     this.strSelectGenres = this.strSelectGenres.concat(this.selectGenres[i].genre, ' ')
                // }
                // selectTitle.innerHTML = this.strSelectGenres
            }
        }
    }
    
</script>



<style>
    .filter-dropdown__item{
        position: relative;
        width: 30%;
        list-style: none;
    }
    .filter-dropdown__label{
        display: flex;
        cursor: pointer;
    }
    .filter-dropdown__text-wrapper{
        display: flex;
        justify-content: space-between;
        width: 180px;
        cursor: pointer;
        border: solid 1px black;
    }
    .filter-dropdown__text{
        width: 180px;
        overflow: hidden;
    }
</style>