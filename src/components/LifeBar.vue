<template>
    <div class="life-bar">
        <div class="life" :class="{ 'danger': life < 20 }" :style="{ width: life + '%' }">
        </div>
    </div>
    <span>{{ life }}%</span>
</template>
<script>
export default {
    name: "LifeBar",
    props: {
        life: Number
    }
}
</script>

<style scoped>
.life-bar {
    width: 80%;
    height: 20px;
    border: 1px solid #aaa;
    border-radius: .8em;
}

.life-bar .life {
    height: 100%;
    background-color: rgb(38, 224, 38);
    transition: 1s width ease-out;
    border-radius: .8em;
}

.life-bar .life.danger {
    background-color: red;
}
</style>