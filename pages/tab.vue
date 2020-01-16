<template>
  <div style="padding:200px">
    <div class="btn">
      <!-- <span>歌手</span>
      <span>新闻</span>
      <span>体育</span> -->
      <span
        v-for="(item, index) in ['歌手', '新闻', '体育']"
        :key="index"
        @click="dianji(index)"
        :class="{red: current===index}"
        >{{ item }}</span
      >
    </div>
    <div v-if="current === 0">
      <ul>
        <li>谢霆锋</li>
        <li>谢霆锋</li>
        <li>谢霆锋</li>
      </ul>
    </div>
    <div v-if="current === 1">
      <ul>
        <li>习近平来广州</li>
        <li>习近平来广州</li>
        <li>习近平来广州</li>
      </ul>
    </div>

    <div v-if="current === 2">
      <ul>
        <li>国足夺冠</li>
        <li>国足夺冠</li>
        <li>国足夺冠</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      //当前高亮的索引
      current: 0
    };
  },
  methods: {
    dianji(index) {
      this.current = index;
    }
  }
};
</script>

<style scoped>
.btn span {
  cursor: pointer;
  padding: 0 20px;
}
.red {
  color: red;
}
</style>
