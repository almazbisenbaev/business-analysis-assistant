<template>
  <div id="leanCanvas" class="lean">

    <div class="lean-grid">

      <div class="div1">
        <div class="lean-card">
          <label for="problem">Problem</label>
          <textarea
            v-model="problemSolution.problem"
            placeholder="Problem"
            id="problem"
          >
          </textarea>
        </div>
      </div>

      <div class="div2">
        <div class="lean-card">
          <label for="solution">Solution</label>
          <textarea
            v-model="problemSolution.solution"
            id="solution"
            placeholder="Problem"
          >
          </textarea>
        </div>
      </div>

      <div class="div3">
        <div class="lean-card">
          <label for="uvp">Unique Value Proposition</label>
          <textarea
            v-model="uniqueValueProposition"
            id="uvp"
            placeholder="Unique Value Proposition"
          >
          </textarea>
        </div>
      </div>

      <div class="div4">
        <div class="lean-card">
          <label for="keymterics">Key Metrics</label>
          <textarea
            v-model="keyMetrics"
            id="keymterics"
            placeholder="Key Metrics"
          >
          </textarea>
        </div>
      </div>

      <div class="div5">
        <div class="lean-card">
          <label for="unfair">Unfair Advantage</label>
          <textarea
            v-model="unfairAdvantage"
            id="unfair"
            placeholder="Unfair Advantage"
          >
          </textarea>
        </div>
      </div>

      <div class="div6">
        <div class="lean-card">
          <label for="channels">Channels</label>
          <textarea
            v-model="channels"
            id="channels"
            placeholder="Channels"
          >
          </textarea>
        </div>
      </div>

      <div class="div7">
        <div class="lean-card">
          <label for="segments">Customer Segments</label>
          <textarea
            v-model="customerSegments"
            id="segments"
            placeholder="Customer Segments"
          >
          </textarea>
        </div>
      </div>

      <div class="div8">
        <div class="lean-card">
          <label for="cost">Cost Structure</label>
          <textarea
            v-model="costStructure"
            id="cost"
            placeholder="Cost Structure"
          >
          </textarea>
        </div>
      </div>

      <div class="div9">
        <div class="lean-card">
          <label for="revenue">Revenue Streams</label>
          <textarea
            v-model="revenueStreams"
            id="revenue"
            placeholder="Revenue Streams"
          >
          </textarea>
        </div>
      </div>

    </div>

    <div class="lean-footer">
      <el-button type="primary" @click="$emit('export', 'leanCanvas')"
        >Export as Image</el-button>
    </div>

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

<style scoped>

  #leanCanvas {
    position: relative;
    margin-bottom: 100px;
  }

  .lean-card {
    /* background: #fafafa; */
    border: 1px solid rgba(0,0,0,0.05);
    border-radius: 10px;
    box-shadow: 0 8px 12px rgba(0,0,0,0.05);
    padding: 20px;

    display: flex;
    flex-direction: column;

    height: 100%;
    min-height: 200px;
  }

  .lean-card textarea {
    font-size: 18px;
    font-family: inherit;
    width: 100%;
    resize: none;
    border: 1px solid rgba(0,0,0,0.05);
    border-radius: 6px;
    background: #fafafa;
    flex: 1;
    height: auto;
    padding: 18px;
  }

  .lean-card textarea:focus {
    outline: none;
  }

  .lean-card label {
    font-size: 14px;
    font-weight: bold;
    text-align: left;
    margin-bottom: 10px;
  }

  .lean-grid {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-template-rows: repeat(3, 1fr);
    grid-column-gap: 10px;
    grid-row-gap: 10px;
    padding: 10px;
  }

  .div1 { grid-area: 1 / 1 / 3 / 2; }
  .div2 { grid-area: 1 / 2 / 2 / 3; }
  .div3 { grid-area: 2 / 2 / 3 / 3; }
  .div4 { grid-area: 1 / 3 / 3 / 4; }
  .div5 { grid-area: 1 / 4 / 2 / 5; }
  .div6 { grid-area: 2 / 4 / 3 / 5; }
  .div7 { grid-area: 1 / 5 / 3 / 6; }
  .div8 { grid-area: 3 / 1 / 4 / 3; }
  .div9 { grid-area: 3 / 3 / 4 / 6; }

  .lean-footer {
    position: absolute;
    width: 100%;
    left: 0;
    top: 100%;
    padding: 20px;

    display: flex;
    justify-content: center;
  }

</style>
