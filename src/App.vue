<template>
  <div id="app">
    <el-container>
      <el-header>
        <h1>Business Analysis Assistant by Almaz Bisenbaev</h1>
      </el-header>

      <el-main>
        <el-row :gutter="40" justify="center">
          <el-col :xs="24" :sm="12" :md="6">
            <el-button type="primary" @click="currentTool = 'leanCanvas'"
              >Lean Canvas Maker</el-button
            >
          </el-col>
          <el-col :xs="24" :sm="12" :md="6">
            <el-button type="success" @click="currentTool = 'swot'"
              >SWOT Analysis Maker</el-button
            >
          </el-col>
        </el-row>

        <div v-if="currentTool === 'leanCanvas'">
          <h2>Lean Canvas</h2>
          <lean-canvas-maker @export="exportAsImage" />
        </div>

        <div v-if="currentTool === 'swot'">
          <h2>SWOT Analysis</h2>
          <swot-maker @export="exportAsImage" />
        </div>
      </el-main>

      <el-divider></el-divider>
      <el-footer>
        Author:
        <a target="_blank" href="https://www.linkedin.com/in/almazbisenbaev/"
          >Almaz Bisenbaev</a
        >
      </el-footer>
    </el-container>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import LeanCanvasMaker from "./components/LeanCanvasMaker.vue";
import SwotMaker from "./components/SwotMaker.vue";
import html2canvas from "html2canvas";

export default defineComponent({
  name: "App",
  components: {
    LeanCanvasMaker,
    SwotMaker,
  },
  setup() {
    const currentTool = ref<"leanCanvas" | "swot" | null>(null);

    const exportAsImage = (elementId: string) => {
      const element = document.getElementById(elementId);
      if (element) {
        html2canvas(element).then((canvas) => {
          const link = document.createElement("a");
          link.download = `${currentTool.value}-export.png`;
          link.href = canvas.toDataURL();
          link.click();
        });
      }
    };

    return {
      currentTool,
      exportAsImage,
    };
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<!-- <script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style> -->
