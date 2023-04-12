<script>
    import {createEventDispatcher} from 'svelte'
    const dispatch = createEventDispatcher();
    let title = '';
    let rating = 1;
    
    const updateMoveTitle = (e) => {       //accept the event from on:keyup
        title = e.target.value;       //retrieve the current value of an input field with the id or name of "title" when an input change event is triggered
    }
    
    const onRatingSelect = (e) =>{
        rating = e.target.value;
    }

    const SubmitMovie = () =>{
        if(title){  //some how user entered sum in DOM
            dispatch('submitMovie',{
                movie:{
                    title,
                    rating,
                }
            });
            title='';
            rating =1;
        }
    }
</script>

<div class="main">
    <input 
    placeholder="Move Title" 
    type='text'
    value={title}
    on:keyup={updateMoveTitle}     
    />
    
    
    <select value={rating} on:change={onRatingSelect}>
        <option value={1}>1</option>
        <option value={2}>2</option>
        <option value={3}>3</option>
        <option value={4}>4</option>
        <option value={5}>5</option>
    </select>
    <button disabled={!title} on:click={SubmitMovie}>Submit</button>

</div>



<style>
.main{
    width: 100%;
    display:flex;

}
.main input{
    flex:1;
}
.main select{
    width: 75%;
    margin-left: 10px;
    margin-right:10px;
}

</style>