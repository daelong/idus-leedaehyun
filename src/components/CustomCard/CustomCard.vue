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
  setup(props: any) {
    const state = reactive({});
    return {
      ...toRefs(state),
    };
  },
});
</script>
<style lang="scss" scoped>
// 모바일
$breakpoint-mobile: 335px;
$breakpoint-mobile-card-size: 320px;

// 모바일에서 태블릿
$breakpoint-tabletToMobile: 535px;
$breakpoint-tabletToMobile-card-size: 270px;

// 태블릿
$breakpoint-tablet: 720px;
$breakpoint-tablet-card-size: 260px;

// 태블릿에서 노트북
$breakpoint-laptopToTablet: 960px;
$breakpoint-laptopToTablet-card-size: 250px;

// 노트북
$breakpoint-laptop: 1024px;
$breakpoint-laptop-card-size: 240px;

// 노트북에서 데스크탑
$breakpoint-desktopToLaptop: 1500px;
$breakpoint-desktopToLaptop-card-size: 230px;

// 데스크탑
$breakpoint-desktop: 1800px;
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
    flex-grow: 4;
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

    // color: #666;
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
  .card__img {
    width: $breakpoint-mobile-card-size;
    height: $breakpoint-mobile-card-size;
  }
  .card__detail__explanation {
    width: calc($breakpoint-mobile-card-size - 20px);
  }
}

// 모바일에서 태블릿 : 최소 '모바일에서 태블릿'사이즈부터 ~ 최대 '태블릿'사이즈까지
@media (min-width: #{$breakpoint-tabletToMobile}) and (max-width: #{$breakpoint-tablet - 1px}) {
  .card__img {
    width: $breakpoint-tabletToMobile-card-size;
    height: $breakpoint-tabletToMobile-card-size;
  }
  .card__detail__explanation {
    width: calc($breakpoint-tabletToMobile-card-size - 20px);
  }
}

// 태블릿 : 최소'태블릿'사이즈부터 ~ 최대 '태블릿에서 노트북'사이즈까지
@media (min-width: #{$breakpoint-tablet}) and (max-width: #{$breakpoint-laptopToTablet - 1px}) {
  .card__img {
    width: $breakpoint-laptop-card-size;
    height: $breakpoint-laptop-card-size;
  }
  .card__detail__explanation {
    width: calc($breakpoint-laptop-card-size - 20px);
  }
}

// 태블릿에서 노트북 : 최소 '태블릿에서 노트북'사이즈부터 ~ 최대 '노트북'사이즈까지
@media (min-width: #{$breakpoint-laptopToTablet}) and (max-width: #{$breakpoint-laptop - 1px}) {
  .card__img {
    width: $breakpoint-desktopToLaptop-card-size;
    height: $breakpoint-desktopToLaptop-card-size;
  }
  .card__detail__explanation {
    width: calc($breakpoint-desktopToLaptop-card-size - 20px);
  }
}

// 노트북 : 최소 '노트북'사이즈부터 ~ 최대 '노트북에서 데스크탑'사이즈까지
@media (min-width: #{$breakpoint-laptop}) and (max-width: #{$breakpoint-desktopToLaptop - 1px}) {
  .card__img {
    width: $breakpoint-desktop-card-size;
    height: $breakpoint-desktop-card-size;
  }
  .card__detail__explanation {
    width: calc($breakpoint-desktop-card-size - 20px);
  }
}
</style>
