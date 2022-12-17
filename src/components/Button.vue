<template>
    <button class="btn">
        <slot />
    </button>
</template>
<script>
export default {
    name: 'Button'
}
</script>
<style scoped>
.btn {
    font-family: 'Press Start 2P', cursive;
    padding: 5px 10px;
    margin: 0px 10px;
    border: none;
    text-transform: uppercase;
    position: relative;
    font-size: 1.1rem;
}

.btn:before,
.btn:after {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    box-sizing: content-box;
}

.btn:before {
    top: -4px;
    left: 0;
    border-top: 4px black solid;
    border-bottom: 4px black solid;
}

.btn:after {
    left: -4px;
    top: 0;
    border-left: 4px black solid;
    border-right: 4px black solid;
}

.new-game {
    /* background-color: #4254af; */
    background-color: #fc0d0d;
    box-shadow: inset -4px -4px 0px 0px #810000;
    color: #fff;
    font-size: 15pt;
    cursor: pointer;
}

.attack {
    background-color: #e51c23;
    box-shadow: inset -4px -4px 0px 0px #810000;
    color: #fff;
}

.special-attack {
    background-color: #ff9800;
    box-shadow: inset -4px -4px 0px 0px #804d01;
    color: #000;
}

.heal {
    background-color: #259b24;
    box-shadow: inset -4px -4px 0px 0px #026b00;
    color: #fff;
}

.give-up {
    background-color: #ddd;
    box-shadow: inset -4px -4px 0px 0px rgb(146, 146, 146);
    color: #000;
}
</style>