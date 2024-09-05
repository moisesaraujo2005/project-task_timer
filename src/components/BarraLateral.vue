<template>
<header class="claro">
    <h1>
        <img style="border-radius: 25px;" class="" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRThtwwSjqFYyogRiW81hxVjCQ8em7VNb_p4A&s" alt="">
    </h1>
    <button class="button" @click="alterTheme">
    {{textoBotao}}
    </button>
</header>
</template>

<script lang="ts">

import { defineComponent} from 'vue';

export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data() {
        return{
            modoClaroAtivo : false
        }
    },
    computed : {
        textoBotao() {
            if(this.modoClaroAtivo) {
                return 'Desativar modo claro'
            }

            else {
                return 'Ativar modo claro'
            }
        }
    },

    methods : {
        alterTheme() {
            this.modoClaroAtivo = !this.modoClaroAtivo
            this.$emit('aoTemaAlterado', this.modoClaroAtivo)
        }
    }
})

</script>


<style scoped>

header {
    padding: 1rem;
    background-color: #032443;
    width: 100%;
    height: 100vh;
    text-align: center;
}

@media only screen and (max-width: 768px) {
    header
    {
        padding: 2.5rem;
        height: auto;
    }
}

img {
    max-width: 90%;
}
.claro {
    background-color: var(--box-primaria);
}
</style>