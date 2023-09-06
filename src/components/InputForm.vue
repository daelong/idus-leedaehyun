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
    <div class="textarea-box">
      <textarea
        class="textarea-box__textarea"
        v-model="secondChar"
        cols="30"
        rows="5"
        placeholder="자신의 의견을 간단히 적어주세요."
      ></textarea>
      <p class="textarea-box__count">{{ maxChars - firstCharCount }}</p>
    </div>
  </form>
</template>

<script lang="ts">
import { reactive, toRefs, computed, defineComponent } from "vue";
import { useForm } from "vee-validate";

export default defineComponent({
  setup() {
    const state = reactive({
      firstChar: "초기값이 있을 수 있습니다",
      secondChar: "입력중.. 또는 내용 변경시",
      maxChars: 500,
    });

    const firstCharCount = computed(() => state.firstChar.length);

    return {
      ...toRefs(state),
      firstCharCount,
    };
  },
});
</script>

<style lang="scss" scoped>
.form-box {
  display: flex;
  flex-direction: column;
  .textarea-box {
    position: relative;
    width: 50%;
    &__textarea {
      width: 100%;
      resize: none;
      padding: 2px 8px;
      border-color: #999;
      border-radius: 2px;
    }
    &__count {
      position: absolute;
      right: 0;
      bottom: -8px;
      color: #999;
      font-size: 14px;
    }
  }
}
</style>
