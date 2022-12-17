<script>
export default {
    data() {
        return {
            loading: true,
            running: false,
            playerLife: 100,
            monsterLife: 100
        }
    },
    computed: {
        hasResult() {
            return this.playerLife === 0 || this.monsterLife === 0
        }
    },
    mounted() {
        // const mainSong = new Audio('../public/songs/main-theme.mp3')
        // mainSong.play()
        // mainSong.loop = true
        setTimeout(() => {
            this.loading = false
        }, 3200)
    },
    methods: {
        startGame() {
            const figth_fx = document.querySelector('.fight-content')
            const fight_voice = new Audio('../public/songs/battle/fight.mp3')
            fight_voice.play()
            fight_voice.volume = 0.2
            setTimeout(() => {
                figth_fx.classList.add('show')
            }, 500)
            setTimeout(() => {
                this.running = true;
                this.playerLife = 100;
                this.monsterLife = 100;
            }, 2000)
            setTimeout(() => {
                figth_fx.classList.remove('show')
            }, 2500)
        },
        attack(especial) {
            this.hurt('monsterLife', 5, 10, false)
            this.hurt('playerLife', 7, 12, especial)
            const voices = [
                '../public/songs/battle/weak-damage.wav',
                '../public/songs/battle/middle-damage.wav',
                '../public/songs/battle/strong-damage.wav',
            ]
            new Audio(voices[this.getRandom(0, voices.length)]).play()
        },
        hurt(target, min, max, especial) {
            const plus = especial ? 5 : 0;
            const hurt = this.getRandom(min + plus, max + plus)
            this[target] = Math.max(this[target] - hurt, 0)
        },
        getRandom(min, max) {
            const value = Math.random() * (max - min) + min
            return Math.round(value)
        }
    },
    watch: {
        hasResult(value) {
            if (value) this.running = false;
        },
        playerLife(value) {
            if (value === 0) new Audio('../public/songs/battle/lose.mp3').play()
        },
        monsterLife(value) {
            if (value === 0) new Audio('../public/songs/battle/win.mp3').play()
        }
    }
}
</script>

<template>
    <main>
        <div class="loading" v-if="loading">
            <img src="../public/loading.gif" alt="loading...">
        </div>
        <template v-else>
            <div class="fight-content">
                <img src="../public/fight.png" alt="fight" class="fight">
            </div>
            <div class="panel scores">
                <div class="score">
                    <div class="character">
                        <img src="../public/characters/mario.gif" alt="zeca">
                        <h1>Zé</h1>
                    </div>
                    <div class="life-bar">
                        <div class="life" :class="{ 'danger': playerLife < 20 }" :style="{ width: playerLife + '%' }">
                        </div>
                    </div>
                    <span>{{ playerLife }}%</span>
                </div>
                <div class="score">
                    <div class="character">
                        <img src="../public/characters/bowser.gif" alt="governo">
                        <h1>Governo</h1>
                    </div>
                    <div class="life-bar">
                        <div class="life" :class="{ 'danger': monsterLife < 20 }" :style="{ width: monsterLife + '%' }">
                        </div>
                    </div>
                    <span>{{ monsterLife }}%</span>
                </div>
                <img src="../public/russo.png" alt="" style="position: absolute">
            </div>
            <div class="panel result" v-show="hasResult">
                <div v-if="monsterLife === 0" class="win">Você ganhou!!</div>
                <div v-else class="lose">Você perdeu!</div>
            </div>
            <div class="panel buttons">
                <template v-if="running">
                    <button @click="attack(false)" class="btn attack">
                        Ataque
                    </button>
                    <button @click="attack(true)" class="btn special-attack">Ataque especial</button>
                    <button class="btn heal">Curar</button>
                    <button @click="running = false" class="btn give-up">Desistir</button>
                </template>
                <button v-else class="btn new-game" @click="startGame">Iniciar Jogo</button>
            </div>
            <!-- <div class="panel logs"></div> -->
        </template>
    </main>
</template>

<style scoped>
.loading {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
}

.loading img {
    width: 350px;
    margin-bottom: 120px;
}

.fight-content {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: none;
}

.fight-content.show {
    display: flex;
    align-items: center;
    justify-content: center;
    animation-name: fight;
    animation-duration: 2s;
    animation-timing-function: ease-in-out;
}

@keyframes fight {
    0% {
        transform: translateX(-1500px);
    }

    25%,
    50%,
    75% {
        transform: translateX(0px);
    }

    100% {
        transform: translateX(1500px);
    }
}

.fight {
    width: 50%;
    height: 40%;
    z-index: 10000;
}
</style>
