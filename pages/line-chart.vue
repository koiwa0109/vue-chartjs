<template>
  <main>
    <h1 class="mb-8 text-center text-xl">Line Chart</h1>
    <ChartsLine :chartData="chartData" :options="options"></ChartsLine>
    <div class="mt-8 flex justify-between text-xl">
      <div>
        <button v-show="chartIndex < maxChartIndex" @click="prevChart">
          前
        </button>
      </div>
      <div><button v-show="chartIndex > 0" @click="nextChart">次</button></div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      allChartData: {
        labels: [
          [
            '2021年7月',
            '2021年8月',
            '2021年9月',
            '2021年10月',
            '2021年11月',
            '2021年12月',
          ],
          [
            '2021年1月',
            '2021年2月',
            '2021年3月',
            '2021年4月',
            '2021年5月',
            '2021年6月',
          ],
          [
            '2020年7月',
            '2020年8月',
            '2020年9月',
            '2020年10月',
            '2020年11月',
            '2020年12月',
          ],
        ],
        datasets: [
          [
            [46, 44, 41, 47, 48, 50],
            [38, 31, 38, 33, 46, 48],
            [34, 32, 38, 35, 39, 40],
            [21, 22, 27, 24, 38, 36],
            [24, 23, 28, 24, 28, 30],
            [12, 18, 13, 19, 26, 25],
          ],
          [
            [38, 45, 41, 47, 46, 47],
            [32, 33, 37, 31, 47, 42],
            [38, 36, 31, 37, 33, 46],
            [22, 25, 21, 27, 38, 34],
            [21, 26, 29, 27, 28, 31],
            [12, 17, 12, 17, 23, 29],
          ],
          [
            [43, 47, 41, 49, 44, 50],
            [38, 33, 32, 37, 43, 48],
            [32, 37, 31, 36, 34, 46],
            [22, 29, 28, 26, 33, 37],
            [26, 23, 28, 29, 21, 38],
            [17, 11, 14, 18, 24, 27],
          ],
        ],
      },
      chartData: null,
      options: {
        animation: {
          duration: 500,
        },
        scales: {
          xAxes: [
            {
              gridLines: {
                display: false,
              },
            },
          ],
          yAxes: [
            {
              gridLines: {
                drawBorder: false,
                zeroLineWidth: 0,
                zeroLineColor: 'transparent',
              },
            },
          ],
        },
        elements: {
          point: {
            radius: 6,
            backgroundColor: '#fff',
            borderWidth: 2,
          },
          line: {
            tension: 0,
            backgroundColor: 'transparent',
            borderWidth: 3,
          },
        },
        legend: {
          labels: {
            usePointStyle: true,
            boxWidth: 8,
          },
        },
      },
      chartIndex: 0,
      maxChartIndex: null,
    }
  },

  mounted() {
    this.maxChartIndex = this.allChartData.datasets.length - 1
    this.fillData()
  },

  methods: {
    fillData() {
      this.chartData = {
        labels: this.allChartData.labels[this.chartIndex],
        datasets: [
          {
            label: '10代',
            data: this.allChartData.datasets[this.chartIndex][0],
            borderColor: '#FCA5A5',
          },
          {
            label: '20代',
            data: this.allChartData.datasets[this.chartIndex][1],
            borderColor: '#FCD34D',
          },
          {
            label: '30代',
            data: this.allChartData.datasets[this.chartIndex][2],
            borderColor: '#6EE7B7',
          },
          {
            label: '40代',
            data: this.allChartData.datasets[this.chartIndex][3],
            borderColor: '#93C5FD',
          },
          {
            label: '50代',
            data: this.allChartData.datasets[this.chartIndex][4],
            borderColor: '#A5B4FC',
          },
          {
            label: '60代',
            data: this.allChartData.datasets[this.chartIndex][5],
            borderColor: '#C4B5FD',
          },
        ],
      }
    },

    prevChart() {
      if (this.chartIndex >= this.maxChartIndex) return
      this.chartIndex++
      this.fillData()
    },

    nextChart() {
      if (this.chartIndex <= 0) return
      this.chartIndex--
      this.fillData()
    },
  },
}
</script>

<style></style>
