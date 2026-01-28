<script>
    import { page } from '$app/state';
</script>
 
{#if page.error}
    {#if page.error.message === 'Not Found'}
        <div>
            <h2 class="subtitle">Page Not Found</h2>
            <h3 class="text-2xl">The page you’re looking for doesn’t exist or has been moved.</h3>
        </div>
    {:else}
        <div>
            <h2 class="subtitle">Oops! Something went wrong</h2>
        </div>
    {/if}
{/if}