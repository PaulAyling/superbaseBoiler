<script>
    import {supabase} from "../superbaseClient"
    let email, password
    
    async function signUp() {
        console.log('signup running....')
        const { user, session, error } = await supabase.auth.signUp({
            email,
            password,
         })
  if (error) alert(error.message)
  console.log('USER:',user,'SESSION:',session)
}
</script>
<div class="h-screen bg-gradient-to-br from-blue-600 to-indigo-600 flex justify-center items-center w-full">
    <form on:submit|preventDefault={signUp}>
      <div class="bg-white px-10 py-8 rounded-xl w-screen shadow-md max-w-sm">
        <div class="space-y-4">
          <h1 class="text-center text-2xl font-semibold text-gray-600">Register New User</h1>
          <div>
            <label for="email" class="block mb-1 text-gray-600 font-semibold">Email</label>
            <input id ="email" type="text"  bind:value={email} class="bg-indigo-50 px-4 py-2 outline-none rounded-md w-full" />
          </div>
          <div>
            <label for="password" class="block mb-1 text-gray-600 font-semibold">Password</label>
            <input id ="password" type="text"  bind:value={password} class="bg-indigo-50 px-4 py-2 outline-none rounded-md w-full" />
          </div>
        </div>
        <button class="mt-4 w-full bg-gradient-to-tr from-blue-600 to-indigo-600 text-indigo-100 py-2 rounded-md text-lg tracking-wide">Signup</button>
      </div>
    </form>
  </div>