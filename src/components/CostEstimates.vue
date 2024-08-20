<script setup>
import { ref, computed } from "vue";

const props = defineProps({
  totalAnnualSalaryFund: {
    type: Number,
    required: true,
  },
  totalInsurancePremiums: {
    type: Number,
    required: true,
  },
});

const tableData = ref([
  {
    name: "Материальные расходы",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Расходы на оплату труда",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Страховые взносы",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Арендная плата",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Прочие расходы",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Итого (без амортизационных отчислений)",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Амортизационные отчисления",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
]);

const salaryData = computed(() => {
  return tableData.value.map((item) => {
    if (item.name === "Расходы на оплату труда") {
      return {
        ...item,
        year1: props.totalAnnualSalaryFund,
        year2: props.totalAnnualSalaryFund,
        year3: props.totalAnnualSalaryFund,
        year4: props.totalAnnualSalaryFund,
        year5: props.totalAnnualSalaryFund,
        total: props.totalAnnualSalaryFund * 5,
      };
    } else if (item.name === "Страховые взносы") {
      return {
        ...item,
        year1: props.totalInsurancePremiums,
        year2: props.totalInsurancePremiums,
        year3: props.totalInsurancePremiums,
        year4: props.totalInsurancePremiums,
        year5: props.totalInsurancePremiums,
        total: props.totalInsurancePremiums * 5,
      };
    } else {
      return item;
    }
  });
});


// функция для того чтоб между тысячными были пробелами, например 1000000 = 1 000
const formatNumber = (number) => {
  return number.toLocaleString("ru-RU");
};

const rentTotal = computed(() => {
  const rentRow = tableData.value.find((item) => item.name === "Арендная плата");
  if (rentRow) {
    return rentRow.year1 + rentRow.year2 + rentRow.year3 + rentRow.year4 + rentRow.year5;
  } else {
    return 0;
  }
});
</script>

<template>
  <div class="container">
    <h3 class="block-header">
      V. Смета расходов на производство и реализацию товаров по стадиям ЖЦИП
    </h3>
    <p class="manual">
      Расчет потребных инвестиций на формирование оборотного капитала.
    </p>

    <table class="table-cost-est">
      <thead>
        <tr>
          <th>Наименование элементов расходов</th>
          <th>1 год</th>
          <th>2 год</th>
          <th>3 год</th>
          <th>4 год</th>
          <th>5 год</th>
          <th>Итого</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in salaryData" :key="index">
          <td>{{ item.name }}</td>
          <td v-if="item.name === 'Арендная плата'">
            <input type="number" v-model.number="item.year1" />
          </td>
          <td v-else>{{ formatNumber(item.year1) }}</td>
          <td v-if="item.name === 'Арендная плата'">
            <input type="number" v-model.number="item.year2" />
          </td>
          <td v-else>{{ formatNumber(item.year2) }}</td>
          <td v-if="item.name === 'Арендная плата'">
            <input type="number" v-model.number="item.year3" />
          </td>
          <td v-else>{{ formatNumber(item.year3) }}</td>
          <td v-if="item.name === 'Арендная плата'">
            <input type="number" v-model.number="item.year4" />
          </td>
          <td v-else>{{ formatNumber(item.year4) }}</td>
          <td v-if="item.name === 'Арендная плата'">
            <input type="number" v-model.number="item.year5" />
          </td>
          <td v-else>{{ formatNumber(item.year5) }}</td>
          <td v-if="item.name === 'Арендная плата'">
          {{ formatNumber(rentTotal) }}
        </td>
        <td v-else>{{ formatNumber(item.total) }}</td>
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

.table-cost-est {
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

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
</style>
