<template>
   <nav>
       <ul>
           <li><router-link to="/">Home</router-link></li>
           <li><router-link to="/add">New Blog</router-link></li>
       </ul>
   </nav>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>

nav{
    /* width: 100%; */
    /* height: 80px; */
    background-color: lightgreen;
    padding: 10px 0;
    }
ul{
    list-style: none;
    text-align: center;
}
li{
    display: inline-block;
    margin: 10px 20px;
}
a{
    color: #222;
    padding: 5px 10px;
    text-decoration: none;
    border-radius: 5px;
    font-size: 20px;
}
.router-link-exact-active{
    color: #eee;
    background-color: #222;
}
</style>