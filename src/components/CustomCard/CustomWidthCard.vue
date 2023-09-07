<template>
  <div class="card">
    <img class="card__img" src="../../assets/idus_icon.jpeg" />
    <div class="card__main">
      <div class="card__main__body">
        <div class="card__main__body__title">{{ title }}</div>
        <div class="card__main__body__explanation">{{ explanation }}</div>
      </div>
      <div class="card__main__footer">
        <span
          class="card__main__footer__grade"
          v-for="i in 5"
          :key="i"
          :style="{ background: grade >= i ? '#ffc801' : '#d9d9d9' }"
        >
        </span>
        <span v-if="author" class="card__main__footer__author">
          | {{ author }}
        </span>
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
    title: {
      type: String,
      default: "Card Title",
      required: true,
    },
    explanation: {
      type: String,
      default: "Lorem Ipsum",
      required: true,
    },
    grade: {
      type: Number,
      default: 3,
    },
    author: {
      type: String,
      default: "author",
    },
  },
});
</script>
<style lang="scss" scoped>
// 모바일
$breakpoint-mobile: 335px;
$breakpoint-mobile-card-size: 260px;

// 모바일에서 태블릿
$breakpoint-tabletToMobile: 535px;
$breakpoint-laptopToTablet: 960px;

// 노트북에서 데스크탑
$breakpoint-desktopToLaptop: 1500px;

// 데스크탑
$breakpoint-desktop-card-size: 180px;

.card {
  display: flex;
  flex-direction: row;
  border: 1px solid #d9d9d9;
  background-color: #f8f9fb;
  padding: 0;
  border-radius: 4px;
  height: 30%;

  &__img {
    width: 40%;
  }

  &__main {
    flex-grow: auto;
    display: flex;
    flex-direction: column;
    line-height: 1.5;
    padding: 0 20px;

    &__body {
      text-align: start;
      height: 100%;
      &__title {
        font-size: 14px;
        font-weight: 700;
        text-overflow: ellipsis;
        margin: 15px 0;
        overflow: hidden;
        height: 21px;
        -webkit-line-clamp: 1;
        -webkit-box-orient: vertical;
      }

      &__explanation {
        display: -webkit-box;
        color: #666;
        text-overflow: ellipsis;
        overflow: hidden;
        font-size: 14px;
        -webkit-line-clamp: 3;
        -webkit-box-orient: vertical;
        line-height: 1.5;
        white-space: pre-line;
        width: 180px;
      }
    }

    &__footer {
      padding: 20px 0;
      text-align: start;
      &__grade {
        margin: 9px 1.5px 0 1.5px;
        display: inline-block;
        width: 15px;
        height: 15px;
        border-radius: 50%;
      }
      &__author {
        color: #666;
      }
    }
  }

  @media (min-width: #{$breakpoint-mobile}) and (max-width: #{$breakpoint-laptopToTablet - 1px}) {
    .card__img {
      width: 40%;
    }
  }

  @media (min-width: #{$breakpoint-laptopToTablet}) {
    .card__img {
      width: $breakpoint-desktop-card-size;
    }
  }
}
</style>
