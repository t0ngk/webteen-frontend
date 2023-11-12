<script>
	import Icon from '@iconify/svelte';
	export let RecommendBooks;
</script>

{#each RecommendBooks as book}
	<a href="/category/detailBook/{book.bookId}">
		<div class="flex flex-row p-2 py-3 bg-transparent h-28 mb-3">
			<div class="flex flex-wrap justify-center max-h-2">
				<img src={book.cover} alt="" class="rounded-[10%] w-28 h-28 object-cover" />
			</div>
			<div class=" pl-5 flex flex-col justify-center w-auto h-28">
				<p class=" text-[#818181]" style="font-size: 12px;">
					{book.type}
				</p>
				<div class="w-56">
					<div class="text-white text-sm font-semibold">{book.title}</div>
					<p class="text-white line-clamp-2 mt-1" style="font-size: 12px;">
						Lorem ipsum dolor sit amet consectetur adipisicing elit. Reiciendis voluptate neque
						quae, dolorum corrupti ex voluptas deserunt est tempora, temporibus id? Repellendus
						consequatur, nihil neque eos aliquam officia maiores totam?
					</p>
				</div>
				<div class="flex flex-col mt-2">
					<div class="flex">
						<div class="flex">
							<Icon icon="tabler:list" color="#818181" class="mt-[2%] mr-1 text-[14px]" />
							<p class="text-[#818181] text-xs">{book.chapter}</p>
						</div>
						<div class="flex ml-2">
							<Icon icon="mdi:eye" color="#818181" class="mt-[4%] mr-1 text-[12px]" />
							<p class="text-[#818181] text-xs">
								{book.view >= 1000 ? book.view / 1000 + 'K' : book.view}
							</p>
						</div>
						<div class="flex ml-2">
							<Icon icon="ph:heart-bold" color="#818181" class="mt-[5%] mr-1 text-[12px]" />
							<p class="text-[#818181] text-xs">
								{book.like >= 1000 ? book.like / 1000 + 'K' : book.like}
							</p>
						</div>
					</div>
				</div>
			</div>
		</div>
	</a>
{/each}
