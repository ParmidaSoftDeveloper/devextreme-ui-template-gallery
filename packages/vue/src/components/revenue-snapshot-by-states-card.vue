<template>
  <card-analytics
    title="Revenue Snapshot by States"
    content-class="sales-by-state"
  >
    <dx-pie-chart
      :data-source="props.data"
      type="doughnut"
      :diameter="0.8"
      :inner-radius="0.6"
    >
      <dx-pie-series
        argument-field="stateName"
        value-field="total"
      >
        <dx-pie-label
          background-color="none"
          :radial-offset="-20"
          :visible="true"
          :customize-text="customizeSaleText"
        >
          <dx-pie-font
            color="#757575"
            :size="15"
          />
        </dx-pie-label>
      </dx-pie-series>

      <dx-pie-legend>
        <dx-pie-margin :top="70" />
      </dx-pie-legend>

      <dx-pie-size :height="270" />
    </dx-pie-chart>
  </card-analytics>
</template>

<script setup lang="ts">
import {
  DxPieChart,
  DxLabel as DxPieLabel,
  DxSeries as DxPieSeries,
  DxFont as DxPieFont,
  DxMargin as DxPieMargin,
  DxLegend as DxPieLegend,
  DxSize as DxPieSize,
} from 'devextreme-vue/pie-chart';
import { Sales } from '@/types/analytics';
import CardAnalytics from '@/components/card-analytics.vue';

const props = defineProps<{
  data: Sales
}>();

const customizeSaleText = (arg: { percentText: string }) => arg.percentText;
</script>

<style scoped>

</style>
