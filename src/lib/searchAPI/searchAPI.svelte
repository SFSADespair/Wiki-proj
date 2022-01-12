<script>
    let id;
    let artSearch;
    
    
</script>

<div class="container div_content">
    <div class="column">
        <form action="/articles/article/{artSearch}" method="get">
            <input type="text" placeholder="Search" name="inpSearch" bind:value="{artSearch}" />
            <!-- {artSearch.toUpperCase()} -->
            <button type="submit" class="btn btn-success">Search</button>
        </form>
    </div>
</div>

<style>

</style>