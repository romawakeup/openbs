<script setup>
import { ref } from "vue";

defineProps({
  calculateYearTotal: {
    type: Number,
    required: true,
  },
});

const tableCashFlow = ref([
  {
    name: "Приток денежных средств",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "доход от продаж по проекту, с НДС",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "другие доходы (кредит)",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Отток денежных средств",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "приобретение основных средств, с НДС",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "затраты на производство и реализацию без амортизации",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "единый налог",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "выплаты по кредиту",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "проценты по кредиту",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Превышение/ Дефицит денежных средств, направляемых на возмещение инвестиций",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Коэффициент дисконтирования(r=0,12)",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "Превышение/Дефицит денежных средств, направляемых на возмещение инвестиций с учетом фактора времени",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
  {
    name: "NPV",
    year1: 0,
    year2: 0,
    year3: 0,
    year4: 0,
    year5: 0,
    total: 0,
  },
]);




</script>

<template>
  <div class="container">
    <h3 class="block-header">VII. Денежные потоки по проекту</h3>
    <p class="manual">
      Таблица денежных потоков по проекту при финансировании из заёмных средств
      представляет собой анализ движения денежных средств, связанных с
      реализацией проекта, включая поступления и выплаты, возникающие в
      результате привлечения заёмных средств.
    </p>

    <table class="table-cash-flow">
      <thead>
        <tr>
          <th>Показатели</th>
          <th>1 год</th>
          <th>2 год</th>
          <th>3 год</th>
          <th>4 год</th>
          <th>5 год</th>
          <th>Итого</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(item, index) in tableCashFlow" :key="index">
          <td>{{ item.name }}</td>
          <td>{{ item.year1 }}</td>
          <td>{{ item.year2 }}</td>
          <td>{{ item.year3 }}</td>
          <td>{{ item.year4 }}</td>
          <td>{{ item.year5 }}</td>
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

.table-cash-flow {
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
