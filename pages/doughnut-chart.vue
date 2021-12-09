<template>
  <main>
    <h1 class="mb-8 text-center text-xl">Doughnut Chart</h1>
    <ChartsDoughnut :chartData="chartData" :options="options"></ChartsDoughnut>
  </main>
</template>

<script>
export default {
  data() {
    return {
      chartData: {
        labels: ['問題なし', '改善の余地あり', '問題あり'],
        datasets: [
          {
            data: [19, 7, 6],
            backgroundColor: ['#6EE7B7', '#FCD34D', '#FCA5A5'],
            borderWidth: 0,
          },
        ],
      },
      options: {
        legend: {
          position: 'left',
          labels: {
            boxWidth: 12,
            font: {
              weight: 'bold',
            },
            generateLabels: function (chart) {
              const chartDataset = chart.data.datasets[0]
              const chartLabels = chart.data.labels
              let legendArray = []
              let total = 0
              for (let i = 0; i < chartDataset.data.length; i++) {
                total += chartDataset.data[i]
              }
              for (let i = 0; i < chartLabels.length; i++) {
                const label = chartLabels[i]
                const data = chartDataset.data[i]
                const bgColor = chartDataset.backgroundColor[i]
                const ratio = Math.round((data / total) * 100)
                const legend = {
                  text: `${label} (${ratio}% ${data}人)`,
                  fillStyle: bgColor,
                  lineWidth: 0,
                }
                legendArray.push(legend)
              }
              return legendArray
            },
          },
        },
      },
    }
  },
}
</script>

<style></style>
