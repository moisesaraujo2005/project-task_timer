<template>
       <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <CronometroTime :timeInSeconds="timeInSeconds"/>
                <button class="button" @click="start" :disabled="stopWatchRunning">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>Play</span>
        </button>
        <button class="button" @click="finish" :disabled="!stopWatchRunning">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>Stop</span>
        </button>
                    </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import CronometroTime from './Cronometro.vue';
export default defineComponent({
    name : 'FormularioComponent',
    emits: ['watchStopped'],
    components : {
        CronometroTime
    },
    data () {
        return{
            timeInSeconds : 0,
            stopWatch : 0,
            stopWatchRunning : false
        
        
        }
    },
  
    methods: {
        start () {
            this.stopWatchRunning = true;
           this.stopWatch = setInterval(() => {
                this.timeInSeconds+=1
            }, 1000)
            console.log('iniciando')
        },
        finish () {
            this.stopWatchRunning = false;
            
            clearInterval(this.stopWatch)
            console.log('finalizando')
            console.log(this.stopWatch)
            this.$emit('watchStopped', this.timeInSeconds);
            this.timeInSeconds =0;
        }
    }
})

</script>

<style>
.button {
    background-color: var(--box-primaria);
}
</style>