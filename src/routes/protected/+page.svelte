<script lang="ts">
  import { page } from "$app/stores"
	import { signIn, signOut } from '@auth/sveltekit/client'
</script>

{#if $page.data.session}
<h1>Protected page</h1>
<p>
  This is a protected content. You can access this content because you are
  signed in.
</p>
<p>Session expiry: {$page.data.session?.expires}</p>

<button on:click={() => signOut()}>Sign out</button>
{:else}
<h1>Access Denied</h1>
<p>
  <button type="button" on:click={() => signIn('github')}>Sign in with GitHub</button>
</p>
{/if}
