<template>

    <div class="layout">
        <header ><slot name="header"></slot></header>
        <main ><slot name="main"></slot></main>
        <footer ><slot name="footer"></slot></footer>
    </div>
</template>
<style>
    .layout
    {
        background-color: red ;
        color: white;
        padding: 25px;
    }
</style>