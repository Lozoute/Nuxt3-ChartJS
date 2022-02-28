<template>
  <section>
    <ClientOnly>
      <DoughnutChart :chartData="doughnutBySources" :options="doughnutBySourcesOptions" :height="200" :width="200" />
    </ClientOnly>
  </section>
</template>

<script>
  import { DoughnutChart } from "vue-chart-3";

  export default {
    components: { DoughnutChart },

    data () {
      return {
        doughnutBySources: {
          labels: ['Foo', 'Bar', 'Baz'],
          datasets: [{
            data: [2000, 1000, 1000],
            backgroundColor: ["#5a4fcf", "#b3afe3", "#ede9fe"],
          }]
        },
        doughnutBySourcesOptions: {
          responsive: false,
          plugins: {
            tooltip: {
              displayColors: false,
              padding: 10,
              boxPadding: 5,
              callbacks: {
                label: (ctx) => `${ctx.label} : ${ctx.parsed.toLocaleString('fr-FR')} €`,
              }
            },
            legend: {
              display: false,
            },
            title: {
              display: true,
              text: "Foo",
            },
          },
        },
      };
    },

  }
</script>
