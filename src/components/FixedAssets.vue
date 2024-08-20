<script setup>
import { ref, computed,  } from "vue";

const objects = ref([
  {
    name: "",
    purchaseCost: 0,
    deliveryCost: 0,
    annualDepreciation: 0,
  },
  {
    name: "",
    purchaseCost: 0,
    deliveryCost: 0,
    annualDepreciation: 0,
  },
  {
    name: "",
    purchaseCost: 0,
    deliveryCost: 0,
    annualDepreciation: 0,
  },
  {
    name: "",
    purchaseCost: 0,
    deliveryCost: 0,
    annualDepreciation: 0,
  },
  {
    name: "",
    purchaseCost: 0,
    deliveryCost: 0,
    annualDepreciation: 0,
  },
  {
    name: "",
    purchaseCost: 0,
    deliveryCost: 0,
    annualDepreciation: 0,
  },
]);

// Вычисляемые свойства для столбцов
objects.value.forEach((item) => {
  item.annualDepreciation = computed(() => {
    return (item.purchaseCost - item.purchaseCost / 6) / 5;
  });
});

// Функция для добавления новой строки
const addTableRow = () => {
  const newRow = ref({
    name: "",
    purchaseCost: 0,
    deliveryCost: 0,
  });
  const annualDepreciation = computed(() => {
    return (newRow.value.purchaseCost - newRow.value.purchaseCost / 6) / 5;
  });
  Object.defineProperty(newRow.value, "annualDepreciation", {
    get: () => annualDepreciation.value,
  });
  objects.value.push(newRow.value);
};

const totalPurchaseCost = computed(() => {
  return objects.value.reduce((sum, item) => sum + item.purchaseCost, 0);
});

const totalDeliveryCost = computed(() => {
  return objects.value.reduce((sum, item) => sum + item.deliveryCost, 0);
});

const totalAnnualDepreciation = computed(() => {
  return objects.value.reduce((sum, item) => sum + item.annualDepreciation, 0);
});

const clearTable = () => {
  objects.value = objects.value.map(() => ({
    name: "",
    purchaseCost: 0,
    deliveryCost: 0,
    annualDepreciation: 0,
  }));
};
</script>

<template>
  <div class="container">
    <h3 class="block-header">II. Затраты на объекты основных средств</h3>
    <p class="manual">
      Введите необходимый перечень и стоимость основных средств.
    </p>

    <p class="manual">
      Пожалуйста, учтите, что необходимо вводить полную стоимость определённого
      товара. Например, если имеется пять одинаковых столов, то их стоимость
      умножается на количество, и полученное значение записывается.<br />
      Годовая аммортизация рассчитывается автоматически и без НДС.
    </p>

    <table class="table-fixed-assets">
      <thead>
        <tr>
          <th>Наименование объекта</th>
          <th>Общая стоимость товара(-ов)</th>
          <th>Затраты на доставку и монтаж</th>
          <th>Годовые амортизационные отчисления</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(item, index) in objects" :key="index">
          <td><input type="text" v-model="item.name" /></td>
          <td><input type="number" v-model.number="item.purchaseCost" /></td>
          <td><input type="number" v-model.number="item.deliveryCost" /></td>
          <td>{{ item.annualDepreciation.toFixed(2) }}</td>
        </tr>

        <tr>
          <td>Итого</td>
          <td>{{ totalPurchaseCost }}</td>
          <td>{{ totalDeliveryCost }}</td>
          <td>{{ totalAnnualDepreciation.toFixed(2) }}</td>
        </tr>
      </tbody>
    </table>
    <div class="btn">
      <button @click="addTableRow" class="add-btn">Добавить объект</button>
      <button @click="clearTable" class="clr-btn">Очистить данные</button>
    </div>
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

.table-fixed-assets {
  width: 100%;
  margin: 0 auto;
  margin-top: 30px;
  border-collapse: collapse;
  text-align: center;
  table-layout: fixed;
}

.btn {
  display: flex;
  justify-content: flex-start;
  gap: 30px;
}

.add-btn {
  margin-top: 10px;
  background-color: blue;
  padding: 5px 15px;
  border-radius: 5px;
  font-size: 16px;
  font-weight: 600;
  color: white;
}

.clr-btn {
  margin-top: 10px;
  background-color: green;
  padding: 5px 15px;
  border-radius: 5px;
  font-size: 16px;
  font-weight: 600;
  color: white;
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
