<template>
  <v-col cols="12" md="6" class="DataCard">
    <time-bar-chart
      :title="$t('新型コロナ相談件数')"
      :title-id="'number-of-reports-to-covid19-telephone-advisory-center'"
      :chart-id="'time-bar-chart-contacts'"
      :chart-data="contactsGraph"
      :date="Data.contacts.date"
      :unit="$t('件.reports')"
      :url="'https://www.pref.hiroshima.lg.jp/soshiki/50/korona-soudan-kennsai.html'"
    />
    <!-- 件.reports = 窓口相談件数 -->
  </v-col>
</template>

<i18n>
{
  "ja": {
    "新型コロナ相談件数": "新型コロナ相談件数",
    "件": {
      "reports": "件"
    }
  },
  "en": {
    "新型コロナ相談件数": "Number of inquiries to COVID-19 advisory center",
    "件": {
      "reports": "reports"
    }
  },
  
  "zh-cn": {
     "新型コロナ相談件数": "新型冠狀病毒就診諮詢窗口諮詢件數",
    "件": {
      "reports": "件"
    }
  },
  
  "zh-tw": {
   "新型コロナ相談件数": "新冠肺炎就诊咨询窗口受理量",
    "件": {
      "reports": "件"
    }
  },
  
  "ko": {
    "新型コロナ相談件数": "코로나19 진찰 상담 창구 상담 건수",
    "件": {
      "reports": "건"
       }
    },
    
  "ja-basic": {
    "新型コロナ相談件数": "コロナウイルス そうだんが　あった かず",
    "件": {
      "reports": "けん"
    }
  }
}
</i18n>

<script>
import Data from '@/data/data.json'
import formatGraph from '@/utils/formatGraph'
import TimeBarChart from '@/components/TimeBarChart.vue'

export default {
  components: {
    TimeBarChart
  },
  data() {
    // 相談件数
    const contactsGraph = formatGraph(Data.contacts.data)

    const data = {
      Data,
      contactsGraph
    }
    return data
  }
}
</script>
