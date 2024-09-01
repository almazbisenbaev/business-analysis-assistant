<template>
  <div id="swot" class="swot">

    <div class="swot-grid">

      <div class="swot-grid-column">
        <div class="stickit">
          <label for="strengths">Strengths</label>
          <textarea
            id="strengths"
            v-model="strengths"
            placeholder="Strengths"
          >
          </textarea>
        </div>
      </div>

      <div class="swot-grid-column">
        <div class="stickit">
          <label for="weaknesses">Weaknesses</label>
          <textarea
            id="weaknesses"
            v-model="weaknesses"
            placeholder="Weaknesses"
          >
          </textarea>
        </div>
      </div>

      <div class="swot-grid-column">
        <div class="stickit">
          <label for="opportunities">Opportunities</label>
          <textarea
            id="opportunities"
            v-model="opportunities"
            placeholder="Opportunities"
          >
          </textarea>
        </div>
      </div>

      <div class="swot-grid-column">
        <div class="stickit">
          <label for="threats">Threats</label>
          <textarea
            id="threats"
            v-model="threats"
            placeholder="Threats"
          >
          </textarea>
        </div>
      </div>

    </div>

    <div class="swot-footer">
      <el-button type="primary" @click="$emit('export', 'swot')"
        >Export as Image</el-button>
    </div>

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

<style scoped>

  .swot {
    position: relative;
    margin-bottom: 100px;
  }

  .swot-grid {
    display: flex;
    flex-wrap: wrap;
  }

  .swot-grid-column {
    flex: 1;
    flex-basis: 50%;
    max-width: 50%;
    padding: 20px;
  }

  .stickit {
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  .stickit label {
    font-size: 14px;
    font-weight: bold;
    margin-bottom: 10px;
  }

  .stickit textarea {
    font:20px "Patrick Hand", "Comic Sans", sans-serif;
    line-height:1.5;
    border:0;
    border-radius:3px;
    background: linear-gradient(#F9EFAF, #F7E98D);
    box-shadow:0 4px 6px rgba(0,0,0,0.1);
    overflow:hidden;
    width: 100%;
    min-height: 200px;
    flex: 1;

    padding: 20px;
    resize: vertical;

    transition:box-shadow 0.5s ease;
  }

  textarea:hover { box-shadow:0 5px 8px rgba(0,0,0,0.15); }
  textarea:focus { box-shadow:0 5px 12px rgba(0,0,0,0.2); outline:none; }

  .swot-footer {
    position: absolute;
    width: 100%;
    left: 0;
    top: 100%;
    padding: 20px;

    display: flex;
    justify-content: center;
  }

</style>
