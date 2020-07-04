
<script>
import * as d3 from "d3";
import Chart from "chart.js";
import VueChart from "vue-chartjs";
import {Bar} from 'vue-chartjs'

export default {
  extends: Bar,
  name: 'chart',
  data () {
    return {
      data: {
        labels: ['A', 'B', 'C', 'D', 'E', 'F'],
        datasets: [
          {
            label: 'Bar Dataset',
            data: [10, 20, 30, 40, 45, 30],
            backgroundColor: 'rgba(255, 99, 132, 0.2)',
            borderColor: 'rgba(255, 99, 132, 1)',
            borderWidth: 1
          },
        ]
      },
      options: {
        scales: {
          xAxes: [{
            scaleLabel: {
              display: true,
              labelString: 'Type'
            }
          }],
          yAxes: [{
            ticks: {
              beginAtZero: true,
              stepSize: 10,
            }
          }]
        }
      }
    }
  },
  mounted () {
    this.renderChart(this.data, this.options)
  }
}
</script>
