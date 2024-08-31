<template>
  <div id="leanCanvas">
    <el-row :gutter="20">
      <el-col :span="8">
        <el-input
          v-model="problemSolution.problem"
          type="textarea"
          :rows="4"
          placeholder="Problem"
        />
      </el-col>
      <el-col :span="8">
        <el-input
          v-model="problemSolution.solution"
          type="textarea"
          :rows="4"
          placeholder="Solution"
        />
      </el-col>
      <el-col :span="8">
        <el-input
          v-model="uniqueValueProposition"
          type="textarea"
          :rows="4"
          placeholder="Unique Value Proposition"
        />
      </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :span="8">
        <el-input
          v-model="keyMetrics"
          type="textarea"
          :rows="4"
          placeholder="Key Metrics"
        />
      </el-col>
      <el-col :span="8">
        <el-input
          v-model="unfairAdvantage"
          type="textarea"
          :rows="4"
          placeholder="Unfair Advantage"
        />
      </el-col>
      <el-col :span="8">
        <el-input
          v-model="channels"
          type="textarea"
          :rows="4"
          placeholder="Channels"
        />
      </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :span="8">
        <el-input
          v-model="customerSegments"
          type="textarea"
          :rows="4"
          placeholder="Customer Segments"
        />
      </el-col>
      <el-col :span="8">
        <el-input
          v-model="costStructure"
          type="textarea"
          :rows="4"
          placeholder="Cost Structure"
        />
      </el-col>
      <el-col :span="8">
        <el-input
          v-model="revenueStreams"
          type="textarea"
          :rows="4"
          placeholder="Revenue Streams"
        />
      </el-col>
    </el-row>
    <el-button type="primary" @click="$emit('export', 'leanCanvas')"
      >Export as Image</el-button
    >
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "LeanCanvasMaker",
  emits: ["export"],
  setup() {
    const problemSolution = ref({ problem: "", solution: "" });
    const uniqueValueProposition = ref("");
    const keyMetrics = ref("");
    const unfairAdvantage = ref("");
    const channels = ref("");
    const customerSegments = ref("");
    const costStructure = ref("");
    const revenueStreams = ref("");

    return {
      problemSolution,
      uniqueValueProposition,
      keyMetrics,
      unfairAdvantage,
      channels,
      customerSegments,
      costStructure,
      revenueStreams,
    };
  },
});
</script>
