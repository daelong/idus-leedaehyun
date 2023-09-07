<template>
  <form class="form-box">
    <div class="textarea-box">
      <textarea
        class="textarea-box__textarea"
        v-model="firstChar"
        cols="30"
        rows="5"
        placeholder="자신의 의견을 간단히 적어주세요."
      ></textarea>
      <p class="textarea-box__count">{{ maxChars - firstCharCount }}</p>
    </div>
    <div class="textarea-save-btn-box">
      <div class="textarea-box">
        <textarea
          class="textarea-box__textarea"
          v-model="secondChar"
          cols="30"
          rows="5"
          placeholder="자신의 의견을 간단히 적어주세요."
        ></textarea>
        <p class="textarea-box__count">{{ maxChars - secondCharCount }}</p>
      </div>
      <button
        class="btn-box"
        :disabled="secondChar === SECOND_FIRST_TEXT"
        :style="{
          color: secondChar === SECOND_FIRST_TEXT ? '#999' : '#00d2d3',
        }"
      >
        Save
      </button>
    </div>
    <div class="textarea-box">
      <textarea
        class="textarea-box__textarea"
        v-model="thirdChar"
        cols="30"
        rows="5"
        placeholder="주문 요청사항을 입력해주세요"
        disabled
      ></textarea>
      <p class="textarea-box__count">{{ maxChars - thirdCharCount }}</p>
    </div>
    <div class="textarea-box">
      <textarea
        class="textarea-box__textarea"
        v-model="fourthChar"
        cols="30"
        rows="5"
        readonly
      ></textarea>
    </div>
  </form>
</template>

<script lang="ts">
import { reactive, toRefs, computed, defineComponent } from "vue";
// import { useForm } from "vee-validate";

export default defineComponent({
  setup() {
    const SECOND_FIRST_TEXT = "입력중.. 또는 내용 변경시";

    const state = reactive({
      firstChar: "초기값이 있을 수 있습니다",
      secondChar: SECOND_FIRST_TEXT,
      thirdChar: "",
      fourthChar: "읽기 전용입니다.",
      maxChars: 500,
    });

    const firstCharCount = computed(() => state.firstChar.length);
    const secondCharCount = computed(() => state.secondChar.length);
    const thirdCharCount = computed(() => state.thirdChar.length);

    return {
      ...toRefs(state),
      firstCharCount,
      secondCharCount,
      thirdCharCount,
      SECOND_FIRST_TEXT,
    };
  },
});
</script>

<style lang="scss" scoped>
.form-box {
  display: flex;
  flex-direction: column;
  width: 100%;

  .textarea-box {
    position: relative;
    width: 100%;
    height: auto;
    :focus {
      border-color: #00d2d3;
      outline: none;
    }

    :disabled::-webkit-input-placeholder {
      color: red;
    }

    :read-only {
      color: blue;
    }

    &__textarea {
      width: 100%;
      resize: none;
      padding: 2px 5px;
      margin: 4px -12px -6px -12px;
      border-color: #999;
      border-radius: 2px;
    }
    &__count {
      position: absolute;
      right: 8px;
      bottom: -8px;
      color: #999 !important;
      font-size: 14px;
    }
  }
  .textarea-save-btn-box {
    display: flex;
    justify-content: space-between;
    width: 100%;

    .textarea-box {
      width: 92%;
    }
    .btn-box {
      width: 8%;
      margin-top: 4px;
      margin-left: 10px;
      border: 1px solid #d9d9d9;
      background-color: #fff;
      border-radius: 2px;
      text-align: center;
      padding: 0;
      color: #999;
    }
  }
}
</style>
