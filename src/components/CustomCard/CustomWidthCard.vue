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
$breakpoint-mobile-card-size: 260px;

// 모바일에서 태블릿
$breakpoint-tabletToMobile: 535px;
$breakpoint-tabletToMobile-card-size: 240px;

// 태블릿
$breakpoint-tablet: 720px;
$breakpoint-tablet-card-size: 230px;

// 태블릿에서 노트북
$breakpoint-laptopToTablet: 960px;
$breakpoint-laptopToTablet-card-size: 220px;

// 노트북
$breakpoint-laptop: 1024px;
$breakpoint-laptop-card-size: 210px;

// 노트북에서 데스크탑
$breakpoint-desktopToLaptop: 1500px;
$breakpoint-desktopToLaptop-card-size: 220px;

// 데스크탑
$breakpoint-desktop: 1800px;
$breakpoint-desktop-card-size: 190px;

.card {
  display: flex;
  flex-direction: row;
  border: 1px solid #d9d9d9;
  background-color: #f8f9fb;
  padding: 0;
  height: 100%;
  border-radius: 4px;

  &__img {
  }

  &__main {
    flex-grow: auto;
    display: flex;
    flex-direction: column;
    line-height: 1.5;
    padding: 0 20px;

    &__body {
      text-align: start;
      height: 40%;
      height: 100%;
      // height: auto;
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

  @media (min-width: #{$breakpoint-mobile}) and (max-width: #{$breakpoint-tabletToMobile - 1px}) {
    .card__img {
      width: $breakpoint-mobile-card-size;
      height: $breakpoint-mobile-card-size;
    }
  }

  // 모바일에서 태블릿 : 최소 '모바일에서 태블릿'사이즈부터 ~ 최대 '태블릿'사이즈까지
  @media (min-width: #{$breakpoint-tabletToMobile}) and (max-width: #{$breakpoint-tablet - 1px}) {
    .card__img {
      width: $breakpoint-tabletToMobile-card-size;
      height: $breakpoint-tabletToMobile-card-size;
    }
  }

  // 태블릿 : 최소'태블릿'사이즈부터 ~ 최대 '태블릿에서 노트북'사이즈까지
  @media (min-width: #{$breakpoint-tablet}) and (max-width: #{$breakpoint-laptopToTablet - 1px}) {
    .card__img {
      width: $breakpoint-laptop-card-size;
      height: $breakpoint-laptop-card-size;
    }
  }

  // 태블릿에서 노트북 : 최소 '태블릿에서 노트북'사이즈부터 ~ 최대 '노트북'사이즈까지
  @media (min-width: #{$breakpoint-laptopToTablet}) and (max-width: #{$breakpoint-laptop - 1px}) {
    .card__img {
      width: $breakpoint-desktopToLaptop-card-size;
      height: $breakpoint-desktopToLaptop-card-size;
    }
  }

  // 노트북 : 최소 '노트북'사이즈부터 ~ 최대 '노트북에서 데스크탑'사이즈까지
  @media (min-width: #{$breakpoint-laptop}) and (max-width: #{$breakpoint-desktopToLaptop - 1px}) {
    .card__img {
      width: $breakpoint-desktop-card-size;
      height: $breakpoint-desktop-card-size;
    }
  }
}
</style>
