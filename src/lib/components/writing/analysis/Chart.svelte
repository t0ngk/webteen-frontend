<script>
  import { chart } from 'svelte-apexcharts?client';
  export let options;
</script>

<div class="w-full" use:chart={options} />
