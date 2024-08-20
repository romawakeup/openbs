<script setup>
import { ref } from "vue";


const objects = ref([
  {
    name: "Итого за 1-ый год",
    salesVolume: 0,
    tax: 0,
  },
  {
    name: "Итого за 2-ой год",
    salesVolume: 0,
    tax: 0,
  },
  {
    name: "Итого за 3-ий год",
    salesVolume: 0,
    tax: 0,
  },
  {
    name: "Итого за 4-ыйгод",
    salesVolume: 0,
    tax: 0,
  },
  {
    name: "Итого за 5-ый год",
    salesVolume: 0,
    tax: 0,
  },
  {
    name: "Итого за 5 лет",
    totalSalesVolume: 0,
    totalTax: 0,
  },
]);
</script>

<template>
  <div class="container">
    <h3 class="block-header">VI. Единый налог</h3>
    <p class="manual">
      Для выплат налогов была выбрана упрощенная система налогообложения для
      индивидуальных предпринимателей, базой которой является доход предприятия.
    </p>

    <table class="table-single-tax">
      <thead>
        <tr>
          <th>Периоды</th>
          <th>Объем продаж</th>
          <th>Сумма налога</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(item, index) in objects" :key="index">
          <td>{{ item.name }}</td>
          <td></td>
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

.table-single-tax {
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
