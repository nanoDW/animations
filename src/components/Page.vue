<template>
  <div
    class="page"
    ref="page"
    :style="{ backgroundColor: page.backgroundColor }"
    @wheel="scrollToAnotherPage"
    @scroll.prevent
  >
    <div>
      <h1 class="page-title">{{ page.name }}</h1>
      <p class="page-content">{{ page.content }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Page",
  data() {
    return {
      time: 0,
    };
  },
  props: {
    page: {
      required: true,
      type: Object,
    },
  },
  methods: {
    scrollToAnotherPage(e) {
      e.preventDefault();
      this.$emit("scroll", { number: this.page.number, deltaY: e.deltaY });
    },
  },
};
</script>

<style scoped>
.page {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.page-title {
  width: 100%;
  margin: 1rem;
}

.page-content {
  max-width: 80%;
  margin: auto;
}
</style>
