<script>
   import axios from 'axios';
    const cvwriten = [
      {
        image: 'https://resizing.flixster.com/MKm9U3QTNzsng_PbR0PC1nTYcSA=/206x305/v2/https://flxt.tmsimg.com/assets/p15630144_e_v8_aa.jpg', // เพิ่ม path ของรูปภาพที่นี้
        username: 'Punimmiki',
        pseudonym : 'ProPunim',
        firstName : 'Numnual',
        lastName: 'Makhai',
        id_Card: 10293939393939,
        status: 'Waiting',
        card_photo:'https://lifestyle.campus-star.com/app/uploads/2017/03/id-cover.jpg',
        bank:'Kbank',
        bank_account_number : 234242342342342
      }
      
    ];

    const addApprovewriter = async () => {
        try {
            const response = await axios.post(
                'http://localhost:8082/approve-service/approve/writer/b862595f-3ff3-420e-9ec6-fc65d7547059/true',
            );
            console.log('Response from backend:', response.data);
        } catch (error) {
            console.error('Error:', error);
        }
    };
  </script>

{#each cvwriten as item (item.username)}
  <div class="flex flex-col items-center justify-center  p-6">
    <div class="rounded-full w-[150px] h-[150px] overflow-hidden mb-4">
      <img src={item.image} alt={item.image} class="object-cover w-full h-full" />
    </div>
    <p class="text-xl font-bold mb-2">{item.username}</p>
    <div class="flex flex-col items-start mb-4">
      <div class="flex items-center mb-2 mt-10">
        <p class="text-[#F7B155] mr-2">Pseudonym:</p>
        <p>{item.pseudonym}</p>
      </div>
      <div class="border-b border-gray-500 w-full mb-2"></div>
      <div class="flex items-center mb-2 mt-5">
        <p class="text-[#F7B155] mr-2">FirstName:</p>
        <p>{item.firstName}</p>
      </div>
      <div class="border-b border-gray-500 w-full mb-2"></div>
      <div class="flex items-center mb-2 mt-5">
        <p class="text-[#F7B155] mr-2">LastName:</p>
        <p>{item.lastName}</p>
      </div>
      <div class="border-b border-gray-500 w-full mb-2"></div>
      <div class="flex items-center mb-2 mt-5">
        <p class="text-[#F7B155] mr-2">ID Card:</p>
        <p>{item.id_Card}</p>
      </div>
      <div class="border-b border-gray-500 w-full mb-2 "></div>
      <div class="w-[350px] h-[200px] rounded-lg overflow-hidden mt-5">
        <img src={item.card_photo} alt={item.card_photo} class="object-cover w-full h-full" />
      </div>
      <div class="border-b border-gray-500 w-full mb-2"></div>
      <div class="flex items-center mb-2 mt-5">
        <p class="text-[#F7B155] mr-2">Bank:</p>
        <p>{item.bank}</p>
      </div>
      <div class="border-b border-gray-500 w-full mb-2"></div>
      <div class="flex items-center mb-2 mt-5">
        <p class="text-[#F7B155] mr-2">Bank Account Number:</p>
        <p>{item.bank_account_number}</p>
      </div>
      <div class="border-b border-gray-500 w-full mb-2"></div>
    </div>
    <div class="flex space-x-6 mt-10">
        <button on:click={addApprovewriter} class="flex-1 bg-[#38920D] text-white px-4 py-2 rounded-full">Approve</button>
        <button class="flex-1 bg-[#C13E3E] text-white px-4 py-2 rounded-full">Decline</button>
      </div>
      
  </div>
{/each}
