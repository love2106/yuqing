# 舆情期末
舆情期末
# 黄杨钿甜"230万耳环事件"舆情分析图表

## 图1：舆情传播平台分布

```html
<div style="width:80%;margin:0 auto;">
  <canvas id="platformChart"></canvas>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
  new Chart(document.getElementById('platformChart'), {
    type: 'pie',
    data: {
      labels: ['微博 42.3%', '新闻客户端 28.5%', '短视频平台 15.2%', '论坛社区 9.7%', '微信公众号 4.3%'],
      datasets: [{
        data: [42.3, 28.5, 15.2, 9.7, 4.3],
        backgroundColor: ['#FF6384','#36A2EB','#FFCE56','#4BC0C0','#9966FF']
      }]
    },
    options: {
      plugins: {
        datalabels: {
          formatter: (v) => v + '%',
          color: '#fff',
          font: { weight: 'bold', size: 14 }
        }
      }
    },
    plugins: [{
      id: 'datalabels',
      afterDraw: (chart) => {
        const {ctx} = chart;
        chart.data.datasets.forEach((dataset, i) => {
          const meta = chart.getDatasetMeta(i);
          meta.data.forEach((element, index) => {
            const {x, y} = element.tooltipPosition();
            ctx.fillStyle = '#fff';
            ctx.textAlign = 'center';
            ctx.textBaseline = 'middle';
            ctx.fillText(dataset.data[index] + '%', x, y);
          });
        });
      }
    }]
  });
</script>
