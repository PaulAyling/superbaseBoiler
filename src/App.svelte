<script>
    import {user} from "./sessionStore"
    import {supabase} from "./superbaseClient"
    import Auth from "./Auth.svelte"
    import Profile from "./Profile.svelte"

    async function signUp() {
        const  {user , error} = await supabase.auth.signUp({
            email: 'example@gmail.com',
        password: 'example password'
        })
    }
</script>
<button on:click={signUp}> Sign up</button>

