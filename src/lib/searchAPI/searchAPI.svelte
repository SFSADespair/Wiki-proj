<script>
    let id;
    let artSearch;
    
    import Fa from 'svelte-fa'
    import { faSearch } from '@fortawesome/free-solid-svg-icons'
</script>

<div class="container div_content">
    <div class="column">
        <form action="/articles/article/{artSearch}" method="get">
            <input type="text" placeholder="Search" name="inpSearch" bind:value="{artSearch}" />
            <!-- {artSearch.toUpperCase()} -->
            <button type="submit" class="btn btn-success"><Fa icon={faSearch} size="md" /></button>
        </form>
    </div>
</div>

<style>

</style>