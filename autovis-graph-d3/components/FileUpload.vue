<template>
    <div>
        <label>ファイルを選択
          <input type="file" @change="onFileChange" />
        </label>
        <p id="error">csv ファイルのみアップロード可能です</p>
        <barchart ref="barchart" :data="data" :options="options"></barchart>
        <v-data-table
           :headers="headers"
           :items="csv_data"
           :items-per-page="5"
           class="elevation-1"
         >
         <template v-slot:items="props">
           <td class="text-xs-right">{{ props.item.A }}</td>
           <td class="text-xs-right">{{ props.item.B }}</td>
           <td class="text-xs-right">{{ props.item.C }}</td>
           <td class="text-xs-right">{{ props.item.D }}</td>
           <td class="text-xs-right">{{ props.item.E }}</td>
           <td class="text-xs-right">{{ props.item.F }}</td>
         </template>
       </v-data-table>
    </div>

</template>

<script>
import Barchart from '~/components/Barchart.vue';

export default {
  components: { Barchart },
  data: function() {
    return {
      headers: [
            { text: 'A', align: 'center', sortable: true, value: 'A' },
            { text: 'B', align: 'center', sortable: true, value: 'B' },
            { text: 'C', align: 'center', sortable: true, value: 'C' },
            { text: 'D', align: 'center', sortable: true, value: 'D' },
            { text: 'E', align: 'center', sortable: true, value: 'E' },
            { text: 'F', align: 'center', sortable: true, value: 'F' },
          ],
      csv_data: [
        {A: 20, B: 50, C: 30, D: 50, E: 45, F: 20}
      ],
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
