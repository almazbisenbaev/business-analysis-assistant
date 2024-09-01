<template>
  <div id="app">
    <el-header>
      <h1 class="app-title">Business Analysis Assistant by Almaz Bisenbaev</h1>
    </el-header>

    <el-main>
      <el-tabs v-model="currentTool" @tab-click="handleTabClick">

        <el-tab-pane label="About" name="welcome">
          <welcome />
        </el-tab-pane>

        <el-tab-pane label="Lean Canvas Template" name="leanCanvas">
          <h2 class="tool-heading">Lean Canvas Template</h2>
          <lean-canvas-maker @export="exportAsImage" />
        </el-tab-pane>

        <el-tab-pane label="SWOT Analysis Template" name="swot">
          <h2 class="tool-heading">SWOT Analysis Template</h2>
          <swot-maker @export="exportAsImage" />
        </el-tab-pane>
        
      </el-tabs>
    </el-main>

    <el-divider></el-divider>
    <el-footer class="author">
      Author:
      <a target="_blank" href="https://www.linkedin.com/in/almazbisenbaev/">Almaz Bisenbaev</a>
    </el-footer>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Welcome from "./components/Welcome.vue";
import LeanCanvasMaker from "./components/LeanCanvasMaker.vue";
import SwotMaker from "./components/SwotMaker.vue";
import html2canvas from "html2canvas";

export default defineComponent({
  name: "App",
  components: {
    Welcome,
    LeanCanvasMaker,
    SwotMaker,
  },
  setup() {
    // const currentTool = ref<"leanCanvas" | "swot" | null>(null);
    const currentTool = 'welcome';

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

    const handleTabClick = (tab: any) => {
      currentTool.value = tab.name;
    };

    return {
      currentTool,
      exportAsImage,
      handleTabClick,
    };
  },
});
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Patrick+Hand&display=swap');

* {
  box-sizing: border-box;
}

#app {
  font-family: sans-serif;
  color: #2c3e50;
  max-width: 100%;
  margin: auto;
  padding: 20px;
}

.app-title {
  text-align: center;
  font-size: 24px;
}

.tool-heading {
  text-align: center;
}

.el-tabs__nav {
  width: 100%;
  justify-content: center;
}

.author {
  text-align: center;
}

</style>
