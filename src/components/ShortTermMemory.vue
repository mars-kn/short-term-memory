<template>
  <div class="s-outer">
    <h1>Short Term Memory</h1>
    <Sheet v-if="!filled" @sheetfinish="sheetFinish" />
    <Test v-if="filled" :sheet="sheet" @end="end" />
  </div>
</template>

<script>
import Sheet from './Sheet.vue';
import Test from './Test.vue';
export default {
  name: 'short-term-memory',
  components: {
    Sheet,
    Test,
  },
  data() {
    return {
      filled: false,
      sheet: [],
    };
  },
  methods: {
    sheetFinish(sheet) {
      this.filled = true;
      this.sheet = sheet.map((s, idx) => ({ i: idx, ...s }));
    },
    end() {
      this.filled = false;
      this.sheet = [];
    },
  },
};
</script>

<style scoped lang="scss">
.s-outer {
  height: 84vh;
  display: flex;
  flex-direction: column;
}
</style>
