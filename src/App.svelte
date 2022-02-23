<script>
    import {user} from "./sessionStore"
    import {supabase} from "./superbaseClient"
    import Auth from "./Auth.svelte"
    import Profile from "./Profile.svelte"
    import "./app.css";


    async function signUp() {
        const  {user , error} = await supabase.auth.signUp({
            email: 'example@gmail.com',
        password: 'example password'
        })
    }
    let room =''
    async function addRoom() {
        // Create a new chat room
        const newRoom = await supabase
        .from('rooms')
        .insert({ name: room, size: 'big' })
    }
    function getRooms() {
        // Get public rooms and their messages
    return supabase
        .from('rooms')
        .select(`
        name,
        size
        `)

}

  
</script>

{#await getRooms()} Loading....
{:then response}
<pre>{JSON.stringify(response,null,2)}</pre>

{/await}

<input bind:value={room}>
<button on:click={addRoom}>Add Room</button>

<button on:click={signUp}> Sign up</button>

<h1 class="text-sky-400 bg-blue-500 font-bold underline">
    Hello world!
  </h1>