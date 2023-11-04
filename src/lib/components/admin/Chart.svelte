<script>
    import { chart } from 'svelte-apexcharts?client';
  
    let categories = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Nov', 'Dec']
  
    let sumMonthChart = {
      chart: {
        type: 'bar'
      },
      series: [
        {
          name: 'follower',
          data: categories.map(() => Math.floor(Math.random() * 100))
        }
      ],
      xaxis: {
        categories
      },
      fill: {
        colors: ['#F7B155']
      },
      plotOptions: {
        bar: {
          borderRadius: 10
        }
      }
    };
  </script>
  
    <p>User Chart</p>
  <div class="w-full text-black">
    <div class="w-full" use:chart={sumMonthChart} />
  </div>
  