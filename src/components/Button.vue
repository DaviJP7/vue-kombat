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
    cursor: pointer;
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


.btn.attack:hover,
.btn.attack:focus,
.btn.new-game:hover,
.btn.new-game:focus {
    background: #cc0f0f;
    box-shadow: inset -6px -6px 0px 0px #7c0000;
}

.btn.special-attack {
    background-color: #ff9800;
    box-shadow: inset -4px -4px 0px 0px #804d01;
    color: #000;
}

.btn.special-attack:hover,
.btn.special-attack:focus {
    background: #da860a;
    box-shadow: inset -6px -6px 0px 0px #6d4201;
}

.btn.heal {
    background-color: #259b24;
    box-shadow: inset -4px -4px 0px 0px #026b00;
    color: #fff;
}

.btn.heal:focus,
.btn.heal:hover {
    background: #126e11;
    box-shadow: inset -6px -6px 0px 0px #045202;
}

.btn.give-up {
    background-color: #ddd;
    box-shadow: inset -4px -4px 0px 0px #929292;
    color: #000;
}

.btn.give-up:focus,
.btn.give-up:hover {
    background: #b3b3b3;
    box-shadow: inset -6px -6px 0px 0px #6b6b6b;
}
</style>