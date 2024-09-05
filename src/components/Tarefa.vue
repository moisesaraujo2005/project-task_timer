<template>
    <BoxComponent>
      <div class="columns">
        <div class="column is-7"> {{ task.description  || 'Tarefa sem descrição'}} </div>
        <div class="column">
          <CronometroTime :timeInSeconds="task.durationInSeconds"/>
        </div>
      </div>
    </BoxComponent>
  </template>
  
  <script lang="ts">
  import { defineComponent, PropType } from 'vue';
  import CronometroTime from './Cronometro.vue';
  import ITarefa from '../interfaces/ITarefa';
  import BoxComponent from './Box.vue'
  
  export default defineComponent({
    name: 'TarefaComponent',
    components: {
      CronometroTime,
      BoxComponent
    },
    props: {
      task: {
        type: Object as PropType<ITarefa>,
        required: true
      }
    }
  });
  </script>
  
  
 
  