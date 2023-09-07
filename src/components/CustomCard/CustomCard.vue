<template>
  <div class="card">
    <img class="card__img" src="../../assets/idus_icon.jpeg" />
    <div class="card__main">
      <div class="card__main__label">{{ label }}</div>
      <div class="card__main__title">{{ title }}</div>
      <div class="card__main__hilight">
        <span class="card__main__hilight__discountPrice">{{
          discountPrice
        }}</span>
        <span class="card__main__hilight__cost">{{ cost }}</span>
      </div>
    </div>
    <div v-if="grade" class="card__detail">
      <span
        class="card__detail__grade"
        v-for="i in 5"
        :key="i"
        :style="{ background: grade >= i ? '#ffc801' : '#d9d9d9' }"
      >
      </span>
      <div v-if="explanation" class="card__detail__explanation">
        {{ explanation }}
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { reactive, toRefs, defineComponent } from "vue";
export default defineComponent({
  //이건 세로
  //필수값: img, 라벨, 타이틀, Highight 설명?
  //선택값: 별점, 상세 설명
  props: {
    label: {
      type: String,
      default: "Card Label",
      required: true,
    },
    title: {
      type: String,
      default: "Card Title",
      required: true,
    },
    discountPrice: {
      type: String,
      default: "Hilight",
      required: true,
    },
    cost: {
      type: String,
      default: "Cross Out",
      required: true,
    },
    // detail: {
    //   type: Object,
    //   default: () => {
    //     return;
    //   },
    // },
    grade: {
      type: Number,
      default: 0,
    },
    explanation: {
      type: String,
      default: "",
    },
  },
});
</script>
<style lang="scss" scoped>
// 모바일
$breakpoint-mobile: 335px;
$breakpoint-mobile-card-size: 320px;

// 모바일에서 태블릿
$breakpoint-tabletToMobile: 535px;

// 노트북에서 데스크탑
$breakpoint-desktopToLaptop: 1500px;

// 데스크탑
$breakpoint-desktop-card-size: 200px;

.card {
  display: flex;
  flex-direction: column;
  border: 1px solid #d9d9d9;
  background-color: #f8f9fb;
  padding: 0;
  height: 100%;
  border-radius: 4px;

  &__img {
    width: 100%;
  }

  &__main {
    display: flex;
    flex-direction: column;
    text-align: start;

    &__label {
      padding: 8px 0 0 8px;
      margin-bottom: 4px;
      color: #999;
      font-size: 12px;
    }
    &__title {
      padding-left: 8px;

      font-size: 14px;
    }

    &__hilight {
      padding: 8px;
      &__discountPrice {
        font-size: 12px;
        color: #e74c3c;
        margin-right: 4px;
        font-weight: 400;
      }
      &__cost {
        font-size: 10px;
        color: #999;
        text-decoration-line: line-through;
      }
    }
  }
  &__detail {
    border-top: 1px solid #d9d9d9;
    padding: 0 10px;
    text-align: start;

    &__grade {
      margin: 9px 1.5px 0 1.5px;
      display: inline-block;
      width: 15px;
      height: 15px;
      border-radius: 50%;
    }
    &__explanation {
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      color: #666;
    }
  }
}

@media (min-width: #{$breakpoint-mobile}) and (max-width: #{$breakpoint-tabletToMobile - 1px}) {
  .card {
    width: 50%;
  }
  .card__detail__explanation {
    width: calc(100% - 40px);
  }
}

@media (min-width: #{$breakpoint-tabletToMobile}) {
  .card {
    width: $breakpoint-desktop-card-size;
  }
  .card__detail__explanation {
    width: calc($breakpoint-desktop-card-size - 40px);
  }
}
</style>
