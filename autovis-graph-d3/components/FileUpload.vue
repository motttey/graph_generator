<template>
  <div>
    <!--
    <label>ファイルを選択
      <input type="file" @change="onFileChange" />
    </label>
    -->
    <p id="error">csv ファイルのみアップロード可能です</p>

    <barchart ref="barchart" :data="data" :options="options"></barchart>
    <client-only>
      <v-data-table
         :headers="headers"
         :items="csv_data"
         class="cdv-data-1">

       <template v-slot:item.colA="props">
         <v-edit-dialog
           :return-value.sync="props.item.colA"
           large
           persistent
           @save="save"
           @cancel="cancel"
           @close="close"
         >
           <div>{{ props.item.colA }}</div>
           <template v-slot:input>
             <div class="mt-4 title">Update A</div>
           </template>
           <template v-slot:input>
             <v-text-field
               v-model="props.item.colA"
               label="Edit"
               single-line
               counter
               autofocus
             ></v-text-field>
           </template>
         </v-edit-dialog>
       </template>
     </v-data-table>
   </client-only>
  </div>
</template>

<script>
import Barchart from '~/components/Barchart.vue';

export default {
  components: { Barchart },
  data: function() {
    return {
      headers: [
            { text: 'colA', align: 'center', sortable: true, value: 'colA' },
            { text: 'colB', align: 'center', sortable: true, value: 'colB' },
            { text: 'colC', align: 'center', sortable: true, value: 'colC' },
            { text: 'colD', align: 'center', sortable: true, value: 'colD' },
            { text: 'colE', align: 'center', sortable: true, value: 'colE' },
            { text: 'colF', align: 'center', sortable: true, value: 'colF' },
          ],
      csv_data: [
        {colA: 20, colB: 50, colC: 30, colD: 50, colE: 45, colF: 20},
        {colA: 20, colB: 50, colC: 30, colD: 80, colE: 45, colF: 40}
      ],
      data: {
        labels: ['colA', 'colB', 'colC', 'colD', 'colE', 'colF'],
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
    this.data.datasets.data = [100, 20, 30, 20, 45, 20];
    this.$refs.barchart.renderChart(this.data, this.options);
  },
  methods: {
    onFileChange(e) {
      // const files = e.target.files || e.dataTransfer.files;
      this.data.datasets.data = [20, 20, 30, 20, 45, 20];
      this.$refs.barchart.renderChart(this.data, this.options);
    },
    save () {
      // this.data.datasets.data = this.csv_data[0]["colA"];
      this.data.datasets.data = [100, 20, 30, 20, 45, 20];
      this.$refs.barchart.renderChart(this.data, this.options);
    },
    cancel () {

    },
    close () {
      console.log('Dialog closed')
    },
  }
}
</script>
