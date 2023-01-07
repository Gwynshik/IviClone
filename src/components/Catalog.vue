<template>
    <div class="catalog">
        <div class="catalog__item">
            <div class="catalog__poster">image</div>
            <span class="catalog__text">title</span>
        </div>
    </div>
</template>



<script>

</script>



<style>
    .catalog{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        
        
    }
    .catalog__item{
        display: flex;
        flex-direction: column;
        width: 150px;
        gap: 30px;
        background-color: #e0552a;
        border-radius: 15px;
        padding: 30px;
    }
</style>