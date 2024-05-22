<template>
  <div class="input-container">
    <label>{{ label }}</label>
    <div class="input-wrapper">
      <input 
        v-model="innerValue"
        v-bind="$attrs"
      />
      <button @click="clearInput">Clear</button>
    </div>
    <p v-if="countSearch > 0">Кол-во символов: {{ countSearch }}
      <span v-if="isLimit" style="color: red;">Количество слов не должно превышать 3</span>
    </p>
  </div>
</template>

<script>
export default {
  props: {
    label: String,
    modelValue: String,
  },
  emits: ['update:modelValue', 'clear'],
  data() {
    return {
      wordsLimit: 3, 
      isLimit: false
    };
  },
  computed: {
    innerValue: {
      get() {
        return this.modelValue;
      },
      set(value) {
        this.$emit('update:modelValue', value)
      }
    },
    countSearch() {
      if(this.innerValue) {
        return this.innerValue.length;
      }
      return 0;
    }
  },
  watch: {
    innerValue(value) {
      this.checkWordsCount(value);
    }
  },
  methods: {
    clearInput() {
      this.innerValue = '';
      this.$emit('clear');
    },
    checkWordsCount(value) {
      const wordsCount = value?.trim().split(/\s+/).length;
      this.isLimit = wordsCount > this.wordsLimit;
    }
  }
};
</script>

<style scoped>
.input-wrapper {
    position: relative;
}

input {
    padding: 5px;
}

button {
    position: absolute;
    left: 200px;
    top: 3px;
    padding: 5px;
}
</style>