<template>
    <div id="app">
        <router-view />
        <router-link to="/login">Login</router-link>
        <span> | </span>
        <router-link to="/">Home</router-link>
    </div>
</template>

<style>
    body {
        margin: 0;
        padding: 0;
        background: #F1F1F1;
    }
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }
</style>