<template>
  <q-page>
    <div class="row q-mt-md q-col-gutter-md">
      <div class="col-6">
        <q-card>
          <q-card-section>
            <apexchart
              type="bar"
              height="350"
              :options="chartOptions"
              :series="series"
            ></apexchart>
          </q-card-section>
        </q-card>
      </div>
      <div class="col-6">
        <q-card>
          <q-card-section>
            <apexchart
              type="bar"
              height="350"
              :options="chartOptions"
              :series="series"
            ></apexchart>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
/* eslint-disable */
import { defineComponent } from "vue";

export default defineComponent({
  name: "PageIndex",
  data() {
    return {
      series: [
        {
          name: "Flamengo",
          data: [44, 55, 57, 56, 61, 58, 63, 60, 66],
        },
        {
          name: "Palmeiras",
          data: [76, 85, 101, 98, 87, 105, 91, 114, 94],
        },
        {
          name: "Santos",
          data: [35, 41, 36, 26, 45, 48, 52, 53, 41],
        },
      ],
      chartOptions: {
        chart: {
          type: "bar",
          height: 350,
        },
        plotOptions: {
          bar: {
            horizontal: false,
            columnWidth: "55%",
            endingShape: "rounded",
          },
        },
        dataLabels: {
          enabled: false,
        },
        stroke: {
          show: true,
          width: 2,
          colors: ["transparent"],
        },
        xaxis: {
          categories: [
            "Fev",
            "Mar",
            "Abr",
            "Mai",
            "Jun",
            "Jul",
            "Ago",
            "Set",
            "Out",
          ],
        },
        yaxis: {
          title: {
            text: "R$ (reais)",
          },
        },
        fill: {
          opacity: 1,
        },
        tooltip: {
          y: {
            formatter: function (val) {
              return "R$ " + val + " reais";
            },
          },
        },
      },
    };
  },
});
</script>
