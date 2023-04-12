
<script>
    import {createEventDispatcher} from 'svelte'
    const dispatch = createEventDispatcher();
    let searchTerm ='';
   
    const search = (e) => {
        searchTerm = e.target.value;

        if(searchTerm){
            dispatch('search', {
                searchTerm,
            });
        }else{
            dispatch('clearSearch', {});
        }
    }
</script>




<input
placeholder="Search"
value={searchTerm}
on:keyup={search}
/>

<style>
    input{
        width:100%;
        margin-bottom: 10px;
        height:30px;
    }
</style>