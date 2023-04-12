<script>
    import {createEventDispatcher} from 'svelte'
    const dispatch = createEventDispatcher();
    let title = '';
    let rating = 1;
    let description ='';
    const updateMoveTitle = (e) => {       //accept the event from on:keyup
        title = e.target.value;       //retrieve the current value of an input field with the id or name of "title" when an input change event is triggered
    }
    
    const onRatingSelect = (e) =>{
        rating = e.target.value;
    }

    const SubmitMovie = () =>{
        if(title && description){  //some how user entered sum in DOM
            dispatch('submitMovie',{
                movie:{
                    title,
                    rating,
                    description,
                }
            });
            title='';
            rating =1;
            description='';
        }
    }
    const updateDescription = (e) =>{
        description = e.target.value;
    };


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
    <input
    placeholder="Description"
    value={description}
    on:keyup={updateDescription}
    />
    <button style="  margin-left: 10px;" disabled={!title} on:click={SubmitMovie}>Submit</button>
  
</div>



<style>
.main{
    width: 100%;
    display:flex;
    
}
.main input{
    flex:1;
    padding:5px;
    margin-left: 10px;
}
.main select{
    width: 75%;
    margin-left: 10px;
    padding:10px;
    
}

</style>