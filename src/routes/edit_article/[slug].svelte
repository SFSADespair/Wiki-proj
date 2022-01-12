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
    import { createEventDispatcher} from 'svelte'
    import { onMount } from 'svelte';
    import { each } from 'svelte/internal';

    let dispatch = createEventDispatcher()
    let put = {
        content: ''
    }

    export let slug;

    const url = 'https://restfulwiki-api.herokuapp.com/articles/' + slug

    const onSubmit = () => {
        console.log(put)
        dispatch('put')
        fetch(url, {
            method: 'PUT',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(put)
        })
        .then(response => response.json())
            .then(data => {
                console.log(data)
            })
            .catch(error => console.error(error))
    };
    

</script>

<section>
    <div class="patch-article container" align="center">
        <div class="row">
            <div class="card" align="center">
                <div class="card-body">
                    <div class="form">
                        <span><i>Edit the article here</i></span>

                            <label for="content">Content:</label>
                            <div class="input container">
                                <textarea name="content" id="" cols="50" rows="10" bind:value="{put.content}"></textarea>
                            </div>
                            <div class="butt">
                                <button type="submit" class="btn btn-primary"><a href="/articles" type="button" class="btn btn-primary" on:click="{onSubmit}">Submit</a></button>
                            </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<style>
    .form {
        margin: 20px 20px;
    }

    .card-body {
        padding: 20px;
        align-items: center;
    }

    .patch-article {
        margin: 290px 0 0 0;
    }

    .input {
        margin: 20px 0;
    }

    span {
        font-size: 20px;
        font-weight: bold;
    }

    label {
        font-size: 50px;
        font-weight: bold;
    }

    textarea {
        width: 100%;
        background-color: rgb(58, 58, 58);
        color:rgb(175, 175, 175);
    }

    .card {
        background-color: rgb(116 116 116);
    }
</style>