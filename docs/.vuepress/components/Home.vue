<template>
<div class="home">
    <div class="item-list">
        <div class="item" @click="gotoDetails(item)" v-for="(item,index) in topics" :key="index">
            <img :src="item.img" alt="">
            <div class="gradient"></div>
            <p>{{item.title}}</p>
        </div>
    </div>
</div>
</template>

<script>
import topics from './topics'
export default {
    name: 'Home',
    data() {
        return {
            topics: topics
        }
    },
    methods: {
        gotoDetails(item) {
            window.location.href = item.path
        }
    }
}
</script>

<style scoped>
.item-list {
    display: flex;
    flex-wrap: wrap;
}

.item {
    display: flex;
    height: 150px;
    width: 300px;
    background: lightblue;
    margin: 12px;
    border-radius: 6px;
    font-weight: bold;
    font-size: 18px;
    box-shadow: -1px 5px 14px 1px rgba(142, 126, 126, 0.45);
    cursor: pointer;
    position: relative;
    transition: 0.2s ease-in-out;
}

.item:hover {
    transform: scale(1.03);
}

img {
    height: 100%;
    width: 100%;
    border-radius: 6px;
}

.gradient {
    position: absolute;
    width: 100%;
    height: 70px;
    bottom: 0;
    background: rgb(0, 0, 0);
    background: linear-gradient(0deg, rgba(0, 0, 0, 1) 0%, rgba(255, 255, 255, 0) 100%);
    border-radius: 0 0 6px 6px;
}

p {
    position: absolute;
    margin: 12px;
    color: white;
    font-weight: bold;
    font-size: 24px;
    bottom: 0;
}

</style>
