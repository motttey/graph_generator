<template>
    <div>
        <label>ファイルを選択
          <input type="file" @change="onFileChange" />
        </label>
        <p id="error">csv ファイルのみアップロード可能です</p>
        <barchart ref="barchart" :data="data" :options="options"></barchart>
    </div>
</template>

<script>
import Barchart from '~/components/Barchart.vue';

export default {
  components: { Barchart },
  data: function() {
    return {
      csv_labels: [""],
      csv_data: [""],
      data: {
        labels: ['A', 'B', 'C', 'D', 'E', 'F'],
        datasets: [
          {
            label: 'Bar Dataset',
            data: [20, 50, 30, 50, 45, 20],
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
  mounted : function(){
    this.$refs.barchart.renderChart(this.data, this.options);
  },
  methods: {
    onFileChange(e) {
      // const files = e.target.files || e.dataTransfer.files;
      this.data.datasets.data = [20, 20, 30, 20, 45, 20];
      this.$refs.barchart.renderChart(this.data, this.options);
    }
  }
}
</script>
