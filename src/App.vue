<template>
  <div id="app" ref="app">
    <Page v-for="page in pages" :page="page" :key="page.number" @scroll="animateScroll" />
  </div>
</template>

<script>
import Page from "./components/Page.vue";

export default {
  name: "App",
  components: {
    Page,
  },
  data() {
    return {
      active: 1,
      time: 0,
    };
  },
  created() {},
  computed: {
    pages() {
      return [
        {
          name: "Page 1",
          number: 1,
          backgroundColor: "#ff5f45",
          content:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.",
        },
        {
          name: "Page 2",
          number: 2,
          backgroundColor: "#0798ec",
          content:
            "Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem.",
        },
        {
          name: "Page 3",
          number: 3,
          backgroundColor: "#ff5f45",
          content:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
        },
        {
          name: "Page 4",
          number: 4,
          backgroundColor: "#0798ec",
          content:
            "Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt.",
        },
      ];
    },
  },
  methods: {
    animateScroll(event) {
      const isNegative = event.deltaY < 0 ? -1 : 1;
      const height = (this.$refs.app.clientHeight / 4) * (event.number + isNegative - 1);
      const currentTime = new Date().getTime();

      if (currentTime - 1000 > this.time) {
        window.scrollTo(0, height);
        this.time = currentTime;
      }
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  scroll-behavior: smooth;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
}
</style>
