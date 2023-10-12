<script>
	const summarys = [
		{
			number: '01',
			name: 'Written',
			sum: 0
		},
		{
			number: '02',
			name: 'Report',
			sum: 0
		},
		{
			number: '03',
			name: 'Withdraw',
			sum: 0
		},
		{
			number: '04',
			name: 'Writer',
			sum: 0
		}
	];
</script>

<div class="box-border border-2 rounded border-[#292932]">
	<p class="text-2xl text-[#696974] px-5 pt-2">Summary</p>
	{#each summarys as summary}
		<div class="flex flex-row box-border rounded-lg bg-[#292932] p-4 m-5">
			<div class="flex flex-row">
				<div class="box-border rounded text-black font-bold px-2 py-1 bg-[#F7B155]">{summary.number}</div>
				<p class="text-1xl px-3 pt-1">{summary.name}</p>
			</div>
			<div class="basis-3/4" />
			<div class="basis-1/4 pt-1">
				<div
					class="box-border rounded-xl font-bold px-5 border-[#F7B155] border-2 text-[#F7B155] text-justify"
				>
					{summary.sum}
				</div>
			</div>
		</div>
    {/each}
</div>
