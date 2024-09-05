<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-claro' : modoClaroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioComponent @aoSalvarTarefa = "saveTask"/>
   
    <div class="lista">
    
      <TarefaComponent v-for="(task , index)  in tarefas" :key="index" :task="task"/>
      <BoxComponent v-if="listaVazia">
    Você não está produtivo hoje :(
  </BoxComponent>
    </div> 
  

  </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioComponent from './components/Formulario.vue';
import TarefaComponent from './components/Tarefa.vue';
import ITarefa from './interfaces/ITarefa';
import BoxComponent from './components/Box.vue'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioComponent,
    TarefaComponent,
    BoxComponent

  },
  data () {
    return {
      tarefas : [] as ITarefa [],
      modoClaroAtivo : false
    }
  },
  methods : {
    saveTask  (task:ITarefa) {
      this.tarefas.push(task) 
    },
    trocarTema(modoClaroAtivo: boolean) {
      this.modoClaroAtivo = modoClaroAtivo
    }
  },
  computed: {
    listaVazia() : boolean {
      return this.tarefas.length==0;
    }
  }
});
</script>

<style >
  .lista {
    padding: 1.5rem;
  }

  main {
    --bg-primario: rgb(13 18 33 / 90%) 
    --texto-primario: #fff;
}

main.modo-claro {
    --bg-primario: rgb(255, 255, 255); 
    --texto-primario: #000000;
    --box-primaria : rgb(150 150 255);
}

.conteudo {
    background-color: var(--bg-primario);
    color: var(--texto-primario);
}

</style>
