<script>

    let usernameInput = '';
	let emailInput = '';
	let passwordInput = '';
    let bodInput = '';

    const addUser = async () => {
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer " + localStorage.getItem('accessToken'));

        var raw = JSON.stringify({
            "email": emailInput,
            "username": usernameInput,
            "password": passwordInput,
            "role": ["reader"],
            "createdDate": new Date(),
            "birthDate": new Date(bodInput)
        });

        var requestOptions = {
            method: 'POST',
            headers: myHeaders,
            body: raw,
            redirect: 'follow'
        };

        fetch("http://localhost:8082/user-service/users", requestOptions)
        .then(response => response.text())
        .then(result => console.log("Add User Successfully: ", result))
        .catch(error => console.log("Add User Error: ", error));

    }
    
    let myNotBindDate = (new Date()).toJSON().slice(0, 10);
	let myBindDate = (new Date()).toJSON().slice(0, 10);
	// $:console.log(myBindDate)

    let inputType = 'text';
    let placeholderText = 'Date';

    function switchToDatePicker() {
        inputType = 'date';
        placeholderText = 'DD/MM/YYYY';
    }

</script>

<div class="flex justify-center text-center items-center h-[95%] p-2">
    <form class="flex flex-col space-y-5 w-10/12" action="/">
        <h1 class="flex text-2xl mt-6 text-white font-bold">
            Sign Up
        </h1>
        
        <input class="shadow appearance-none border bg-transparent border-[#B4B4B4] rounded-3xl w-full p-3 text-[#B4B4B4] text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
        id="emailInput" bind:value={emailInput}
        name="email" 
        placeholder="Email"
        required
        type="email"
        
        />
        <input class="shadow appearance-none border bg-transparent border-[#B4B4B4] rounded-3xl w-full p-3 text-[#B4B4B4] text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
        id="passwordInput" bind:value={passwordInput}
        name="password"
        placeholder="Password"
        type="password"
        required
        />
        <input class="shadow appearance-none border bg-transparent border-[#B4B4B4] rounded-3xl w-full p-3 text-[#B4B4B4] text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
        name="comfirmPassword"
        placeholder="Confirm Password"
        type="password"
        required
        />
        <input class="shadow appearance-none border bg-transparent border-[#B4B4B4] rounded-3xl w-full p-3 text-[#B4B4B4] text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
        id="usernameInput" bind:value={usernameInput}
        name="username"
        placeholder="Username"
        type="text"
        required
        />

        <input class="dark:[color-scheme:dark] shadow appearance-none border bg-transparent border-[#B4B4B4] rounded-3xl w-full p-3 text-[#B4B4B4] text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
        id="bodInput" bind:value={bodInput}
        type="date"
        placeholder={placeholderText}
        required
        />

    
        <div></div>
        <button class=" text-black bg-[#F7B155] h-10 rounded-3xl font-bold text-sm tracking-wide"
        on:click={addUser}>SIGN UP</button>

    </form>
</div>
<div class="text-center font-medium text-sm mb-5">
    <p class="text-white">
        Already have an account ? 
        <a href="/login" class="ml-auto text-[#F7B155] hover:underline">Log in</a>
    </p>
</div>
