<script>
	import IncomeHistory from "./IncomeHistory.svelte";
	import WithdrawHistory from "./WithdrawHistory.svelte";

    const tabs = [
		{
			name: 'Income',
            component: IncomeHistory
		},
        {
			name: 'Withdraw',
            component: WithdrawHistory
		},
	];

    let activeTab = tabs[0]

    // function toTop() {
    //     window.scrollTo({ top: 0, behavior: "smooth" });
    // }

</script>
<div class="sticky top-[150px] pt-5 pb-0.5 bg-[#161218]"> 
    <div class="flex flex-row h-9 mx-6 mb-5 rounded-lg bg-[#373739]">
        {#each tabs as tab}
            <button
                on:click={() => {
                    activeTab = tab;
                    // toTop();
                }}
                class="w-1/2 rounded-lg flex items-center justify-center {activeTab.name === tab.name ? 'border-2 border-[#F7B155]' : ''}"
            >
                <p class="text-md {activeTab.name === tab.name ? 'text-[#F7B155]' : 'text-[#F1F2F450]'} ">{tab.name}</p>
            </button>
        {/each}
    </div>
</div>

<svelte:component this={activeTab.component} />