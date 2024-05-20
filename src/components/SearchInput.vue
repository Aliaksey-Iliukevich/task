<template>
  <div class="input-container">
    <label>{{ label }}</label>
    <div class="input-wrapper" :style="{ 'position': buttonPosition }">
      <input v-model="inputValue" @input="updateParentValue" @keyup="checkWordsCount"
             :style="{ 'fontSize': fontSize + 'px' }"
             :class="inputClasses" />
      <button @click="clearInput">Clear</button>
    </div>
    <p v-if="inputValue !== null">
      Кол-во символов: {{ charCount }}
      <span v-if="wordsLimit" style="color: red;">Количество слов не должно превышать 3</span>
    </p>
  </div>
</template>

<script>
export default {
  props: {
    fontSize: {
      type: Number,
      default: 16
    },
    label: String,
    buttonPosition: String,
    value: String,
    inputClasses: String
  },
  data() {
    return {
      inputValue: this.value,
      wordsLimit: false
    };
  },
  computed: {
    charCount() {
      if (this.inputValue) {
        return this.inputValue.length;
      }
      return 0;
    }
  },
  watch: {
    value(newValue) {
      this.inputValue = newValue;
    }
  },
  methods: {
    clearInput() {
      this.inputValue = '';
      this.$emit('clearInput');
    },
    updateParentValue() {
      this.$emit('update:value', this.inputValue);
    },
    checkWordsCount() {
      const words = this.inputValue.trim().split(/\s+/);
      this.wordsLimit = words.length > 3;
    }
  }
};
</script>

<style scoped>
.input-container {
    position: relative;
}
  
.input-wrapper {
    position: relative;
}

input {
    padding: 5px;
}

button {
    position: absolute;
    right: 40px;
    top: 0;
    padding: 5px;
}
</style>