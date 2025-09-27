<script lang="ts">
    let mode = $state<'login' | 'register'>('register')
</script>

<section class="border flex flex-col justify-center items-center">
   {#if mode === 'login'}
   <h2>Create an account</h2>
   <p>Join to track your daily mood and sleep with ease.</p>
   <form>
    <label for="email">Email address</label>
    <input id="email" placeholder="name@mail.com"/>
    <label for="password">Password</label>
    <input id="password"/> 
    <button>Sign up</button>
    <p>Already got an account? <button onclick={() => mode = 'register'}>Log in</button></p>
   </form>

   {:else}
   <h2>Welcome back!</h2>
   <p>Log in to continue tracking your mood and sleep.</p>
   <form>
    <label for="email">Email address</label>
    <input id="email" placeholder="name@mail.com"/>
    <label for="password">Password</label>
    <input id="password"/> 
    <button>Sign in</button>
    <p>Haven't got an account? <button onclick={() => mode = 'login'}>Sign up</button></p>
   </form>
   {/if}
</section>