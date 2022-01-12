<script context="module">
    export async function load({ page, fetch, session, context }) {
        return { 
            props: {
                slug: page.params.slug
            }
        }
    }
</script>

<script>
    import { onMount } from 'svelte';
    import { each } from 'svelte/internal';

    let fArticle = [];

    onMount(async () => {
        const response = await fetch('https://restfulwiki-api.herokuapp.com/articles');
        const data = await response.json();
        fArticle = data;
    })

    export let slug;
</script>

<section class="result">
    {#each fArticle as article}
        {#if slug == article._id || slug == article.title}
            <div class="container articles">
                <h1>{article.title}</h1>
                <p>{article.content}</p>
                <a href="/edit_article/{article._id}" class="btn btn-dark editMe">Edit this article</a>
            </div>
        {/if}
    {/each}
</section>

<style>
    .articles {
        margin-top: 100px;
        text-align: center;
    }

    h1 {
        font-size: 50px;
        font-weight: bold;
        margin-bottom: 50px;
    }

    p {
        font-size: 25px;
        font-weight: bold;
        margin-bottom: 50px;
    }

    .editMe {
        margin-top: 50px;
        margin-bottom: 50px;
        /* position: absolute;
        right: 900px;   */
    }
</style>