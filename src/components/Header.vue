<template>
    <div class="header">
        <div class="container">
            <nav class="navbar">
                <a href="" class="navbar__item logo"><img src="@/images/logo.svg" alt="ivi"></a>
                <div class="navbar__item darkmode-switch">switch</div>
            </nav>
        </div>
    </div>
</template>

<style>
    .header{
        height: 70px;
        display: flex;
        align-items: center;
        background-color: #e0552a;
    }
    nav{
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 100%;
        width: 100%;

    }
</style>