<template>    
        <header>
            <h1>{{ title }}</h1>
        </header>  
</template>

<script>
export default {
  props: ["title"]
}
</script>

<style scoped>

header {
    width: 70%;
    margin: 0 auto;
    height: 5rem;
    background-color: rgb(179, 194, 196);
    display: flex;    
    justify-content: center;    
    border: 2px solid rgb(6, 6, 97);
    border-radius: 12px;
    padding: 5px;    

}

h1 {
    color: white;
}


</style>