    <template>
        <div class="box formulario">
            <div class="columns is-flex is-justify-content-center">
                <div class="column is-8 " role="form" aria-label="Formulario pra criação de uma nova tarefa">
                    <input type="text" class="input" placeholder="Qual tarefa você deseja fazer agora?" v-model="description">
                    <div class="column">
                    <Temporizador @watch-stopped="finishTask"/>
                    </div>
                

                </div>
            </div>
        </div>
    </template>


    <script lang="ts">
    import { defineComponent } from 'vue';
    import Temporizador from './Temporizador.vue'
    export default defineComponent({
        name : "FormularioComponent",
        emits : ['aoSalvarTarefa'],

        components : {
        Temporizador 
        },
        data () {
            return {
                description : ''

                
            }
        },
        methods: {
            finishTask(timeNow: number) : void {
                console.log('tempo decorrido', timeNow)
                console.log('descrição da tarefa' , this.description)
            
                this.$emit('aoSalvarTarefa', {
                    durationInSeconds : timeNow,
                    description : this.description
                }) 
            }
            
        }
    })

    </script>

    <style>
    .formulario {
        color: var(--texto-primario);
        background-color: var(--bg-primario);
    }

    .input {
        background-color: var(--box-primaria);

    }

    .input::placeholder {
       color: var(--bg-primario);
       
    }

    </style>


