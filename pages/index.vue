<template>
  <section>
    <DetailCards class="mt-10" />
    <div style="margin-top: 70px">
      <MbsaEnergyConsumption />
    </div>
  </section>
</template>

<script>
import DetailCards from "~/components/DetailCards";
import MbsaEnergyConsumption from "~/components/MbsaEnergyConsumption";

export default {
  components: {
    DetailCards,
    MbsaEnergyConsumption,
  },
};
</script>

<style scoped>
/* .v-main__wrap {
  background-color: #e1e1e1;
} */
</style>
