<script>
import * as d3 from "d3";
import Chart from "chart.js";
import VueChart from "vue-chartjs";
import {Bar} from 'vue-chartjs'

export default {
  extends: Bar,
  name: 'chart',
  mounted () {
    this.renderChart(this.data, this.options)
  }
}
</script>
