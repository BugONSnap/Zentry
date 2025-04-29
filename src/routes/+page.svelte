<script>
  import Background from '../lib/Background.svelte';
  import { goto } from '$app/navigation';
  let isLogin = true;
  let email = '';
  let password = '';
  let confirmPassword = '';

  function handleSubmit() {
    // TODO: Add actual authentication logic here
    // This will include:
    // 1. API call to verify credentials
    // 2. Store authentication token
    // 3. Handle errors
    // 4. Validate password match for registration
    
    // For now, just log and redirect
    console.log('Form submitted with:', { email, password, isLogin });
    
    // Navigate to dashboard
    goto('/dashboard');
  }
</script>

<Background />
<div class="min-h-screen flex items-center justify-center bg-gradient-to-b from-indigo-300 via-purple-300 to-pink-300">
  <div class="bg-white/10 backdrop-blur-md p-8 rounded-2xl shadow-lg w-full max-w-md border border-white/20">
    <div class="flex mb-8 gap-4">
      <div class="flex w-full bg-white/10 rounded-xl p-1">
        <button 
          class="{isLogin ? 'bg-gray-800 text-white' : 'text-gray-800'} px-6 py-2.5 rounded-xl flex-1 transition-all font-medium"
          on:click={() => isLogin = true}>
          Login
        </button>
        <button 
          class="{!isLogin ? 'bg-gray-800 text-white' : 'text-gray-800'} px-6 py-2.5 rounded-xl flex-1 transition-all font-medium"
          on:click={() => isLogin = false}>
          Register
        </button>
      </div>
    </div>

    <form on:submit|preventDefault={handleSubmit} class="space-y-6">
      <div>
        <label for="email" class="block text-sm font-medium text-gray-800 mb-1">Email</label>
        <input
          type="email"
          id="email"
          bind:value={email}
          class="w-full px-3 py-2 bg-white/10 border-none rounded-xl focus:outline-none focus:ring-2 focus:ring-white/50 placeholder-gray-500 text-gray-800"
          placeholder="Enter your email"
          required
        />
      </div>

      <div>
        <label for="password" class="block text-sm font-medium text-gray-800 mb-1">Password</label>
        <input
          type="password"
          id="password"
          bind:value={password}
          class="w-full px-3 py-2 bg-white/10 border-none rounded-xl focus:outline-none focus:ring-2 focus:ring-white/50 placeholder-gray-500 text-gray-800"
          placeholder="Enter your password"
          required
        />
      </div>

      {#if !isLogin}
        <div>
          <label for="confirmPassword" class="block text-sm font-medium text-gray-800 mb-1">Confirm Password</label>
          <input
            type="password"
            id="confirmPassword"
            bind:value={confirmPassword}
            class="w-full px-3 py-2 bg-white/10 border-none rounded-xl focus:outline-none focus:ring-2 focus:ring-white/50 placeholder-gray-500 text-gray-800"
            placeholder="Confirm your password"
            required
          />
        </div>
      {/if}

      <button
        type="submit"
        class="w-full bg-gray-800 text-white py-2.5 px-4 rounded-xl hover:bg-gray-700 transition-colors">
        {isLogin ? 'Login' : 'Register'}
      </button>

      {#if isLogin}
        <div class="text-center text-sm space-y-2">
          <p class="text-gray-800">Don't have an account? 
            <button 
              type="button"
              class="text-gray-800 hover:underline font-medium"
              on:click={() => isLogin = false}>
              Sign Up
            </button>
          </p>
          <button type="button" class="text-gray-800 hover:underline">Forgot Password?</button>
        </div>
      {:else}
        <div class="text-center text-sm space-y-2">
          <p class="text-gray-800">Already have an account? 
            <button 
              type="button"
              class="text-gray-800 hover:underline font-medium"
              on:click={() => isLogin = true}>
              Login
            </button>
          </p>
        </div>
      {/if}
    </form>
  </div>
</div>