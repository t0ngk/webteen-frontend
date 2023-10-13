<script>
	let isActive = false;
	export let selectedStatus = ""; 

	function toggleDropdown(status) {
		isActive = !isActive;
		selectedStatus = status; 
	}
</script>

<style>
	.dropdownMenu {
		position: absolute;
		z-index: 10;
		background-color: #161218; /* พื้นหลังสีดำ */
		border: 1px solid #F7B155; /* ขอบสี #F7B155 */
		opacity: 1;
	}

	.dropdownMenu ul li a {
		color: #F7B155; /* ตัวอักษรสี #F7B155 */
	}

	.dropdownMenu ul li a:hover {
		background-color: #F7B155; /* เปลี่ยนสีพื้นหลังเมื่อ hover */
		color: #000000; /* เปลี่ยนสีตัวอักษรเมื่อ hover */
	}
</style>

<button
	id="dropdownDefaultButton"
	class="text-black bg-[#F7B155] font-medium rounded-full text-sm px-3 py-1 text-center inline-flex items-center dropdownButton"
	on:click="{toggleDropdown}"
	class:selected="{isActive}"
	on:selectedStatusChange="{selectedStatus}"
>
	All
	<svg
		class="w-2.5 h-2.5 ml-2.5"
		aria-hidden="true"
		xmlns="http://www.w3.org/2000/svg"
		fill="none"
		viewBox="0 0 10 6"
	>
		<path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 1 4 4 4-4"/>
	</svg>
</button>

{#if isActive}
  <div
      id="dropdown"
      class="z-10 bg-white divide-y divide-gray-100 rounded-lg shadow w-44 dark:bg-gray-700 dropdownMenu"
  >
      <ul class="py-2 text-sm text-black" aria-labelledby="dropdownDefaultButton">
          <li>
            <a href="FilteredData" class="block px-4 py-2 hover:bg-[#F7B155]  dark:hover:text-black" on:click="{(e) => toggleDropdown('Approve')}">Approve</a>
          </li>
          <li>
            <a href="FilteredData" class="block px-4 py-2 hover:bg-[#F7B155]  dark:hover:text-black" on:click="{(e) => toggleDropdown('Decline')}">Decline</a>
          </li>
          <li>
            <a href="FilteredData" class="block px-4 py-2 hover:bg-[#F7B155]  dark:hover:text-black" on:click="{(e) => toggleDropdown('Waiting')}">Waiting</a>
          </li>
      </ul>
  </div>
{/if}
