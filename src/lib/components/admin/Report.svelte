<script>
	import Comment from './../feed/Comment.svelte';
	import { onMount } from 'svelte';
	import axios from 'axios';

	let ReportComment = [];
	const getReportComment = async () => {
		try {
			const resR = await axios.get(`http://localhost:8082/report-service/getReport`);
			const resC = await axios.get(`http://localhost:8082/comment-service/getComment`);
			// ReportComment = resR.data;
			// CommentsId = resC.data;
			for (const reportcomment of resR.data) {
				for (const Comment of resC.data) {
					// console.log('reportcomment ', reportcomment.reportTargetId);
					// console.log('Comment ', Comment.commentId);
					if(reportcomment.reportTargetId === Comment.commentId)
					// console.log('reportcomment', Comment);
					ReportComment.push(Comment);
				}
			}
			console.log('ReportComment ', ReportComment);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};
	onMount(() => {
		getReportComment();
	});

	const reportdata = [
		{
			image:
				'https://img.lovepik.com/free-png/20211201/lovepik-basketball-png-image_401244406_wh1200.png', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimEIEI',
			Text: 'Proident sunt aliquip deserunt quis elit ex.',
			date: '3 June 2024'
		},
		{
			image: 'https://i.pinimg.com/736x/fc/40/a8/fc40a8296427427a88b4bc682f6f7325.jpg', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimKIKI',
			Text: 'Aliquip non pariatur qui et adipisicing consectetur incididunt minim anim.',
			date: '4 June 2024'
		},
		{
			image: 'https://cisalvvf.org/wp-content/uploads/2022/11/dog.jpg', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimJIJI',
			Text: 'Incididunt in aliquip duis aliqua ea veniam mollit eiusmod officia mollit et nostrud.',
			date: '5 June 2024'
		},
		{
			image: 'https://cisalvvf.org/wp-content/uploads/2022/11/dog.jpg', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimJIEI',
			Text: 'Incididunt in aliquip duis aliqua ea veniam mollit eiusmod officia mollit et nostrud.',
			date: '6 June 2024'
		}
	];

	const addApprovereport = async () => {
        try {
            const response = await axios.post(
                'http://localhost:8082/approve-service/approve/report/a202ac35-63e7-47b6-8be1-2a9dd457e201/true'
            );
            console.log('Response from backend:', response.data);
        } catch (error) {
            console.error('Error:', error);
        }
    };
</script>

<!-- {#each ReportComment as comment}
  <div><h1>{comment.commentId}</h1></div>
{/each} -->


{#each reportdata as item (item.username)}
	<div class="p-4 my-4 border-b border-gray-500 flex space-x-6 relative">
		<div class="w-12 h-12 rounded-full overflow-hidden">
			<img src={item.image} alt={item.image} class="object-cover w-full h-full" />
		</div>
		<div class="flex-1">
			<div class="flex items-center justify-between">
				<p class="font-bold text-xl mb-5">{item.username}</p>
				<div class="flex space-x-2 mt-[-20px]">
					<button class="bg-[#C13E3E] text-white px-2 py-[1.5px] rounded-full">Delete</button>
					<button class="bg-[#929292] text-white px-2 py-[1.5px] rounded-full">Decline</button>
				</div>
			</div>
			<p class="text-gray-400 mb-5">{item.Text}</p>
			<p class="text-gray-400">{item.date}</p>
		</div>
	</div>
{/each}
