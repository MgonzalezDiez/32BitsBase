<template>
  <div>
    <ul v-if="sales.length > 0">
      <li v-for="(sale, index) in sales" :key="index">
        {{sale.id}} {{sale.name}} {{sale.price}}
      </li>
    </ul>
    <ul v-else>
      <p>No hay ventas registradas</p>
    </ul>

    <p>Total de Ventas : {{totalSales}}</p>

  </div>
</template>

<script>

import {mapState} from 'vuex'

export default {
computed: {
  ...mapState(["sales"]),
  totalSales() {
    return this.sales.reduce( (accumulator, currentSale) => accumulator + currentSale.price, 0)
  }
}
}
</script>

<style>

</style>