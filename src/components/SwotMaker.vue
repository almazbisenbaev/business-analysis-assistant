<template>
  <div id="swot">
    <el-row :gutter="20">
      <el-col :span="12">
        <el-input
          v-model="strengths"
          type="textarea"
          :rows="6"
          placeholder="Strengths"
        />
      </el-col>
      <el-col :span="12">
        <el-input
          v-model="weaknesses"
          type="textarea"
          :rows="6"
          placeholder="Weaknesses"
        />
      </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :span="12">
        <el-input
          v-model="opportunities"
          type="textarea"
          :rows="6"
          placeholder="Opportunities"
        />
      </el-col>
      <el-col :span="12">
        <el-input
          v-model="threats"
          type="textarea"
          :rows="6"
          placeholder="Threats"
        />
      </el-col>
    </el-row>
    <el-button type="primary" @click="$emit('export', 'swot')"
      >Export as Image</el-button
    >
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "SwotMaker",
  emits: ["export"],
  setup() {
    const strengths = ref("");
    const weaknesses = ref("");
    const opportunities = ref("");
    const threats = ref("");

    return {
      strengths,
      weaknesses,
      opportunities,
      threats,
    };
  },
});
</script>
