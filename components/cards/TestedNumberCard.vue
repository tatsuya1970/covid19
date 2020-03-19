<template>
  <v-col cols="12" md="6" class="DataCard">
    <time-stacked-bar-chart
      :title="$t('検査実施数')"
      :title-id="'number-of-tested'"
      :chart-id="'time-stacked-bar-chart-inspections'"
      :chart-data="inspectionsGraph"
      :date="Data.inspections_summary.date"
      :items="inspectionsItems"
      :labels="inspectionsLabels"
      :unit="$t('件.tested')"
      :url="'https://www.pref.hiroshima.lg.jp/soshiki/50/korona-kensazisseki.html'"
      
    />
    <!-- 件.tested = 検査数 -->
  </v-col>
</template>

<i18n>
{
  "ja": {
    "検査実施数": "検査実施数",
    "県内": "県内",
    "県内発生": "県内発生",
    "その他": "その他",
    "件": {
      "tested": "件"
    }
  }
}
</i18n>

<script>
import Data from '@/data/data.json'
import TimeStackedBarChart from '@/components/TimeStackedBarChart.vue'

export default {
  components: {
    TimeStackedBarChart
  },
  data() {
    // 検査実施日別状況
    const inspectionsGraph = [
      Data.inspections_summary.data['都内'],
      Data.inspections_summary.data['その他']
    ]
    const inspectionsItems = [
      this.$t('県内発生'),
      this.$t('その他')
    ]
    const inspectionsLabels = Data.inspections_summary.labels
    
    const data = {
      Data,
      inspectionsGraph,
      inspectionsItems,
      inspectionsLabels
    }
    return data
  }
}
</script>
