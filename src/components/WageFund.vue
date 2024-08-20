<script setup>
import { ref, computed, watch } from "vue";

const objects = ref([
  {
    name: "",
    numberEmployees: 1,
    salary: 0,
  },
  {
    name: "",
    numberEmployees: 1,
    salary: 0,
  },
  {
    name: "",
    numberEmployees: 1,
    salary: 0,
  },
  {
    name: "",
    numberEmployees: 1,
    salary: 0,
  },
  {
    name: "",
    numberEmployees: 1,
    salary: 0,
  },
]);

objects.value.forEach((item) => {
  item.annualSalaryFund = computed(() => {
    return item.numberEmployees * item.salary * 12;
  });
  item.insurancePremiums = computed(() => {
    return item.annualSalaryFund * 0.3;
  });
});

const totalAnnualSalaryFund = computed(() => {
  return objects.value.reduce((sum, item) => sum + item.annualSalaryFund, 0);
});

const totalInsurancePremiums = computed(() => {
  return objects.value.reduce((sum, item) => sum + item.insurancePremiums, 0);
});





const emit = defineEmits(["update:total-annual-salary-fund", "update:total-insurance-premiums"]);

watch(totalAnnualSalaryFund, (newValue) => {
  emit("update:total-annual-salary-fund", newValue);
});

watch(totalInsurancePremiums, (newValue) => {
  emit("update:total-insurance-premiums", newValue);
});
</script>

<template>
  <div class="container">
    <h3 class="block-header">III. Фонд оплаты труда персонала</h3>
    <p class="manual">Расчет общий фонд оплаты труда персонала.</p>

    <table class="table-wage-fund">
      <thead>
        <tr>
          <th>Профессия (должность)</th>
          <th>Списочная численность, чел.</th>
          <th>Месячная заработная плата, руб.</th>
          <th>Годовой фонд оплаты труда, руб.</th>
          <th>Страховые взносы, руб.</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(item, index) in objects" :key="index">
          <td><input type="text" v-model="item.name" /></td>
          <td><input type="number" v-model.number="item.numberEmployees" /></td>
          <td><input type="number" v-model.number="item.salary" /></td>
          <td>{{ item.annualSalaryFund.toFixed(2) }}</td>
          <td>{{ item.insurancePremiums.toFixed(2) }}</td>
        </tr>

        <tr>
          <td>Итого</td>
          <td class="dash">&mdash;</td>
          <td class="dash">&mdash;</td>
          <td>{{ totalAnnualSalaryFund.toFixed(2) }}</td>
          <td>{{ totalInsurancePremiums.toFixed(2) }}</td>
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

.table-wage-fund {
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
