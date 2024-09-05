<template>
<div class="box has-text-weight-bold claro">
    <slot>

    </slot>
</div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BoxComponent'
})
</script>

<style scoped>
  .box {
    background: #284661;
    color: rgb(255, 255, 255);
  }

  .claro {
    background-color: var(--box-primaria);
  }
 </style>
