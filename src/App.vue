<script setup>
import { ref } from "vue";

import TheHeader from "./components/TheHeader.vue";
import TheDescription from "./components/TheDescription.vue";
import SalesVolumes from "./components/SalesVolumes.vue";
import FixedAssets from "./components/FixedAssets.vue";
import WageFund from "./components/WageFund.vue";
import MaterialResources from "./components/MaterialResources.vue";
import CostEstimates from "./components/CostEstimates.vue";
import SingleTax from "./components/SingleTax.vue";
import CashFlow from "./components/CashFlow.vue";

const totalAnnualSalaryFund = ref(0);
const totalInsurancePremiums = ref(0);
const calculateYearTotal = ref(0);

const handleTotalAnnualSalaryFund = (value) => {
  totalAnnualSalaryFund.value = value;
};

const handleTotalInsurancePremiums = (value) => {
  totalInsurancePremiums.value = value;
};

const handleCalculateYearTotal = (value) => {
  calculateYearTotal.value = value;
};



</script>

<template>
  <div >
    <TheHeader />
    <TheDescription />
    <SalesVolumes @update:calculate-year-total="handleCalculateYearTotal" />
    <FixedAssets />
    <WageFund @update:total-annual-salary-fund="handleTotalAnnualSalaryFund" @update:total-insurance-premiums="handleTotalInsurancePremiums"/>
    <!-- <MaterialResources /> -->
    <CostEstimates :total-annual-salary-fund="totalAnnualSalaryFund" :total-insurance-premiums="totalInsurancePremiums"  />
    <SingleTax />
    <CashFlow :calculate-year-total="calculateYearTotal"/>
  </div>
</template>

<style scoped></style>
