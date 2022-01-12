<script>

    import { createEventDispatcher} from 'svelte'
    
    let dispatch = createEventDispatcher();
    let opp = {
        title: '',
        content: ''
    };
    
    const url = 'https://restfulwiki-api.herokuapp.com/articles';
    
    // send POST request
    const submitHandler = () => {
        console.log(opp)
        dispatch('add')

        fetch(url, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(opp)
        })
            .then(response => response.json())
            .then(data => {
                console.log(data)
            })
            .catch(error => console.error(error))
    };

</script>

<div class="container">
    <div class="row">
        <div class="col-lg-12"> 
            <form on:submit={submitHandler} action="/articles" method="post">
                <div class="inp">
                    <label for="title">Title</label>
                    <div class="column inp">
                        <input type="text" class="input" name="title" bind:value="{opp.title}">
                    </div>
                </div>
                <div class="inp">
                    <label for="title">Content</label>
                    <div class="column">
                        <input type="text" class="input" name="content" bind:value="{opp.content}">
                    </div>
                </div>
                <div class="container btnAdd"  align="center">
                    <div class="row col-lg-6">
                        <button type="submit" class="btn btn-success">Post</button>
                    </div>
                </div>
            </form>
        </div>
    </div>
</div>

<style>
    .container {
        align-items: center;
    }

    .inp {
        justify-content: center;
        align-items: center;
        margin-bottom: 35px;
    }

    label {
        display: block;
        margin-bottom: 10px;
    }

</style>