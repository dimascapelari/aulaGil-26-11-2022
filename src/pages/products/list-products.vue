<script lang="ts">
import { Vue, Component, Prop, Watch } from 'vue-facing-decorator'
import Product from '../../models/Product'


@Component({
  emits: ['changeBrand']
})
export default class ListProducts extends Vue {
  listProducts: Array<Product> = [{ id: 32432, name: 'Produto Dimas', descriprion: 'DEscrição', stock: 34, price: 34.59 }]

  @Prop({ default: 300 }) preco!: number

  foiVendido =  false

  productName!: string

  productBrand = 'Adidas'

  mounted() {
    console.log('Mounted')
  }

  @Watch('productBrand')
  onproductBrandChange(): void {
    console.log('Variável productBrand mudou')
  }

  nomeEmarcaDoProduto(): string {
    return `${this.productName} - ${this.productBrand}`
  }

  mudarNomedaMarca(): void {
    this.$emit('changeBrand')
    this.productBrand = 'Nome da marcar mudou'
  }


  valorMaiorQueCem(price: number): boolean {
    return price > 100
  }
}

</script>
<template>
  <h2> Lista de produtos {{ nomeEmarcaDoProduto() }}</h2>
  <p> Preço: {{ preco }}</p>
  <button type="button" @click="mudarNomedaMarca"> Mudar nome da marca </button>

  <table>
    <thead>
      <th>
        <td> Nome </td>
        <td> Preço </td>
        <td> É maior que 100 </td>
      </th>
    </thead>
    <tbody>
      <tr v-for="product in listProducts" :key="product.id">
        <td> {{ product.name }} </td>
        <td> {{ product.price }} </td>
        <td> {{ valorMaiorQueCem(product.price) }} </td>
      </tr>
    </tbody>
  </table>
</template>
<style>
  h2 {
    width: 100vh;
    display: flex;
    align-items: center;
  }
</style>