<script setup>
import { ref, computed } from "vue";

const objects = ref([
  {
    name: "",
    consumptionRate: 0,
    productionVolume: 0,
    purchasePrice: 0,
    purchasePriceAll: 0,
  },
  {
    name: "",
    consumptionRate: 0,
    productionVolume: 0,
    purchasePrice: 0,
    purchasePriceAll: 0,
  },
  {
    name: "",
    consumptionRate: 0,
    productionVolume: 0,
    purchasePrice: 0,
    purchasePriceAll: 0,
  },
  {
    name: "",
    consumptionRate: 0,
    productionVolume: 0,
    purchasePrice: 0,
    purchasePriceAll: 0,
  },
  {
    name: "",
    consumptionRate: 0,
    productionVolume: 0,
    purchasePrice: 0,
    purchasePriceAll: 0,
  },
  {
    name: "",
    consumptionRate: 0,
    productionVolume: 0,
    purchasePrice: 0,
    purchasePriceAll: 0,
  },
]);
</script>

<template>
  <div class="container">
    <h3 class="block-header">IV. Материальные ресурсы для производства <span style="color: RED;">НА ДОРАБОТКЕ</span></h3>
    <p class="manual">
      Оценка примерных расходов на сырье, материалы, полуфабрикаты и
      комплектующие изделия, а также электроэнергию, газ, воду. Для этого
      определяется количественная потребность в материальных ресурсах на и год,
      исходя из технологии и объемов производства продукта.
    </p>

    <table class="table-mat-res">
      <thead>
        <tr>
          <th>Наименование ресурса</th>
          <th>Норма расхода на ед. продукта</th>
          <th>Объем производства, ед.</th>
          <th>Цена приобретения за ед., руб.</th>
          <th>Стоимость приобретения</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(item, index) in objects" :key="index">
          <td><input type="text" v-model="item.name" /></td>
          <td><input type="number" v-model="item.consumptionRate" /></td>
          <td><input type="number" v-model="item.productionVolume" /></td>
          <td><input type="number" v-model="item.purchasePrice" /></td>
          <td><input type="number" v-model="item.purchasePriceAll" /></td>
        </tr>

        <tr>
          <td>Итого</td>
          <td class="dash">&mdash;</td>
          <td class="dash">&mdash;</td>
          <td class="dash">&mdash;</td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.container {
  margin: 0 auto;
  padding: 0 15px;
  max-width: 1400px;
  margin-top: 70px;
  font-size: 16px;
  font-family: "Kanit", sans-serif;
}

.block-header {
  font-size: 21px;
  font-weight: 700;
}

.manual {
  margin-top: 10px;
  font-size: 16px;
}

.table-mat-res {
  width: 100%;
  margin-top: 30px;
  border-collapse: collapse;
  text-align: center;
  table-layout: fixed;
}

td {
  text-align: left;
  padding: 10px;
  border: 1px solid black;
}

th {
  text-align: left;
  padding: 10px;
  border: 1px solid black;
}

.dash {
  text-align: center;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
</style>
