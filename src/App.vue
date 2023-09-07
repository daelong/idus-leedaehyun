<template>
  <div class="main">
    <div class="card-section">
      <CustomCard v-bind="{ ...card1 }" />
      <CustomCard v-bind="{ ...card2 }" />
      <CustomCard v-bind="{ ...card3 }" />
      <CustomWidthCard v-bind="{ ...card4 }" />
    </div>
    <div class="form-section">
      <InputForm />
    </div>
  </div>
</template>

<script lang="ts">
import { reactive, toRefs } from "vue";
import CustomCard from "./components/CustomCard/CustomCard.vue";
import CustomWidthCard from "./components/CustomCard/CustomWidthCard.vue";
import InputForm from "./components/InputForm.vue";

export default {
  components: { CustomCard, CustomWidthCard, InputForm },
  setup() {
    const state = reactive({
      card1: {
        label: "Card1 label",
        title: "Card1 title",
        discountPrice: "500원",
        cost: "700원",
        grade: 4,
        explanation: "700원 -> 500원",
      },

      card2: {
        label: "Card2 label",
        title: "Card2 title",
        discountPrice: "1000원",
        cost: "2000원",
        grade: 3,
        explanation: "lorem ipsum dolor sit amet,lorem ipsum dolor sit amet,",
      },
      card3: {
        label: "Card3 label",
        title: "Card3 title",
        discountPrice: "1000원",
        cost: "2000원",
      },
      card4: {
        title: "Card4 title",
        grade: 3,
        explanation:
          "lorem ipsum dolor sit amet, consectet lorem ipsum dolor sit amet, 2lorem ip2sum dolor sit amet, consectet lorem ipsum dolor sit amet",
        author: "author",
      },
    });
    return {
      ...toRefs(state),
    };
  },
};
</script>

<style scoped lang="scss">
.card-section {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}
.form-section {
  margin-top: 10%;
  text-align: start;
}
</style>
