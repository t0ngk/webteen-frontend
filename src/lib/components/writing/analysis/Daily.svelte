<script>
  import { chart } from 'svelte-apexcharts?client';

  let categories = ['sun', 'mon', 'tue', 'wed', 'thu', 'fri', 'sat']

  let incomeChart = {
    chart: {
      type: 'bar'
    },
    series: [
      {
        name: 'sales',
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

  let viewChart = {
    chart: {
      type: 'bar'
    },
    series: [
      {
        name: 'view',
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

  let followerChart = {
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

<div class="w-10/12 text-black">
  <div class="w-full" use:chart={incomeChart} />
</div>
  <p>Income Chart</p>
<div class="w-10/12 text-black">
  <div class="w-full" use:chart={viewChart} />
</div>
  <p>View Chart</p>
<div class="w-10/12 text-black">
  <div class="w-full" use:chart={followerChart} />
</div>
  <p>Follower Chart</p>
