<template>
          <section>
                    <strong class="display"> 
                        {{ timeNow }}
                    </strong>
                </section>
</template>

<script lang='ts'>
import { defineComponent } from 'vue';

export default defineComponent ({
    
    name : 'CronometroTime',
    props: {
        timeInSeconds : {
            type: Number,
            default : 0
        }
    },

    computed : {
        timeNow () : string {
            return new Date(this.timeInSeconds*1000).toISOString().substr(11,8)
        }
    }
})



</script>

<style>

.display {
    color: var(--texto-primario);
    
}
</style>