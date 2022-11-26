<script lang="ts">
import { Component, Vue } from 'vue-facing-decorator';
import ListProducts from './pages/products/list-products.vue';

@Component({
  components: {
    ListProducts
  }
})
export default class App extends Vue {
  quandoEvendoForEmitidoExecutaEssaFuncao(): void {
    console.log('Evento disparado no componente App')
  }
}

</script>

<template>
  <ListProducts @change="quandoEvendoForEmitidoExecutaEssaFuncao" />
</template>