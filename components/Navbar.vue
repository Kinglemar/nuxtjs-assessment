<template>
    <div>
        <Nuxt-link :to="link.path" class="add-btn">{{link.name}}</Nuxt-link>
    </div>
</template>

<script>
export default {
    props:{
        link : {
            type : Object,
            required: true
        },
    }
}
</script>

<style scoped>
.add-btn {
    font-family: "Roboto", helvetica, arial, sans-serif;
    border: none;
    font-size: 20px;
    background-color: green;
    color: #fff;
    border-radius: 4px;
    cursor: pointer;
    width: 160px;
    height: 50px;
    margin: 12px;
    transition: transform 0.3s ease-in;
    text-decoration: none;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
}
.add-btn:hover {
    transform: scale(1.1);
}
</style>