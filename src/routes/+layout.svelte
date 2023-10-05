<script>
	import Tabbar from '$lib/components/Tabbar.svelte';
	import '../app.postcss';
	import { page } from '$app/stores';
</script>

<div class="flex flex-col w-full h-[100dvh] bg-[#161218] text-white">
	<div class="flex-1 overflow-y-auto">
		<slot />
	</div>
	<Tabbar urlPath={$page.url.pathname}/>
</div>
