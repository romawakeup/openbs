<script setup>
import { ref, computed, watch } from "vue";

const yearsData = ref([
  { price: 0, volume: 0, total: 0 },
  { price: 0, volume: 0, total: 0 },
  { price: 0, volume: 0, total: 0 },
  { price: 0, volume: 0, total: 0 },
  { price: 0, volume: 0, total: 0 },
]);



const projectTotal = computed(() => {
  return yearsData.value.reduce((sum, year) => sum + year.total, 0);
});

function calculateYearTotal(index) {
  yearsData.value[index].total =
    parseFloat(yearsData.value[index].price) *
    parseFloat(yearsData.value[index].volume);
}

const volumeTotal = computed(() => {
  return yearsData.value.reduce((sum, year) => sum + year.volume, 0);
});




const emit = defineEmits(["update:calculate-year-total"]);

watch(yearsData, (newValue) => {
  const total = newValue.reduce((sum, year) => sum + year.total, 0);
  emit("update:calculate-year-total", total);
});
</script>

<template>
  <div class="container">
    <h3 class="block-header">I. Расчет объема продаж</h3>
    <p class="manual">
      Выберите объект инвестиционного проекта. Это может быть, например, как
      гончарная мастерская, так и небольшая пекарня.
    </p>
    <p class="manual">
      Необходимо ввести в таблицу расчета плана производства продуктов в
      натуральных измерителях. Имейте в виду, что на ликвидационной стадии
      производство прекращается, поэтому в последнем году реализации объем
      производства с учетом его постепенного снижения устанавливается в размере
      50% от проектного.
    </p>

    <table class="table-sales-volumes">
      <thead>
        <tr>
          <th>Стадии ЖЦИП</th>
          <th>Розничная цена, руб.</th>
          <th>Объем продаж, ед.</th>
          <th>Итого, руб.</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(yearData, index) in yearsData" :key="index">
          <td>Итого за {{ index + 1 }}-ый год</td>
          <td>
            <input
              type="number"
              v-model.number="yearData.price"
              @input="calculateYearTotal(index)"
            />
          </td>
          <td>
            <input
              type="number"
              v-model.number="yearData.volume"
              @input="calculateYearTotal(index)" 
            />
          </td>
          <td>{{ yearData.total }}</td>
        </tr>
        <tr>
          <td>Итого по проекту</td>
          <td class="dash">&mdash;</td>
          <td>
            <span>{{ volumeTotal }}</span>
          </td>
          <td>
            <span>{{ projectTotal }}</span>
          </td>
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

.table-sales-volumes {
  width: 100%;
  margin: 0 auto;
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

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}

.dash {
  text-align: center;
}
</style>
