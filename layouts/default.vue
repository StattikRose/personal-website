<template>
  <div>
    <div>
      <star
        v-for="i in 35"
        :key="`star-${i}`"
        class="fixed fill-current hidden md:block"
        :class="randomizeClass()"
        :style="randomizeLocation()"
      ></star>
      <sparkles
        v-for="i in 25"
        :key="`sparkle-${i}`"
        class="fixed fill-current hidden md:block"
        :class="randomizeClass()"
        :style="randomizeLocation()"
      ></sparkles>
    </div>
    <Nuxt
      class="antialiased text-grey-900 flex items-center justify-center w-screen h-screen lg:py-16"
    />
  </div>
</template>

<script>
import star from '../components/Star';
import sparkles from '../components/Sparkles';

export default {
  components: {
    star,
    sparkles,
  },
  methods: {
    randomizeClass() {
      const index = Math.floor(Math.random() * 3);

      const colors = {
        1: ['text-green-200', 'text-blue-200', 'text-yellow-200'],
        2: ['text-green-300', 'text-blue-300', 'text-yellow-300'],
        3: ['text-green-400', 'text-blue-400', 'text-yellow-400'],
      };

      switch (index) {
        case 0:
          return `h-1 opacity-75 ${
            colors[1][Math.floor(Math.random() * 3)]
          }`;
        case 1:
          return `h-2 opacity-25 ${
            colors[2][Math.floor(Math.random() * 3)]
          }`;
        case 2:
          return `h-3 opacity-50 ${
            colors[3][Math.floor(Math.random() * 3)]
          }`;
      }
    },
    randomizeLocation() {
      return {
        top: `${Math.floor(Math.random() * 100)}vh`,
        left: `${Math.floor(Math.random() * 100)}vw`,
      };
    },
  },
};
</script>

<style>
html,
body {
  overflow-x: hidden;
}
html {
  overflow: hidden;
  font-family: Inter var, system-ui, -apple-system, BlinkMacSystemFont,
    Segoe UI, Roboto, Helvetica Neue, Arial, Noto Sans, sans-serif,
    Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol,
    Noto Color Emoji;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: rgb(0, 36, 41);
  background: linear-gradient(
    105deg,
    rgba(0, 36, 41, 1) 0%,
    rgba(2, 14, 42, 1) 35%,
    rgba(2, 14, 42, 1) 55%,
    rgba(0, 36, 41, 1) 100%
  );
}
</style>
