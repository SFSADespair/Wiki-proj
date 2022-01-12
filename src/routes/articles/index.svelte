<script>
    import { onMount } from 'svelte';
    import { each } from 'svelte/internal';
    import { store } from '$lib/store';

    let articles = [];
    onMount(async () => {
        const response = await fetch('https://restfulwiki-api.herokuapp.com/articles');
        const data = await response.json();
        articles = data;
    })

    $store = articles._id;

</script>

<div class="container">
    {#each articles as article}
        <a href="/articles/article/{article._id}" id="{article._id}">
             {article.title}
            <hr>
        </a>
        {:else}
            <p><b><i>Loading...</i></b></p>
    {/each}
</div>

<style>
    a {
        text-decoration: none;
        color: rgb(223, 209, 209);
        font-weight: bold;
        font-size: 1.5rem;
    }

    a::hover {
        text-decoration: underline;
    }

    div {
        margin-top: 90px;
        text-align: center;
    }
</style>